# Core Deposit Circuit

The core deposit circuit is what most users interact with, proving that a user has created a commitment representing the deposit of some corresponding asset denomination, that they haven't yet withdrawn that asset, and that they know the secret that they supplied when generating the initial commitment.

## Making a Deposit

A deposit into Tornado.cash is a very simple operation, which doesn't actually involve any ZK proofs. At least not yet. To make a deposit, you invoke the `deposit` method of a [Tornado contract](https://github.com/tornadocash/tornado-core/blob/master/contracts/Tornado.sol) instance, supplying a [Pedersen Commitment](https://crypto.stackexchange.com/questions/64437/what-is-a-pedersen-commitment), along with the asset denomination that you're depositing. This commitment is inserted into a specialized [Merkle Tree](https://en.wikipedia.org/wiki/Merkle_tree), where the structure of the Merkle Tree is aligned to an elliptic curve associated with a prime in the order of the BN128 elliptic curve, and the labels of the tree are computed using MiMC hashing.

### Commitment Scheme

When you make a "commitment" in the context of cryptography, what you're doing is taking a secret value - often large and random - and running it through some cryptographic function (e.g. a hash function), then disclosing the result. Later, when you need to make good on the commitment, you prove that you know the original secret value.

This is known as a [commitment scheme](https://en.wikipedia.org/wiki/Commitment_scheme).

### Pedersen Hash

A [Pedersen Hash](https://iden3-docs.readthedocs.io/en/latest/iden3\_repos/research/publications/zkproof-standards-workshop-2/pedersen-hash/pedersen.html) is an extremely specialized hashing function that is particularly well-suited for use in applications leveraging Zero Knowledge proving circuits. Where other hashing functions like SHA-256 are designed to exhibit properties such as producing very different outputs for even slightly different inputs (the [avalanche effect](https://en.wikipedia.org/wiki/Avalanche_effect)), Pedersen hashing instead prioritizes the ability to compute the hash extremely efficiently in Zero Knowledge circuits.

Hashing a message with Pedersen compresses the bits of the message down to a point along an [elliptic curve](https://en.wikipedia.org/wiki/Elliptic-curve_cryptography) called [Baby Jubjub](https://github.com/barryWhiteHat/baby_jubjub). Baby Jubjub is in the order of the BN128 elliptic curve that is supported by precompiled operations on the Ethereum network which were added in [EIP-196](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-196.md). This means that operations that use the Baby Jubjub curve, such as Pedersen Hashing, are highly gas-efficient.

When you compute the Pedersen hash of a message, the resulting point along the its elliptic curve is very efficient to verify, but infeasible to reverse back into the original message.

### Tornado Commitment

To generate a commitment for a Tornado.cash deposit, you first generate two large random integers, each 31 bytes in length. The first value is a nullifier that you will later disclose in order to withdraw your deposit, and the second is a secret that secures the confidential relationship between your deposit and withdrawal.

The preimage of your deposit note is the concatenation of these two values (`nullifier` + `secret`), resulting in a message 62 bytes in length. This message is Pedersen hashed, resulting in an output representing an element of the Baby Jubjub elliptic curve encoded as a 32-byte big-endian integer.

If you want to see this in code form, you can reference the [tornado-cli deposit function](https://github.com/tornadocash/tornado-cli/blob/master/cli.js#L53-L112).

### MiMC Merkle Tree

The [Tornado contract](https://github.com/tornadocash/tornado-core/blob/master/contracts/Tornado.sol) is a specialized [Merkle Tree](https://en.wikipedia.org/wiki/Merkle_tree) which labels its nodes using MiMC hashes.

For those not familiar with Merkle Trees, they are binary trees where each non-leaf node is labelled with the hash of the labels of its child nodes, and the leaf nodes are labelled with the hash of their data. Ordinarily, Merkle Trees use a one-way cryptographic hashing function like SHA-2, but in this case, we're using MiMC, which has some useful properties.

One of the useful properties of MiMC is that it's well-suited to operating over prime fields, which is important to us because Zero Knowledge proofs are fundamentally based on prime fields, and Pedersen Hashes are points within a prime field defined by the Baby Jubjub elliptic curve - which is in turn within the order of the BN128 curve supported natively on Ethereum. Because Zero Knowledge proofs are operationally expensive, and each operation in an Ethereum transaction has a corresponding gas cost, the specific types of operations we design around need to be as gas-efficient as possible.

The other particularly useful properties of MiMC are that it's non-parallelizable, and difficult to compute but easy to verify. These properties add to the security of the contract by making it computationally infeasible to calculate a forged "commitment" which has a colliding path within the merkle tree.

### Zero Nodes

During the initialization of the Tornado Merkle Tree, a single path spanning the height of the tree is preallocated starting with a "zero leaf" node with a label of `keccak256("tornado") % FIELD_SIZE`. Each subsequent non-leaf node toward the root is then labelled as if the entire bottom of the tree were populated by that same same leaf node.

The purpose of these "zero nodes" is to ensure that all paths within the merkle tree are invalid until they terminate in a valid commitment.

### Inserting a Commitment

When you insert a commitment into the Tornado contract's merkle tree, you are replacing a "zero leaf" with a new leaf whose label is the MiMC hash of your Pedersen commitment, and then traversing up the tree updating each subsequent parent node with a new label based on the label updates that your new leaf introduces below.

Commitments are inserted from left to right within the tree, with every two commitment insertions filling a "subtree". Each insertion increments the "index" of the tree, determining whether the next commitment will be inserted on the left or right side of the entry to its merkle path.

Once your deposit has updated the tree, the label of the top-most node becomes the tree's new "root", and is added to a rolling history containing the labels of the last 100 roots, for later use in processing withdrawal transactions.

The Tornado.cash deposit contracts are deployed with 20 "levels", with each level increasing the number of potential leaves by a power of 2. That means that the contract's merkle tree supports up to 2^20 leaves, allowing for up to 1,048,576 deposits to be made into the contract before it needs to be replaced.

The reason behind this seemingly-low number of levels is that every deposit has to perform as many updates to the tree as there are levels. A tree with more levels would require more gas per deposit, as well as correspondingly larger proof sizes when withdrawing notes.

## Making a Withdrawal

Having made a deposit, you now have a set of truth claims that you can generate a proof based upon. Generally speaking, Zero Knowledge proofs are anchored to some value(s) known by both the prover and the verifier, to which a relationship is going to be proven to a set of values known only by the prover. The circuit verifier can confirm that the prover has used the value(s) that are known, and that the proof that they computed satisfies the constraints imposed by the circuit.

### Inputs to a Withdrawal Proof

In the case of Tornado.cash deposits, the prover (the person submitting a withdrawal transaction), and the verifier (the deposit contract's withdrawal method) both know a recent merkle root. The prover also supplies a set of other public inputs that they used for the generation of their proof.

#### The total set of public inputs for a withdrawal proof are:

1. A recent merkle root
2. The Pedersen hash of the nullifier component from their deposit commitment
3. The address of the recipient of their withdrawal
4. The address of the relayer that they've selected (or their own address)
5. The fee that they're paying the relayer (or zero)
6. The refund that they're paying the relayer (or zero)

#### The additional private inputs for a withdrawal proof are:

1. The nullifier component from their deposit commitment
2. The secret component from their deposit commitment
3. The set of node labels that exist in the path between the root and the leaf nodes of the merkle tree
4. An array of `0/1` values indicating whether each specified path element is on the left or right side of its parent node

### Proven Claims

It would be easy to miss the clever new piece of knowledge we created when we constructed and inserted our commitment into the merkle tree. You might be inclined to think that to make a withdrawal, we're simply going to prove that we know the components of the Pedersen commitment, and that the merkle tree is just an efficient way to store those commitment hashes.

What's special about this construction is that it enables us to prove not just that we know the components of a deposited commitment, but rather it enables us to prove simply that we **know the path to a commitment within the tree**, and **how to get there** starting with a commitment preimage.

If we were only to prove that we knew the preimage to a deposited hash, we would risk revealing which commitment is ours. Instead, we're not disclosing the commitment preimage, but instead we're simply proving that we have knowledge of a preimage to a commitment within the tree. Which commitment is ours remains completely indistinguishable on the withdrawal side of the circuit protocol.

### Computing the Witness

**Nullifier Hash Check**

In order to compute the witness for the withdrawal proof, our circuit first takes the private deposit commitment inputs (`nullifier` + `secret`), and runs them through a circuit component which simultaneously computes the Pedersen hash of the full commitment message, and the Pedersen hash of the nullifier alone. The circuit then compares the resulting nullifier hash to the one you supplied as a public input, and asserts their equality.

**This proves that the nullifier hash that you supplied publicly is in fact a component of your original commitment.**

**Merkle Tree Check**

Next, the circuit takes the commitment hash it has computed, the merkle root you have specified publicly, and the path elements and left/right selectors that you specified privately, as inputs to a component which checks your merkle tree path claim.

The Merkle Tree Checker starts from the bottom of the path, inputting your commitment hash and the first element of your proposed path into a Muxer. The Muxer takes a third input, which is an element from your supplied left/right directions. The Muxer component uses these directions to inform an MiMC hashing component as to the order of its inputs. If the supplied direction is 0, then the supplied path element is on the left, and your commitment hash is on the right. If the direction is 1, then the order is reversed.

The MiMC hasher outputs the resulting hash, and the Merkle Tree Checker proceeds to the next level. It repeats the last process, except this time, instead of using your commitment hash, it uses the hash of the last level. It continues to run through each level of the proposed path, until it ends up with a final hash output.

The Merkle Tree Checker compares the hash that it has computed to the public merkle root input that you supplied, and asserts their equality.

**This proves that your commitment exists within some path beneath the specified merkle root.**

**Extra Withdrawal Parameter Check**

Before finishing, the circuit takes each of the remaining four public inputs, and squares them into a public output. While this isn't strictly necessary, it creates a set of constraints within your proof that ensure that your transaction parameters can't be tampered with before your withdrawal transaction is processed. If any of those parameters were to change, your proof would no longer be valid.

### Computing the Proof

Now that we have a witness for our proof, we take those witnessed state values and input them into the R1CS corresponding to the Withdrawal circuit, and run the prover over it. Out of the prover comes two proof artifacts. The first is the proof itself, according to the SNARK protocol we're using, and the second is the set of public inputs and outputs corresponding to that proof.

### Completing a Withdrawal Transaction

With the withdrawal proof now generated, you supply that proof, along with its public inputs, to the `withdraw` method of the deposit contract. This method verifies that:

1. The specified relayer fee does not exceed the value of the denomination of asset being withdrawn
2. The supplied nullifier hash has not been spent before
3. The supplied merkle root is known, using the 100-root historical record
4. The supplied proof is valid

One of the artifacts deployed as a dependency of the deposit contract is a Solidity contract that is generated using the proving key of the Withdrawal circuit as an input. This Verifier contract is an optimized proof verifier with a single public view function, which accepts a proof and the array of six public inputs as `uint256` values.

This function returns `TRUE` if the proof is valid according to the public inputs.

If the above preconditions are met, the supplied nullifier hash is inserted into the set of spent nullifiers, and then the value of the deposit is distributed amongst the recipient and relayer, according to the specified fee parameters.

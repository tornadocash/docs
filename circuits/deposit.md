# Tornado.cash Core Deposit Circuit

The core deposit circuit is what most users interact with, proving that a user has created a commitment representing the
deposit of some corresponding asset denomination, that they haven't yet withdrawn that asset, and that they know the
secret that they supplied when generating the initial commitment.

## Making a Deposit

A deposit into Tornado.cash is a very simple operation, which doesn't actually involve any ZK proofs. At least not yet.
To make a deposit, you invoke the `deposit` method of a [Tornado contract](https://github.com/tornadocash/tornado-core/blob/master/contracts/Tornado.sol)
instance, supplying a [Pedersen Commitment](https://crypto.stackexchange.com/questions/64437/what-is-a-pedersen-commitment),
along with the asset denomination that you're depositing. This commitment is inserted into a specialized
[Merkle Tree](https://en.wikipedia.org/wiki/Merkle_tree), where the structure of the Merkle Tree is aligned to an
elliptic curve associated with a prime in the order of the BN128 elliptic curve, and the labels of the tree are computed
using MiMC hashing.

### Commitment Scheme

When you make a "commitment" in the context of cryptography, what you're doing is taking a secret value - often large
and random - and running it through some cryptographic function (e.g. a hash function), then disclosing the result.
Later, when you need to make good on the commitment, you prove that you know the original secret value.

This is known as a [commitment scheme](https://en.wikipedia.org/wiki/Commitment_scheme).

### Pedersen Hash

A [Pedersen Hash](https://iden3-docs.readthedocs.io/en/latest/iden3_repos/research/publications/zkproof-standards-workshop-2/pedersen-hash/pedersen.html)
is an extremely specialized hashing function that is particularly well-suited for use in applications leveraging
Zero Knowledge proving circuits. Where other hashing functions like SHA-256 are designed to exhibit properties
such as producing very different outputs for even slightly different inputs
(the [avalanche effect]([avalanche effect](https://en.wikipedia.org/wiki/Avalanche_effect))), Pedersen hashing instead
prioritizes the ability to compute the hash extremely efficiently in Zero Knowledge circuits.

Hashing a message with Pedersen compresses the bits of the message down to a point along an
[elliptic curve](https://en.wikipedia.org/wiki/Elliptic-curve_cryptography) called
[Baby Jubjub](https://github.com/barryWhiteHat/baby_jubjub). Baby Jubjub is in the order of the BN128 elliptic curve
that is supported by precompiled operations on the Ethereum network which were added in
[EIP-196](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-196.md). This means that operations that use the
Baby Jubjub curve, such as Pedersen Hashing, are highly gas-efficient.

When you compute the Pedersen hash of a message, the resulting point along the its elliptic curve is very efficient
to verify, but infeasible to reverse back into the original message.

### Tornado Commitment

To generate a commitment for a Tornado.cash deposit, you first generate two large random integers, each 31 bytes in
length. The first value is a nullifier that you will later disclose in order to withdraw your deposit, and the second
is a secret that secures the confidential relationship between your deposit and withdrawal.

The preimage of your deposit note is the concatenation of these two values (`nullifier` + `secret`), resulting in a
message 62 bytes in length. This message is Pedersen hashed, resulting in an output representing an element of the
Baby Jubjub elliptic curve encoded as a 32-byte big-endian integer.

If you want to see this in code form, you can reference the
[tornado-cli deposit function](https://github.com/tornadocash/tornado-cli/blob/master/cli.js#L53-L112).

### MiMC Merkle Tree

The [Tornado contract](https://github.com/tornadocash/tornado-core/blob/master/contracts/Tornado.sol) is a specialized
[Merkle Tree](https://en.wikipedia.org/wiki/Merkle_tree) which labels its nodes using MiMC hashes.

For those not familiar with Merkle Trees, they are binary trees where each non-leaf node is labelled with the hash
of the labels of its child nodes, and the leaf nodes are labelled with the hash of their data. Ordinarily, Merkle Trees
use a one-way cryptographic hashing function like SHA-2, but in this case, we're using MiMC, which has some useful
properties.

One of the useful properties of MiMC is that it's well-suited to operating over prime fields, which is important to us
because Zero Knowlege proofs are fundamentally based on prime fields, and Pedersen Hashes are points within a prime
field defined by the Baby Jubjub elliptic curve - which is in turn within the order of the BN128 curve supported
natively on Ethereum. Because Zero Knowledge proofs are operationally expensive, and each operation in an Ethereum
transaction has a corresponding gas cost, the specific types of operations we design around need to be as gas-efficient
as possible.

The other particularly useful properties of MiMC are that it's non-parallelizable, and difficult to compute but easy to
verify. These properties add to the security of the contract by making it computationally infeasible to calculate a
forged "commitment" which has a colliding path within the merkle tree.

### Inserting a Commitment

When you insert a commitment into the Tornado contract's merkle tree, you are adding a new leaf node whose label is the
MiMC hash of your Pedersen commitment, and then traversing up the tree updating each subsequent parent node with a new
label based on the label updates that your new leaf introduces below.

Once your deposit has updated the tree, the label of the top-most node becomes the tree's new "root", and is added to
a rolling history containing the labels of the last 100 roots, for later use in processing withdrawal transactions.

The Tornado.cash deposit contracts are deployed with 20 "levels", with each level increasing the number of potential
leaves by a power of 2. That means that the contract's merkle tree supports up to 2^20 leaves, allowing for up to
1,048,576 deposits to be made into the contract before it needs to be replaced.

The reason behind this seemingly-low number of levels is that every deposit has to perform as many updates to the tree
as there are levels. A tree with more levels would require more gas per deposit, as well as correspondingly larger
proof sizes when withdrawing notes.

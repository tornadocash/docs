# Anonymity Mining

The anonymity mining protocol underpins the [Anonymity Mining Program](../anonymity-mining.md), which rewards users according to the block duration that they wait before withdrawing their deposits.

## Tornado Trees

Before we get into how rewards are calculated and claimed for anonymity mining, we first need to understand how some important state information is recorded regarding deposits and withdrawal events.

### Tornado Proxy

When accessing the Tornado.cash deposit contracts using the official UI, all transactions execute through a proxy contract called the [Tornado Proxy](https://github.com/tornadocash/tornado-trees/blob/master/contracts/TornadoTrees.sol). Since the deposit contracts themselves are immutable, and many features of Tornado.cash were added well after the original deposit contracts were deployed, the Tornado Proxy provides a way to inject additional functionality without replacing the battle-tested deposit contract instances.

The two most noteworthy functions of the Tornado Proxy are its ability to back up user deposits on-chain using encrypted note accounts, and the function which queues deposits and withdrawals for processing in the Tornado Trees contract.

### Registering Deposits and Withdrawals

When you make a deposit through the Tornado Proxy, and when you later make a withdrawal through the same, the proxy calls corresponding methods on the [Tornado Trees](https://github.com/tornadocash/tornado-trees/blob/master/contracts/TornadoTrees.sol) contract.

Registering a deposit takes the address of the deposit contract `uint160`, the commitment Pedersen hash `bytes32`, and the current block number `uint`, [ABI encodes](https://docs.soliditylang.org/en/v0.8.9/abi-spec.html#abi) them, then produces a `keccak256` (a.k.a. [SHA3-256](https://en.wikipedia.org/wiki/SHA-3)) hash over the resulting message. This hash is inserted into a queue within the contract, to be later batched into the deposit Merkle Tree (not to be confused with the deposit contract).

Registering a withdrawal is the essentially the same as registering a deposit, except instead of using the commitment hash, the nullifier hash of the withdrawal is used instead. The resulting `keccak256` hash is inserted into the withdrawal queue, to be later batched into the withdrawal Merkle Tree.

The `registerDeposit` and `registerWithdrawal` contract methods of the Tornado Trees contract each emit a corresponding event, `DepositData` and `WithdrawalData` containing the same values as were included in the computed hash, plus an additional event field indication the order in which they entered into the queue.

### Chunked Merkle Tree updates in Zero Knowledge

Standard Merkle Trees are fairly expensive to store and update, especially if you want to commit to a large number of leaves. Depositing a note into the Tornado.cash deposit contracts can cost upwards of 1.2M gas, which can be hundreds of dollars worth of ETH if depositing on Ethereum mainnet. Most of this gas cost results from simply inserting a commitment into the deposit contract Merkle Tree.

What if, instead of spending all of that gas, we could instead simply propose a new Merkle Root that we computed off-chain, and prove that it's valid using a Zero Knowledge proof?

However, verifying Zero Knowledge proofs is itself quite expensive. So, instead of updating the Merkle Tree for every change, we can batch insertions together into aggregate commitments which can be verified as a whole.

#### Chunked Tree Structure

The deposit and withdrawal trees are both fixed-size Merkle Trees 20 levels deep, but with a notable feature. The "chunk size" of the tree determines a level at which updates are computed in aggregate, instead of as individual insertions.

In the case of Tornado Trees, the chunk size is 256 (2^8), so each chunk is 8 levels high. The complete tree is still limited to 2^20 leaves, but those leaves are divided into 256-leaf chunks, with a total of 2^12 chunks.

The hash function used to produce node labels is [Poseidon](https://www.poseidon-hash.info), which is similar to the [Pedersen](https://iden3-docs.readthedocs.io/en/latest/iden3\_repos/research/publications/zkproof-standards-workshop-2/pedersen-hash/pedersen.html) hash function used in the core deposit contract, in that it's an elliptic curve hashing algorithm. The major difference between the two is that Poseidon operates over the BN128 elliptic curve instead of Baby Jubjub, and where Pedersen uses 1.7 constraints per bit in a ZK proof, Poseidon only uses between 0.2 and 0.45 constraints per bit.

#### Collecting the Events

In order to compute an update to the tree, it's necessary to know the existing structure of the tree. To obtain this, you query from the contract logs the `DepositData` or `WithdrawalData` events emitted earlier, depending on which tree you're updating.

Using the index indicated by `lastProcessedDepositLeaf` or `lastProcessedWithdrawalLeaf`, you can then split the events into two sets of leaves - "committed" and "pending". As the names would imply, the former set of leaves are the ones that are already committed within the Merkle Tree, and the latter are all of the leaves which still need to be inserted.

#### Computing a Tree Update

Using the committed events, we're able to reconstruct the current state of Merkle Tree by first computing the Poseidon hash for each of the existing leaves, using the Tornado instance address, commitment/nullifier hash, and block number as the inputs to the hashing algorithm.

The empty state of the Merkle Tree starts with every leaf node labelled using a "zero value" of `keccak256("tornado") % BN254_FIELD_SIZE`, similarly to how zero nodes work in the core deposit circuit, except using the BN254 elliptic curve. This ensures that all paths within the tree are invalid until a valid commitment is inserted on a leaf, and gives a constant, predictable label for each node whose children are zeroes.

The leaves of the tree are then populated from left to right with the leaf hashes for the set committed events, and then the non-leaf nodes are updated up to the root. If everything is done right, the resulting root should be equal to what's currently stored in `depositRoot` / `withdrawalRoot` of the Tornado Trees contract.

Now that we have the "old root", we can proceed to take a chunk of pending events (256 of them), compute their Poseidon hashes, and insert them into the tree. After updating the non-leaf nodes up to the root, we will have the "new root".

Next, we need to collect a list of path elements starting from the right-most non-zero leaf in the tree, as well as an array of `0/1` bits indicating whether each path element is to the left or right of its parent node.

#### Computing the Args Hash

The last thing that we need before we can compute a proof is a hashed list of arguments that we'll be passing into our proving circuit, with a very particular structure.

Construct a message that is the concatenation of these fields:

1. The old root label (32 bytes)
2. The new root label (32 bytes)
3. The path indices as bits, left-padded with zeroes (4 bytes)
4. For each event
   1. The commitment/nullifier hash (32 bytes)
   2. The Tornado instance address (20 bytes)
   3. The block number (4 bytes)

Compute the SHA-256 hash of this message, and then compute its modulus against the BN128 group modulus found in the `SNARK_FIELD` constant of the Tornado Trees contract.

#### Inputs to a Tree Update Proof


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
elliptic curve associated with a prime in the order of the BN128 elliptic curve.

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
length. The first value is a 

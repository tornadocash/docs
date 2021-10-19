# How does Tornado.Cash work?

Before diving in tutorials explaining & easing the use of Tornado.Cash, here is an overall overview of the protocol global functioning.

### Global overview of Tornado.Cash functioning

To achieve privacy, Tornado.Cash **uses smart contracts that accept tokens deposits from one address and enable their withdrawal from a different address**. Those smart contracts work as pools that mix all deposited assets. 

Once the funds are withdrawn by a complete new address from those pools, the on-chain link between the source & the destination is broken. The withdrawn crypto-assets are therefore anonymized. 

When a user puts funds into a pool \(a.k.a. the deposit\), a private note is generated. This private note works as a private key for the user to access those funds later. To withdraw them, the same user can use a different address - an old or a new one - and recover his/her funds thanks to this private key.

The strength of such a protocol comes naturally from its number of users and the size of its pool. The more users deposit into the pool the merrier. However, to preserve privacy & anonymity, the user must keep some basic rules in mind such as:

* Using a relayer to pay gas at withdrawal;
* Leaving a lapse of time between the deposit & the withdrawal action;
* Mixing its funds with the crowd by waiting for several transactions before recovering its assets.

_More recommendations are provided on:_ [_Tips to remain anonymous_](tips-to-remain-anonymous.md)_._

### Contribution of zk-SNARK & hashing process

Tornado.Cash use Zero-Knowledge Succinct Non-Interactive Argument of Knowledge \(also called zk-SNARK\) to verify & allow transactions.

To process a deposit, Tornado.Cash generates a random area of bytes, computes it through the [Pederson Hash](https://iden3-docs.readthedocs.io/en/latest/iden3_repos/research/publications/zkproof-standards-workshop-2/pedersen-hash/pedersen.html) \(as it is friendlier with zk-SNARK\), then send the token & the 20 mimc hash to the smart contract. The contract will then insert it into the Merkle tree.

To process a withdrawal, the same area of bytes is split into two separate parts: the **secret** on one side & the **nullifier** on the other side. The nullifier is hashed. This nullifier is a public input that is sent on-chain to get checked with the smart contrat & the Merkle tree data. It avoids double spending for instance.

Thanks to zk-SNARK, it is possible to prove the 20 mimc hash of the initial commitment and of the nullifier without revealing any information. Even if the nullifier is public, privacy is sustained as there is no way to link the hashed nullifier to the initial commitment. Besides, even if the information that the transaction is present in the Merkle root, the information about the exact Merkle path, thus the location of the transaction, is still kept private.

Deposits are simple on a technological point of view, but expensive in terms of gas as they need to compute the 20 mimc hash & update the Merkle tree. At the opposite, the withdrawal process is complex, but cheaper as gas is only needed for the nullifier hash and the zero-knowledge proof.



_Translated by_ [_**@chieftalion**_](https://torn.community/u/chieftalion/)


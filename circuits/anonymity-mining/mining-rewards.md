---
description: >-
  Anonymity Mining rewards are claimed using ZK proofs showing the block
  duration that notes were left deposited. Anonymity Points are kept in shielded
  accounts until swapped for TORN.
---

# Reward Claim

## Account Tree

Anonymity Points claimed as rewards for anonymity mining are stored in "shielded" accounts within a Merkle Tree, using many of the same patterns as in the core deposit contract and Tornado Trees.

### Shielded Balance

The special property that the accounts tree brings to the table is that only the owner of the account knows its balance. Each time that an account's balance is updated by claiming additional rewards, or withdrawing from it, a new account is created, and the old account is nullified.

The balance of an account is stored as a component of the commitment hash that is inserted into the tree. The balance of an account can only by known by having the private key used to produce an encrypted backup of its commitment inputs.

### Account Commitment

An account commitment consists of three components:

1. The 31-byte amount of AP in the account
2. A 31-byte random secret
3. A 31-byte random nullifier

An account commitment hash is the Poseidon hash of these three components

## Claiming a Reward

### Inputs to a Reward Proof

#### The total set of public inputs for a reward proof are:

1. The block reward rate for the claim
2. The fee that you're paying the relayer (or zero)
3. The Tornado instance address associated with the note
4. The reward nullifier (Poseidon hash of the note nullifier)
5. The args hash
6. The root of the account tree pre-claim (input)
7. The nullifier of the existing account being added to
8. The root of the account tree after updating it (output)
9. The path indices to the new account, as an integer, left-padded with zeroes
10. The commitment for the new account
11. The root of the deposit tree
12. The root of the withdrawal tree

#### The total set of private inputs for a reward proof are:

1. The secret of the note being claimed
2. The nullifier of the note being claimed
3. The amount coming from an existing account
4. An array of path elements to the existing account commitment in the tree
5. The path indices to the existing account, as an integer, left-padded with zeroes
6. The balance of the new account
7. The secret of the new account
8. The nullifier of the new account
9. An array of path elements to the new account
10. The block number when the claimed note was deposited
11. The path indices to the deposit in the Tornado Trees deposit tree, as an integer, left-padded with zeroes
12. An array of path elements to the deposit in the Tornado Trees deposit tree
13. The block number when the claimed note was withdrawn
14. The path indices to the withdrawal in the Tornado Trees withdrawal tree, as an integer, left-padded with zeroes
15. An array of path elements to the withdrawal in the Tornado Trees withdrawal tree

### Proven Claims

Rewards are claimed by proving that:

1. You know the path to a deposit and withdrawal event pair
2. The deposit and withdrawal correspond to the same note whose secret and nullifier you know
3. The withdrawal event's block number is a specified duration after the deposit event's block number
4. The amount you're claiming is then a multiple of the agreed-upon reward rate, times the specified block duration
5. The disclosed "reward nullifier" is the Poseidon hash of the original note nullifier

### Sanity Checks

An invariant constraint is first created showing that the amount that is coming from an existing account, plus the block reward rate times the block duration, is equal to the new account's balance plus the relayer fee.

An overflow check is then performed on the input, output, and block duration values to ensure that they fit within 248 bits, 248 bits, and 32 bits, respectively, without overflowing.

### Input Account Validation

The input account balance, secret, and nullifier are hashed to obtain the input account commitment, and then the path elements and path indices are used to verify that such a commitment exists within the specified input root, but in such a way that if the input account balance is 0, the check passes regardless.

This scheme allows for new accounts to be created without publicly disclosing that they are new.

The public input nullifier hash is checked against the input account's nullifier component.

### Output Account Validation

The output account balance, secret, and nullifier are hashed to obtain the output account commitment, and are checked against the public output commitment hash.

The account tree update is validated using the input root, output root, output commitment as a new leaf, and the specified output path elements and indices.

### Tornado Trees Validation

The Tornado Commitment used for the note being claimed is computed using the note secret and nullifier, and then the corresponding commitment in the Tornado Trees deposit tree is computed using the Tornado instance address, note commitment, and deposit block number as components.

The deposit commitment is then verified to exist at the specified deposit path beneath the deposit tree root.

The withdrawal commitment in the Tornado Trees withdrawal tree is then computed using the Tornado instance address, note nullifier hash, and withdrawal block number as components. The withdrawal commitment is verified to exist at the specified withdrawal path beneat the withdrawal tree root.

### Reward Nullifier

The reward nullifier for the provided note is then computed by generating the Poseidon hash of the note's nullifier. This is compared to the reward nullifier specified as a public input.

### Args Hash Square

As a last step, the args hash is squared into a public output, to ensure that the reward transaction parameters cannot be tampered with relative to the proof.

## Completing the Reward Transaction

Using the generated proof, we can now call the `reward` method of the Miner contract.

The reward method takes the proof, and the public inputs to the proof, and verifies:

1. The input account nullifier has not already been used
2. The output account path corresponds to the input root leaf index
3. The deposit and withdrawal roots are the current or previous roots of the Tornado Trees contract (are known roots)
4. The args hash is correct with respect to the extData args
5. The relayer fee is within a valid 248-bit integer range
6. The reward rate equals what is expected for the Tornado instance specified
7. The reward has not already been claimed according to the reward nullifier
8. The proof is valid according to the Reward verifier, using the public inputs provided

If these preconditions are met, then:

1. The input account is nullified
2. The reward is nullified
3. The account tree root is updated to the specified output account root
4. If applicable, the relayer is rewarded TORN using the fee AP at the current AMM rate
5. A New Account event is emitted

#### Batch Rewards

There is an alternate method in the Miner contract which deals with "batch rewards". While most transactions claim rewards individually, batch reward transactions claim multiple rewards at once. This avoids having to wait for the next block for each reward claim, since each claim has to insert a new leaf from the last account root.

A batch reward transaction specifies a sequence of `reward` method parameter sets, which are executed incrementally.

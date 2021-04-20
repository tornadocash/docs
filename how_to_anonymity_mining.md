# Anonymity Mining
## Introduction & Purpose
Tornado Cash's privacy is based on an Anonymity Set (AS). Users deposit a fixed amount cryptocurrency into a smart contract, and receive a note. Because the amount of the note is fixed, when cryptocurrency is withdrawn from the contract, it could in principle come from any note previously deposited. The amount of notes ever deposited in the contract pool represent the anonymity set. Furthermore, Tornado Cash hides the transaction graph. Both are needed so that an external observer could not link a withdraw to a deposit. 

To incentivize users to deposit into the contract, Tornado Cash has added anonymity mining: while notes are in the pool, they accumulate Anonymity Points (AP), which can be claimed and then swapped for TORN anonymously.

This document aims to explain step by step the process a normal user can follow to successfully perform Anonymity Mining.

## How To
The basic process of Anonymity Mining is as follows:
1. Deposit a note: a user must deposit cryptocurrency into an anonymity set
2. Withdraw a note: the note must be spent, ie. the deposited cryptocurrency is sent to an unlinked address
3. Update Merkle Tree: Wait until deposit and withdrawal metadata is uploaded to the Anonymity Mining contract 
4. Claim Anonymity Points (AP): once the note is withdrawn, AP can be claimed anonymously
5. Swap AP for TORN: the AP can be swapped for TORN in a unlinked address


### Deposit a note
On tornado Cash, choose Deposit and the amount you wish to send to the contract. You can choose between fixed amounts of ETH or other cryptocurrency. The amount is fixed to establish an anonymity set. The more users deposit a certain pool, the larger the set any withdrawals can potentially be from.

When you deposit into the contract, tornado cash gives you a note representing a secret that is needed to withdraw. The commitment is a hash of the secret. Don't lose this note!  
In the background, the deposit is registered on chain.

Your note is now accumulating Anonymity Points. The longer you keep your ETH / Tokens locked in the contract, the more you contribute to the anonymity set, allowing all users to gain anonymity. The AP compensate you for this.

### Withdraw a note
When you are ready to withdraw the note, click the Withdraw tab on the Tornado Cash interface. Copy paste the note into the field, and the address to which you want to withdraw. You can choose any address; if you use a different address than the one you used to deposit, it will receive the amount with absolutely no link to the deposit address.

If you use a relayer, the withdrawal transaction is payed for using the accumulated anonymity points, and thus, there is no gas fee linking you to your Ethereum deposit address. You can also pay the gas using Eth in an address, but this may compromise your privacy.

The withdrawal is also registered on chain, and your Anonymity Point accumulation stops. 

### Update the Merkle Tree
Before you can claim the Anonymity Points, the Merkle Tree (a [smart contract](https://etherscan.io/address/0x527653eA119F3E6a1F5BD18fbF4714081D7B31ce#code) must be updated. In simplified terms, the deposit transaction and the withdrawal transaction must be successfully linked. When a user deposits, the deposit is registered in this smart contract. Once there are 256 of them, anyone can upload the deposits metadata (the most important is the block number) to the deposits merle tree managed by the contract. It’s a complex operation that’s why it’s done in batches and cost so much

To fully decentralize Tornado Cash, the Merkle Tree lies in a smart contract that can be updated by anyone. In the Tree Updater Github, edit the .env file and run the docker container. The Tree Updater Contract updates in batches of 256 deposit transactions, linking them to any withdrawals that happened in between. Updating the tree costs around 1.2M gas per batch. 

Thus, the Tree Updater requires a wallet containing a certain multiple of ETH to bridge your deposit and withdrawal. It executes one transaction every **x minutes / blocks**.

### Claim Anonymity Points (AP)
When the tree is updated beyond your withdrawal block, you are ready to claim AP. Go to the Mining tab at the top of Tornado Cash page, and enter your note. If you use a relayer, you can spend some AP to claim anonymously. Without relayer very little information is leaked too. A hypothetical observer only knows that address that paid for gas claimed some reward of unknown size for some unknown note, but it's public for which instance it was done.

A proof will be calculated and a transaction submitted to the mining contract. The proof is based on the current status of the Merkle Tree, and if any Claim is made before yours goes through, your transaction will be rejected! You will simply need to claim again, generating a new proof. Note that in times of many users claiming, there will be congestion on the claim contract, and it may be difficult to get your claim through.

Using a relayer can also help in times of congestion, and send a claim transaction multiple times, in case the first transaction is rejected, queuing the transactions and letting the claim be included in the next block.

You can claim several notes and pool your AP before swapping.

### Swap AP for TORN
Once you have been able to claim, you can Swap some or all of your AP for TORN, which is then sent to the wallet of your choice.

TORN drips into the Mining Contract pool at a variable rate which can be seen on the swap interface and AP accumulate a the rate of all the notes. AP is swapped for TORN [at the rate defined by the AMM](https://tornado-cash.medium.com/tornado-cash-governance-proposal-a55c5c7d0703).

The current rate and trend can be seen here on the [Tornado Cash Dune Analytics page](https://duneanalytics.com/poma/tornado-cash_1).


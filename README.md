# Introduction of Tornado.Cash

![](.gitbook/assets/image.png)

Tornado Cash is a **fully decentralized** **non-custodial** **protocol** allowing private transactions in the crypto-space.&#x20;

As a decentralized protocol, Tornado.Cash smart contracts have been implemented within the Ethereum blockchain which makes them immutable. They can neither be changed or tampered with. Therefore, nobody - including initial developers - can modify or shut them down. All governance and mining smart contracts are deployed by the community in a decentralized manner.

As a non-custodial protocol, users keep custody of their cryptocurrencies while operating Tornado.Cash. Indeed, at each deposit, they are provided with the private key enabling the access to the deposited funds, which gives users complete control over their assets.

## How privacy is achieved?

Tornado Cash improves transaction privacy by breaking the on-chain link between source and destination addresses. It uses a smart contract that accepts ETH & other tokens deposits from one address and enable their withdrawal from a different address.

To preserve privacy, few good practices are in order, such as the use of a relayer for gas payments to withdraw funds towards an address with no pre-existing balance.&#x20;

More details are available in _Behind the scenes: _[_How does Tornado.Cash work?_](how-does-tornado.cash-work.md)_** **_& [Tips to remain anonymous](tips-to-remain-anonymous.md).

## Where is Tornado.Cash at?

The protocol has been operating on the **Ethereum blockchain** since its inception in 2019. It was recently deployed, in June 2021, on **Binance Smart Chain** & **Polygon**.

As of today, Tornado.Cash can be used with the following tokens:

* On Ethereum : **ETH** _(Ethereum)_, **DAI** _(Dai)_, **cDAI** _(Compound Dai)_, **USDC** _(USD Coin)_, **USDT** _(Tether)_ & **WBTC** _(Wrapped Bitcoin)_
* On Binance Smart Chain: **BNB** _(Binance Coin)_.
* On Polygon Network: **MATIC** _(Polygon)_
* On xDai Chain : **XDAI** (_Stake_)
* On Avalanche : **AVAX**

![](.gitbook/assets/non-custodial-anonymous-transactions-on-ethereum-3-.png)

The protocol also includes an **anonymity mining system for some of its token**, allowing its users to earn a **governance token**. Thanks to TORN tokens, Tornado Cash users actively participate in shaping the protocol. The community has a strong weight regarding the evolution of Tornado Cash and the improvement of its features. Indeed, protocol parameters & token distribution are completely under the community's control through this governance.

_More information about _[_Anonymity mining_](anonymity-mining.md)_ & _[_Tornado.Cash token_](torn.md)_ are available._

## How does Tornado.Cash run?

[Codes behind Tornado.Cash functioning](https://github.com/tornadocash) - smart contacts, circuits & toolchain -  are fully **open sourced. **Working as a DAO (Decentralized Autonomous Organization), Tornado.Cash governance and mining smart contracts are deployed by its community.

The protocol also functions with zk-SNARK, which enables zero-knowledge proofs allowing users to demonstrate possession of information without needing to reveal it. The use of this technology is based **on open source research made by Zcash team with the help of Ethereum community**. To set-up zk-SNARK initial keys, Tornado.Cash[ Trusted Setup Community](https://tornado-cash.medium.com/tornado-cash-trusted-setup-ceremony-b846e1e00be1) was launched in May 2020 & accounted [for 1114 contributions](https://tornado-cash.medium.com/the-biggest-trusted-setup-ceremony-in-the-world-3c6ab9c8fffa). This significant number of contributors makes it impossible to compromise the protocol by faking zero-knowledge proofs.

User interface is hosted on **IPFS** (InterPlanetary File System) by the community, minimizing risks of data being deleted. Indeed, the interface will work as long as at least one user is hosting it.



_Written by _[_@ayefda_](https://torn.community/u/ayefda)__

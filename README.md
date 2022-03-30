# Tornado Cash介绍

![](.gitbook/assets/image.png)

Tornado Cash是一种**完全去中心化的非托管协议** ，允许用户在加密货币世界进行隐私交易。

作为一个去中心化协议，Tornado Cash智能合约已经在以太坊区块链中部署，这使得它们无法被改变。它们既不能被改变，也不能被篡改。因此，任何人——包括最初的开发人员——都不能修改或关闭它们。社区以去中心化的方式部署所有治理和挖矿的智能合约。

作为一种非托管协议，用户在使用Tornado.Cash时拥有其加密货币保管权。因此，在每次存款中，他们都获得了能够访问存款资金的私钥，这使用户能够完全控制他们的资产。

## 隐私是如何实现的?

Tornado Cash通过打破资金来源地址和资金到达地址之间的链上关联，来提高交易的私密性。它使用智能合约，接受用户从一个地址的ETH和其他代币的存款，并允许用户从不同的地址提取资金。

为了保护隐私，部分良好的做法是有效的，比如通过中继来支付gas，来使得资金提取到一个没有预存余额的钱包地址。

更多细节可在这里查看：[_Tornado Cash是如何工作的？_](general/how-does-tornado.cash-work.md) 和 [保持匿名的窍门](general/tips-to-remain-anonymous.md)。

## Tornado.Cash现在到哪个阶段？

自2019年成立以来，Tornado Cash一直**在以太坊区块链上运行**。协议提供6种代币（ETH、DAI、cDAI、USDC、USDT 和 WBTC）多种固定金额池。

从2021年6月开始，除了以太坊区块链，Tornado Cash智能合约**也已部署在其他侧链和区块链上**。这些部署使得协议能够支持新代币且受益于Layer-2优势，比如交易速度更快、更便宜。

因此，截至今天，在Tornado Cash上可以使用以下代币：

* **以太坊**：**ETH** (Ethereum)， **DAI** (Dai)， **cDAI** (Compound Dai)， **USDC** (USD Coin)， **USDT** (Tether) & **WBTC** (Wrapped Bitcoin)，
* **币安智能链**：**BNB** (Binance Coin)，
* **Polygon网络**：**MATIC** (Polygon)，
* **Gnosis Chain (原xDAI Chain)**：**xDAI** (xDai)，
* **Avalanche主网**：**AVAX** (Avalanche)，
* **Optimism**， 以太坊的Layer-2，
* **Arbitrum One**， 以太坊的Layer-2。

![](.gitbook/assets/logos.png)

在2021年12月之前，协议还包括一些代币的匿名挖矿系统，允许其用户获得治理代币（**TORN**）。用户可以在ETH、DAI、cDAI 和 WBTC池中存入资产来赚取TORN。

_点击了解更多关于_ [_匿名挖矿_](tornado-cash-classic/anonymity-mining.md) _&_ [_Tornado.Cash的代币信息_ ](general/torn.md)。

**通过TORN治理代币，Tornado Cash用户可以积极参与协议的制定**。社区对 Tornado Cash的发展及其功能的改进有很大的影响力。事实上，协议参数和代币分发通过这种治理方式完全由社区控制。

上面提到的所有池都可以在[tornadocash.eth.link](https://tornadocash.eth.link)上访问。这些池 **在固定金额存款和取款的原则下运作**。每个代币有2至4个不同金额的池，这意味着只允许2至4个不同固定金额的存取 _（例如ETH有四个不同金额的池：0.1、1、10和100 ETH）_。

### Tornado Cash Nova

随着[**2021年12月Tornado Cash Nova（测试版）的发布**](https://tornado-cash.medium.com/tornado-cash-introduces-arbitrary-amounts-shielded-transfers-8df92d93c37c)，协议中添加了**具有独特新功能**的升级池。用户不再受固定金额交易的限制。随着Tornado Cash Nova的加入，用户可以从使用**任意金额池进行隐蔽交易**中受益。

Tornado Cash Nova在Gnosis链（前xDai链）上作为Layer2运行，以优化速度和成本。它允许**在ETH中完全自定义金额进行存款和取款**。该池还支持隐蔽交易，用户可以**保留其池中的代币，并转移其代币的保管**。

Tornado Cash Nova（测试版）可以在[nova.tornadocash.eth.link](https://nova.tornadocash.eth.link)上访问。您可以在我们文档找到专门介绍Tornado Cash Nova 功能的更多相关信息。

## Tornado.Cash是如何运行的？

[Tornado Cash背后运作的代码](https://github.com/tornadocash) -智能合约、线路和工具链- 是\*\*完全开源的。\*\*作为一个DAO(去中心化自治组织)工作，Tornado Cash治理和挖矿的智能合约由其社区部署。

该协议还与zk-SNARK一起使用，zk-SNARK支持零知识证明，其允许用户在证明拥有信息的情况下而不需要透露它。这项技术的使用是基于**Zcash团队在以太坊社区的帮助下进行的开源研究**。要设置zk-SNARK的初始密钥, Tornado.Cash[ 可信设置社区](https://tornado-cash.medium.com/tornado-cash-trusted-setup-ceremony-b846e1e00be1)于2020年5月推出，[共有1114位贡献者参与](https://tornado-cash.medium.com/the-biggest-trusted-setup-ceremony-in-the-world-3c6ab9c8fffa)。如此大量的参与者使得伪造零知识证明来破坏协议成为不可能的。

用户界面由社区托管在**IPFS** (InterPlanetary File System)上，减少数据被删除的风险。事实上，只要至少有一个用户托管该界面，它就可以工作。

_编写_ [_@ayefda_](https://torn.community/u/ayefda)

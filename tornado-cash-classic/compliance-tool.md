# 合规工具

根据设计，区块链上的一切都是公开的，这可能会剥夺用户的隐私权。任何人都可以查看所有人的全部交易记录。为了解决这个核心问题，Tornado Cash协议允许加密货币持有者赚回他们的隐私和获得匿名。实际上，它允许用户断开源地址和目的地址之间的链上关联。

然而，维护隐私和维护财务自由绝不应以不合规为代价。隐私权在于能够控制我们提供的信息以及我们向谁提供这些信息。

在这个程度上，**Tornado Cash合规工具使用户能够证明其资金的来源。** 由于每次存款后生成的Note，该工具通过用于存款和提取资产的以太坊地址**生成加密验证的交易历史证明。**

你可以访问与此工具相关的Medium帖子，了解更多关于其开发和发布的信息：[**Tornado.Cash compliance Medium Post**](https://tornado-cash.medium.com/tornado-cash-compliance-9abbf254a370).

因此，如果你曾经需要证明从Tornado Cash池之一中提取的持有资产的来源，我们邀请你使用以下[Compliance Tool](https://tornadocash.eth.link/compliance)：

![https://app.tornado.cash/compliance/](../.gitbook/assets/capture-de-cran-2021-09-02-a-14.57.11.png)

## 如何使用合规工具?

通过[Tornado.Cash](https://tornadocash.eth.link)的每一笔存款，协议都会生成一个新的凭证。这张凭证是必要的，方便以后在任何收款地址提取存款的资产。同样，如果需要，允许用户生成合规报告来证明其资产的来源。

_更多关于如何在Tornado Cash上存款和取款的信息可在这里找到：_ [_存款和取款_](deposit-withdraw.md)_._

要获得合规报告，用户只需要将存款后生成的凭证复制到专用框中。

### 在取款前

如果Note凭证还没有被使用(即资产还没有被提取)，合规工具将只向你提供有关存款的信息：

* 存款的交易哈希；
* 源地址；
* 承诺的哈希。

承诺是每笔存款处生成的哈希随机字节区域，在发送到Tornado Cash的智能合约来描述交易。

![https://app.tornado.cash/compliance/](../.gitbook/assets/capture-de-cran-2021-09-02-a-15.07.01.png)

_你可以找到更多Tornado Cash实现提供隐私的信息，通过阅读_ [_Tornado.Cash 是如何工作的？_](../general/how-does-tornado.cash-work.md)

### 在取款后

如果凭证已被使用(即通过使用凭证将资产提取到指定地址)，合规工具将通过添加以下内容来完善上述信息：

* 取款的交易哈希； 
* 目的地址；
* Nullifier哈希。

Nullifier哈希是一个在链上发送的公共输入，用于使用智能合约和Merkle树数据进行检查，以允许提款。

![https://app.tornado.cash/compliance/](../.gitbook/assets/capture-de-cran-2021-09-02-a-15.12.23.png)

因此，该工具允许用户重新关联源和目的地址，以证明在Tornado.Cash上使用的资产的交易历史。

该信息也可以以PDF格式下载，使其更容易发送到任何想要的第三方：

![https://app.tornado.cash/compliance/](../.gitbook/assets/capture-de-cran-2021-09-02-a-15.12.53.png)

_编写_ [_@ayefda_](https://torn.community/u/ayefda)

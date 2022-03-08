# 治理

以下治理规则适用于所有Tornado Cash池（包括 Tornado Cash Nova）。

### 如何提出提案？

为了参加Tornado.Cash治理，用户首先需要在治理合约中锁仓代币。如果用户投票或创建提案，那么在提案执行周期结束(提案创建后的8.25天)之前，代币无法解锁。锁仓的代币也可以委托给另一个地址。

要创建提案，用户至少需要拥有 `1000个TORN`。所有提案都必须是带有经过验证的智能合约，这些代码是从[治理合约](https://etherscan.io/address/0x5efda50f22d34F262c29268506C5Fa42cB56A1Ce)执行的（使用 `delegatecall`）。这样，审计和测试任何治理更改都很容易。

提案的投票期为5天。如果一个提案获得多数的投票，并且至少有`25000个TORN`的投票，那么提案就通过（如果投票率过低，提案就会自动失败）。

提案成功后，将有2天的锁定时间。在时间锁定之后，任何用户都可以执行提案（启动更改）。如果提案在此之后3天仍未执行，则视为 _已过期_ ，无法再执行。

所有这些初始参数都相对较小，因为早期流通中的TORN代币不会很多。但随着流通供应量的增加，治理可能会调整这些阈值。

提案可以是以下性质：

* 在代理中添加新的Tornado Cash池
* 更改AP奖励率参数
* 取消暂停/暂停 TORN 代币
* 更改合约等一些核心挖矿 `TornadoTrees` 合约
* 以上所有的组合

还有很多事情可以做。要确切地找出在协议中通过治理可以更改什么，请在智能合约中查找`onlyGovernance`修饰符的函数。

治理功能在[此架构图中红色箭头表示](https://viewer.diagrams.net/?highlight=0000ff\&edit=\_blank\&layers=1\&nav=1\&title=tornado-cash-contract-overview.drawio#Uhttps%3A%2F%2Fraw.githubusercontent.com%2FRezan-vm%2Ftornado-cash-edu%2Fmain%2Ftornado-cash-contract-overview.drawio)。

注意：本文的部分内容摘自[这篇medium文章](https://tornado-cash.medium.com/tornado-cash-governance-proposal-a55c5c7d0703) 。归功于Tornado cash团队。

### 如何投票？

首先您需要将TORN代币存入(或锁入)治理合约。

前往：[https://tornadocash.eth.link/governance](https://tornadocash.eth.link/governance)

点击 `Manage` -> `Lock`标签

通过点击 `Approve` 按钮，批准治理合约来转移你的TORN代币。一旦确认批准，选择你想要存入的金额，并单击 `Lock`。确认你钱包中的交易，并等待确认。

![](../.gitbook/assets/c05e5a1813edad280544b627b24002dc8d5adcf2.png)

在投票之前，下一个关键步骤是审阅该提案。\
合法的提案应该在[Torn.community ](https://torn.community)的“Proposal”类别下有一个专门的帖子。论坛帖子将提供有关该提案的更多背景和论据。阅读主题并在这个问题上做出自己的想法。

提交提案后，它应该出现在：\
[https://tornadocash.eth.link/governance](https://tornadocash.eth.link/governance)\
提案以智能合约的形式实施，对系统进行更改。因此，验证智能合约的地址并查看其代码非常重要。在此处找到提案的合约地址：

![](../.gitbook/assets/181d612b6c57964bab59c8e5b766f5247211083d.png)

在Etherscan上查找合约地址，并确保源代码经过验证且可读。

![](../.gitbook/assets/d2d37d169a94f09156e76fa522b7974cb7c9ac3f.png)

阅读源代码，并确保它与论坛帖子中的描述相匹配。

如果你不是技术人员，或者不喜欢阅读solidity代码，那就找你信任的人帮你检查合约。

如果你同意(或不同意)提案的代码，是时候投票了！

提案有5天的投票窗口。这意味着我们有5天时间达到2万5千的投票规定人数。

重要提示：一旦您投票了，您的代币将从提案提交之日起锁定8.25天（5天投票期的开始）。在8.25天之后，您可以从治理合约中提取您的代币。请注意，您可以同时对2个提案进行投票，而不会产生额外的锁定期（只有最近提交的提案才对8.25天锁定很重要）。

如要投票，只需点击绿色打勾标记或红十字标记，这取决于你是接受还是拒绝提案。与Metamask确认交易，你的投票就会生效！

### 如何委托投票？

如果您是TORN代币持有者，您可以将您的投票权委托给其他人，而无需向他发送代币。

重要提示：如果您委托代币并且您的代表投票或发起提案，您的代币将在代表投票的提案开始后锁定 8.25 天。请注意，您始终可以随时取消委托。

要实现委托，请访问： [https://tornadocash.eth.link/governance](https://tornadocash.eth.link/governance)

你首先需要在治理合约中锁定你的代币。单击 **`Manage`** -> **`Lock`** 标签

通过单击 **`Approve`** 按钮，批准治理合同以转移您的TORN代币。确认批准后，选择您要委托的金额并单击 **`Lock`**。确认您钱包中的交易并等待确认。

![](<../.gitbook/assets/c05e5a1813edad280544b627b24002dc8d5adcf2 (1).png>)

最后一步，是进行实际的委托。再次访问 [https://tornadocash.eth.link/governance](https://tornadocash.eth.link/governance)

单击 **`Manage`** -> **`Delegate`** 标签

填写您要委托的地址，然后单击 **`Delegate`**。 批准您钱包中的交易并等待确认。

![](../.gitbook/assets/43c05d176d7f75a336af7a865565c9b23786b98c.png)

您锁定的全部余额将被委托。

您可以随时取消委托。要取消委托，只需使用 `Manage` -> `Undelegate` 标签中的 `Undelegate` 按钮。



_编写_ [_@rezan_](https://torn.community/u/Rezan/summary)

_更新_ [_@bt11ba_](https://torn.community/u/bt11ba/)

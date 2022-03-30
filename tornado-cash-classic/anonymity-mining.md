# 匿名挖矿

匿名挖掘是一种激励机制，通过根据参与者在池中对冲资产的时间长短来奖励参与者匿名点(AP)，从而提高任何投币或混币协议中的隐私级别。

{% hint style="warning" %}
_Tornado Cash匿名挖矿激励措施于2020年12月18日开始，将于2021年12月18日结束。_
{% endhint %}

个人将存款存入任何一个支持的匿名池(ETH, WBTC, DAI或cDAI)，他们的存款留在池中的期间，可以获得每个区块固定金额的AP奖励。这些点数可以在申领后兑换成TORN。

### **匿名点(AP)**

_在本文撰写时，读者应该意识到，一些较低面额的存款，由于提取、兑换和交换匿名点数所需的gas成本，不会产生正回报_。

一个社区成员创建了一个关[于挖矿的电子表](anonymity-mining.md#ni-ming-dian-ap)格资源，通过估算领取奖励所需的费用，帮助计算每个池和其中设置的每个面值的年收益率百分比(APY)。在期望获得收益之前，强烈建议查看这一资源并计划自己的行动。在电子表格的底部，您可以通过选择相关的选项卡来查看每个池。

### **如何获得AP**

1. 在点击“Connect”和“Deposit”之前，通过下拉菜单选择要存款的金额和资产。

![](../.gitbook/assets/M3FH0gL.png)

2\. 将你的存款凭证做好记录并安全备份，**不要与任何人分享，否则可能会失去存款和奖励**。

![](../.gitbook/assets/vhUstrU.png)

3\. 生成证明并提交交易。

4\. 你的存款现在应该可以在页面的底部看到，你可以在这里跟踪它赚多少AP；记住，你的存款保持有效的时间越长，你赚的AP越多。

![](../.gitbook/assets/K6juetP.png)

有效的(未提款的)凭证称为“unspent”凭证。

### **如何申领AP**

1. 首先，你必须创建一个挖矿账户，并将这些凭证存储在链上，以便容易恢复(需要一次交易)，**就像存款凭证一样，你不应该与任何人共享你的挖矿恢复密钥**，并确保在一个安全的地方备份它。硬件钱包不支持此功能，因此鼓励直接储存显示的信息。

![](../.gitbook/assets/LsKZKgK.png)

2\. 通过提供未使用的凭证并将其取出到指定的地址，然后决定是否使用中继器(为了保持存款的匿名性，总是建议使用中继器)，这些操作将使凭证进入“spent”状态。

![](../.gitbook/assets/AID86Cj.png)

**记住，即使在取款后也要保密你的存款凭证，因为它们仍然保留着兑换AP的效力。**

![](../.gitbook/assets/bpsQxxR.png)

3\. 访问应用程序的挖矿路线，并输入您的已花费凭证，您可能会面临以下情况之一：&#x20;

* **认领已花费凭证的成功情况**：点击“Claim reward”按钮，通过或不通过中继器来提交交易，一旦确认，你的AP余额应更新来反应该行动。

![](../.gitbook/assets/E9JYQhU.png)

* **认领已花费凭证的不成功情况**：“Warning: The note is not yet ready for anonymity mining. You can wait few days before trying again” - 这意味着Merkle树暂时不同步，需要更新交易。

![](../.gitbook/assets/I6QTr0F.png)

更新Merkle树可能是一个昂贵的过程，**建议拥有少量存款的用户等待拥有较大的存款的用户来更新Merkle树，这可能需要几天到一周的时间**。如果你想查看关于当前待办批次的事件。点击“Show mining note information”超链接，在这里你也可以通过“Update trees”按钮支付交易费用来同步与你的提款相关的树。

![](../.gitbook/assets/D8dMXJj.png)

### **如何交换AP**

1. 导航到挖矿页面的“Swap”选项卡，可以通过页面顶部的第二个导航栏访问该选项卡。

![](../.gitbook/assets/ahrjxbq.png)

2\. 输入要求兑换的AP金额或选择“Maximum”选项来转换你的有效余额。在这个输入下面，关于当前AP/TORN兑换率和奖励输出的信息将显示。提供想要接收奖励的地址，生成证明，并通过或不通过中继器提交交易。

![](../.gitbook/assets/wO55lAo.png)

3\. 如果所有步骤都正确执行，TORN将被转移到本节第二步中提供的接收地址。

### **小结**

祝贺你，你已经成功地参与了匿名挖矿！

我们推荐在决定参与任何匿名集挖矿前，用户也应该意识到, [AP/TORN](https://dune.xyz/luckyallocator/Daily-AP-TORN-Rate-v2)的兑换率取决于供给和需求，因此，越多的人申领，比率就越高，越少的人申领，比率就越低。

要了解更多关于匿名挖掘的信息，请查找以下资源：

* [Tornado.Cash governance proposal article ](https://tornado-cash.medium.com/tornado-cash-governance-proposal-a55c5c7d0703)
* [Tornado.Cash anonymity mining optimisation article ](https://tornado-cash.medium.com/gas-price-claimed-anonymity-mining-a-victim-but-now-everyone-can-claim-ap-5441aaa32a1a)
* [Anonymity mining explained (technical)](https://torn.community/t/anonymity-mining-technical-overview/15)



感谢[@sockawoo](https://torn.community/u/sockawoo)和[@ethdev](https://torn.community/u/ethdev)协助审阅

编写 [@xgozzy](https://torn.community/u/xgozzy/summary)

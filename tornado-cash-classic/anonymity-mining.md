# 匿名挖矿

匿名挖矿是一种激励机制，通过根据参与者在池中存储资产的时间长短来奖励参与者匿名点(AP)，从而提高任何存款或混币协议中的隐私级别。

{% hint style="warning" %}
_Tornado Cash匿名挖矿激励措施于2020年12月18日开始，将于2021年12月18日结束。_
{% endhint %}

个人将存款存入任何一个支持的匿名池(ETH, WBTC, DAI或cDAI)，他们的存款留在池中的期间，可以获得每个区块固定金额的AP奖励。这些点数可以在领取后兑换成TORN。

### 匿名点(AP)

_在本文撰写时，读者应该意识到，一些较低面额的存款，由于提取、兑换和交换匿名点数所需的gas成本，不会产生正回报。_

一个社区成员创建了一个关于[挖矿的电子表](https://torn.community/t/anonymity-mining-spreadsheet/720)资源，通过估算领取奖励所需的费用，帮助计算每个池和其中设置的每个面值的年收益率百分比(APY)。在期望获得收益之前，**强烈建议查看这一资源并计划自己的行动。**在电子表格的底部，您可以通过选择相关的选项卡来查看每个池。 

### 如何获得AP

1\. 在点击“Connect”和“Deposit”之前，通过下拉菜单选择要存款的金额和资产。

![](../.gitbook/assets/m3fh0gl.png)

2\. 将你的存款凭证做好记录并安全备份，**不要与任何人分享，否则可能会失去存款和奖励。**

![](../.gitbook/assets/vhustru.png)

3\. 生成证明并提交交易。

4\. 你的存款现在应该可以在页面的底部看到，你可以在这里跟踪它赚多少AP；记住，你的存款保持有效的时间越长，你赚的AP越多。

![](../.gitbook/assets/k6juetp.png)

_有效的(未提款的)凭证称为“unspent”凭证。_

### 如何领取AP

1\. 首先，你必须创建一个挖矿账户，并将这些凭证存储在链上，以便容易恢复(需要一次交易)，**就像存款凭证一样，你不应该与任何人共享你的挖矿恢复密钥**，并确保在一个安全的地方备份它。硬件钱包不支持此功能，因此鼓励直接储存显示的信息\_。\_

![](../.gitbook/assets/lskzkgk.png)

2\. 通过提供未使用的凭证并将其取出到指定的地址，然后决定是否使用中继器(_为了保持存款的匿名性，总是建议使用中继器_)，这些操作将使凭证进入“spent”状态。

![](../.gitbook/assets/aid86cj.png)

**记住，即使在取款后也要保密你的存款凭证，因为它们仍然保留着兑换AP的效力。**

![](../.gitbook/assets/bpsqxxr.png)

3\. 访问应用程序的挖矿路线，并输入您的已花费凭证，您可能会面临以下情况之一。

* **认领已花费凭证的成功情况**：点击“Claim reward”按钮，通过或不通过中继器来提交交易，一旦确认，你的AP余额应更新来反应该行动。

![](../.gitbook/assets/e9jyqhu.png)

* **认领已花费凭证的不成功情况:** _：“Warning: The note is not yet ready for anonymity mining. You can wait few days before trying again” - 这意味着Merkle树暂时不同步，需要更新交易。

![](../.gitbook/assets/i6qtr0f.png)

更新Merkle树可能是一个昂贵的过程，**建议拥有少量存款的用户等待拥有较大的存款的用户来更新Merkle树，这可能需要几天到一周的时间。** 如果你想查看关于当前待办批次的事件。点击“Show mining note information”超链接，在这里你也可以通过“Update trees”按钮支付交易费用来同步与你的提款相关的树。

![](../.gitbook/assets/d8dmxjj.png)

### 如何兑换AP

1\. 导航到挖矿页面的“Swap”选项卡，可以通过页面顶部的第二个导航栏访问该选项卡。

![](../.gitbook/assets/ahrjxbq.png)

2\. 输入要求兑换的AP金额或选择“Maximum”选项来转换你的有效余额。在这个输入下面，关于当前AP/TORN兑换率和奖励输出的信息将显示。提供想要接收奖励的地址，生成证明，并通过或不通过中继器提交交易。

![](../.gitbook/assets/wo55lao.png)

3\. 如果所有步骤都正确执行，TORN将被转移到本节第二步中提供的接收地址。

### 小结

祝贺你，你已经成功地参与了匿名挖矿！

我们推荐在决定参与任何匿名集挖矿前，用户也应该意识到，[AP/TORN兑换率](https://duneanalytics.com/luckyallocator/Daily-AP-TORN-Rate-v2) 取决于供给和需求，因此，**越多的人领取，比率就越高，越少的人领取，比率就越低。**

要了解更多关于匿名挖掘的信息，请查找以下资源：

* [Tornado.Cash 治理提案文章](https://tornado-cash.medium.com/tornado-cash-governance-proposal-a55c5c7d0703)
* [Tornado.Cash 匿名挖矿文章](https://tornado-cash.medium.com/gas-price-claimed-anonymity-mining-a-victim-but-now-everyone-can-claim-ap-5441aaa32a1a)
* [匿名挖矿解释 (技术))](https://torn.community/t/anonymity-mining-technical-overview/15)

_感谢_ [_@sockawoo_](https://torn.community/u/sockawoo) _和_ [_@ethdev_](https://torn.community/u/ethdev) _协助评审_

_编写_ [_**@xgozzy**_](https://torn.community/u/xgozzy/summary)\_\_

# 如何成为中继器？

[Tornado Cash 治理提案#10](https://tornadocash.eth.link/governance/10)执行后，任何人都可以成为Tornado Cash的中继器。

{% hint style="success" %}
能在Tornado Cash UI中列出的中继器，唯一条件是至少质押 `300个TORN`。 这个最低质押数可以随时通过治理投票来改变。
{% endhint %}

中继器是Tornado Cash生态系统的重要组成部分。它们的使用保证了隐私，因为它们解决了“支付交易费用困境”：如何在保持匿名的同时从池中支付代币取款的费用？

因此，中继器充当第三方并负责整个提款。他们直接从提款金额中扣除金额来支付交易费用。他们从中收取额外的服务费用。

自[中继器注册表提案](https://tornadocash.eth.link/governance/10)执行以来，协议将通过`StakingReward`合约直接从中继者的质押余额中收取每次提款的费用。该费用的百分比可能因池而异，并且也可能通过链上治理进行更改。

协议收取的费用，暂时固定为`0.3%`，一些池仍然不收费，要么是因为金额太小而无法分配费用（0.1 ETH、100 DAI/USDT、1000 DAI/USDT），要么是因为 Uni v3（所有cDAI）上没有足够的流动性。

## 如何成为中继器？

通过中继器注册界面 (UI) ，通过**6个简单的步骤**任何人都可以成为该协议的中继器。

您将在下方找到加入我们的中继器所需的一切，并在Tornado Cash去中心化中继器注册表中列出。

### 1. 要求: 意识并接受潜在的风险

在您承诺作为Tornado Cash的中继器之前，您需要了解并接受协议中继器的所有潜在风险。

### 2. 设置中继器

第一个具体步骤是在您的计算机上运行以太坊主网的 Tornado Cash Relayer程序。所有步骤都在协议的 github中进行解释说明。要成功完成此任务，您必须仔细遵循[这里说明](https://github.com/tornadocash/tornado-relayer#deploy-with-docker-compose).

{% embed url="https://github.com/tornadocash/tornado-relayer#deploy-with-docker-compose" %}

完成后，您需要在输入框中输入您的网址。

![](../.gitbook/assets/2.png)

### 3. 设置ENS子域

下一步包括：

* 为您的中继器创建一个ENS域名，
* 设置主网子域，
* 根据此特定格式将带有Relayer URL的TXT记录添加到主网子域：

#### **以太坊中继器 (强制)**

| TXT record              |
| ----------------------- |
| mainnet-tornado.xxx.eth |
| goerli-tornado.xxx.eth  |

#### **侧链中继器 (可选)**

您还可以添加带有相应TXT记录的子域，以支持以太坊以外的其他链。侧链中继器使用不同版本的中继器软件。您可以[在此处](https://github.com/tornadocash/tornado-relayer/blob/light/README.md)。

| TXT record                |
| ------------------------- |
| bsc-tornado.xxx.eth       |
| gnosis-tornado.xxx.eth    |
| polygon-tornado.xxx.eth   |
| optimism-tornado.xxx.eth  |
| arbitrum-tornado.xxx.eth  |
| avalanche-tornado.xxx.eth |

#### **Nova中继器 (可选)**

Tornado Cash Nova使用自己的软件版本。如果您想成为Tornado Cash Nova的中继器，您将[在此处](https://github.com/tornadocash/tornado-pool-relayer#deploy-with-docker-compose)找到要遵循的说明。

| TXT record          |
| ------------------- |
| gnosis-nova.xxx.eth |

![](../.gitbook/assets/3.png)

### 4. 设置Workers

Worker是允许中继器向用户发送ZK证明的地址。默认情况下，第一个Worker是ENS域所有者的地址。

为确保更高级别的安全性，我们建议您设置多个Worker。

只有主网要求您注册Worker。所有其他网络不需要注册Worker。

![](<../.gitbook/assets/4 (1).png>)

### 5. 质押

随着去中心化中继器注册表的执行，质押条件的介绍以在Tornado Cash UI上列出。**现在已将质押TORN功能添加到推荐的中继器列表中。**

Tornado Cash治理目前设定的最低质押数量为 **`300个TORN`**。Tornado Cash治理可以随时更改此阈值。

当在Tornado Cash池上使用中继器时，`StakingReward`合约会自动从该中继器质押余额中扣减少量的TORN，中继器需要始终保持其质押至少 `300个TORN`，必须牢记这一要素。

之后，这些收取的费用将分配给将TORN代币锁入DAO的用户。TORN代币通常锁入以参与链上治理（提案和投票）。[您可以在此论坛帖子](https://torn.community/t/proposal-relayer-registry-setting-parameters-after-audit/2134) 和 [质押TORN文档页面](staking.md)中找到更多信息。

{% hint style="warning" %}
中继器质押的TORN不可以提取，也不会退还。
{% endhint %}

![](../.gitbook/assets/5.png)

### 6. 摘要：最后验证和注册

最后要说的，但不是最不重要的，我们建议您在注册前**仔细检查**摘要中的所有信息。

![](../.gitbook/assets/6.png)

_欢迎加入中继者队伍！多亏有你，隐私才能得到更好的尊重_ 💚



_编写_ [_**@bt11ba**_](https://torn.community/u/bt11ba/) _和_ [_**@ayefda**_](https://torn.community/u/ayefda)

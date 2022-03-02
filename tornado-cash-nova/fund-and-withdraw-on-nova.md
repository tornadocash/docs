# 在Nova存款和提款

Tornado Cash的工作原理是断开源地址和目标地址之间的链上链接。为此，协议需要将代币从一个地址存入池中，然后通过另一个地址提取。

Tornado Cash Nova的这一原则保持不变。对于传统的固定金额池，这两个动作是工具效率的核心：

* “存款”流程，
* “提款”流程。

## 存款流程 <a href="#funding-process" id="funding-process"></a>

与传统Tornado Cash池相比，最大的新颖之处在于**存款金额不再是预定义的**。用户可以在钱包余额的范围内选择自定义金额。

因此，如果您想将0.4 ETH放入池中，您可以一次完成所有操作，而不是使用传统的0.1 ETH池进行4次存款。

![](https://i.imgur.com/rqmzdgG.gif)

### 它是如何工作的？ <a href="#how-does-it-work" id="how-does-it-work"></a>

#### **第一笔存款 💰**

* 第一步是通过Metamask钱包地址登录Tornado Cash Nova。
* •	您的账户尚未设置时（右上角的`Set up account` 按钮为激活状态）。设置您的账户，您需要：
  * **点击`Set up account`**按钮：您连接的钱包地址将注册到Nova，无需存入任何代币。设置账户后，使您能够接收Nova其他账户的转账或存款。
  * **选择您的登录地址作为接收地址**：通过将代币存入池中，您的账户（带有其隐蔽地址和隐蔽密钥）将被自动创建。存入的资金将补足您的受隐蔽余额。
  * **选择另一个注册地址**：代币将添加到所选接收人地址的隐蔽余额中。此接收人地址需要是已经注册到Nova中的隐蔽地址。

登录时，`Recipient address`默认填写您的登录地址。您可以根据实际情况更改。

如果您设置了一个新账户，您将能够稍后登录，检查您的Tornado隐蔽余额或使用您的隐蔽地址或隐蔽密钥接收转账。

_有关如何使用这些选项登录或在哪里可以找到您的隐蔽密钥的所有信息，请访问_ [logging-in-tornado-cash-nova.md](logging-in-tornado-cash-nova.md "mention")_。_

#### **后续存款 💸**

以后存款与第一个存款的规则相同，但账户已设置。

通过使用您的隐蔽地址/密钥登录，您可以根据需要将您选择的金额存入您选择的隐蔽地址。

⚠️由于是测试版，目前存款上限为每笔1 ETH。 但是，如果社区希望提高此上限，则可以通过治理提案更改1 ETH的上限。

## 提款流程 <a href="#withdrawing-process" id="withdrawing-process"></a>

![](https://i.imgur.com/qn9eJXS.gif)

要从Nova池中提取资金，您可以：

* 从一组四个预定数量（0.1、0.3、0.5 和 1 ETH）中选择，
* 通过`Set custom`按钮自定义金额。

### 提款的自定义选项 <a href="#custom-option-for-withdrawal" id="custom-option-for-withdrawal"></a>

**只有在充分了解以下情况并完全相信自己的行为后，才能选择自定义选项。**

强烈建议选择四个建议金额之一，因为它可以让您的提款金额与其它人的提款金额混淆一体，从而保护您的隐私。

但是，使用自定义金额，如果出现以下情况，可能会在您的初始存款和取款之间推断出有关联：

* 初始存款金额和取款金额完全相同，
* 存款和取款的金额可以很容易地通过一个金额联系起来。

_比如，0.42ETH的存款可以与恰好0.42 ETH或两笔0.21 ETH的提款相关联，这可能会损害匿名性。如果提款金额用0.391 ETH，隐私就能得到了更好的保护，因为0.42和0.391之间没有明显的联系。_

### 通过Gnosis链(Layer2)进行的交易<a href="#transctions-through-gnosis-chain-l2" id="transctions-through-gnosis-chain-l2"></a>

交易手续费更便宜，使用Gnosis链（前xDAI链）作为Layer2层。为此，在以太坊主网和 Gnosis链的WETH之间使用了一座桥梁。

因此，为了防止垃圾交易攻击导致桥超载，提款金额限制必须大于0.05 ETH。

_编写_ [_@ayefda_](https://torn.community/u/ayefda)

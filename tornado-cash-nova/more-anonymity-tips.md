# 更多匿名窍门

对于本节，我们建议您先参考 [tips-to-remain-anonymous.md](../general/tips-to-remain-anonymous.md "mention") 教程，该教程中提到的所有要点仍然适用于Tornado Cash Nova。

快速提醒一下，这些窍门包括：

* 使用VPN，
* 不共享隐蔽密钥或访问此隐蔽地址
* 如果下载隐蔽密钥，将此密钥保存在安全的地方，
* 使用后清除数据，
* 避免对所有交易使用相同的API token，
* 在存款和取款之间留有充分的时间间隔，
* 使用多个地址进行提款。

然而，凭借其新功能，Tornado Cash Nova需要进一步的预防措施以保持匿名性。

## 中继器的使用 <a href="#use-of-relayers" id="use-of-relayers"></a>

交易需要支付gas费。对于隐蔽转账和取款，有两种交易方式需用ETH支付gas费用。您可以选择**您的钱包或中继器支付**。

如果使用的ETH可与您的身份相关联，即通过您的钱包支付这笔gas费可能会损害交易的匿名性。因此，**建议使用中继器来保护隐私**。

![Tips1](https://i.imgur.com/PsZ89Ym.png)

## 提款金额的选择 <a href="#choice-of-withdrawal-amounts" id="choice-of-withdrawal-amounts"></a>

自定义金额功能提供了更大的灵活性和使用自由度。但是，如果使用不慎，它可能会损害您的隐私

### 选择预定义的提款金额 <a href="#choosing-predefined-amounts-for-withdrawals" id="choosing-predefined-amounts-for-withdrawals"></a>

![Tips2](https://i.imgur.com/dKYvNQT.png)

强烈建议选择四个预定义金额之一，因为它可以让您的提款与其它人提款混淆一体并保持匿名。

您仍然可以使用`Set custom`按钮自定义金额。但是，根据自定义的金额，如果出现以下情况，可能会在您的初始存款和提款之间推断出关联：

* 初始存款金额和取款金额完全相同，
* 存款和提款的金额可以很容易地通过一个金额联系起来。

比如，0.42ETH的存款可以与恰好0.42 ETH或两笔0.21 ETH的提款相关联，这可能会损害匿名性。如果提款金额用0.391 ETH，隐私就能得到了更好的保护，因为0.42和0.391之间没有明显的联系。

只有在充分了解这些事实并完全相信自己的行为的情况下，才能选择自定义金额选项。

_编写_ [_@ayefda_](https://torn.community/u/ayefda)

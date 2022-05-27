# Staking

Since its inception, the TORN token is used by Tornado Cash users for governance. Its main utility is to allow the suggestion of proposals & voting both in-chain (through locked TORN for governance proposals) and off-chain (on Snapshot).

Since the execution of [Tornado Cash 10th governance proposal](https://tornadocash.eth.limo/governance/10), TORN token has gained one other useful utility. Indeed, **with the introduction of a decentralized relayer register,** **a staking reward has been implemented for all holders with locked TORN in the governance contract.**

[TORN](torn.md) holders can still lock their tokens into the governance contract as they used to for governance purposes. The significant difference is that they are now able to receive a portion of the fees collected by the protocol from relayers. Obviously, the proportion of the reward will be equal to the proportion of their locked TORN.

#### **FROM WHERE THESE COLLECTED FEES COME FROM ?**

The collection of these fees was made possible by the implementation of a decentralized relayer registry. In order to be listed on the protocol UI, relayers need to stake a given amount of TORN (currently set by governance at `300 TORN`) and keep enough TORN locked (\~`40 TORN` at the moment in April 2022) to be able to pay back the transaction fee to the staking contract. The functioning of this relayer registry is more extensively explained [on this forum post](https://torn.community/t/proposal-relayer-registry-setting-parameters-after-audit/2134) & on the [Relayer Registry documentation page](how-to-become-a-relayer.md).

In a nutshell, for each withdrawal through the relayer method, the chosen relayer has to pay a fee to the protocol from the staked balance (that should still be maintained above the `300 TORN` threshold). Currently, this fee has been fixed at `0.3%` by the governance and can be changed at any time through an on-chain proposal & vote.

### How to Stake TORN token ?

First, [connect your wallet to Tornado Cash](./tornado-cash-classic/how-to-connect-your-wallet.md).

As mentioned above, the process to lock TORN tokens has remained unchanged.

* It happens here ➡️ [https://tornadocash.eth.limo/governance](https://tornadocash.eth.limo/governance) ⬅️, by clicking on **`Manage`**, then going on the **`Lock`** tab
* The governance contract need to be approved in order to allow the transfer of your tokens to the smart contract. To do so, you need to click on the **`Approve`** button
* Once the approval is confirmed, you can chose the amount of token to lock, then click on **`Lock`**
* All you have to do after that is to confirm the transaction in your wallet & wait for the confirmation to come through

![](../.gitbook/assets/c05e5a1813edad280544b627b24002dc8d5adcf2.png)

### How to Claim Your Staking Reward ?

Now that your TORN tokens have stayed nice & warm locked in the governance contract, you are able to claim your staking reward. How to do that? Everything is still happening here ➡️ [https://tornadocash.eth.link/governance](https://tornadocash.eth.limo/governance) ⬅️

As soon as you log in the page, you will be able to see your staking reward at the top, just waiting for you to collect it 💰

![](../.gitbook/assets/head.png)

* Click **`Manage`** -> **`Claim`** tab -> **`Claim`** _button._

![](<../.gitbook/assets/claim (1).png>)

_That's it, we're done, easy peasy lemon squeezy_ :wink:

\_\_

_Written by_ [_**@bt11ba**_](https://torn.community/u/bt11ba/) _&_ [_**@ayefda**_](https://torn.community/u/ayefda)

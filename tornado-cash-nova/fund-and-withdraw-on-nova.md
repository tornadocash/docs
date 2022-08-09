# Fund & Withdraw on Nova

Tornado Cash works by breaking the on-chain link between source & destination addresses. To do so, the protocol needs tokens to be deposited in a pool from one address, then to be withdrawn through another address.

This principle remains the same for Tornado Cash Nova. As for traditional fixed amount pools, these two actions are core to the efficiency of the tool:

* The “Funding” process,
* The “Withdrawing” process.

## Funding Process <a href="#funding-process" id="funding-process"></a>

The great novelty compared to traditional Tornado Cash pools is that **deposited amounts are no longer predefined.** Users can choose a customized amount within the capacity of their wallet balance.

Therefore, if you want to put 0.4 ETH in the pool, you can do it all at once rather than making four separate transactions with the traditional 0.1 ETH pool.

![](https://i.imgur.com/rqmzdgG.gif)

### How Does It Work? <a href="#how-does-it-work" id="how-does-it-work"></a>

#### **The First Deposit 💰**

* The first step is to log in Tornado Cash Nova through a Metamask account.
* Your account is not set yet (button `Set up account` available on the top right corner). To set up your account, you can either:
  * **Click on `Set up account`**: your logged-in address will be registered to Nova without needing to deposit any tokens. This action will enable you to receive transfers or deposits within the pool from any another address.
  * **Choose your logged-in address as a recepient address**: by depositing tokens into the pool, your account (with its shielded address & shielded key) will be automatically created. The deposited funds will come top up your shielded balance.
  * **Choose another registered address:** tokens will be added to the shielded balance of the chosen recipient address. This recipient address needs to be a shielded address that was formerly registered to the pool.

When you log in, the `Recipient address` is filled by default with your logged-in address. You can change it depending on how you want to use the tool.

If you set a new account, you will be able to log into the pool later, check your Tornado shielded balance or receive shielded transfers by using either your shielded address or shielded key.

_All information about how to use these elements to log in or where to find your shielded key are available on_ [logging-in-tornado-cash-nova.md](logging-in-tornado-cash-nova.md "mention")_._

#### **The following deposits 💸**

The following deposits answer to the same rules that the first one, except that the account is already set.

By logging into the pool with your shielded address / key, you can deposit your chosen amounts to your chosen shielded address as you wish to.

⚠️ Since it is a beta version, deposits are currently limited to 1 ETH/transaction.\
However, if the community wishes to increase this limit, the 1 ETH cap amount can always be changed through a governance proposal.

## Withdrawing Process <a href="#withdrawing-process" id="withdrawing-process"></a>

![](https://i.imgur.com/qn9eJXS.gif)

To withdraw funds from the Nova pool, you can either:

* choose from a set of four predetermined amounts (0.1, 0.3, 0.5 & 1 ETH),
* choose a completely customized amount by going through the button `Set custom`.

### Custom Option For Withdrawal <a href="#custom-option-for-withdrawal" id="custom-option-for-withdrawal"></a>

**The custom option should only be chosen with full knowledge of the following facts and in complete confidence in your actions.**

To maintain your privacy, choosing one of the four suggested amounts is strongly recommended as it will allow your withdrawal to blend with the crowd.

Indeed, depending on the chosen amount, a connection might be deduced between your initial fund transaction and your withdrawal if:

* the initially funded amount & the withdrawn amount are exactly the same,
* the funded & withdrawn amounts can be easily linked through a sum.

_For instance, a deposit of 0.42 ETH can be linked to a withdrawal of exactly 0.42 ETH or two times 0.21 ETH, which might compromise anonymity. However, with a withdrawal of 0.391 ETH, privacy is better preserved as there is no obvious link between the 0.42 & 0.391 amounts._

### Transactions through Gnosis Chain (L2) <a href="#transctions-through-gnosis-chain-l2" id="transctions-through-gnosis-chain-l2"></a>

For cheaper transactions, Gnosis Chain (former xDAI Chain) is used as a Layer-2. To this end, a bridge is used between ETH from the Mainnet & WETH from Gnosis Chain.

Therefore, to prevent spam attacks that will overload the bridge, the withdrawal amount has to be larger than 0.05 ETH.

### Bridge daily limits

Daily limits on token exits (bridging tokens from Gnosis Chain to Ethereum) have been established for several tokens on the Gnosis chain.
For more information about the daily limits please visit Gnosis Chain documentation:
https://developers.gnosischain.com/for-users/bridges/bridge-daily-limits

_Written by_ [_@ayefda_](https://torn.community/u/ayefda)

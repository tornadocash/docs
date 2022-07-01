---
description: Staking options for $TORN
---

# Staking

Since its inception, the TORN token is used by Tornado Cash users for governance. Its main utility is to allow the suggestion of proposals & voting both in-chain (through locked TORN for governance proposals) and off-chain (on Snapshot).

Since the execution of [Tornado Cash 10th governance proposal](https://tornadocash.eth.limo/governance/10), TORN token has gained one other useful utility. Indeed, **with the introduction of a decentralized relayer register,** **a staking reward has been implemented for all holders with locked TORN in the governance contract.**

[TORN](../torn.md) holders can still lock their tokens into the governance contract as they used to for governance purposes. The significant difference is that they are now able to receive a portion of the fees collected by the protocol from relayers. Obviously, the proportion of the reward will be equal to the proportion of their locked TORN.

#### **FROM WHERE THESE COLLECTED FEES COME FROM ?**

The collection of these fees was made possible by the implementation of a decentralized relayer registry. In order to be listed on the protocol UI, relayers need to stake a given amount of TORN (currently set by governance at `300 TORN`) and keep enough TORN locked (\~`40 TORN` at the moment in April 2022) to be able to pay back the transaction fee to the staking contract. The functioning of this relayer registry is more extensively explained [on this forum post](https://torn.community/t/proposal-relayer-registry-setting-parameters-after-audit/2134) & on the [Relayer Registry documentation page](../how-to-become-a-relayer.md).

In a nutshell, for each withdrawal through the relayer method, the chosen relayer has to pay a fee to the protocol from the staked balance (that should still be maintained above the `300 TORN` threshold). Currently, this fee has been fixed at `0.3%` by the governance and can be changed at any time through an on-chain proposal & vote.

### Where to stake $TORN ?

#### 1. Tornado Cash

The first option to stake is the usual URL for Tornado Cash. This has been available since February 2022. You will find a step-by-step tutorial here.

{% content-ref url="tornado-cash.md" %}
[tornado-cash.md](tornado-cash.md)
{% endcontent-ref %}

#### 2. Altornado

An alternative option to stake $TORN has been brought by the community. The need for a staking UI and in the long run, the necessity for a Tornado Cash full **alternative UI** made this happen. Altornado provides the community with an intuitive and rich user experience, using the same Tornado Cash contracts.\
You will always have information about your wallet as well as information about your future rewards depending on the amount you want to stake.

{% content-ref url="altornado.md" %}
[altornado.md](altornado.md)
{% endcontent-ref %}

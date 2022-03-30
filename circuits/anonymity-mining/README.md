# Anonymity Mining

The anonymity mining protocol underpins the [Anonymity Mining Program](../../anonymity-mining.md), which rewards users according to the block duration that they wait before withdrawing their deposits.

Anonymity Mining uses a Tornado Trees contract as a ZK-efficient register of deposit and withdrawal transactions, which enables users to make efficient proofs regarding their usage.

{% content-ref url="tornado-trees.md" %}
[tornado-trees.md](tornado-trees.md)
{% endcontent-ref %}

Once deposits and withdrawals are registered into the Tornado Trees contract, they become eligible for having their rewards claimed into a shielded AP account.

{% content-ref url="mining-rewards.md" %}
[mining-rewards.md](mining-rewards.md)
{% endcontent-ref %}

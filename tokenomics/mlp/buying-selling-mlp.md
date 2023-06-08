---
description: Buying and selling MLP can be done through the MLPRewardRouter.
---

# Buying / Selling MLP

To buy MLP, call `mintAndStakeMlp`

* `_token`: the token to buy MLP with
* `_amount`: the amount of token to use for the purchase
* `_minUsdg`: the minimum acceptable USD value of the MLP purchased
* `_minMlp`: the minimum acceptable MLP amount

To sell MLP, `unstakeAndRedeemMlp`

* `_tokenOut`: the token to sell MLP for
* `_mlpAmount`: the amount of MLP to sell
* `_minOut`: the minimum acceptable amount of `tokenOut` to be received
* `_receiver`: the address to send `tokenOut` to

{% hint style="info" %}
Note that MLP can only be redeemed up to the `reservedAmount`, which is based on the amount of open interest, if the pool has been fully redeemed up to the `reservedAmount` then redeemers will need to wait for positions to close before further redemptions can be done, in this scenario the borrowing fee APR would be very high so liquidity providers will be incentivised to mint MLP and traders will be incentivised to close positions
{% endhint %}

The price of MLP can be retrieved from the MlpManager.

* The buy price would be getAum(true) / mlpSupply&#x20;
* The sell price would be getAum(false) / mlpSupply

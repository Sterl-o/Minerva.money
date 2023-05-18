---
description: The PriceFeed contract accepts submissions from the price feed keeper.
---

# 🏷 Price Feeds

The keeper calculates prices using the median price of Binance, Bitfinex and Coinbase. There are two types of keepers:

* Price feed keeper: submits prices routinely for swaps
* Position keeper: submits prices when executing a position

The vault uses the price from the keeper if it is within a configured percentage of the corresponding Chainlink price. If the price exceeds this threshold then a spread would be created between the bounded price and the Chainlink price, this threshold is based on the historical max deviation of the Chainlink price from the median price of reference exchanges. For example, if the max deviation is 2.5% and the price of the token on Chainlink is $100, if the keeper price is $103, then the pricing on the vault would be $100 to $103. When opening a long position, the higher price is used and when closing the lower price is used, for short positions, the lower price is used when opening and the higher price is used for closing.\
\
Prices from the keeper also have an expiry of five minutes, if the last price has been submitted more than five minutes ago, the Chainlink price will be used instead.\
\
For liquidations, these can only occur if the Chainlink price reaches the liquidation price for a position.\
\
Aside from the keeper nodes, watcher nodes are also ran to verify that the prices submitted by the keepers have not been tampered with. Watcher nodes continually compute the median price and compare this with the prices submitted by keepers, if the prices submitted by a keeper does not match the computed median price, then the watcher sends a transaction to enforce a spread between the keeper price and the Chainlink price. For example, if the keeper is operating normally and the Chainlink price is $100 while the keeper price is $101, there would be no spread and $101 would be used for pricing, if the keeper is not operating normally, and the watcher sends a transaction to enforce a spread, then the pricing used would be $100 to $101.\
\
The keepers and watchers are currently run by separate contributors, as we become more certain of the watcher’s reliability, we can open the watcher to be run by any user to receive notifications. Multiple watcher accounts are currently setup to have the ability to send the transaction to enable spreads. It would also be possible to allow more users to send the transaction to enforce a spread by requiring the account to stake or lock a minimum amount of MINE tokens.\
\
The price feed and position keepers can be further decentralized by using [Chainlink keepers](https://docs.chain.link/docs/chainlink-keepers/introduction/).\
\
As the price feed contract may be updated to improve its security, the most reliable way to find the contract address for it would be to check the value of `Vault.priceFeed`.

{% hint style="info" %}
Additional contract level checks have been added. On each fast price update, contract variables store the percentage change in price for the update as well as the percentage change of the Chainlink price since the last update, if the cumulative percentage change in the fast prices over a duration exceeds the cumulative percentage change in the Chainlink prices by a configured threshold, the spread between the fast price and Chainlink price will be automatically enabled. The configuration for this is in `Vault.priceFeed.secondaryPriceFeed.maxCumulativeDeltaDiffs`.
{% endhint %}

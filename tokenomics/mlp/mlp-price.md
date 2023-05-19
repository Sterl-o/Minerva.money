---
description: >-
  The price of MLP is based on the total worth of all tokens in the pool and
  factors in pending profits and losses from all currently opened positions.
---

# MLP Price

* Buy price: `mlpManager.getPrice(true)`
* Sell price: `mlpManager.getPrice(false)`

Since there might be a spread for token pricing, passing in `true` into the `getPrice` function returns the maximum price at that point in time, while passing in false returns the minimum price.

For the calculation of pending PnL for shorts the `mlpManager.shortsTracker.globalShortAveragePrices` value should be used instead of `vault.globalShortAveragePrices`.

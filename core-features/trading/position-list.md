# Position List

A list of position details can be retrieved by calling Reader.getPositions

* `_vault`: the vault contract address&#x20;
* `_account`: the account of the user
* `_collateralTokens`: an array of collateralTokens
* `_indexTokens`: an array of indexTokens
* `_isLong`: an array of whether the position is a long position

The returned positions will be in the order of the query, for example, given the following inputs:

* `_collateralTokens`: \[WBTC.address, WETH.address, USDC.address]&#x20;
* `_indexTokens`: \[WBTC.address, WETH.address, WBTC.address]
* `_isLong`: \[true, true, false]

The position details would be returned for

* Long BTC position, positionIndex: 0
* Long ETH position, positionIndex: 1
* Short BTC position, positionIndex: 2

The returned array would be a list of values ordered by the positions:

* size&#x20;
  * position size in USD
  * value at: positionIndex \* 9
* collateral
  * position collateral in USD
  * value at: positionIndex \* 9 + 1
* averagePrice
  * average entry price of the position in USD
  * value at: positionIndex \* 9 + 2
* entryFundingRate
  * a snapshot of the cumulative funding rate at the time the position was entered
  * value at: positionIndex \* 9 + 3
* hasRealisedProfit
  * 1 if the position has a positive realised profit, 0 otherwise
  * value at: positionIndex \* 9 + 4
* realisedPnl&#x20;
  * the realised PnL for the position in USD
  * value at: positionIndex \* 9 + 5
* lastIncreasedTime
  * timestamp of the last time the position was increased
  * value at: positionIndex \* 9 + 6
* hasProfit
  * 1 if the position is currently in profit, 0 otherwise
  * value at: positionIndex \* 9 + 7
* delta
  * amount of current profit or loss of the position in USD
  * value at: positionIndex \* 9 + 8

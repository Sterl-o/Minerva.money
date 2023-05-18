# Closing / Decreasing a Position

To close

* Call `PositionRouter.createDecreasePosition` with parameters:
  * `_path`: \[collateralToken] or \[collateralToken, tokenOut] if a swap is needed
  * `_indexToken`: the index token of the position
  * `_collateralDelta`: the amount of collateral in USD value to withdraw
  * `_sizeDelta`: the USD value of the change in position size
  * `_isLong`: whether the position is a long or short
  * `_receiver`: the address to receive the withdrawn tokens
  * `_acceptablePrice`: the USD value of the min (for longs) or max (for shorts) index price acceptable when executing the request
  * `_minOut`: the min output token amount
  * `_executionFee`: can be set to PositionRouter.minExecutionFee
  * `_withdrawETH`: only applicable if WETH will be withdrawn, the WETH will be unwrapped to ETH if this is set to true
  * `_callbackTarget`: an optional callback contract, this contract will be called on request execution or cancellation
* After this transaction is sent a keeper will execute the request, the request will either be executed or cancelled
* If the position cannot be decreased for reasons such as the `_acceptablePrice` not being fulfillable then the request will be cancelled and there will be no change to the position
* `_minOut` can be zero if no swap is required

&#x20;or decrease an existing position:

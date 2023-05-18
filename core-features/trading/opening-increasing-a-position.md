# Opening / Increasing a Position

To open or increase the size of an existing position:

* Approve the PositionRouter as a Router plugin for your account
  * Router.approvePlugin(PositionRouter address)
* Approve the Router contract for the token and amount you would deposit as collateral for the position
* Call `PositionRouter.createIncreasePosition` with parameters:
  * `_path`: \[collateralToken] or \[tokenIn, collateralToken] if a swap is needed
  * `_indexToken`: the address of the token you want to long or short
  * `_amountIn`: the amount of tokenIn you want to deposit as collateral
  * `_minOut`: the min amount of collateralToken to swap for
  * `_sizeDelta`: the USD value of the change in position size&#x20;
  * `_isLong`: whether to long or short
  * `_acceptablePrice`: the USD value of the max (for longs) or min (for shorts) index price acceptable when executing the request
  * `_executionFee`: can be set to PositionRouter.minExecutionFee
  * `_referralCode`: [referral code](../referall.md) for affiliate rewards and rebates
  * `_callbackTarget`: an optional callback contract, this contract will be called on request execution or cancellation
* After this transaction is sent a keeper will execute the request, the request will either be executed or cancelled
* If the position cannot be increased for reasons such as the `_acceptablePrice` not being fulfillable or there being insufficient liquidity then the request will be cancelled and funds will be sent back to the msg.sender that called `PositionRouter.createIncreasePosition`
* `_minOut` can be zero if no swap is required
* USD values for \_sizeDelta and \_price are multiplied by (10 \*\* 30), so for example to open a long position of size 1000 USD, the value 1000 \* (10 \*\* 30) should be used

# Swap

**To execute a swap:**

* Approve the Router contract for the token and amount you would like to swap
* Call Router.swap with parameters:
  * \_path: \[tokenIn, tokenOut]
  * \_amountIn: amount of tokenIn to swap
  * \_minOut: minimum expected output amount
  * \_receiver: address of the receiver of tokenOut
* The function will revert if the amount of tokenOut sent to the receiver is less than _\__minOut

**To get swap amounts before execution:**

* Call Reader.getMaxAmountIn with parameters:
  * \_vault: address of the vault
  * \_tokenIn: address of token that will be given
  * \_tokenOut: address of token to be received
  * The max amount of tokenIn that can be swapped will be returned
* Call Reader.getAmountOut with parameters:
  * \_vault: address of the vault
  * \_tokenIn: address of token that will be given
  * \_tokenOut: address of token to be received
  * \_amountIn: amount of tokenIn to swap
  * Two values will be returned, the first is the amount out after fees, and the second is the fee amount
  * The fee amount will be in terms of tokenOut

Tokens have a usdgAmount in the Vault contract used for some calculations, this amount is updated on minting of MLP, redemption of MLP and swaps based on the price of the token at the time. Due to price fluctuations this value may drift slightly from the actual USD value of the tokens in the pool, the usdgAmount is periodically updated to re-align values.

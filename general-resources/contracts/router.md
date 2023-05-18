---
description: The Router contracts provide convenience functions on top of the vault.
---

# 📨 Router

The [Position Router](./) contract handles a two part transaction process for increasing or decreasing long / short positions, this process helps to reduce front-running issues:

1. A user sends the request to increase / decrease a position to the PositionRouter
2. A keeper requests the index price from an aggregate of exchanges
3. The keeper then executes the position at the current index price
4. If the position cannot be executed within the allowed slippage the request is cancelled and the funds are sent back to the user

A user can execute the position on their own if three minutes have passed between the request transaction and the execution transaction. The function of the position keepers is to provide convenience and the protocol can continue to operate even without these keepers.\
\
For swaps, the base fee is 0.25%, while price feeds update within 0.12% price movements, this helps to reduce front-running issues.

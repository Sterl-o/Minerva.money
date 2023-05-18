---
description: >-
  The maximum sum of all position sizes is limited by the amount of tokens there
  are in the pool and any additional caps.
---

# Query Available Amounts

**To calculate the available amount of liquidity for long positions:**

* indexToken: the address of the token to long
* Available amount in tokens: Vault.poolAmounts(indexToken) - Vault.reservedAmounts(indexToken)
* Available amount in USD: PositionRouter.maxGlobalLongSizes(indexToken) - Vault.guaranteedUsd(indexToken)
* The available liquidity will be the lower of these two values
* PositionRouter.maxGlobalLongSizes(indexToken) can be zero, in which case there is no additional cap, and available liquidity is based only on the available amount of tokens

**To calculate the available amount of liquidity for short positions:**

* indexToken: the address of the token to short
* collateralToken: the address of the stablecoin token to be used as collateral
* Available amount in tokens: Vault.poolAmounts(collateralToken) - Vault.reservedAmounts(collateralToken)
* Available amount in USD: PositionRouter.maxGlobalShortSizes(indexToken) - Vault.globalShortSizes(indexToken)
* The available liquidity will be the lower of these two values
* PositionRouter.maxGlobalShortSizes(indexToken) can be zero, in which case there is no additional cap, and available liquidity is based only on the available amount of tokens

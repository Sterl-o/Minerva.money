# 🛡 Flash Loan Attack Mitigations

Opening and closing of positions as well as swaps, minting and redeeming of MLP are settled at the oracle price covered in the **Price Feeds** section since these prices are not dependent on pool composition or parameters like long / short ratios, so a flash loan would not have an impact on these functions. The dynamic fees for swaps are dependent on pool composition, however, this does not lead to positive slippage so the maximum benefit from a flash loan would be a zero fee swap which adjusts pool composition towards the desired token weights.

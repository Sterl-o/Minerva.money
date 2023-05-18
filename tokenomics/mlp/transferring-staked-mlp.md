---
description: >-
  When MLP is bought it is automatically staked and when it is sold it is
  automatically unstaked, for integrations adding MLP the StakedMlp contract can
  be used to transfer staked MLP tokens.
---

# Transferring Staked MLP

StakedMlp behaves like a regular ERC20 token, the user can call approve on it to approve your contract, then your contract can call transferFrom to transfer the MLP tokens to any receiving account or contract. When transferring, the StakedGlp contract will unstake MLP from the user and stake the MLP for the receiving account, the receiving account or contract would then start earning rewards which can be compounded or claimed by calling `handleRewards` on the RewardRouter contract.\
\
Since there is a 15 min cooldown duration after minting MLP, this amount of time needs to pass for the user before transferFrom can be called for their account.


---
description: >-
  Certain Parameters can adjusted by the Controller, which is currently under
  the Multisig's control
---

# 🔐 Access Control

* Setting of swap and margin trading fees up to a maximum of 5%
* Setting of token weights for the MLP pool, token weights affect the dynamic fees of swaps, these fees are such that a swap which increases the balance towards the specified token weight will be lower, while a swap that moves the token weight away from the desired amounts will have higher fees, the details of the calculation can be found from `Vault.vaultUtils.getSwapFeeBasisPoints`
* Pausing of swaps or leverage trading for emergency use
* Setting of the maximum allowed leverage
* Setting of maximum total capacity for long and short positions

Parameters that can be adjusted by a [**Timelock**](./#timelock) controlled by the team:

* Listing of new tokens
* Updating `Vault.priceFeed`
* Updating `Vault.vaultUtils`, the VaultUtils contract validates the opening and closing of positions and also specifies how fees are calculated
* Updating of `gov` values

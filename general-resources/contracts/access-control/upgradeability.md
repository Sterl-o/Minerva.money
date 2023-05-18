# 🛠 Upgradeability

The core logic of the MINE contracts cannot be changed, but certain peripheral functions such as fee and pricing calculations can be updated. This update is done by implementing new fee / pricing contracts and updating the core contracts to use the new contracts. For example, the Vault contract has a `priceFeed` value that can be changed by the [Timelock](timelock.md) contract.

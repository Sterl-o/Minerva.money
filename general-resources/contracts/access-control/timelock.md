---
description: >-
  The Timelock works by requiring a 24 hour gap between when the full details of
  an action is signalled on-chain to when the action is executed.
---

# ⏰ TimeLock

An example flow would be:

* `Timelock.signalSetPriceFeed` is called, this specifies the Vault address and the address of the new price feed
* At least 24 hours must pass
* `Timelock.setPriceFeed` can be called, this will update the `Vault.priceFeed` value

{% hint style="info" %}
24 hours was selected as it helps to be able to respond quickly to any issues that may occur.
{% endhint %}

The Timelock contract is monitored by the team and can be monitored by anyone without coding by subscribing to the `Timelock.SignalPendingAction` event. This is doable using [OpenZeppelin Sentinel](https://openzeppelin.com/defender/). The Timelock contracts can be found by checking the `gov` values of contracts.\
\
In the event of a malicious transaction being sent, it is possible for all funds in the pool to be compromised. To mitigate this, all actions which can impact user funds must pass through the signal, time gap, execute process mentioned above. If a malicious transactions is detected through the monitoring process or Bug Bounty, a multi-sig consisting of advisors and community members can be used to override the `Timelock.admin` value, this would prevent the action from being executed. This also applies for actions such as pausing trading when there was no need to, in this case, the admin can be replaced by the multi-sig and trading can be re-activated.

{% hint style="info" %}
Note that the multi-sig can only override the admin value, it cannot bypass the time gap required for Timelock actions.
{% endhint %}

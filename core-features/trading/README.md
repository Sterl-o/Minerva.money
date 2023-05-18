---
description: >-
  Minerva is a decentralized exchange allowing trading without the need for a
  username or password. The platform uses an aggregate price feed which reduces
  the risk of liquidations from temporary wicks.
---

# 🔄 Trading

### **Swaps**

Minerva supports both swaps and leverage trading. For swaps, click on the "Swap" tab on [https://minerva.money/](https://minerva.money/) this will open the interface to swap tokens with zero price impact.\
\
For leverage trading, please see the below sections for more information.

### **Opening a position**

Click on "Long" or "Short" depending on which side you would like to open a leverage position on.&#x20;

* Long position
  * Earns a profit if the token's price goes up
  * Makes a loss if the token's price goes down
*   Short position

    * Earns a profit if the token's price goes down
    * Makes a loss if the token's price goes up



After selecting your side, key in the amount you want to pay and the leverage you want to use. For example, 0.1 ETH worth 352.33 USD can be used to buy a 5x ETH (Ethereum) long position of size 1752.89 USD\
\
The "Entry Price" can be $3541.17 and the Liquidation Price would be $2903.76. Your "Exit Price" is the price that would be used to calculate profits if you open and then immediately close a position. The exit price will change with the price of the token you are longing or shorting.\
\
The trading fee to open a position is 0.1% of the position size, similarly there is a 0.1% fee when closing the position.\
\
There is also a "Borrow Fee" that is deducted at the start of every hour. This is the fee paid to the counter-party of your trade. The fee per hour will vary based on utilization, it is calculated as (assets borrowed) / (total assets in pool) \* 0.01%. The "Borrow Fee" for longing or shorting is shown below the swap box.\
\
While there are no price impacts for trades, there can be slippage due to price movements between when your trade transaction is submitted and when it is confirmed on the blockchain. Slippage is the difference between the expected price of the trade and the execution price, this can be customized by clicking on the "..." icon next to your address at the top right of the page.

### Managing Positions

After opening a trade, you would be able to view it under your Positions list, you can also click on "Edit" to deposit or withdraw collateral, this allows you to manage your leverage and liquidation price.\
\
When you open a position or deposit collateral, a snapshot of the USD price of your collateral is taken, so e.g. if your collateral is 0.1 ETH and the price of ETH is 3523.30 at the time, then your collateral is 352.33 USD and will not change even if the price of ETH changes.\
\
The amount of profit and loss you make will be proportional to your position size. In this example, 352.33 USD has been used to buy 1752.89 USD of ETH. If the price of ETH increases by 10%, the position would have a profit of 175.29 USD, if the price of ETH decreases by 10%, the position would have a loss of 175.29 USD.\
\
If a short position was opened instead, then if the price of ETH decreased by 10% the position would have a profit of 175.29 USD, if the price of ETH increased by 10%, the position would have a loss of 175.29 USD.\
\
Leverage for a position is displayed as (position size) / (position collateral). If you'd like to display the leverage as (position size + PnL) / (position collateral), you can customise this by clicking on the "..." button next to your address.\
\
Note that when depositing collateral into a long position, there is a 0.3% deposit fee for the conversion of the asset to its USD value, e.g. ETH amount to USD value. This is to prevent deposits from being used as a zero fee swap. This does not apply to shorts. Withdrawing of collateral from longs and shorts do not have this fee as well.

## **Closing a Position**

You can close a position partially or completely by clicking on the "Close" button.\
\
For long positions, profits are paid in the asset you are longing, e.g. if you long ETH you would get your profits as ETH.\
\
For short positions, profits will be paid out in the same stablecoin that you used to open the position, e.g. USDC or USDT.\
\
Note that [https://optimistic.etherscan.io/](https://optimistic.etherscan.io/)  may not always show ETH transfers so when you close long positions on Optimism and receive ETH the transaction might not show the transfer but your ETH balance would have increased. If the ETH transfer does show, it would be displayed under the "Interacted With" section.

### Stop-Loss / Take-Profit Orders

You can also set stop-loss and take-profit orders by clicking on the "Close" button and selecting the "Trigger" tab.\
\
After creating a trigger order, it will appear in your position's row as well as under the "Orders" tab, you can edit it the order and change the trigger price if needed. \
\
If you close a position manually, the associated trigger orders will remain open, you would need to cancel them manually if you do not want the order to be active when opening future positions.\
\
Note that orders are not guaranteed to execute, this can occur in a few situations including but not exclusive to:

* The mark price which is an aggregate of exchange prices did not reach the specified price
* The specified price was reached but not long enough for it to be executed
* No keeper picked up the order for execution

{% hint style="info" %}
Trigger orders are market orders and are not guaranteed to execute at the trigger price.
{% endhint %}

### **Partial Liquidations**

In the example, since only 352.33 USD worth of tokens is used as collateral to open the position, there will be a price at which the loss amount is very close to the collateral amount.\
\
This is the Liquidation Price and is calculated as the price at which the (collateral - losses - borrow fee) is less than 1% of your position's size. If the token's price crosses this point then the position will be automatically closed.\
\
Due to the borrow fee your liquidation price will change over time, especially if you use a leverage that is more than 10x and have the position open for more than a few days, so it is important to monitor your liquidation price.\
\
If there is any collateral remaining after deducting losses and fees, then the corresponding amount would be returned to your account.

### **Pricing**

There is no price impact for trades on Minerva, so you can execute large trades exactly at the mark price. During times of high volatility there will be a spread from the Chainlink price to the median price of reference exchanges.\
\
The mark prices are displayed next to the market name, long positions will be opened at the higher price and closed at the lower price while short positions will be opened at the lower price and closed at the higher price.\
\
The chart will indicate the average of the two mark prices.

### Fees

The cost to open / close a position is 0.1% of the position size.\
\
The collateral of long positions is the token being longed, for ETH longs the collateral is ETH and for BTC longs the collateral is WBTC, etc. The collateral of shorts positions is any of the supported stablecoins e.g. USDC, USDT, ~~**LUSD**~~. If a swap is needed when opening or closing a position then the regular swap fee would apply, this fee is 0.2% to 0.8% of the collateral size, the exact fee depends on whether the swap improves balance or reduces it.\
\
There is also an execution fee detailed below which is used to pay for the blockchain network costs.

### Execution Fee

There are two transactions involved in opening / closing / editing a position:\
\
1\. User sends the first transaction to request open / close / deposit collateral / withdraw collateral\
2\. Keepers observe the blockchain for these requests then execute them\
\
The cost of the second transaction is displayed in the confirmation box as the "Execution Fee". This network cost is paid to the blockchain network.

### Stablecoin Pricing

In case the price of a stablecoin depegs from 1 USD:

* Opening and closing short positions during this time would incur a cost on the collateral based on a spread of 1 USD to the Chainlink price of the stablecoin. For example, if the price of the chosen stablecoin depegs to 0.95 USD, opening a position using 1000 of that stablecoin would result in a position collateral of 950 USD based on a price of 0.95 USD, when closing the position, 950 of the stablecoin would be withdrawn based on a price of 1 USD, this is to prevent front-running issues during a depeg since collateral is stored as a USD value and converted to tokens based on the latest price.
* To ensure that profits for all short positions can always be fully paid out, the contracts will pay out profits in the stablecoin based on a price of 1 USD or the current Chainlink price for the stablecoin, whichever is higher.&#x20;
* For swaps using the depegged stablecoin, the spread from 1 USD to the Chainlink price of the stablecoin will similarly apply.
* Long positions should not be affected though there may be a spread if swapping from a depegged stablecoin into the long collateral needed for the position, e.g. to long ETH, ETH collateral is needed. Alternative swap platforms could be used to execute the swap before opening the long position. The interface should show a warning if there is a large spread for this.

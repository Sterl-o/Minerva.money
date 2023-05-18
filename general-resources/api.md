# 📕 API

For contract interaction: [Contracts](contracts/)

### **Tokens**

* URL:&#x20;
* Retrieve a list of tokens and info for each token
* USD amounts are multiplied by (10 \*\* 30)
* Token amounts are multiplied by (10 \*\* token.decimals)

### **Prices**

The tokens endpoint will return the current prices in the contract, these prices are used for swaps, GLP minting / redeeming. For opening and closing positions, the real-time median prices are used, to get these values:

* URL:&#x20;
* Retrieve a list of token prices
* Prices are multiplied by (10 \*\* 30)

### **Actions**

* URL:&#x20;
* Retrieve a list of actions, these will include swaps, increasing a position, decreasing a position, orders and liquidations

### **Volume**

* Hourly:&#x20;
* Daily:&#x20;
* Weekly:&#x20;
* Total:

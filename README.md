# CBlindBroker - ReadMe

## Developer's site: forexroboteasy.com
## Development name: Forex Robot Easy Team

This code represents an Expert Advisor called 'Blind Broker'. It is designed to conceal trading strategies and orders from the broker, providing a stealthy approach to Forex trading.

### Functionality

The CBlindBroker Expert Advisor operates with the following variables:

- `stopLossLevel`: Represents the level at which a stop loss order should be triggered.
- `takeProfitLevel`: Represents the level at which a take profit order should be triggered.
- `tradeVolume`: Defines the volume of the market order to be placed.

The Expert Advisor also manages a collection of orders through the `CArray <COrder> orders` variable.

#### OnTick()

The `OnTick()` function is triggered on every new tick received. It performs the following operations:

1. Retrieves the current market price using `MarketInfo(Symbol(), MODE_BID)`.
2. Checks for existing orders.
3. For each order, it checks if the current price has reached the stop loss or take profit level.
4. If the conditions are met, the order is closed using `order.Close(order.Volume())`.
5. If there are no existing orders, a market order request is placed using `OrderSend(Symbol(), OP_BUY, tradeVolume, currentPrice, 0, 0, 0, 'Blind Broker')`.

#### OnTrade()

The `OnTrade()` function is triggered whenever a trade event occurs. It performs the following operations:

1. Retrieves trading account information using `AccountGet(account)`.
2. Calculates the trade volume based on the account balance and the tick value of the symbol.
3. Sets the stop loss and take profit levels based on the current market price and the symbol's point value.
4. Creates a market order request using `OrderSend(Symbol(), OP_BUY, tradeVolume, MarketInfo(Symbol(), MODE_BID), 0, stopLossLevel, takeProfitLevel, 'Blind Broker')`.

#### OnDeinit()

The `OnDeinit(const int reason)` function is triggered when the Expert Advisor is removed from the chart or the terminal is closed. It performs the following operations:

1. Closes all existing orders by iterating over the `orders` collection and calling `order.Close(order.Volume())`.

### Product Description

'Blind Broker' is a stealthy Forex trading software developed by the Forex Robot Easy Team. It conceals trading strategies and orders from the broker, providing a discreet approach to trading.

Key Features:
- Conceals trading strategies and orders from the broker
- Automatically places market orders based on predefined stop loss and take profit levels
- Dynamically calculates trade volume based on the account balance and symbol's tick value

For detailed reviews and trading results of this product, please visit [Forex Robot Easy - Blind Broker MT5 Review](https://forexroboteasy.com/forex-robot-review/blind-broker-mt5-review-stealthy-forex-trading-software/).

Please note that ForexRobotEasy is not the official developer of this product. We only provide a sample code that demonstrates how the product works. To find the official developer of this product, please refer to MQL5.

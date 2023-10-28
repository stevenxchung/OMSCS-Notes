# Lesson 15

In this lesson we will learn about how the market works (e.g., what actually happens behind the scenes when you buy or sell a stock).

## What Is In An Order

To understand what happens when we buy or sell a stock (essentially placing n order), we should know what composes an order:

- Order type (buy or sell)
- Symbol
- Number of shares
- Limit or market order
- Price

## The Order Book

Each exchange keeps an order book for each stock that is traded. The order book enables the exchange to track metrics such as:

- Order type
- Price
- Size

This allows the exchange to track and order which stocks people are selling and buying such that orders can be fulfilled in a sequential manner. Hence, not everyone gets all their desired shares at the desired price. In some cases orders may not be fulfilled if certain specified order conditions are not met (e.g., limit orders where orders may not fulfilled if the price does not meet the limit sell or buy price).

## How Orders Get To The Exchange

A simple example of how orders get to an exchange is through a broker where the broker places the order at the best price on one of the exchanges.

However, it is common now to see 80-90% of all trades going through a **dark pool** which acts as an intermediary between brokerages and exchanges. Dark pools examine vast amounts of orders across various exchanges to predict where prices will go and pay brokers the privilege of peeking into people's orders before orders make it to the exchange. By having brokers interact with dark pools, both parties save money on exchange fees.

## How Hedge Funds Exploit Market Mechanics

Hedge funds can exploit the market in a variety of ways:

- Order book exploit: a hedge fund may have a co-located server which observes the order book microseconds faster than anyone else - this essentially allows them to buy and sell at the best prices before anyone else
- Geographic arbitrage: differences in prices may occur due to market inefficiencies which allows hedge funds to buy in at a lower price in one region of the world and sell at a higher price in another region

## Additional Order Types

Exchanges have the following order types:

- Buy and sell
- Market limit

Additional order types are offered by the broker:

- Stop loss - sell shares when it drops to a certain price
- Stop gain - sell shares when it reaches a certain price
- Trailing stop - combination of stop loss and an adjustable margin (stop loss limit drags along with price rise)
- Sell short - take a negative position on a stock (sell shares when prices go down)

Note that when _shorting_, we are selling stocks we do not own.

## Mechanics Of Short Selling: Exit

**Short selling** or _shorting_ is a way someone could make or lose money (generally large amounts) since shares are borrowed from another investor through a brokerage.

Positive example:

- Person A borrows $10000 worth of shares (100 shares at $100 each) from an investor through a broker to short
- The stock trading at $100 _drops_ to $90 - a $10 difference so Person A pockets 100 shares multiplied by $10 which equals $1000

Negative example:

- Person B borrows $10000 worth of shares (100 shares at $100 each) from an investor through a broker to short
- The stock trading at $100 _rises_ to $150 - a $50 difference so Person B is out 100 shares multiplied by $50 which equals $5000

## Section Quizzes

### Up Or Down Quiz

_Given the order book with a specific set of orders, is the price of the stock going to go up or down_? The price will go down since the size of the sell is much higher.

### Short Selling Quiz

_What would be the net return if you shorted IBM in this given situation_? Since we have 100 shares and it drops $10, $10 multiplied by 100 shares would give us $1000.

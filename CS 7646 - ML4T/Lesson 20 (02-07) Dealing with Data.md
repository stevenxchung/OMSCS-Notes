# Lesson 20

Data is at the core of machine learning for trading. In this lesson we will focus on data, more specifically share price and volume data.

## How Data Is Aggregated

Every second there is a large amount orders placed in the market for any particular stock in the market. We might be interested in details such as:

- Open price
- High price
- Low price
- Close price
- Volume

Each of these metrics are core for trading and analysis. For the purposes of this course, we focus primarily on the above metrics over the time period of days instead of seconds. Note that the smaller the time period, the more computing power is needed.

## Stock Splits

Why do stocks split? A stock split occurs when the price of a stock gets too high where it becomes difficult for many people to purchase a single stock.

Once a stock is split, traders are able to buy more shares for the same amount it would have cost to buy one share previously. However, people who held a stock position do **not** get diluted since their stock volume increases proportionally to the split. By increasing the stock volume also allows investors to diversify their portfolio more easily.

In terms of trading analysis, the problem introduced by stock splits is that prices are not reflected in a useful manner for analysis. We may account for stock splits by utilizing the **adjusted close** price which accounts for subtleties by dividing the price according to the stock split ratio.

## Dividends

Some companies pay a dividend to shareholders for investing in their company. Therefore, the expected price is typically higher the day before the dividend is issued versus after dividend issue.

How do we adjust the prices to account for dividend payments? Similar to stock splits, we would adjust the price proportional to the dividend payment while looking back in time.

## Survivor Bias

A common mistake is when traders will use current or more recent data (e.g., S&P 500) to simulate their strategies. They will discover that most of their strategies will fair well but only due to **survivor bias** (i.e., they did not take into account the comprehensive sample where companies no longer exist).

To account for survivor bias, it is recommended to simulate using survivor bias-free data which is readily available online.

## Section Quizzes

### Price Anomaly Quiz

_Given the trade history of a particular stock, what would cause the stock price to drop as shown_? Stock split since the price per unit is reduced but the amount of shares remain the same.

### Split Adjustment Quiz

_Given the following charts and split ratio, determine the adjusted close price at specific points_.

1. $25 from $50 since this was before the 2:1 split
2. $50 from $100 since this was right before the 2:1 split
3. $100 since this is after the 2:1 split so not adjustment is needed

### Dividends Quiz

_Given the chart, what would the stock price be before and after the the dividend is issued_? $101 before and $100 after the dividend issue.

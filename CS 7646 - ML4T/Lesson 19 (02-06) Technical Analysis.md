# Lesson 19

There are generally two types of analysis one may conduct to select stocks:

- **Fundamental analysis**: focused around estimating the value of a company to select stocks below value
- **Technical analysis**: focused around pricing patterns or trends regarding a particular stock

In this lesson we will be examining technical analysis for trading.

## Characteristics

Some characteristics of technical analysis:

- Focuses on historical _prices_ and _volume_ only (whereas fundamental analysis examines earnings, dividends, cash flow, etc.)
- Compute statistics which are used as indicators
- Indicators are heuristics

Technical analysis is controversial in that most investors believe that it is not viable as an _investing_ technique. However, technical analysis may still be useful as a _trading_ technique:

- There is information in price
- Heuristics generally work

## When Is Technical Analysis Valuable

There are several things to keep in mind when using technical analysis:

- Individual indicators are often weak
- Combinations of indicators are often stronger
- Stocks which contrast the market may be good to examine further
- Technical analysis is generally more effective for shorter time periods

Additionally, when examining the value of fundamental versus technical analysis over time, the following comparisons could be drawn:

- Fundamental:
  - The _longer_ the trading horizon, the _higher_ the value but the _more_ complex the decision
  - Consequently, decision speed decreases as the trading horizon increases
- Technical:
  - The _shorter_ the trading horizon, the _higher_ the value and the _less_ complex the decision
  - Consequently, decision speed is most critical at the beginning of the trade execution

## A Few Indicators

There are many indicators to examine for technical analysis but in this class we will focus on:

- **Momentum**: the price change over $n$ days (e.g., `price[t] / price[t-n]` where `n` is number of days)
- **SMA (Simple Moving Average)**: the average price over $n$ days (e.g., `(price[t] / price[t-n:t].mean()) - 1` where `n` is number of days)
- **Bollinger Bands**: the standard deviation for low and high volume trading periods (e.g., `(price[t] - SMA[t]) / (2 * std[t])`)

SMA may be used to examine SMA crosses between the SMA line and the price trend. Additionally, SMA could be used as a proxy to determine the true value of a company and identify the most optimal buy or sell opportunity.

Bollinger Bands may be used to determine when the stock price crosses the standard deviation line from outside to inside (a buy or sell opportunity depending on an upward or downward trend).

## Normalization

Because indicators may vary:

- SMA: +/- 0.5
- Momentum: +/- 0.5
- Bollinger Bands: +/- 1.0

We need to normalize the values such that no indicator overwhelms the other. We may normalize using the following:

```python
normalized = (values - mean) / values.std()
```

## Section Quizzes

### Potential Indicators Quiz

_Given the following questions, select the best answer_.

1. _Is the moving average of the price a fundamental or technical indicator_? Technical, since it deals with price
2. _Is the % change in volume a fundamental or technical indicator_? Technical, since it deals with volume
3. _Is the price to earnings ratio a fundamental or technical indicator_? Fundamental
4. _Is the intrinsic value a fundamental or technical indicator_? Fundamental

### Buy Or Sell Quiz

_Given the following graphs and indicators, select the best answer_.]

1. _At time point 1, do you buy, sell, or do nothing_? Sell, since the trend is downward
2. _At time point 2, do you buy, sell, or do nothing_? Do nothing (crosses from inside the standard deviation line)
3. _At time point 3, do you buy, sell, or do nothing_? Buy, since the trend is upward
4. _At time point 4, do you buy, sell, or do nothing_? Buy, since the trend is upward

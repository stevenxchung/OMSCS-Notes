# Lesson 7

Previously, we have been mainly focused on statistics for stocks. In this lesson we will examine statistics for portfolios and how to evaluate performance.

We consider a portfolio an allocation of funds to a set of stocks and will follow a buy-and-hold strategy (for this lesson) where we invest in a certain set of stocks with a certain allocation and observe returns over time.

## Daily Portfolio Values

There are several steps we want to perform to determine our portfolio value:

1. Normalize the stock prices in our dataframe by dividing the prices after the first row with the first row
2. Multiply the normalized stock prices with the allocated amount for each stock
3. Multiply the allocated prices with the start value for each stock to determine the stock _position value_ for each day
4. Get the sum of each row (each day) from the stock position value dataframe to determine the _daily portfolio value_

## Portfolio Statistics

After we determine the portfolio value, we can examine several key portfolio metrics:

- Cumulative returns
- Average returns
- STD daily returns (risk)
- Sharpe ratio

## Sharpe Ratio

**Sharpe ratio** is a metric which adjusts returns according to risks (risk adjusted return). In general, the Sharpe ratio advocates (all else equal):

- Lower risk is better
- Higher return is better

The Sharpe ratio also considers risk free rate or return (e.g., returns from depositing money into a bank account).

## Computing Sharpe Ratio

Given that the Sharpe ratio is defined as $S = \frac{R_p - R_f}{\sigma_p}$, where $R_p$ is the portfolio return, $R_f$ is the risk free rate of return, and $\sigma_p$ is the STD of portfolio return. The ratio may be computed in Python as follows:

```python
s = mean(daily_returns - daily_rf_returns)/std(daily_returns - daily_rf_returns)
```

Where `daily_rf_returns` in the denominator may be dropped in most cases as it is a constant. A traditional shortcut is to use `daily_rf_returns = (1.0 + 0.1)^(1/252) - 1`.

## But Wait - There Is More

The Sharpe ratio can vary widely depending on how frequently you sample. The Sharpe ratio is an annual measure so if sampling more frequently we need to adjust as follows:

- Use `s_annualized = k * s` where `k = (samples per year)^(1/2)`
- If sampling daily use `k = (252)^(1/2)` (252 trading days a year)
- If sampling weekly use `k = (52)^(1/2)`
- If sampling monthly use `k = (12)^(1/2)`

## Section Quizzes

### Which Portfolio Is Better Quiz

1. _Which portfolio (provided) is better? ABC or XYZ_? ABC, since the volatility is the same but the return is higher
2. _Which portfolio (provided) is better? ABC or XYZ_? XYZ, since the volatility is lower
3. _Which portfolio (provided) is better? ABC or XYZ_? XYZ, based on the Sharpe ratio

### Form Of The Sharpe Ratio Quiz

_Given the following portfolio metrics (provided), which formula is best_? The Sharpe ratio which is $\frac{R_p - R_f}{\sigma_p}$, where $R_p$ is the portfolio return, $R_f$ is the risk free rate of return, and $\sigma_p$ is the STD of portfolio return.

### What Is The Sharpe Ratio Quiz

_What is the Sharpe ratio given the following (provided)_? 12.7, based on the given formula for Sharpe ratio from lecture.

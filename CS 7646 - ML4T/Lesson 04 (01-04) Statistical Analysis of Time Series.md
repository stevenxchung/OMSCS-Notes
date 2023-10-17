# Lesson 4

In this lesson we will examine various kinds of statistics that can help us work with time series data and extract value.

## Global Statistics

**Global statistics** allow us to look at the overall attributes of our dataframe. Some commonly used global statistics include:

- Mean
- Median
- STD (standard deviation)
- Sum
- Prod (product of values over request axis)
- Mode

For more global statistics, see the [dataframe docs](https://pandas.pydata.org/pandas-docs/stable/reference/frame.html).

## Rolling statistics

**Rolling statistics** comes in handy when working with a window of data (smaller sample of the overall data). Some commonly used rolling statistics include:

- [Rolling mean](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.rolling.html)
- [Rolling STD](https://pandas.pydata.org/docs/reference/api/pandas.core.window.rolling.Rolling.std.html)

For more examples, see the page on pandas [computational tools](https://pandas.pydata.org/pandas-docs/stable/user_guide/computation.html).

## Bollinger Bands

**Bollinger Bands** are:

> Envelopes plotted at a standard deviation level above and below a simple moving average of the price. Because the distance of the bands is based on standard deviation, they adjust to volatility swings in the underlying price.

Bollinger Bands uses two primary parameters:

- Period
- STD

## Daily Returns

**Daily returns** refers the increase or decrease of the price of a stock on a particular day. Daily return may be calculated by using the following formula:

```python
daily_returns[t] = (price[t] / price[t - 1]) - 1
```

Where `t` refers to the specific day.

## Cumulative Returns

**Cumulative returns** refers to the total returns up to current day (or latest date available). Cumulative returns may be calculated by using the following formula:

```python
cumulative_returns[t] = (price[t] / price[0]) - 1
```

Where `t` refers to the current day.

## Section Quizzes

### Which Statistic To Use Quiz

_Which statistic_? Rolling standard deviation.

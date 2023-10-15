# Lesson 2

In this lesson we will cover how to properly load data into a pandas dataframe such that we can visualize what we want.

## Problems To Solve

What are some of the basic problems we want to solve with the pandas dataframe?

1. How to look at specific date ranges?
2. How to look at multiple stocks?
3. How to align equity and dates?
4. How to order dates?

## Building A Dataframe

The first step to building a dataframe is loading the range of dates we are interested in. We then load in equity and dates for SPY ETF (SPDR S&P 500 Exchange Traded Fund) since we know that SPY does not trade on weekends, we can use SPY for reference.

## Obtaining A Slice Of Data

To obtain a slice of data, we can specify the following in a dataframe:

```python
df[startDate:endDate, ['A', 'B']]
```

Which is not limited to just certain rows or columns. We may decide to slice entire rows and copy onto another dataframe if needed.

## Problems With Plotting

Although we can just use `plot()` to plot dataframes, how do we go about comparing stocks such that data is normalized?

## Section Quizzes

### NYSE Trading Days Quiz

_How many days were U.S. stocks traded at NYSE in 2014_? 252.

### Types Of `join()` Quiz

`df1.join(dfSPY, how='inner')`, where inner (from the docs, [pandas.DataFrame.join](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.join.html)):

> forms intersection of calling frame’s index (or column if on is specified) with other’s index, preserving the order of the calling’s one.

### How To Plot On Equal Footing Quiz

_What is the best way to normalize price data so that all prices start at 1.0 (normalize to one)_? B, `df = df / df.ix[0, :]`.

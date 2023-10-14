# Lesson 1

In this lesson we will learn about reading and plotting stock data with Python. Why use Python? Python is an optimal tool because we can quickly prototype algorithms with high computational speed. Some features of Python include:

1. Strong scientific libraries
2. Strongly maintained
3. Fast

## Data In CSV Files

**CSV (Comma Separated Values) files** contain data typically formatted in rows and columns. We typically denote the top row for headers and the rest of the rows as data under each header.

## Real Stock Data

A _closing_ price on a stock may differ greatly from _adjusted closing_ price (since adjusted closing price accounts for splits, dividends, etc.).

## Pandas Dataframe

**Pandas** is a Python data analysis library created by Wes McKinney at a hedge fund called AQR Capital Management out of the need for a high performance, flexible tool to perform quantitative analysis on financial data.

A **dataframe** consists of a two dimensional chart consisting of stocks, prices, times, etc. There may also be additional layers to the dataframe such that different stock attributes may be evaluated (e.g., adjusted close, close, volume, etc.).

## Section Quizzes

### Which Fields Should Be In A CSV File Quiz

_Which fields would you expect to see in a csv file of stock data_?

- Date and time
- Price of the stock

# Lesson 5

Data is a very important part of finance and accounting and can often be incomplete. In this lesson we will look into incomplete data and remedies around this issue.

## Pristine Data

When it comes to financial data, most people believe e.g.:

- Data is perfectly recorded minute by minute
- There are no gaps or missing data points

However, in reality data is aggregated from many different sources. Not all stocks trade when looking at specific times.

## Why Data Goes Missing

Data may go missing for a variety of reasons. If a company using a particular stock symbol (e.g., JAVA) was acquired or sold to another company, the stock may stop trading (at least under that symbol).

Another reason may be that the company is thinly traded (companies that do not have a high market capitalization tend to trade in-and-out the market during periods of time).

## Why This Is Bad - What Can We Do

So how do we deal with data that is missing?

Recommended approach: we want to **fill forward** (or **fill backwards** depending on the gap and last traded price of interest) such that the last traded price before the gap is extended until it fills the gap (until the next non-empty traded price).

**Not** recommended: interpolation since it will modify the original data and attempt to predict prices (we do not want to create predictions with this activity).

## Section Quizzes

### Pandas `fillna()` Quiz

_How would you call fillna() to fill forward missing values_?

According to the [pandas docs](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.fillna.html): `df.fillna(method='ffill')`.

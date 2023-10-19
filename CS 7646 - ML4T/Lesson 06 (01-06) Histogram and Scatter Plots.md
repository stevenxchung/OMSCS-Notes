# Lesson 6

Daily returns from a stock is important but having a way to visually compare daily returns for different stocks is also key. In this lesson we look at how to use histograms and scatter plots to visualize stock data.

## Histogram Of Daily Returns

When we plot our recorded daily returns, we can examine characteristics such as:

- Mean
- STD
- **Kurtosis**: measures how different the distribution is from a Gaussian normal distribution by examining the tails of the distribution

A _positive_ kurtosis indicates a fat tail (tails are outside of the Gaussian normal distribution) and a _negative_ kurtosis indicates skinny tail (tails are inside of the Gaussian normal distribution)

## Scatter Plots

Another way to visualize data is through scatter plots. We can plot the daily return value for each specific day on the scatter plot for two or more separate stocks and determine the overall trend.

## Fitting A Line To Data Points

When using scatter plots, it is common to use line of best fit for the data. The line of best fit may yield the following information:

- Slope ($\beta$): allows us to gauge how reactive a stock is to the market or another stock (`stock A % / stock B %`)
- Y-intercept ($\alpha$): allows us to gauge how well a stock is doing on average when compared to S&P 500 or another stock

## Slope Does Not Equal Correlation

Slope should **not** be confused with **correlation** (how well the line actually fits the data). A correlation close to one indicates high correlation whereas a correlation of close to zero indicates low correlation.

## Real World Use Of Kurtosis

In many cases, returns are assumed to be normally distributed (Gaussian distribution) in financial research. However, in reality kurtosis occurs and assuming that returns follow a normal distribution may cause disasters. One such incident is when investment banks created bonds based on mortgages (assuming normal distribution of returns and that the returns were independent) which unfortunately led to the [2008 financial crisis](https://www.investopedia.com/articles/economics/09/financial-crisis-review.asp).

## Section Quizzes

### What Would It Look Like Quiz

_Suppose we measured the daily return each day for the S&P 500, what would the histogram plot look like_?

C, a bell curve

### Compare Two Histograms Quiz

_Given a histogram of SPY and XYZ stock (imaginary stock), which of the following is true_?

XYZ has lower return and higher volatility, since the mean of XYZ is lower than the mean of SPY (lower return) and the spread of the data is greater indicating a higher STD (higher volatility).

### Correlation Vs. Slope Quiz

_Given the two scatter plots of SPY and XYZ (imaginary stock), which of the following is true_?

ABC has higher beta and higher correlation, since the slope is steeper (higher beta) and the line fits the data well (high correlation).

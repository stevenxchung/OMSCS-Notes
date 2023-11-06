# Lesson 23

In this lesson we examine how to determine proper allocations given a set of stocks with mean variance optimization. Mean variance optimization can be broken into:

- **Given**:
  - Set of equities
  - Target return
- **Find**: allocation to each equity that minimizes Risk

## What Is Risk

Risk is measured by the standard deviation of historical daily returns (which is the same as volatility of a portfolio)

## Visualizing Return Vs. Risk

We may visualize returns vs. risk by plotting all stock returns and risks on the portfolio along with their weights (allocations) as shown in lecture.

## Can We Do Better

Can we do better than picking stock that is just within the spread of the return v risk scatter? We can according to Harry Markowitz's [Modern Portfolio Theory](https://www.investopedia.com/terms/m/modernportfoliotheory.asp) who also showed that a blend of stocks and bonds has a lower risk than just holding bonds (for risk adverse investors).

Portfolios are not just a blend of returns and risks but also how those risks interact day-to-day. If we pick the right stocks and allocations, we may have a portfolio that maximizes expected return based on a given level of market risk.

## Why Covariance Matters

Why does covariance matter? Covariance is how much one variable relates to another (in this case two stocks). If we know the covariance for each pair of stocks, we may allocate the proper amount to each stock such that the overall portfolio return is smoothed (less volatility as shown in lecture).

## Mean Variance Optimization

Markowitz showed that a blend of anti-correlated stocks can lower the overall risk of a portfolio. The _mean variance optimization_ algorithm was designed to select the proper allocations such that risk is minimized. To set up the optimizer:

- **Inputs**:
  - Expected return
  - Volatility
  - Covariance
  - Target return
- **Output**: asset weights for portfolio that minimize risk

## The Efficient Frontier

**The Efficient Frontier** is a set of optimal portfolios that offer the highest expected return for a defined level of risk or the lowest risk for a given level of expected return (see [Investopedia](https://www.investopedia.com/terms/e/efficientfrontier.asp)).

Graphically, the Efficient Frontier is shown as a line of possible optimal portfolios on the return vs. risk scatter plot. No portfolios exist above the line and any portfolio below the line is sub-optimal. Therefore, all possible optimal portfolios are on the line.

A tangent line from the origin to the frontier will yield an optimal portfolio with maximum Sharpe ratio.

## Section Quizzes

### Building A Portfolio Quiz

_Consider the following return vs. risk scatter plots (provided), match each plot with respect to their combined results_.

1. B
2. A
3. C

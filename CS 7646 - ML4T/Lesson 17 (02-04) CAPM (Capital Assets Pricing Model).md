# Lesson 17

In this lesson we will examine the **CAPM (Capital Assets Pricing Model)** (developed by Sharpe, Markowitz, Merton, and Miller) which explains how the market impacts individual stock prices and provides a mathematical framework for hedge fund investing. CAPM led to the belief of index funds and the idea of _"you can't beat the market"_.

## Definition Of A Portfolio

A **portfolio** is a weighted set of assets where the sum of all weights must equal 1 (i.e., 100%). The returns of a portfolio for a particular point in time may be calculated by:

$r_p(t) = \sum_{i} w_i r_i(t)$

Where $r_p(t)$ is the portfolio return at time $t$, $w_i$ is the weight of the asset, and $r_i(t)$ is the return of the asset on a particular day.

## The Market Portfolio

The market portfolio is an index that broadly covers a wide variety of stocks (e.g., S&P 500). Most stocks in an index is set according to their weighted cap:

$w_i = \frac{m_cap_i}{\sum_{j} m_cap_j}$

Where $m_cap_i$ is the market cap for a particular stock and $m_cap_j$ is the market cap of any other stock in the index.

## The CAPM Equation

The CAPM equation is a linear equation (e.g., below for a particular stock) could be modeled as follows:

$r_i(t) = \beta_i r_m(t) + \alpha_i(t)$

Where $\beta_i r_m(t)$ represents market effects on returns (e.g., if the market goes up X percent then the stock will go up Y percent) and $\alpha_i(t)$ represents residual effects (with an expected value of zero although not always zero in practice). The extent to which the market affects a particular stock is represented by $\beta_i$.

Both $\beta_i$ (represented as the slope of the daily return line) and $\alpha_i(t)$ (represented as the y-intercept of the daily return line) are derived from daily returns for a particular stock when compared to an index.

## CAPM Vs. Active Management

Since the invention of CAPM, there have been two schools of though on the CAPM model regarding investing:

- **Passive investing**: the idea that you should buy an hold since $\alpha_i(t)$ from the CAPM model is random and the expected value is nearly zero in most cases
- **Active investing**: the idea that you should actively pick stocks as $\alpha_i(t)$ is predictable and the expected value is **not** necessarily random

## CAPM For Portfolios

CAPM for portfolios leverages the same equation but for a variety of stocks:

$r_p(t) = \sum_{i} w_i (\beta_i r_m(t) + \alpha_i(t))$

Recall that passive investing CAPM would be different than an active investing CAPM:

- Passive CAPM: $r_p(t) = \beta_p r_m(t) + \alpha_p(t)$
- Active CAPM: $r_p(t) = \beta_p r_m(t) +  \sum_{i} w_i \alpha_i(t)$

## Implications Of CAPM

The implications of CAPM are:

- Expected value of $\alpha$ is almost always zero
- The only way to beat the market is by choosing $\beta$
- Choose high $\beta$ in up markets
- Choose low $\beta$ in down markets

However, EMH (Efficient Markets Hypothesis) claims that you cannot predict the market with $\beta$.

## Arbitrage Pricing Theory

**Arbitrage Pricing Theory** suggests that instead of treating $\beta$ as representing a particular stock with respect to the entire market, there are instead multiple $\beta$ for representing a particular stock with respect to various sectors of the market. Therefore, the return becomes:

$r_i(t) = \sum_{i} (\beta_i r_m(t)) + \alpha_i(t)$

Where $\beta_i r_m(t)$ represents a particular stock in a particular sector.

## Section Quizzes

### What Is The Portfolio Return As A Percentage Quiz

_Given the following weights and returns (provided), what is the portfolio return as a percentage_? `(0.75)(0.01) + (-0.25)(0.02) = 1.25`

### Compare Alpha And Beta Quiz

_Given the following scenarios for $\beta$ and $\alpha$, select the best answer_.

1. _Which has a higher $\beta$_? ABC, since the slope is steeper
2. _Which has a higher $\alpha$_? ABC, since the y-intercept is greater

### Implications Of CAPM Quiz

_Given the following market scenarios (provided), select the best answer_.

1. _In upward markets, do you want a larger or smaller $\beta_p$_? Larger, since you can take advantage of the high prices
2. _In downward markets, do you want a larger or smaller $\beta_p$_? Smaller, since you do not want to risk crashing

# Lesson 10

In this lesson we will examine how financial institutions utilize ML (machine learning) techniques and tools to predict future prices for stocks or other assets.

## The ML problem

ML models are used for many things. In general, a ML model is one that takes in an input $x$ (typically a vector of observations) and outputs $y$ (predictions).

Not all financial models utilize ML (e.g., [Black Scholes Model](https://www.investopedia.com/terms/b/blackscholes.asp))

The ML process consists of:

1. Feeding data into a ML algorithm
2. Producing a ML model from the ML algorithm
3. Using the ML model to predict $y$ with observations $x$

## Supervised Regression Learning

**Supervised regression learning** is simply a numerical prediction that occurs after an ML model is developed with data ($x$ and $y$ examples). Some techniques include:

- Linear regression (parametric since it does not store previous results)
- K-nearest neighbors (instance based since it stores previous results)
- Decision trees
- Decision forests

## How It Works With Stock Data

To leverage ML we have to start with out historical data for $x$ observations (which may be multi-dimensional depending on how many things we want to look at) and map each of our $x$ to the corresponding $y$ outputs. This information will be stored in our database.

## Example At A FinTech Company

How does the ML process work at a typical FinTech company?

1. Select $x$ (predictive factors) and $y$ outputs
2. Set desired time period and how many stock parameters we want to look at (e.g., P/E ratio, alpha, beta, etc.)
3. Train our model using a ML algorithm (in this case one of the supervised regression learning algorithms)
4. Plug a new $x$ into our trained ML model to produce a new $y$ prediction

## Backtesting

How can we be confident that our models can predict future stock prices? One way to evaluate our model is through **backtesting** which utilizes a portion of historical data to predict prices in the future (the _historical future_ which is the time period that _already_ occurred) then compare that to the _actual_ prices which occurred within the same time period.

## Problems With Regression

There are several problems with regression however:

- Predictions are noisy and uncertain (the more data the better)
- Challenging to estimate prediction confidence
- Unknown holding time and allocation

Some of these challenges may be solved with reinforcement learning (e.g., policy learning where a system learns whether to buy or sell a stock).

## Section Quizzes

### What Is X And Y Quiz

1. _Which of the following (provided) could be X_?
   - Price momentum
   - Bollinger value
   - Current price
2. _Which of the following (provided) could be Y_?
   - Future price
   - Future return

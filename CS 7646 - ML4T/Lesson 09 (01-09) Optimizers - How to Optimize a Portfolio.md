# Lesson 9

The final project of this course is to create a portfolio optimizer. In this lesson we will define what a portfolio optimizer is and how to go about creating one.

## What Is Portfolio Optimization

A portfolio optimizer works as follows:

- _Given_ a set of assets and a time period
- _Find_ an allocation of funds to assets that maximizes performance

What is performance? Recall that we can use metrics such as cumulative return, risk (STD returns), risk adjusted return (Sharpe ratio)

## Framing The Problem

One way to optimize our portfolio while minimizing risk is to optimize the Sharpe ratio of our portfolio. We may do approach optimization by:

1. Providing a function to minimize $f(x) = SR - 1$ (where SR is Sharpe ratio)
2. Providing an initial guess for $x$
3. Calling the optimizer

Where $x$ are the allocations (a vector of allocations for each stock) we are looking for to optimize our portfolio $f(x)$.

## Ranges And Constraints

To make the optimizer more efficient we could set:

- **Ranges**: limits on values for $x$ (e.g., each allocation cannot be over 100%)
- **Constraints**: properties of $x$ which must be true (e.g., sum of all allocations cannot be over 100%)

## Section Quizzes

### Which Criteria Is Easiest To Solve For Quiz

_For which (given criteria) would it be easiest to solve_? Cumulative return since all we have to do is invest all money into one stock which would optimize our portfolio (no good for risk however).

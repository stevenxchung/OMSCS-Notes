# Lesson 8

In this lesson we will be examining optimizers which will allow us to theoretically optimize portfolios and other statistics.

## What Is An Optimizer

An **optimizer** works by finding minimum values of functions. An optimizer also allows us to build parameterized models based on data. We can also refine allocations to stocks in portfolios as mentioned previously.

In general, we use an optimizer by:

1. Providing a function to minimize
2. Providing an initial guess
3. Calling the optimizer

## Convex Problems

**Convex problems** are easiest for the optimizer to solve. These problems are characterized by having a single minima where a line segment drawn between any two points on the graph is always above the graph (does not intersect more than two points).

## Building A Parameterized Model

When building out a parameterized model, we should think about what we are minimizing. E.g., find a line of best fit for scatter plot which requires finding the coefficients that minimize the distance between all points on the plot.

## Section Quizzes

### How To Defeat A Minimizer Quiz

1. _Would this function (provided) be hard to solve and why_? Yes, because this function has a constant initial condition which does not provide a gradient until later
2. _Would this function (provided) be hard to solve and why_? Yes, because this function has multiple minima (local)
3. _Would this function (provided) be hard to solve and why_? No, because the minima would be at the intersection of the two lines
4. _Would this function (provided) be hard to solve and why_? Yes, because this function is not continuous and because of the constant initial condition

### What Is A Good Error Metric Quiz

_Which of these metrics (provided) would be good for minimizing_? Either `sum(abs(error))` or `sum(squared(error))`.

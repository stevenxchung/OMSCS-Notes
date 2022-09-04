# Lesson 2

In this lesson we will be covering **Kalman Filters** which:

> ... is an algorithm that uses a series of measurements observed over time, containing statistical noise and other inaccuracies, and produces estimates of unknown variables that tend to be more accurate than those based on a single measurement alone, by estimating a joint probability distribution over the variables for each time frame. -Wiki

## Gaussian Intro

In localization, we observed probabilities distributed in terms of a histogram filter which discretely approximates the continuous distribution (Monte Carlo localization). However, for Kalman Filters the distribution is characterized by the **Gaussian distribution** or Gaussian which serves as the _belief_ of where a robot is in the world.

The Gaussian distribution has the following characteristics:

- The shape of the Gaussian is unimodal
- The area underneath a Gaussian sums to 1
- Mean $\mu$: the average of all data points in the distribution
- Width $\sigma^2$: the variance of a specific data point from the mean

A 1-D Gaussian is characterized by $\mu \sigma^2$ which is the estimation of the location of an object of interest. The formal definition of the Gaussian function is as follows:

$f(x) = \frac{1}{\sqrt{2\pi\sigma^2}} e^-\frac{(x - \mu)^2}{2\sigma^2}$

The larger the variance, the more uncertain we are in our measurements.

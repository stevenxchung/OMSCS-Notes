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

## Shifting The Mean

Recall that there were two main parts for localization:

1. _Measurements_ (via Bayes' Rule or a product)
2. _Motion_ (via Total Probability or convolution)

Similarly, when using Kalman Filters in robotics, the main objectives are:

1. _Measurements (or update)_ (via Bayes' Rule or a product)
2. _Predictions_ (via Total Probability or convolution)

We leverage the Gaussian function to implement each of these steps.

## Parameter Update

Suppose we have a prior Gaussian characterized by $\mu\sigma^2$ and the _measurement_ Gaussian is characterized by $\nu r^2$. After an update the mean and variance of the new Gaussian can be determined by:

- Mean of Gaussian after update: $\mu = \frac{\mu r^2 + \nu \sigma^2}{r^2 + \sigma^2}$
- Variance of Gaussian after update: $\sigma^2 = \frac{1}{(r^-2 + \sigma^-2)}$

**Note**: the variance terms in the new mean of the Gaussian after update are swapped in the numerator.

## Gaussian Motion

For the _prediction_ step, the motion update after a _motion_ Gaussian is applied can be determined by:

- Mean of Gaussian after update: $\mu = \mu + \nu$
- Variance of Gaussian after update: $\sigma^2 = \sigma^2 + r^2$

Where $\nu$ is the displacement and $r$ is the variance of the motion Gaussian.

## More Kalman Filters

In the 2-D space, Kalman Filters can make use of multi-variable Gaussian, to predict states (e.g. position) without directly measuring hidden states (e.g., velocity). This is done by collecting observable data that helps us build a slanted Gaussian (correlated Gaussian) on the x-y plane. In this way, we are able to predict new locations with the following relation:

$x = x + \dot{x} \Delta t$

Where $\dot{x}$ is the hidden state (velocity). Note that this is exactly one of [Newton's equations of motion](https://en.wikipedia.org/wiki/Equations_of_motion) for position.

The variable of Kalman Filters (or states) separate into two categories:

1. **Observables**: states we _can_ directly observe (e.g., the location in the classroom example)
2. **Hidden**: states we _cannot_ directly observe (e.g., the velocity in the classroom example)

Because observable states can interact with hidden states, we can gather information about the hidden states.

# Lesson 1

In this lesson we will examine a classic problem in AI and robotics: how to we determine a robot's position in an environment? This problem is also known as **localization**:

> ... the robot's ability to establish its own position and orientation within the frame of reference. -Wiki

## Total Probability

Imagine a robot is in a one dimensional world. Imagine a that robot has a map of the world and knows what a door looks like.

How might a robot determine where it is locally?

1. The robot starts out by not knowing where it is (it has a _belief_ modeled by _uniform maximum confusion_)
2. A robot can determine it's _posterior belief_ after measurements are taken of where possible objects are (e.g., doors)
3. When a robot moves, a _convolution_ of the posterior belief occurs a creates a _prior belief_
4. If we multiply the posterior belief with the prior belief, we get a brand new posterior belief that allows the robot to localize itself

This is the general idea of a [histogram filter](https://www.deepideas.net/robot-localization-histogram-filter/).

## Sense And Move

The localization problem can be generalized into a _sense and move_ iterative process that begins with an initial belief (initial conditions). In general, the following occur based on robot action:

- When a robot _senses_ it _gains_ information
- When a robot _moves_ it _loses_ information

We may measure the information gained or lost with **entropy** (measures the amount of information in our distribution):

$\sum p(x_i) * log(p(x_i)\\$

## Localization Summary

What did we learn in this lesson?

- Localization maintains a function over all possible places an object of interest might be where each cell has an associated probability value (_belief_)
- The _measurement_ update function can be generalized into a _product_ followed by normalization
- _Motion_ is a _convolution_ (for each possible location after the motion, we guess where the object of interest might have come from and collect the corresponding probabilities)

## Bayes' Rule

Formally, **Bayes' Rule** is as follows:

$P(A_i | B) = \frac{P(B | A_i) * P(A_i)}{P(B)}\\$

- Where $A, B$ are events
- $P(A | B)$ is probability of $A$ given $B$ is true (posterior)
- $P(B | A)$ is probability of $B$ given $A$ is true (likelihood)
- $P(A), P(B)$ are the independent probabilities of $A$ and $B$

In terms of localization, $A$ are the grid cells, and $B$ is the measurement taken by the robot. $P(B | A)$ is the measurement probability, $P(A)$ is the prior, and $P(B) = \sum P(B | A_i) * P(A_i)$.

We may define a normalizer $\alpha = \sum \bar{P}(A_i | B)$ such that $P(A_i | B) = \frac{\bar{P}(A_i | B)}{\alpha}$.

# Lesson 3

In this lesson we will examine a third way to estimate the state of a system known as **particle filters** which are:

> ... Sequential Monte Carlo (SMC) methods are a set of Monte Carlo algorithms used to solve filtering problems arising in signal processing and Bayesian statistical inference. The filtering problem consists of estimating the internal states in dynamical systems when partial observations are made, and random perturbations are present in the sensors as well as in the dynamical system. The objective is to compute the posterior distributions of the states of some Markov process, given some noisy and partial observations. -Wiki

Particle filters have an advantage of being easiest to program and are the most flexible.

## Particle Filters

Some characteristics of particle filters include:

- Continuous state space
- Multi-modal _belief_
- Variable efficiency depending on the problem (scales well in the tracking domain but not recommended to use outside of 4 dimensions)
- Offer approximate results

However, the biggest key advantage is that they are easy to program.

In application, particle filters may be represented as dots which counts as a single guess as to where a robot is (consists of x and y coordinates and heading direction). Overall, there may be several thousand dots (discrete guesses) which comprise of a filter (approximate representation of the _posterior_ for the robot). In order for the filter to work, only the particles consistent with the measurements are to be kept (thereby localizing the robot).

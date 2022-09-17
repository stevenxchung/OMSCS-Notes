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

## Importance Weight

The **importance weight** may be calculated from comparing the actual measurement to the predicted measurement. The larger the weight, the more important the particle. The probability of _survival_ for the particles will depend on the importance weight. Particles with high weight tend to cluster around regions of higher posterior probability.

## Resampling

**Resampling** is an activity that takes $n$ particles and creates a new set with those $n$ particles $m$ times. After $m$ counts of resampling, only particles with high importance weights are kept.

## Resampling Wheel

One way to go about resampling particles from one set to another is through a resampling wheel:

```python
p3 = []
index = int(random.random() * N)
beta = 0
mw = max(w)
for i in range(N):
    beta += random.random() * 2 * mw
    while beta > w[index]:
        beta -= w[index]
        index = (index + 1) % N
    p3.append(p[index])

p = p3
```

In this implementation, the particles which occupy more space in the array (since their weights are higher) will have greater chance of being selected.

## Filters

Recall that filters have two main parts in AI for robotics:

1. _Measurement_ updates
2. _Motion_ updates

In terms of particle filters, the measurement update (resampling process) may be formalized as:

$P(X|Z) \propto P(Z|X) P(X)\\$

Where $P(Z|X)$ represents the importance weights and $P(X)$ represents the particles.

Similarly, the motion updates may be given by:

$P(X') = \sum P(X'|X) P(X)\\$

Where $P(X'|X)$ represents the samples and $P(X)$ represents the particles.

## Section Quizzes

### State Space Quiz

1. _Are Histogram Filters discrete or continuous_? Discrete
2. _Are Kalman Filters discrete or continuous_? Continuous

### Belief Modality Quiz

1. _Can a Histogram Filter be multi-modal, or just unimodal_? Can be multi-modal
2. _Can a Kalman Filter be multi-modal, or just unimodal_? Cannot be multi-modal (just unimodal)

### Efficiency Quiz

1. _In regards to Histogram Filters, when it comes to scaling in the number of dimensions of the state space, which of the following is the amount of storage that must be assigned_? Exponential
2. _In regards to Kalman Filters, when it comes to scaling in the number of dimensions of the state space, which of the following is the amount of storage that must be assigned_? Quadratic

### Exact Or Approximate Quiz

1. _When applied to robots, do you believe the Histogram Filter is exact or approximate_? Approximate
2. _When applied to robots, do you believe the Kalman Filter is exact or approximate_? Approximate

### Resampling Quiz

_Suppose you have 5 particles, $P_1 ... P_5$, with the following importance weights: $W_1 ... W_5$ equals 0.6, 1.2, 2.4, 0.6, and 1.2 respectively. When resampling, if you randomly draw a particle in accordance with the importance weights, calculate the probability of drawing each particle_.

1. $P(P_1) = (0.6/6) = 0.1$
2. $P(P_2) = (1.2/6) = 0.2$
3. $P(P_3) = (2.4/6) = 0.4$
4. $P(P_4) = (0.6/6) = 0.1$
5. $P(P_5) = (1.2/6) = 0.2$

### Never Sampled 1 Quiz

_With $N = 5$ and given these alpha values (provided), is it possible that $P_1$ is never sampled_? Yes.

### Never Sampled 2 Quiz

_With $N = 5$ and given these alpha values (provided), is it possible that $P_3$ is never sampled_? Yes.

### Never Sampled 3 Quiz

_What is the probability that $P_3$ is never sampled after $N = 5$ resamples_? The probability that $P_3$ is never sampled after 5 resamples is $P(\lnot P_3) = 0.6^N = 0.6^5 = 0.0777$.

### Orientation 1 Quiz

_Will orientation never play a role_? No, orientation eventually will matter

### Filters Quiz

_Which filters did Sebastian use in his job talk at Stanford_?

- Histogram filters
- Particle filters

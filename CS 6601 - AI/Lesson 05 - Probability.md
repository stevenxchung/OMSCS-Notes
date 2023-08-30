# Lesson 5

In this lesson we will introduce the building blocks for **Bayes networks** which is a compact representation of a distribution over a typically large joint probability distribution of many variables. Topics include:

- Binary events
- Probability
- Simple Bayes networks
- Conditional independence
- Bayes networks
- D-separation
- Parameter counts

## Bayes Network

A [Bayes network](https://en.wikipedia.org/wiki/Bayesian_network) is a _DAG (directed acyclic graph)_ composed of nodes or events that we may or may not know (random variables). The arcs (arrows) suggests that the child of a node (arrow pointing to) is influenced by the parent (arrow pointing out). The graph structure and associated probabilities specify a probability distribution in the space of all specified variables.

Once we specify the Bayes network, we can observe events (e.g., the car won't start) and compute probabilities of certain hypotheses (e.g., the car won't start because the battery is dead).

Bayes networks are used extensively in almost all fields of smart computer systems including but not limited to:

- Diagnostics
- Prediction
- Machine Learning
- Finance
- Google
- Robotics

Bayes networks are also the building blocks of more advanced AI techniques including but not limited to:

- [Particle filters](https://en.wikipedia.org/wiki/Particle_filter)
- [HMM (hidden Markov models)](https://en.wikipedia.org/wiki/Hidden_Markov_model)
- [MDPs (Markov decision process)](https://en.wikipedia.org/wiki/Markov_decision_process)
- [POMDPs (partially observable MDPs)](https://en.wikipedia.org/wiki/Partially_observable_Markov_decision_process)
- [Kalman filters](https://en.wikipedia.org/wiki/Kalman_filter)

## Probabilities

We can take away a few things from the brief exercises:

- **Complementary probability**: if $P(A) = p$ then $P(\neg A) = 1 - p$
- **Independence**: $X \perp Y: P(X) * P(Y) = P(X, Y)$

Additionally, we can specify total probability as $P(B) = \sum P(B | A_i) * P(A_i)$ and that $P(\neg A | B) = 1 - P(A | B)$

## Bayes' Rule

As covered previously in AI4R:

> Formally, **Bayes' Rule** is as follows:
>
> $P(A_i | B) = \frac{P(B | A_i) * P(A_i)}{P(B)}\\$
>
> - Where $A, B$ are events
> - $P(A | B)$ is probability of $A$ given $B$ is true (posterior)
> - $P(B | A)$ is probability of $B$ given $A$ is true (likelihood)
> - $P(A), P(B)$ are the independent probabilities of $A$ and $B$
>
> Note that the total probability is defined as $P(B) = \sum P(B | A_i) * P(A_i)$ which is the same as marginal likelihood. $P(A)$ is known as the prior.

## Section Quizzes

**Note**: will be somewhat limited for this semester.

### Probability Quiz

_Given the following, determine the probability of occurrence_.

1. _The probability that 4 coin flips will be the same given there are always two outcomes (heads or tails)_? $P(x_1 = x_2 = x_3 = x_4) = P(H^4) + P(T^4) = \frac{1}{16} + \frac{1}{16} = \frac{1}{8}$
2. _The probability that 4 coin flips contains 3 or more heads_? $P(x_1, x_2, x_3, x_4) = 5 * P(H^4) = \frac{5}{16}$

### Dependence Quiz

_Given the following_:

$P(x_1 = H) = \frac{1}{2}\\$
$P(x_2 = H | x_1 = H) = 0.9\\$
$P(x_2 = T | x_1 = T) = 0.8\\$

_Determine $P(x_2 = H)$_.

$P(x_2 = H) = P(x_2 = H | x_1 = H) * P(x_1 = H) + P(x_2 = H | x_1 = T) * P(x_1 = T) = 0.9 * \frac{1}{2} + 0.2 * \frac{1}{2} = 0.55$.

### Rainy Or Sunny Quiz

_Given the following_:

$P(D_1 = sunny) = 0.9\\$
$P(D_2 = sunny | D_1 = sunny) = 0.8\\$
$P(D_2 = sunny | D_1 = rainy) = 0.6\\$

_Determine $P(D_2 = sunny)$ and $P(D_3 = sunny)$_.

- $P(D_2 = sunny) = P(D_1 = sunny) * P(D_2 = sunny | D_1 = sunny) + P(\neg D_1 = sunny) * P(D_2 = sunny | D_1 = rainy) = 0.9 * 0.8 + 0.1 * 0.6 = 0.78$
- $P(D_3 = sunny) = P(D_2 = sunny) * P(D_2 = sunny | D_1 = sunny) + P(\neg D_2 = sunny) * P(D_2 = sunny | D_1 = rainy) = 0.78 * 0.8 + 0.22 * 0.6 = 0.756$

## Cancer Or No Cancer Quiz

_Given the following_:

$P(c) = 0.01\\$
$P(\neg c) = 0.99\\$
$P(+ | c) = 0.9\\$
$P(- | c) = 0.1\\$
$P(+ | \neg c) = 0.2\\$
$P(- | \neg c) = 0.8\\$

_Determine $P(c | +)$_.

First the joint probabilities are given by:

- $P(+, c) = P(c) * P(+ | c) = 0.01 * 0.9 = 0.009$
- $P(-, c) = P(c) * P(- | c) = 0.01 * 0.1 = 0.001$
- $P(+, \neg c) = P(\neg c) * P(+ | \neg c) = 0.99 * 0.2 = 0.198$
- $P(-, \neg c) = P(\neg c) * P(- | \neg c) = 0.99 * 0.8 = 0.792$

Therefore, $P(c | +) = \frac{P(+, c)}{P(+, c) + P(+, \neg c)} = 0.043$.

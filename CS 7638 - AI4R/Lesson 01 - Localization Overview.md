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

## Theorem Of Total Probability

The theorem of total probability is as follows:

$P(A) = \sum P(A \sqcap B_n)\\$

- Where, $P$ is the probability
- $A$ is any event
- $B_n$ is a specific event

In terms of motion, $P(A)$ represents the probability of being _in a specific grid cell_ after forward motion.

## Section Quizzes

### Uniform Probability Quiz

_For all cells `X = 1... 5`, what is the probability of any of those `X`'s_? 1/5 or 0.2.

### Probability After Sense Quiz

_Fill in the blanks below based on the values provided. Each blank corresponds to the cells in order as shown in the image_.

| Green | Red  | Red  | Green | Green |
| ----- | ---- | ---- | ----- | ----- |
| 0.04  | 0.12 | 0.12 | 0.04  | 0.04  |

### Compute Sum Quiz

_Input the sum of the values of the cells (provided)_. The sum is 0.36.

### Normalize Distribution Quiz

_Based on the instructions in the quiz intro video, normalize the distribution by dividing the value of each cell by the sum. Give your answers in the form of a fraction below corresponding to the cell in the image from the video. The sum should equal 1_.

| Green | Red | Red | Green | Green |
| ----- | --- | --- | ----- | ----- |
| 1/9   | 1/3 | 1/3 | 1/9   | 1/9   |

### Exact Motion Quiz

_Enter posterior probability after a single move to the right, assuming the world is cyclic_.

| Green | Red | Red | Green | Green |
| ----- | --- | --- | ----- | ----- |
| 1/9   | 1/3 | 1/3 | 1/9   | 1/9   |

### Inexact Motion 1 Quiz

_Given the initial distribution provided above (provided), input the distribution after the motion_.

| X_0 | X_1 | X_2 | X_3 | X_4 |
| --- | --- | --- | --- | --- |
| 0   | 0   | 0.1 | .8  | 0.1 |

### Inexact Motion 2 Quiz

_Given the initial distribution provided above (provided), input the distribution after the motion_.

| X_0 | X_1  | X_2  | X_3 | X_4 |
| --- | ---- | ---- | --- | --- |
| 0.4 | 0.05 | 0.05 | 0.4 | 0.1 |

### Inexact Motion 3 Quiz

_Given the initial distribution provided above (provided), input the distribution after the motion_.

| X_0 | X_1 | X_2 | X_3 | X_4 |
| --- | --- | --- | --- | --- |
| 0.2 | 0.2 | 0.2 | 0.2 | 0.2 |

### Limit Distribution Quiz

_Given the initial distribution above (provided), suppose you run infinitely many motion steps (U = 1 to the right forever) in a cyclical world, what will be the limit, or stationary, distribution be in the end_?

| X_0 | X_1 | X_2 | X_3 | X_4 |
| --- | --- | --- | --- | --- |
| 0.2 | 0.2 | 0.2 | 0.2 | 0.2 |

### Formal Definition Of Probability 1 Quiz

_Supposing x can only take two values, solve the following_:

$0 \leqq P(X) \leqq 1\\$
$P(X_1) = 0.2\\$
$P(X_2) = ?\\$

Since `P(X) = P(X1) + P(X2)`, `P(X2) = 0.8`

### Formal Definition Of Probability 2 Quiz

_Supposing x can only take two values, solve the following_:

$0 \leqq P(X) \leqq 1\\$
$P(X_1) = 0\\$
$P(X_2) = ?\\$

Since `P(X) = P(X1) + P(X2)`, `P(X2) = 1`

### Formal Definition Of Probability 3 Quiz

_What is the probability of the 5th, and final, cell grid_?

$0 \leqq P(X) \leqq 1\\$

| X_0 | X_1 | X_2 | X_3 | X_4 |
| --- | --- | --- | --- | --- |
| 0.1 | 0.1 | 0.1 | 0.1 | 0.6 |

Since `P(X) = P(X_i) + ... + P(X_n)`, `P(X_n) = 0.6`

### Cancer Test Quiz

_Using the probabilities above (provided), calculate the probability of cancer given a positive result_.

Since `P_bar(C|Pos) = P(C) * P(POS|C) = 0.0008` and `P_bar(!C|Pos) = P(!C) * P(POS|!C) = 0.0999`, recalling that the normalizer `alpha = P_bar(C|Pos) + P_bar(!C|Pos) = 0.1007`, therefore, the final answer is `P(C|Pos) = P_bar(C|Pos) / alpha = 0.0079`.

### Coin Flip Quiz

_Given these conditions (provided), what is the total probability of the final result being heads_?

`P(H) = P(H|H) * P(H) + P(H|T) * P(T) = 0.5 * 0.5 + 0 * 0.5`

### Two Coin Quiz

_Presume a fair coin for which $P(H) = 0.5$ and a loaded coin for which $P(H) = 0.1$, and that you will choose one of the coins with a 50% chance of being either coin. If you flip the coin and observe heads, what is the probability that the coin you chose was fair_?

Since `P_bar(F|H) = P(F) * P(H|F) = 0.25` and `P_bar(!F|H) = P(!F) * P(H|!F) = 0.05`, recalling that the normalizer `alpha = P_bar(F|H) + P_bar(!F|H) = 0.3`, therefore, the final answer is `P(C|Pos) = P_bar(F|H) / alpha = 0.833`.

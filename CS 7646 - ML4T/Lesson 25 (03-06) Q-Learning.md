# Lesson 25

In this lesson we will examine how Q-learning (model-free approach) is able to build a table of utility values (from _experience tuples_ as discussed in last lesson) in real-time while interacting with the world. A Q-learner generates an optimal policy which seeks to maximize portfolio returns.

## What Is Q

$Q(s, a)$ is a variable or table that represents the _immediate reward_ plus _discounted reward_ if we perform action $a$ at state $s$. How do we use $Q(s, a)$? We compute:

$\pi(s) = argmax_a(Q(s, a))\\$

Where we find the maximum $a$ that maximizes $Q(s, a)$. After a period of time, $\pi(s)$ will converge to $\pi^*(s) = Q^*(s, a)$ which represents the optimal policy.

## Learning Procedure

The Q-learner procedure is as follows:

1. Select training data
2. Iterate over time (we obtain an experience tuple $(s, a, s', r)$ with each iteration)
3. Test policy $\pi(s)$ (where performance should get better each time)
4. Repeat until $\pi^*(s)$ is obtained

During the iteration step, we perform the following:

1. Set start time and initialize $Q$
2. Compute state $s$
3. Select action $a$
4. Observe reward $r$ and resultant state $s'$
5. Update $Q$

## Update Rule

Each subsequent iteration from initial will require a blended $Q$ value:

$Q'(s, a) = (1 - \alpha) Q(s, a) + \alpha (r + \gamma * Q(s', argmax_a'(Q(s', a')))\\$

Where the learning rate $0 \leq \alpha \leq 1$ is usually set around 0.2. We can break down the improved estimates term $(r + \gamma * Q(s', argmax_a'(Q(s', a')))$ as follows:

- Immediate reward $r$ for taking action $a$ at state $s$
- Discount rate $0 \leq \gamma \leq 1$ (as discussed in previous lesson)
- Later rewards $Q(s', argmax_a'(Q(s', a'))$ which includes action $argmax_a'(Q(s', a')$ that maximizes the Q-value among all possible actions $a'$ at resultant state $s'$.

## Two Finer Points

While training Q-learners, success depends on exploration. Therefore we choose random actions at the beginning of training with probability (usually around 0.3). We also want to decrement the randomness with each iteration such that we do not introduce randomness when converging to an optimal policy.

## Creating The State

When creating the state we need to represent the state as a single integer by:

- Discretizing each factor into an integer
- Combining integers from each factor into a single integer (not adding)

## Discretizing

How do we discretize each factor into an integer between some range? First determine how many `steps` we want to have between the minimum and maximum values. Then we can use an algorithm:

```python
step_size = len(data)/steps
data.sort()

for i in range(0, steps)
    threshold[i] = data[(i + 1) * step_size]
```

## Q-Learning Recap

The Q-learning process could be summarized as:

- **Training**:
  - Define states, actions, rewards
  - Choose in-sample training period
  - Iterate: Q-table update
  - Back test, evaluate performance, and iterate until convergence
- **Testing**: Back test on later data

## Section Quizzes

### Rewards Quiz

_Which results in faster convergence_? Setting `r = daily_return` since a reward at each step allows the Q-learner to get feedback on each individual action it takes (including doing nothing).

### State Quiz

_Which of the following (provided) could or should be a state_?

- Adjusted close / SMA
- Bollinger Band value
- P/E ratio
- Holding stock
- Return since entry

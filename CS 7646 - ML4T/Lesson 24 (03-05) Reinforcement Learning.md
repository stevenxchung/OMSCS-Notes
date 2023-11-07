# Lesson 24

So far we have focused on learners which forecast price changes. However, these learners are not able to help with determining certainty or when to exit a position. In this lesson we examine reinforcement learners which enable decision making based on policies.

## The RL Problem

The **RL (reinforcement learning)** problem is one where a learner:

- Senses outputs $S$ from an environment $T$ (or the market in our case)
- Thinks about how to act via algorithm $Q$
- Produces an action $A$ to the environment $T$

An objective of the reinforcement learner is to maximize rewards $R$ (or portfolio returns in our case) with each cycle of reinforcement learning (as shown in lecture).

## Markov Decision Problems

At the heart of the RL problem are **MDP (Markov decision problems)** which consist of:

- Set of states: $S$
- Set of actions: $A$
- Transition function: $T(s, a, s')$, where $s'$ is a resultant state
- Reward function: $R(s, a)$

The objective for the learner is to find a policy $\pi^*(s)$ that will maximize reward using algorithms such as _policy iteration_ or _value iteration_.

## Unknown Transitions And Rewards

One of the challenges in using RL in trading is that we do not have a transition function or a reward function. So how do we leverage RL in trading? We have to _interact_ with the world and observe _outputs_ in order to build a policy. Each time we interact with the world we add to our experience via _experience tuple_ (tuple containing current state, action, next state, and reward).

There are various ways to leverage experience tuples:

- Model-based:
  - Build model of $T(s, a, s')$ and $R(s, a)$
  - Use value or policy iteration to solve the problem
- Model-free:
  - E.g., Q-learning (solve as experience tuples come in real-time)

## What To Optimize

We may determine what to optimize by examining the sum of all rewards for an infinite horizon:

$\sum_{n=1}^{\infty} \lambda^{i-1} r_i \\$

Where $\lambda$ represents the discounted reward coefficient and may range from $0 \leq \lambda \leq 1$. If $\lambda = 1$ then an infinite horizon case applies. Note that we may also examine finite reward horizons as well.

A Q-learner will seek to maximize the rewards equation above.

## Reinforcement Learning Summary

The summary for this lesson is as follows:

- RL algorithms solve MDPs
- MDPs are represented by $S$, $A$, $T(s, a, s')$, and $R(s, a)$
- Goal for RL is to find an optimal policy $\pi^*(s)$ that maps a state $s$ to an action $a$ we should take such that reward $R(s, a)$ is maximized

By mapping trading to an RL problem, we may find an optimal policy which allows us to maximize portfolio returns.

## Section Quizzes

### Trading As An RL Problem Quiz

_For each given attribute, select whether the attribute is a state, action, reward, or a combination_.

1. Buy: action
2. Sell: action
3. Holding long: state
4. Bollinger value: state
5. Return from trade: reward
6. Daily return: state and reward

### Which Approaches Gets $1M Quiz

_Given the scenario (provided), which approach will get $1M_?

- Infinite horizon
- Finite with `n = 10`
- Discounted with `gamma = 0.95`

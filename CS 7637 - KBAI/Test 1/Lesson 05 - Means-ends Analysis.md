# Lesson 5

Not all problems are well-formed but for those that are, another type of analysis which will be useful for us is the means-ends analysis. This lesson will cover the following:

- State spaces
- Means-ends analysis
- Problem solving with means-ends analysis
- Problem reduction

## State Spaces

We can imagine problem solving as occurring in a state space. There is an initial state and a goal state where the goal state consists of all of the states that could be produced from the initial state to fulfill the goal.

## Differences In State Spaces

So how does an AI agent get from the initial state to the goal state? When examining differences in state spaces compared to the goal state, the agent can select an operator (means) which will produce a state that matches the goal state (ends) or gets closer to the goal state. This is what we mean by means-ends analysis, to select an operator to meet the end state.

## Process Of Means-ends Analysis

For each operator that can be applied:

1. Apply the operator to the current state
2. Calculate the difference between new state and goal state

The agent should prefer the state that minimizes the distance between new and goal state.

## Problem Reduction

The concept of problem reduction is to reduce a problem and find the solutions for those sub-problems. Then once those solutions are found, combine them to solve the whole problem.

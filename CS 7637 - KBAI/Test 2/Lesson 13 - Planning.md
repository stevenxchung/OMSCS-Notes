# Lesson 13

An intelligent agent maps perceptual histories into actions. Consequently, _planning_ is a powerful tool for action selection. In this lesson we will cover:

1. States, goals, and operators
2. Conflicts in planning
3. Partial-order planning
4. Hierarchical task networks

## Planning And State Spaces

Referring back to state spaces, a search method is inefficient because it uses no knowledge. Since we have knowledge of the goal and asset knowledge (i.e., how to select an operator), we could better select actions which allow us to obtain our goal as we saw with means-ends analysis.

Planning provides more systematic processes for selecting different operators. How to we do operator selection? We can do this the same way as mapping perceptual histories into actions. Operators represent mental representations of actions available in the world.

## Planning

In means-ends analysis we saw that we could generate states which make it impossible to achieve the goal. This is also know as **goal clobbering** a linear planning technique (e.g., means-ends analysis) that goes about generating states without reasoning conflicts which could block the goal state. How might an intelligent agent be able to reason about the order of actions such that the goal is achieved?

## Partial-order Planning

**Partial-order planning** occurs when there are multiple goals and the plan for achieving one goal clobbers with another.

## Detecting Conflicts

How might a planner detect conflicts?

For each precondition in the current plan:

- If pre-condition for an operator in the current plan is clobbered by a state in another plan:
  - Promote current plan's goal above the other plan's goal

## Open Preconditions

How does partial-order planning work in practice? We can begin to understand by examining the following principles:

1. Knowledge is not just about the world but it is control knowledge which helps us select between operators
2. Goals provide us control knowledge as they can be used to decide between different operators which help us move closer to the goal
3. We can view partial-order planning as an interaction between several different agents or abilities where each agent represents a small micro ability:
   - An agent that helps us generate plans for each goal independently
   - An agent that is responsible for detecting conflicts between them
   - An agent that is responsible for resolving these conflicts

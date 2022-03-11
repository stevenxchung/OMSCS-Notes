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

## Hierarchical Task Network Planning

Referring to our partial order planning exercises, can we abstract some operations at a higher-level? The idea here is to make the the problem space much smaller and simpler to navigate.

## Hierarchical Decomposition

Referring to the block exercises, we can decompose several higher-level operations into micro-operations which may include definitions on pre-conditions, post-conditions, and methods.

## Hierarchical Planning

Most real-world problems have a large and complex problem space. In order for AI agents to handle such problems, it must be able to think at multiple levels of abstraction. An AI agent must be able to use knowledge at various levels of abstraction in order to solve difficult problems.

## Section Quizzes

### Partial Order Planning I Quiz

_Write the current and goal states in propositional logic_.

1. `On(D, B) ˄ On(B, A) ˄ On(A, C) ˄ On(C, Table)`
2. `On(A, B) ˄ On(B, C) ˄ On(C, D) ˄ On(D, Table)`

### Partial Order Planning II Quiz

_Write the pre- and post-conditions for the two Move operators_.

1. `Clear(x) ˄ Clear(y)`
2. `On(x, y)`
3. `Clear(x)`
4. `On(x, Table)`

### Partial Order Planning III Quiz

_Write plans for accomplishing each goal_.

1. `Move(D, Table) Move(B, Table) Move(A, B)`
2. `Move(D, Table) Move(B, Table) Move(A, Table) Move(B, C)`
3. `Move(D, Table) Move(B, Table) Move(A, Table) Move(C, D)`

### Partial Order Planning IV Quiz

_Use partial-order planning to order the plans_.

1. 3rd
2. 2nd
3. 1st

### Partial Order Planning V Quiz

_Write a final plan for converting the current state to the goal state_.

1. `Move(D, Table) Move(B, Table) Move(A, Table) Move(C, D) Move(B, C) Move(A,B)`

### Final Quiz

_What did you learn in this lesson_?

- Planning is a process central to cognition as action selection is central to cognition
- Planning is required to select the appropriate action
- Control knowledge helps us select different actions and operators
- Intelligent agents can deal with goal clobbering by detecting conflicts with one micro agent and resolving conflicts with another agent
- Intelligent agents simplify large complex problems by using knowledge at many layers of abstraction to reduce the problem space and tackle hard problems

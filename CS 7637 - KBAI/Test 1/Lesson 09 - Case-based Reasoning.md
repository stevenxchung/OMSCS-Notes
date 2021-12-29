# Lesson 9

In this lesson we will cover topics on _case-based reasoning_ where cognitive agents address new problems by tweaking solutions to similar previously encountered problems. Case-based reasoning builds on top of learning by recording cases. We will also cover the following:

1. Recording cases revisited
2. Need for case-based reasoning
3. Phases of case-based reasoning
4. Advanced case-based reasoning

## Recording Cases To Case-based Reasoning

There are several of steps for case-based reasoning:

1. **Retrieval**: retrieving a case from memory similar to the current problem
2. **Adaptation**: adapting the solution to that case to fit the current problem
3. **Evaluation**: evaluating how well the adapted solution addresses the current problem
4. **Storage**: storing the new problem and solution as a case

## Assumptions Of Case-based Reasoning

There are several assumptions for case-based reasoning:

1. Patterns exist in the world
2. Similar problems have similar solutions

## Case Adaptation

There are several ways an agent could use case adaptation to solve a problem:

1. Case adaptation by model of the world: use a previous solution or model to adapt and solve a new problem
2. Case adaptation by recursive reasoning: break the new problem into sub-problems then use partial solutions from other problems to solve the new problem
3. Case adaptation by rules: use rules to adapt to a new problem

## Case Evaluation

There are multiple ways to evaluate possible solutions, one common way is to run a simulation or in terms of programming, run unit or end-to-end tests.

## Case Storage

Once solutions are evaluated for correctness, we could store solutions in multiple ways:

1. Case storage by index: storing a solution in such a way that it could be retrieved via index where the index could be some sort of property related to the solution
2. Case storage by discrimination tree: storing a solution in such a way that it could be retrieved via tree structure where each node could have multiple branches

## Advanced Case-Based Reasoning

Case-based reasoning does not always have to go from retrieval to storage, it could also do the following:

- Evaluation to adaptation: evaluation found, the solution failed; try adapting again
- Evaluation to retrieval: evaluation found, the solution failed; try retrieving a different solution
- Adaptation to retrieval: the retrieved solution could not be adapted; retrieve a different solution
- Retrieval to evaluation: retrieved case perfectly matches the current problem, no adaptation needed

When storing cases, we should only store noteworthy cases, including interesting failed cases. However, we should **not** simply store all successful or failed cases.

## Section Quizzes

### Case Storage By Index I Quiz

_What tags should be used for case Y (given)_?

1. 1E
2. 9N

### Case Storage By Index II Quiz

_What tags should be used for case Y (given)_?

1. 1E
2. 9N

### Storage By Discrimination Tree I Quiz

_What case (given) should be retrieved and adapted_?

Y should be the answer based on the tree.

### Storage By Discrimination Tree II Quiz

_Where should this branch (given) be divided for maximum differentiation_?

2E since it would allow for differentiation between A and Y.

### Retrieval By Index Quiz

_What case (given) should be retrieved and adapted_?

C since it yields the exact destination.

### Retrieval By Discrimination Tree Quiz

_What case (given) should be retrieved and adapted_?

Y should be the answer based on the tree.

### Final Quiz

_What did you learn in this lesson_?

- There is a spectrum of similarity when it comes to problems: on one end problems are identical to previous problems and on the other end problems are very dissimilar problems. The problems in the middle of the spectrum are similar but not identical to previous problems and these problems are most common in human cognition
- Case-based reasoning includes retrieving, adapting, evaluating, and storing noteworthy solutions
- Case-based reasoning is able to tie reasoning, learning, and memory with retrieval, adaptation, evaluation and storage

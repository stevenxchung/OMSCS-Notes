# Lesson 10

How can we abstract concepts out of case-based reasoning? We will examine this problem by covering:

1. Purpose of incremental concept learning
2. Variabilization
3. Specialization
4. Generalization
5. Heuristics for specialization and generalization

## Incremental Concept Learning

Incremental concept learning could be thought of as follows, given a new example:

1. Is this an example of the concept?
   1. If yes, does it fit the current definition of the concept?
      1. If yes, do nothing
      2. If no, generalize
   2. If no, does it fit the current definition of the concept?
      1. If yes, specialize
      2. If no, do nothing

## Variabilization

**Variabilization** refers to taking similar constants in some problem and abstracting them into a more general variable.

## Generalization To Ignore Features

To ignore redundant features, we can utilize the _drop-link_ heuristic whereby problems similar to a model have specific links dropped to match the model. This is useful if a problem is has a structure that is very similar to our model.

## Specialization To Require Features

To require features, we can utilize the _require-link_ heuristic whereby problems are required to have specific links to be considered a match.

## Specialization To Exclude Features

To exclude features, we can utilize the _fobid-link_ heuristic whereby problems should not possess links which are not permitted.

## Generalization To Abstract Features

To abstract features, we can utilize the _enlarge-set_ heuristic whereby problems could be considered a match if the problem possesses variables considered by our model.

## Generalization With Background Knowledge

To include background knowledge, we can utilize the _climb-tree_ heuristic whereby problems could be considered a match if the problem possesses variables considered by our model based on existing knowledge (in the form of a tree structure as shown in lecture).

## An Alternative Visualization

Over time an agent will be able to include all positive examples and exclude all negative examples. This occurs over many iterations where the agent's concept definition is repeatedly updated.

## Heuristics For Concept Learning

Models could also include the _close-interval_ heuristic to expand the range of values to be a positive example of the concept

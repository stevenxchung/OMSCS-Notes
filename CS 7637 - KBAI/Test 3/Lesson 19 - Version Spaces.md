# Lesson 19

In this lesson we will cover generalization and learning using _version spaces_. Generalization and learning are closely related to incremental concept learning (learning by one step at a time) which relied on background knowledge. Generalization and learning is useful in cases where background knowledge might not be available. We will also cover the following:

1. Version space definition
2. Abstract version spaces
3. Algorithm for version spaces
4. Identification trees

## Incremental Concept Learning Revisited

**Version spaces** are a technique for learning concepts incrementally. In incremental concept learning, concepts are introduced in an order such that concepts may be refined desirably. We also made use of background knowledge to help us further generalize or specialize our model of a concept (e.g., model of an arch).

However, there are many scenarios where a concept is not introduced in a useful order and background knowledge is not provided. In these scenarios, version spaces are useful in that it will allow an agent to converge to a refined concept.

## Abstract Version Spaces

Version spaces always have a general model and a specific model attached to the concept we are trying to learn:

- **Generalized model progression**: as more _negative_ examples are given, the descriptions of this model become more _specialized_
- **Specialized model progression**: as more _positive_ examples are given, the descriptions of this model become more _generalized_

We could observe then that generalized and specialized models must converge at some point where an ideal model exists.

## Version Spaces Algorithm

The algorithm for version spaces could be summarized as follows:

- For each example:
  - If the example is _positive_:
    - _Generalize_ all _specific_ models to include it
    - Prune away _general_ models that cannot include it
  - If the example is _negative_:
    - _Specialize_ all general models to include it
    - Prune away _specific_ models that cannot include it
  - Prune away any models _subsumed_ by other models

## Identification Trees

To build more efficient and optimal classification trees we could create a tree where attributes are _carefully_ selected such that examples could be separated out to their own branch. This technique to use classification trees to find examples is called _decision tree learning_. However, the tradeoff is that we need to know all the examples in order to create such a tree.

There are some differences between decision trees and discrimination trees (discussed in incremental learning):

- Decision trees are more optimal classification trees but we need all examples upfront
- Discrimination trees are sub-optimal trees but we can use them to learn incrementally

## Section Quizzes

### Version Spaces I Quiz

_What would the initial general and specific models be (based on given frame)_?

- General model has `any` for all
- Specific model includes everything in the given frame

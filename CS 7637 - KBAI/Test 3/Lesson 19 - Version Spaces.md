# Lesson 19

In this lesson we will cover generalization and learning using _version spaces_. Generalization and learning are closely related to incremental concept learning (learning by one step at a time) which relied on background knowledge. Generalization and learning is useful in cases where background knowledge might not be available. We will also cover the following:

1. Version space definition
2. Abstract version spaces
3. Algorithm for version spaces
4. Identification trees

## Incremental Concept Learning Revisited

**Version spaces** are a technique for learning concepts incrementally. In incremental concept learning, concepts are introduced in an order such that concepts may be refined desirably. We also made use of background knowledge to help us further generalize or specialize our model of a concept (e.g., model of an arch).

However, there are many scenarios where a concept is not introduced in a useful order and background knowledge is not provided. In these scenarios, version spaces are useful in that it will allow an agent to converge to a refined concept.

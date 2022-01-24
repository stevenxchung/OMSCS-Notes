# Lesson 11

In this lesson we will be going over **classification** which refers to mapping sets of percepts in the world into unique classes so that we can take actions in the world in an efficient manner. These classes could be learned through incremental concept learning. We will also cover the following:

1. Equivalence classes and hierarchies
2. Kinds of concepts
3. Bottom-up and top-down processes

## The Challenge Of Classification

Recall the cognitive architecture, given `2^n` percepts from the input to our agent there could be `2^m` possible actions for the output of our agent. Given many percepts and actions, the mapping between them could be very large. How can we select the right action if our agent has finite resources?

## Equivalence Classes

As discussed previously, how is it that many percepts can be mapped to the correct action given many actions? By equivalence classes, we can say that `2^n` percents can map `k` concepts to `2^m` actions. This means that we may have only a few classes that serve as a mapping between many percepts to possible actions.

## Concept Hierarchies

For each concept, there are also top-down hierarchies which could help an agent reason and classify objects in an organized manner using _establish and refine_ iterative processes.

## Types Of Concepts

We can think of concepts as a spectrum from formal to less formal:

1. **Axiomatic** - concept defined by a formal set of necessary and sufficient conditions (e.g., mathematical equations)
2. **Prototype** - base concepts defined by a typical example with variable properties (e.g., a chair)
3. **Exemplar** - concepts defined by implicit abstractions of instances, or exemplars, of the concept (e.g., beauty, freedom)

## Order Of Concepts

To add to the previous list, some expert claim that _qualia_ (concepts more abstract than exemplar) are difficult to define but are able to invoke memories e.g., tasting something bitter

## Bottom-up Search

**Bottom-up search** is a technique whereby agents determine an answer by searching lower-level details and then aggregating those results up the chain using _identify and abstract_ iterative processes.

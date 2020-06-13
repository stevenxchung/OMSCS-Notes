# Lesson 5

In this lesson, we will focus on analysis or the process of understanding the problem. In particular, this lesson will go over a specific form of analysis known as **OOA (Object-oriented Analysis)**.

## Object Oriented Analysis (OOA)

OOA is a requirements analysis technique which models real-world objects based on their descriptions. This will produce an object analysis model using UML class model diagrams.

## Object Oriented Analysis And Design

Structured analysis and design techniques are functionally oriented. Whereas OOA is primarily concerned with data objects.

## OOA

The goal of OOA is to use identified words to build up descriptions of classes and their relationships:

- Nouns to classes
- Action to operations
- Adjectives to attributes
- Stative verbs to relationships

## Steps In OOA

Below are steps in OOA:

1. Candidate object classes are indicated by the occurrence of nouns in the natural language description of the system to be built
2. The nouns can then be organized into related groups termed classes
3. The next step looks for adjectives, which often indicate properties that can be modeled as attributes
4. Subsequently, action verbs can be modeled as operations and assigned to an appropriate provider class
5. Other stative verbs are indicative of relationships among classes

## Technique

Below are some techniques for successful OOA:

1. Obtain or prepare textual description of problem
2. Underline all nouns
3. Organize the nouns into groups to become candidate classes
4. Underline all the adjectives
5. Assign the adjectives as attributes of the candidate classes
6. Underline the verbs, differentiating action from stative verbs
7. Assign action verbs as operations of classes
8. Assign stative verbs as attributes of classes or relationships

## Issues

Some issues with the previously mentioned OOA technique is that:

- Some words are duplicated
- Some words share the same stem

## Initial Class Model Diagram

The **initial class model diagram** includes groups which form candidate classes. A class is a description of a group of related objects (also called instances). Classes are represented by rectangles.

## Caveats

We should keep in mind the following caveats:

- Conclusions that are reached are **always** tentative
- Questions may arise requiring research or going back to customers
- The overall process is inherently incremental

## Adjective Issues

Some issues with the adjectives step in the previously mentioned OOA technique is that:

- Parts of the tree does not appear to have an adjective
- The use of the word long in _as long as_ is serving as an adverb, not an adjective
- The phrase _single leaf_ can be interpreted as _the count of leaves_ equals one

## Operations

**Operations** are the computational service provided by an object. They are suggested by looking for verbs. There are several kinds of verbs:

- Operations correspond to action verbs
- Linking verbs are related to attributes
- Stative verbs are indicative of a relationship among objects

## Operations Issues

Some issues with the operations step in the previously mentioned OOA technique is that:

- What do we do about the phrase _keep a pile_?
- What do we do about the phrase _have been counted_?
- What do we do about the phrases: _is set to, examine, and consists of_?

## Step 5: Relationships

**Relationships** are indicated by lines connecting classes adorned in one of three ways:

1. Generalizations: solid line with an empty arrowhead
2. Aggregations: solid line with an empty diamond-head
3. Associations: solid line

## Generalizations

**Generalizations** indicate that instances of one of the two classes (the child class) are a kind of instances of the other class (the parent class). Words like _is a_, _kind of_, and _type of_ indicate the generalization relationship. Class names themselves can serve as indicators.

## Aggregations

**Aggregations** are collections of some sort. An aggregation is text by words such as:

- _Consists of_
- _Part of_
- _Contains_
- _Has_
- _Incorporates_
- _Belongs to_

## Associations

**Associations** tend to be more general. Stative verbs denote a state of being and often indicate associations. Associations are indicated by lines connecting the associated classes with no special adornments.

## Relationship Issues

Some issues with the relationship step in the previously mentioned OOA technique is that:

- All of the classes are really a part of an overarching `TreeCountingSystem` class
- The textual description was not truly characteristic of typical requirements documents

## Summary

OOA is a valuable first take to take during a software development effort. It can help in understanding the problem to be solved and suggesting a breakdown of a solution system into its component parts.

## Section Quizzes

### Object Quiz

_Can you think why objects might be a better starting point for analysis than functions?_

During maintenance, functions change more frequently than objects.

### Step 1: Locate Nouns Quiz

_Locate the nouns:_

> Keep a pile of the parts of the tree that have not yet been counted. Initially, get a tree and put it on the empty pile; the count of the leaves is initially set to zero. As long as the pile is not empty, repeatedly take a tree off the pile and examine it. If the tree consists of a single leaf, then increment the leaf counter and throw away that tree. If the tree is not a single leaf but instead consists of two subtrees, split the tree into its left and right subtrees and put them back on the pile. Once the pile is empty, display the count of the leaves.

Pile, parts, tree, count, leaves, leaf, subtrees, and zero

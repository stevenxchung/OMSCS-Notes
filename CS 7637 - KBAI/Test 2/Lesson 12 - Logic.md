# Lesson 12

In this lesson we will cover _logic_ which is the basis for additional topics such as planning. We will also cover the following:

1. Formal notation
2. Conjunctions, disjunctions, negations, implications
3. Truth tables
4. Rules of inference
5. Resolution theorem proving

## Why Do We Need Formal Logic

We need formal logic for:

- **Soundness**: only valid conclusions can be proven
- **Completeness**: all valid conclusions can be proven

## Predicates

A **predicate** is a function that maps object arguments to true or false values.

## Conjunctions And Disjunctions

Conjunctions (_and_) are denoted by an up arrow head, disjunctions (_or_) are denoted by a down arrow head. A negation (_not_) will be denoted by the negation symbol as shown in lecture.

## Notation Equivalency

The following notations could be used for formal logic descriptions:

1. `AND`: e.g., `A & B` or `A && B`
2. `OR`: e.g., `A | B` or `A || B`
3. `NOT`: e.g., `!A` or `~A`
4. `IMPLIES`: e.g., `A = B`, `A == B`, `A => B`

## Rules Of Inference

**Rules of inference** suggests to instantiate general rules to prove specific claims. There are two techniques in particular:

1. **Modus Ponens**: `p => q`, `p`, therefore `q`
2. **Modus Tollens**: `p => q` `!q`, therefore `!p`

## Universal Quantifiers

_For all_ qualifiers are also known as **universal qualifiers**. _For at least one_ qualifiers are also known as **existential qualifiers**.

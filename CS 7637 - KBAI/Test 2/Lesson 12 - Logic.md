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

## Section Quizzes

### Inferences About Foos Quiz

_Mark the sufficient conditions that would make this (provided) a foo_.

- A brick supports two blocks
- Those two blocks do not touch
- Those two blocks support a brick

### Practicing Formal Logic Quiz

1. _If an animal lays eggs and does not have feathers, it is a reptile_.
   - `lays-eggs(animal) ∧ ¬feathers(animal) ⇒ reptile(animal)`
2. _If an animal has feathers or has talons, it is a bird_.
   - `feathers(animal) ∨ talons(animal) ⇒ bird(animal)`
3. _If an animal lays eggs, has a beak, and flies, it is a duck_.
   - `lays-eggs(animal) ∧ beak(animal) ∧ flies(animal) ⇒ duck(animal)`
4. _If an animal lays eggs, has a beak, and do not fly, it is a platypus_.
   - `lays-eggs(animal) ∧ beak(animal) ∧ ¬flies(animal) ⇒ platypus(animal)`

### Truth Tables I Quiz

_Given the logic table, please enter either True or False below_:

1. True
2. True
3. False
4. True
5. False
6. False
7. False
8. True

### Truth Tables II Quiz

_Given the logic table, please enter either True or False below_:

1. True
2. True
3. True
4. True
5. False
6. True
7. False
8. False

### Commutative Property Quiz

_Given the logic table, please enter either True or False below_:

1. True
2. True
3. False
4. False
5. False
6. False
7. False
8. False

### Distributive Property Quiz

_Given the logic table, please enter either True or False below_:

1. True
2. True
3. True
4. True
5. True
6. True
7. False
8. False
9. False
10. False
11. False
12. False
13. False
14. False
15. False
16. False

### Associative Property Quiz

_Given the logic table, please enter either True or False below_:

1. True
2. True
3. True
4. True
5. True
6. True
7. True
8. True
9. True
10. True
11. True
12. True
13. True
14. True
15. False
16. False

### De Morgans Law Quiz

_Please fill in the blanks below with True or False below_:

1. False
2. False
3. True
4. True
5. True
6. True
7. True
8. True

### Proof I Quiz

_Write (provided) in formal logic, how do we prove this is a bird_?

`has-wings ∧ ¬has-fur ⇒ bird`

### Proof II Quiz

_Use implication elimination to rewrite as a conditional, how do we prove this is a bird_?

`¬has-wings ∧ ¬has-fur ⋁ bird`

### Proof III Quiz

_Use De Morgan's Law to rewrite in conjunctive normal form, how do we prove this is a bird_?

`¬has-wings ⋁ has-fur ⋁ bird`

### Proof IV Quiz

_What sentence would be assumed to facilitate the proof, how do we prove this is a bird_?

`¬bird`

### Proof V Quiz

_What part of `S1` (provided) would we eliminate first, how do we prove this is a bird_?

We have to eliminate the `bird` first.

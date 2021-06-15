# Lesson 15

In this lesson we will cover software refactoring in agile development which focuses on code understandability, maintainability, and design. We will also discuss concepts such as fully automated refactoring and _bad smells_ which will allow us to determine when we should perform refactoring.

## Software Refactoring Introduction

What is refactoring? **Refactoring** is an activity in software where the goal is to keep the program readable, understandable, and maintainable.

A key factor is that refactoring should be _behavior preserving_; any refactoring done to a particular piece of software will **not** change functionality. This could be checked but **not** guaranteed by testing.

## Reasons To Refactor

Why should we refactor? We should refactor because of the following:

1. Requirements change
2. Design needs to be improved
3. Sloppiness/laziness creeping into software

## History Of Refactoring

Refactoring is something programmers have always done. Refactoring is especially important for OO languages and is an increasingly popular and important part of agile software development.

## Types Of Refactoring

There are many types of refactoring but for this class we will cover the following:

- **Collapse hierarchy**: useful when a superclass and a subclass are too similar
- **Consolidate conditionals**: useful when a set of conditionals has the same result
- **Decompose conditionals**: useful when a conditional statement is particularly complex
- **Extract method**: useful when a cohesive code fragment exists in a large method
- **Extract class**: useful when a class is doing the work of two classes
- **Inline class**: useful when a class is not doing much

## Refactoring Risks

Refactoring is a powerful tool but there are several drawbacks:

- May introduce subtle faults
- Should not be abused
- Should be used carefully on systems in production

## Cost Of Refactoring

The cost of refactoring depends on a several factors:

- Manual work
- Test development and maintenance
- Documentation maintenance

## When Not To Refactor

We should not refactor when:

- Code is broken
- A deadline is close
- There is no reason to

## Bad Smells

**Bad smells** are symptoms in the code which may indicate deeper problems. There are many types of bad smells. Below are some of the common bad smells and the solution that may be applied to resolve them:

- Duplicated code -> solved by extract method
- Long method -> extract method, decomposed conditional, etc.
- Large class -> extract class (or subclass)
- Shotgun surgery -> move method/field, inline class, etc.
- Feature envy -> extract method, move method

## Section Quizzes

### Introduction Quiz

_Why can't testing guarantee that a refactoring is behavior preserving_?

Because testing is inherently incomplete.

### Extract Method Refactoring Quiz

_When is is appropriate to apply refactoring "extract method"_?

- When there is duplicated code in two or more methods
- When a method is highly coupled with a class other than the one where it is defined

### Bad Smell Quiz

_Which of the following can be considered to be "bad smells" in the context of refactoring_?

- Method `m()` in class `C` is very long
- Every time we modify method `m1()`, we also need to modify method `m2()`

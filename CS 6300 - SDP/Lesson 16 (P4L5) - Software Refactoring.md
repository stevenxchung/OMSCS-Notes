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

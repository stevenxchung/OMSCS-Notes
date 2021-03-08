# Lesson 10

It can be difficult to decide on a design that will best fit our software system. Therefore, in this lesson we will look into _design patterns_ which can help to provide reusability to our software system.

## History Of Design Patterns

The history of design patterns could be summarized as:

- 1977: Christopher Alexander introduces the idea of patterns as successful solutions to problems
- 1987: Ward Cunningham and Ken Beck leverage Alexander's idea in the context of an OO language
- 1987: Eric Gamm's dissertation on importance of patterns and how to capture them
- 1992: Jim Coplien's book, _Advanced C++ Programming Styles and Idioms_
- 1994: Gang of Four (Erich Gamma, Richard Helm, Ralph Johnson, and John Vlissides) and their book, _Design Patterns: Elements of Reusable Object-Oriented Software_

## Patterns Catalogue

There are five main categories of design patterns we may be concerned with:

1. **Fundamental**
2. **Creational**
3. **Structural**
4. **Behavioral**
5. **Concurrency**

We will cover some patterns from each category. For more information on patterns in each category see the [Wiki page on software design patterns](https://en.wikipedia.org/wiki/Software_design_pattern).

## Pattern Format

The format of a design pattern is as follows:

- Name
- Intent
- Applicability
- Structure
- Sample code

There are more formats which include fields such as motivation, consequences, implementation, and related patterns. However, for the purpose of this class we will mainly focus on the five attributes above for each design pattern.

## Factory Method Pattern

Below are properties of the factory method pattern:

- **Name**: factory method pattern
- **Intent**: allows for creating objects without specifying their class by invoking a factory method (i.e., a method whose main goal is to create class instances)
- **Applicability**:
  - Class can't anticipate the type of objects it must create
  - Class wants its subclasses to specify the type of objects it creates
  - Class needs control over the creation of its objects
- **Structure**: an example of factory method may include:
  - **Creator**: provides interface for factory method
  - **ConcreteCreator**: provides method for creating actual object
  - **Product**: object created by the factory method

See lecture for sample code example.

## Strategy Pattern

Below are properties of the strategy pattern:

- **Name**: strategy patter
- **Intent**: allows for switching between different algorithms for accomplishing a task
- **Applicability**:
  - Different variants of an algorithm
  - Many related classes differ only in their behavior
- **Structure**: an example of strategy pattern may include:
  - **Context**: interface to outside world
  - **Algorithm (strategy)**: common interface for the different algorithms
  - **Concrete strategy**: actual implementation of the algorithm

See lecture for sample code example.

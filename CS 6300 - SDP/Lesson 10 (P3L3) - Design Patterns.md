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

## Other Common Patterns

Other patterns include:

- **Visitor**: a way of separating an algorithm from an object structure on which it operates
- **Decorator**: a wrapper that adds functionality to a class (stackable)
- **Iterator**: access elements of a collection without knowing underlying representation
- **Observer**: notify dependents when object changes
- **Proxy**: surrogate controls access to an object

## Choosing A Pattern

There are several guidelines to choosing a design pattern:

1. Understand your design context
2. Examine the patterns catalog
3. Identify and study related patterns
4. Apply suitable pattern

However, there are pitfalls when selecting design patterns which may include (but are not limited to):

- Selecting wrong patterns
- Abusing patterns

We should always be careful to not rely too heavily on design patterns and ensure that whichever design pattern we select fits our problem.

## Negative Design Patterns

In addition to design patterns, there are also negative design patterns, i.e., how not to design manage, etc. These are also called _anti-patterns_ and _bad smells_ as discussed in Christoper Alexander's book: [A Pattern Language](https://en.wikipedia.org/wiki/A_Pattern_Language)

## Section Quizzes

### Choosing A Pattern Quiz

_Answer following questions:_

1. _Imagine that you have to write a class that can have one instance only. Which of the design pattern that we've discussed is most appropriate?_ Factory
2. _Imagine that you have to write a class that can have one instance only. Using one of the design patterns that we discussed in this lesson, write the code of a class with only one method (except for possible constructors) that satisfy this requirement._ The code should be as follows:

```java
public class Singleton {
    private static Singleton instance;
    private Singleton() {}

    public static Singleton factory() {
        if (instance == null) {
           instance = new Singleton();
        }
        return instance;
    }
}
```

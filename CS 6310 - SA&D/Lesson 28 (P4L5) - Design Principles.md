# Lesson 28

Recall that design cannot be taught, rather it has to be learned through experience. So far we have gone through several ways to learn from the experience of others. In this lesson we will examine design principles.

## Design Quality

**Design quality** is one of the several ways of gauging the quality of designs. The ultimate validation of design is to build the program and have its users report their satisfaction. We could build a prototype or conduct design reviews (least expensive but oftentimes most valuable).

## Design Guidelines

**Design guidelines**, also called a design principle or design heuristics, is an informal piece of advice about the structure of a design.

## Coupling

Recall that coupling is the extent to which a module is dependent on other modules. Coupling of modules should be low in order to make it easier to maintain them.

## Cohesion

Recall that cohesion is the extent to which a module has a single purpose. Cohesion should be high in order to enhance understandability and promote reuse.

## Orthogonality

**Orthogonality** is the extent to which the features of a system can be varied independently. We could enhance the orthogonality of our system in order to make more options available to its users. Orthogonality also clarifies system descriptions and support automatic generation.

## Information Hiding Principle

**Information hiding** is also known as encapsulation. It is the extent to which the implementation details of a system are encapsulated behind abstract interfaces. Use of inheritance can violate information hiding.

## Design Principles Catalog

Below we will describe a principle based on name, author, definition, and implications of use. We should note that these are only guidelines and not hard-and-fast rules.

1. **Liskov substitution principle**
   - Subclass instances should satisfy parent-class constraints
   - Implication: implies that child class instances should obey parent class invariants and method contracts
2. **Law of Demeter**
   - Suggests limits on the classes that can be referred to by a given method
   - Limits the objects that can be referred to
   - Implication: reduces coupling but sometimes requires extra wrapper classes
3. **Hollywood principle**
   - Frameworks consist of a set of abstract classes together with rules for the ways that their concrete subclasses may interact
   - Implication: suggests that calls should be made from the framework to client classes (inversion control)
4. **Dependency inversion principle**
   - High level modules should not depend upon low level modules; instead both should depend upon abstractions (related to inversion of control)
   - Opposite to the way that modules are structured in traditional layered architectures
   - Layering should be one of abstraction, rather than one of control or data access
   - Implication: controlling principles are enforced at the highest levels in our architecture
5. **Open-closed principle**
   - A class should be open for extension but closed for modification
   - Implication: after releasing a class, any enhancement to it should be made only in subclasses; this helps deal with fragile base class problem
6. **Interface segregation principle**
   - Suggests that clients depend on an interface to a part of the large class's features
   - Note the relation of the principle to role-based design
   - Implication: class interfaces should be broken into small pieces corresponding to single use case
7. **Reuse equivalency principles**
   - The granule of reuse should be the granule of release
   - Implication: release highly cohesive code units
8. **Common closure principle**
   - Regardless of the level of granularity, we are forced to use, group the related elements into a common release unit
   - Implication: classes that change together, should be released together

## Dependency Structure Matrix

The next set of principles utilize a **DSM (dependency structure matrix)**. This is a device devised by Baldwin and Clark to deal with the management of design changes. Boolean matrix in which rows and columns correspond to components. Order of rows and columns do not matter to the information conveyed.

1. **Acyclic dependency principle**
   - Dependencies between packages must not form cycles (should be able to permute the rows and columns of the DSM)
   - Component only depends on other components beneath it
   - Implication: violation of this property would lead to a system that is difficult to maintain and understand
2. **Stable abstraction principle**
   - A module is hard to change if a lot of other modules depend on it
   - Implication: we should depend in the direction of stability; in other words, no package should be dependent on packages that are more likely to change than itself
3. **Bad smells principle**
   - Move some design activities into the actual implementation phase of development
   - Implication: reduce rework in situations with rapidly changing requirements
4. **Design heuristics principle**
   - Do not change the state of an object without going through its public interface
   - A method in a class cannot change an instance variable without calling the setter
   - Users of a class must be dependent on its public interface, but a class should not be dependent on its users
   - Implications:
     - Distribute system intelligence horizontally as uniformly as possible
     - Distribute system intelligence vertically down narrow and in deep containment hierarchies
5. **Single choice principle**
   - In procedural code, systematic variation is often dealt with via case statements or else-if cascades
   - In object-oriented code, this approach is considered a _bad smell_
   - Implication: use parallel, factored subclasses with the choice-specific code embodied in a subclass method

## Transparency And Intentionality

There are two other principles we should examine along with the previous principles:

1. **Transparency principle**
   - Suggests providing interfaces that enable clients to be written without having to be concerned with extraneous details
   - Implication: generality comes with the cost of extra design and testing work
2. **Intentionality principle**
   - Design software in such a way that intent is manifest and localized in the code (supports traceability, validation, and maintainability)
   - Implication: improve intentionality by appropriate use of cohesion and naming conventions

## Summary

A catalog of design principles may be too abstract to be immediately useful. However, by being made aware of these principles we will be sensitized to problematic situations when they arise.

## Section Quizzes

### Foundational Concepts Quiz

_Match the described design principal (provided in lecture) with the situation_.

- Coupling: requires more code reading
- Cohesion: improves reusability
- Orthogonality: enables maximum variability
- Information hiding: raises the level of abstraction

### Design Principles Quiz

_Assume the robot class is very complex, and now we have to change it to include a new Fancy motor. Making this change will be difficult with the current design (provided in lecture) because it violates which design principle_?

Dependency inversion principle since high level modules should not depend upon low level modules.

### Principles And Heuristics Quiz

_James Gosling was the author of the Java programming language. At a Java users' group meeting, he was asked, "If you could do Java over again, what would you change?" He replied, "I'd leave out classes." Which of the principles or heuristics (provided in lecture) that have been mentioned in this lesson supports this idea_?

Liskov substitution, interface segregation, stable abstraction, and Riel's design heuristics principle. These principles suggest that inheritance should be used only to model a generalization hierarchy.

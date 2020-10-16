# Lesson 27

The most important predictor of a successful product design effort is the extent to which a team possesses experience on related problems. An indicator of design experience is **design pattern** knowledge. Design patterns are a description of a solution to a problem in a context. In this lesson, we will examine design patterns more thoroughly.

## Architectural Patterns

The concept of patterns derives from building architecture. The _Gang of Four_ (Gamma, Helm, Johnson, and Vlissides, also known as _GOF_) published a classical book on design patterns and since then many other outlets have followed along.

## Definition

From GOF, a design pattern is:

> A description of communicating objects and classes that are customized to solve a general design problem in a particular context.

## Patterns

There are various design patterns in software design, the foundation is the **composite pattern**:

- Very common, tries to answer how to organize information about whole-part relationships
- Class model diagram is the essence of this pattern

Other patterns in GOF are divided into three categories:

1. **Structural**
   - **Composite**: complex data structure whose parts have many different types
   - **Adapter**: covert interface to improve interoperability
   - **Bridge**: decouple abstraction and implementation; abstract class contains member that is its implementation (may be used in language that does not have interfaces)
   - **Decorator**: attach additional responsibility to an object dynamically
   - **Facade**: higher-level interface for a subsystem; support for non-OO legacy applications
   - **Flyweight**: use sharing to support large number of fine-grained objects
   - **Proxy**: control access to an object
2. **Creational**
   - E.g., Singleton, Prototype, Builder, Factory Method, and Abstract Factory
3. **Behavioral**
   - Are the most complex and powerful patterns; they describe interesting ways that objects can interact
   - There are many behavioral patterns, GOF describes 11:
     - **Chain of responsibility**: separate request from handler; allow multiple handlers
     - **Command**: turn a request into an object; logging; undo
     - **Interpreter**: represent a grammar and interpret its instances
     - **Iterator/enumeration**: access elements of a collection without exposing the underlying representation
     - **Mediator**: encapsulate object interactions
     - **Momento**: capture object's internal state for later restore
     - **Observer/listener**: notify dependents when an object changes
     - **State**: class with attribute of type `State` whose instance tracks current state; effectively allows an object;s class to change at run-time
     - **Strategy**: family of algorithms with the same purpose and interface; instance is a specific algorithm
     - **Template method**: skeleton for algorithm with hooks for specific steps
     - **Visitor**: apply a method to elements of a structure; a popular way to navigate a complex data structure applying item-specific operations and is complementary to the composite pattern

## Intent And Motivation

According to GOF, for each pattern there should be:

- **Intent**: a summary of the value provided by the pattern
- **Motivation**: a scenario demonstrating that having a solution would be valuable

## Applicability And Structure

Patterns should also take into account:

- **Applicability**: important design considerations that the pattern addresses
- **Structure**: the UML class model diagram depicting the pattern

## Participants

**Participants** include a description of each class in the diagram:

- Component (graphic)
- Leaf (rectangle, line, text, etc.)
- Composite (picture)
- Client (drawing program)

## Collaborations

**Collaborations** detail how the participants work together to accomplish the patterns goals. Composite is an example of a structural pattern. Collaborations play a less important role than structure in providing information to the designer.

## Consequences

**Consequences** highlight the advantages and disadvantages of using a pattern. It is important to understand what tradeoffs when using a particular pattern.

## Implementation Alternatives

For each patterns we should also consider alternatives based on factors such as _consequences_ as discussed earlier.

## Problems With Patterns

There are a couple of problems with patterns however:

- Patterns are primarily implemented using two standard composition mechanisms: inheritance and object composition
- Using patterns can add complexity, e.g., introduction of extra objects, extra level of indirection, etc.

## Problem Areas

There are several problem areas regarding patterns:

1. **Object schizophrenia**
   - Splitting off part of functionality into other objects in order to support variation
   - Broken delegation (the self problem)
   - Additional complexity
2. **Preplanning**
   - Oftentimes a pattern is only useful if you know enough in advance to include them in your plans
   - Solutions to this may include:
     - Refactoring
     - Work on reverse engineering patterns
3. **Traceability**
   - Code of the program does not necessarily make explicit that it is part of the pattern; this can lead to increased fragmentation of code

## Summary

Patterns are an essential part of all developers' vocabularies. It is difficult to passively learn design patterns. Although there are some costs and potential problems might arise, they are so powerful that we should take advantage of them when possible.

## Section Quizzes

### Patterns And UML Quiz

_UML class model diagrams distinguish associations in which deleting a collection deletes its elements from those that don't. What is the visual indication of the former?_

A filled diamond on the collection end of the line.

### Composite Pattern Quiz

_Imagine that you were writing an application to manage parts inventories. Match the class names from the Composite pattern given to the application data in the list._

- Client: `OutOfStockDetector`
- Component: `InventoryItem`
- Leaf: `StainlessSteelHexBolt(3/8")`
- Composite: `BlueBirdBoxKit`

### Singleton Quiz

_Say you wrote a battery of unit tests for an application that you intend to run frequently during development. Assuming you use a single process for testing, what difficulty does a Singleton impose on this approach?_

Support of independent tests as there is only one instance of the class.

### Pattern Quiz 1

_Which design pattern does the following object model (provided in lecture) represent?_

Adapter since it is responsible for altering the interface that an object provides to conform to the needs of its clients. Often, these clients comprise of legacy code that cannot be readily altered.

### Pattern Quiz 2

_Which design pattern does the following object model (provided in lecture) represent?_

Builder since it isolates the steps involved in constructing a complex object from the representation of that object.

### Pattern Quiz 3

_Which design pattern does the following object model (provided in lecture) represent?_

Iterator because it is responsible for traversing a collection, applying some action to each element. This enables clients to visit each element without necessarily knowing how the collection is implemented.

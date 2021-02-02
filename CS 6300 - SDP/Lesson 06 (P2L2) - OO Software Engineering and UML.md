# Lesson 6

Previously we covered requirements engineering. In this lesson we will look into OOD (object oriented design) and UML (Unified Modeling Language) which we will use in the rest of the course.

## Object Orientation Introduction

What is **OO (object orientation)**? Object orientation focuses several key concepts:

1. Data over function
2. Information hiding
3. Encapsulation
4. Inheritance

## Objects And Classes

An **object** is a computing unit organized around a collection of state or instance variables that define the state of the object. Each object has operators which are methods that allow reading and writing instance variables.

On the other hand, a **class** is a template or blueprint from which new objects (instances) can be created.

## Benefits Of OO

Why should we use OO?

1. Reduce maintenance costs
2. Improve development process
3. Enforce good design

## OO Analysis History

At the time OMT (Object Modeling Techniques) were being developed (led by Rumbaugh), scientists (Jacobson and Booch) also began to think about another technique (UML). OMT comprises of data, functions, and control.

## OO Analysis Overview

In OO analysis, we are concerned about defining the data objects first then the functions between each object second. We also look to transfer real world objects into requirements.

## UML Structural Diagrams: Class Diagrams

We will discuss several UML diagrams in this lesson. The class diagram will be one of them. The class diagram is a static, structured view of the system which describes: classes and their relationships.

**Classes** include:

- Class name
- Attributes and their types
- Operations and their types

**Attributes** represent the structure of a class and may be found by:

- Examining class definitions
- Studying requirements
- Applying domain knowledge

**Operations** represent the behavior of a class and may be found by examining interactions among entities.

**Relationships** describe interactions between objects. There are several types of relationships:

- Dependencies (e.g., x uses y)
- Associations/aggregations (e.g., x has a y)
- Generalization (e.g., x is a y)

## Class Diagram: Creation Tips

Below are several recommendations when working with class diagrams:

1. Understand the problem
2. Choose good names
3. Concentrate of the _what_
4. Start with a simple diagram
5. Refine until you feel it is complete

## UML Structural Diagrams: Component Diagram

The component diagram is a static view of components and their relationships. Unlike class diagrams, component diagrams have:

- _Nodes_ to represent components (set of classes with a well-defined interface)
- _Edges_ to represent a relationship

Component diagrams can be used to represent an architecture.

## UML Structural Diagrams: Deployment

The deployment diagram is a static deployment view of system. Physical allocation of components to computational units.

- _Nodes_ are computational units
- _Edges_ represent communication

## UML Behavioral Diagrams: Use Case

Use case diagrams describe the outside view of the system as well as:

- Sequence of interactions of outside entities (actors) with the system
- System actions that yield an observable result of value to the actors

Use cases have three parts:

1. Use case
2. Actor (human or a device)
3. Relationship

## Building A Use Case Diagram

The behavior of a use case can be specified by describing its flow of events:

- How the use case starts and ends
- Normal flow of events
- Alternative flow of events
- Exceptional flow of events

## Role Of Use Cases

There are several of reasons why use cases are important:

1. Requirements elicitation
2. Architectural analysis
3. User prioritization
4. Planning
5. Testing

## Use Case Diagram: Creation Tips

Below are several recommendations when working with use case diagrams:

1. Use name that communicates purpose
2. Define one atomic behavior per use case
3. Define flow of events clearly
4. Provide only essential details
5. Factor common behaviors
6. Factor variants

## UML Behavioral Diagrams: Sequence

Sequence diagrams emphasizes the time ordering of messages.

## UML Behavioral Diagrams: State Transition Diagram

State transition diagrams specify the events that cause an object to move from one state to another and effects. These diagrams are composed of the following for each class:

- Possible states of the class
- Events that cause a transition from one state to another
- Actions that result from a state change

## Section Quizzes

### OO Benefits Quiz

_Acme Corporation decided to use an OO approach in its software development process. What benefits can they expect to receive from this decision?_

- Increased reuse because of the modular coding style
- Increased maintainability because the system design can accommodate changes more easily
- Increased understandability because the design models real-world entities

### Modeling Classes Quiz

_Consider the following requirement for an online shopping website: "Users can add more than one item on sale at a time to a shopping cart." Which of the following elements should be modeled as classes?_

- Item
- Shopping cart
- User

### Class Diagram Relationships Quiz

_Which of the following relationships is an actual relationship for the system we are modeling?_

- `RegistrationManager` uses `SchedulingAlgorithm` (dependency)
- `RegistrationManager` uses `Student` (dependency)
- `Student` registers for `CourseOffering` (association)
- `Course` consists of `CourseOffering` (aggregation)
- `Student` is a `RegistrationUser` (generalization)
- `Professor` is a `RegistrationUser` (generalization)

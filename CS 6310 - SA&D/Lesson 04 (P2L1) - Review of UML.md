# Lesson 4

In this lesson we will cover the different types of diagrams used in software architecture and design.

## OMT

**OMT (Object Management Technique)** was developed by James Rumbaugh and others at GE. OMT included:

- Class model diagram - structural aspects of software
- State chart diagram - behavior aspects of software
- Dataflow diagram - functional aspects of software

## UML

**UML (Unified Modeling Language)** was standardized by OMG (Object Management Group) and championed by companies like IBM. UML is used for analysis or design models.

## Diagram Types

There are 14 different types of diagrams. However, in this class we will only be using a few of those diagrams. There are two main categories of diagrams:

1. Structural: give you the pieces of the system and the relationships
2. Behavioral: concerned with the executions of the system

## Class Models

**Class model diagrams** are the most popular diagrams (also called static models) and have structural properties, classes, and relationships.

## UML Relationships

There are several types of relationships:

- **Dependency**: X uses Y (dashed directed line)
- **Associations**: X affects Y (solid undirected line)
- **Generalization**: X is a kind of Y (solid directed line with open arrowhead)

## Object Diagram

**Object diagrams** convey objects and links instead of classes and relationships.

## Composite Structure Diagram

**Composite structure diagrams** convey the internal structure of a class.

## Component Diagram

**Component diagrams** convey a static implementation view and is a physical, replaceable part of a system that packages implementation and conforms to and provides the realization of a set of interfaces.

They are usually used to:

- Model code entities
- Convey architecture

## Deployment Diagram

**Deployment diagrams** convey configuration of run-time processing nodes and the component instances and objects that live on them.

For these diagrams:

- Nodes denote a computational device
- Arcs indicate communications

## Packages

Packages are general purpose organizing mechanisms. They also provide namespace scoping. The system is the top-level package and the dependency arrows between packages indicate the existence of dependencies between constituents.

## Profile Diagram

**Profile diagrams** convey higher level; properties of diagrams not models. Profiles allow you to extends the basic UML notation.

## Behavior Diagrams

**Behavior diagrams** are focused on specific uses. You may have to have multiple diagrams to convey the overall system behavior.

## Use Case Diagram

**Use case diagrams** include a sequence of user-visible actions along with system responses. This type of diagram is useful for:

- Eliciting system requirements and organizing development activities
- Depicting relationships among system actors and use cases

## Use Case Diagrams

For use case diagrams:

- Stick figures denote external actors
- Ovals are use cases
- Lines without annotations indicate participation
- `<<extends>>` and `<<uses>>` stereotype support factoring

## Individual Use Cases

Use case diagrams convey a system of system uses and the actors that are involved with them. Use cases themselves may be conveyed with unstructured text or in a table.

## Context Diagrams

**Context diagrams** are **not** part of UML but provide interesting capabilities:

- Dataflow diagrams provide a different view
- DFDs (data flow diagrams) depict processes, actors, and the data-flows among them

## Sequence Diagram

**Sequence diagrams** convey a single use case.

## Communication Diagram

**Communication diagrams** are object diagrams annotated with ordered interactions instead of links. These diagrams are semantically equivalent to sequence diagrams.

## Activity Diagram

**Activity diagrams** are a variant of a state machine in which states may be simultaneously active. For these diagrams:

- Transitions are typically triggered by activity completion
- Modeling can be done on workflows, process synchronization, and concurrency

## Interaction Overview Diagram

**Interaction overview diagrams** are a kind of activity diagram where the nodes in the diagram correspond to lower level interaction.

## Timing Diagram

**Timing diagrams** convey specific timing of situations in a system.

## State Diagrams

**State diagrams** are the most powerful and most complex type of UML behavior diagram. They are also called state charts and extend finite state machines.

## Object Constraint Language

**OCL (Object Constraint Language)** provides textual extension to UML's visual notation. Some features include:

- Applicable to class and state chart diagrams
- First-order predicate logic + diagram navigation + collection classes
- Enables more precise specifications

## UML MetaModel

The **UML Meta-model** is the definition of UML in UML and can be extended by a modeler using profiles.

## Summary

You cannot design a complex system without having some idea of what it is suppose to do and what problem it is trying to solve. Diagrams are used to help express that understanding and the solution to the problem.

## Section Quizzes

### Diagram Quiz

_We want to convince a development shop of the benefits of design diagrams by indicating some pros and cons of using them. Mark the following with pro (P) or con (C):_

- Communication: P
- Maintainability: C
- Support for existing methods: P
- Tool support: P

### UML Structure Diagram Quiz

_Match up each of the UML Structure Diagram types with their descriptions:_

- Class: components and structural properties
- Composite structure: internal structure and possible interactions
- Component: organization of physical software components
- Deployment: physical system resources and how they map to hardware
- Object: static structure at a particular time
- Package: logical groupings and dependencies
- Profile: Extensions to the UML meta model

### UML Quiz

_Which of the UML Structure Diagram types could be used to convey system architecture?_

- Class diagram
- Component diagram
- Deployment diagram
- Package diagram

### Behavior Diagram Quiz

_Match the following behavior diagrams with their descriptions:_

- Activity: flow of control from activity to activity
- Sequence: interaction of classes of message exchange
- Communication: object interaction of numbered messages
- Interaction overview: synthesis of lower-level activity diagrams
- Timing: rotated sequence diagram
- Use case: system functionality provided to external actors
- State: dynamic behavior in response to stimuli

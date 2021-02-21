# Lesson 8

In this lesson we will cover the Unified Software Process starting with _software architecture_ where the goal is to lay the foundation on which to build successful and long lasting software systems.

## Interview With Nenad Medvidovic

Why is software architecture important? Architectural design decisions are really the principal design decisions in a software system because it could have long-term implications if not made correctly. Architectural erosion happens when software grows over time while the architecture of a software system is ignored or poorly designed to begin with.

## What Is Software Architecture

What is **SWA (software architecture)**? Depends on the source but generally software architecture could be thought of as:

- Perry and Wolf: Composed of elements (the what), form (the how), and rationale (the why)
- Shaw and Garland:
  - A level of design that involves description of elements from which systems are built
  - Interactions among those elements
  - Patterns that guide their composition
  - Constraints on these patterns

## General Definition Of SWA

A general definition of SWA: a set of principal design decisions about the system. The blueprint of a software system includes:

- Structural properties
- Behavioral properties
- Non-functional properties
- Interactions

There is also a temporal aspect of SWA since it should change over the lifetime of a software system.

## Prescriptive Vs Descriptive Architecture

A **prescriptive architecture** captures the design decisions made prior to the system's construction (as-conceived SWA). A **descriptive architecture** describes how the system has actually been built (as-implemented SWA).

## Architectural Evolution

When a system evolves, ideally its prescriptive architecture should be modified first. However, in practice this almost never happens.

## Architectural Degradation

Over time, two types of architectural degradation occurs for software systems with poor SWA:

1. **Architectural drift**: introduction of architectural design decisions orthogonal to a system's prescriptive architecture
2. **Architectural erosion**: introduction of architecture design decisions that violate a system's prescriptive architecture.

## Architectural Recovery

What happens when an architecture drifts or erodes? We have to take a path leading to **architectural recovery** which typically means to determine SWA from implementation and fix it. Developers should not simply _tweak_ code to recover their SWA.

## Architectural Elements

A SWA typically is not a monolith composition and interplay of different elements. SWA includes:

1. Processing elements
2. Data elements
3. Interaction elements
4. Components
5. Connectors
6. Configuration composed of components and connectors

## Components - Connectors - And Configurations

Regarding architectural components, connectors, and configurations:

A **component** is an architectural entity that:

1. Encapsulates a subset of the system's functionality and/or data
2. Restricts access to that subset via an explicitly defined interface

A **connector** is an architectural entity affecting and regulating interaction. Finally, a **configuration** is an association between components and connectors of a SWA.

## Architectural Styles

An **architectural style** is a named collection of architectural design decisions applicable in a given context. Alternatively from Shaw and Garland, an architectural style:

> ...defines a family of systems in terms of a pattern of structural organization, a vocabulary of components and connectors, with constraints on how the can be combined.

## Types Of Architectural Styles

There are many types of architectural styles in SWA:

1. Pipes and filters
2. Event-driven
3. Publish-subscribe
4. Client-server
5. P2P (Peer-to-peer)
6. REST (Representational State Transfer)

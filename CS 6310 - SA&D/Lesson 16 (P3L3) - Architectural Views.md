# Lesson 16

An software architecture is not a diagram, instead we can think of software architecture as a set of decisions. We will start by examining Kruchten's 4+1 Views on architecture.

## Logical View

The first of Kruchten's views is the **logical view** which is the structural breakdown of computational, communicational, and behavioral responsibilities. Diagrams that support this view include:

- Box and arrow
- UML class model diagram
- UML interaction overview diagram
- UML collaboration diagram
- Components and connectors

## Developmental View

The second view is the **developmental view** which includes units of source code such as packages, classes, subsystems, libraries, and files. Diagrams that support this view include:

- UML package diagram
- UML component diagram
- CVS modules

## Process View

The third view is the **process view** which depicts processes and threads into which execution is divided. Diagrams that support this view include:

- UML deployment diagram

## Physical View

The fourth view is the **physical view** which depicts machines used for system execution and how processes are allocated to them. Diagrams that support this view include:

- UML deployment diagram
- UML sequence diagram

## Use Case View

The last of Kruchten's views is the _+1_ view. The **use case view** includes important execution sequences from the external actors' points of view. Diagrams that support this view include:

- UML use case diagram
- UML communication diagram
- UML sequence diagram
- UML activity diagram
- Context diagram
- Individual use case (text or table)

## Context View

The **context view** emphasizes the relationship of a system to its environment. It includes high-level dataflow diagram where details can be described with lower-level diagrams and tables.

## Individual Use Cases

**Individual use cases** can include actors, actions, and optional objects.

## Feature View

**Feature view** depicts conceptual units from the user's point of view. Diagrams that support this view include:

- Feature diagram
- Inter-feature constraints

## Non-functional View

**Non-functional view** examines how non-functional requirements affect the software architecture. This could include explicit tradeoffs and be noted in tabular text.

## Bug Reporting View

**Bug reporting view** depicts units to which bugs are allocated and can include bug report tool components.

## Utility Views

**Utility views** may include supporting software or tabular text.

## Summary

When it comes to software architecture, there is no single tangible thing as _the architecture_. Software architecture is about a set of decisions that are conveyed with various architectural views.

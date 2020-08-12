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

## Section Quizzes

### Diagram Types Quiz

_Match the diagram in the first column with the text in the second column that most closely describes the meaning of its lines._

- Component diagram: calls
- Package diagram: imports
- Class diagram: generalization

### Feature Diagram Quiz 1

_How many differently configured cars does the diagram allow (diagram shown in lecture)?_

1 (car body) \* 2 (auto or manual) \* 3 (electric, gas, or hybrid) \* 2 (trailer or no trailer) = 12

### Feature Diagram Quiz 2

_Which of the following are valid configurations of cars (diagram shown in lecture)?_

- Sunroof body, automatic transmission, gas, engine, and pulls trailer
- Sedan body, manual transmission, gas engine, and electric engine

### Non Functional Requirements Quiz

1. _Match a single non-functional requirement with the description that best characterizes it._

   - Support of SSL (ex. for online shopping): security
   - Plugin capable: extensibility
   - Cross-platform: portability

2. _What are some other non-functional requirements in which a web browser might be interested? Why?_

   - Accessibility is important because there are many users who may have limited ability to use the web browser due to age or disabilities.

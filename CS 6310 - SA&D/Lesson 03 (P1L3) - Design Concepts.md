# Lesson 3

This lesson will cover design concepts. Design is everywhere so it is important to know what role design will play in terms of software.

## Software Design

Software design is the process of building a program while satisfying a problem's functional requirements and not violating its non-functional constraints.

Software design is typically broken up into two phases:

1. **Architectural design**: the process of identifying and assigning the responsibility for aspects of behavior to various modules or components of a software
2. **Detail design**: the process of specifying the behavior of each of the system components that you've identified during architectural design

## Design Notation

There are several of notations used in software design:

- **Pseudo code and PDL (program design language)**: keywords, free syntax of natural language, data declaration, subprogram, definition, and calling
- **Structured programming**: sequence, condition, repetition, chunking
- **Flowcharts and call graphs**: directed graphs - node is computational unit; arc is flow of control
- **Decision tables**: rules, conditions, actions

## Approaches To Software Design

A **method** is a systematic sequence of steps that a design team uses to solve a problem.

## Issues With Design

There are many issues with design however, one important aspect is the tension between long-term maintainability and short-term schedule.

## Design Validation

Below are some issues with design validation:

- Independence of validators
- Dependence on design method
- On-going versus after-the-fact

## Other Design Issues

Here are some other design issues:

- Architectural versus detail design
- Functional behavior versus non-functional constraints
- Specification/what versus design/how
- Application specificity

## Traditional Design Documentation

Traditional design documentation might include:

- Sub-components:
  - Processes/activities
  - Data/data flows
- Control flow: control regime
- Performance
- Resources

## Leonardo Objects

Below are some examples of Leonardo objects:

- **Stakeholders**: views/interests and work procedures
- **Issue bases**: issues, alternatives, analyses, resolutions (commitments, decisions), rationale, impacts, conflicts
- **Temporal relations**: histories, schedules, transformations, versions (revisions, releases, variants)
- **Constraints**: internal, external (requirements, specifications)
- **Aggregates**: configurations, packages, components

## Design Rationale

Design decisions are explicit choices of how to trade off two non-functional aspects of a design, such as speed versus size.

## Coupling And Cohesion

- **Coupling** is the extent to which two components depend on each other for successful execution. Generally, low coupling is good
- **Cohesion** is the extent to which a component has a single purpose or function. In general, high cohesion is good

## Abstraction And Refinement

Below are some abstraction mechanisms:

- **Declarative**: what, not how
- **Aggregation**: container, not contents
- **Generalization**: class, not individuals
- **Parameterization**: bind details later
- **Non-determinism**: leaving choices unspecified

## Design Philosophy

Some design philosophies from philosophers include:

- Descartes - analysis and use of models
- Marx - understanding of the social context of design solutions and user-centered design
- Heidegger - tools for accomplishing goals, e.g., CASE, IDE
- Wittgenstein - language games desktop metaphor

## Summary

Design is the most creative part of software development.

## Section Quizzes

### Terms Quiz

_Can you distinguish the following definitions?_

- Design: deliberative, purposive planning
- Engineering: skillful or artful contrivance applying scientific and mathematical principles
- Craft: skilled occupation
- Art: use of skill, taste, and imagination in the production of aesthetic objects

### Programming Or Design Quiz

_Which of the following are differences between software design and programming?_

- Scale
- Emphasis on non-functional requirements

### Weather Quiz

_If you were designing for performance, would you use an array or a collection of interdependent objects to hold data about weather for a region?_

We would use an array.

### Design Review Quiz

_What are the negative consequences of testing a design for the first time once the project has been completed?_

That would not be cost or time effective.

### Documentation Quiz

_Pick an organization that would require formal documentation:_

A military contractor would require formal documentation.

### Java Quiz 1

_Which of (reduced) coupling or (increased) cohesion do Java packages support?_

Java packages support reduced coupling.

### Java Quiz 2

_Does the Java class inheritance mechanism increase or decrease coupling between the parent and child classes?_

The Java class inheritance mechanism increases coupling.

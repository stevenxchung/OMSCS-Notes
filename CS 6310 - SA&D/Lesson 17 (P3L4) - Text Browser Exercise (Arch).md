# Lesson 17

In this lesson we will conduct a `TextBrowser` case study (based on a paper by Stirewalt and Rugaber) but this time regarding software architecture. The objectives are as follows:

- Analyze and determine an appropriate architecture
- Suggest a process for the `TextBrowser`
- Use UML diagrams and constraints to describe system architecture

## Text Browser

Recall that the `TextBrowser` is composed of the following features:

- Source of textual data (`Document`) with a file system interface (`FileManager`)
- Resizable viewing window resource capable of displaying lines of text (`ViewPort`)
- Controlling device (`ScrollBar`) capable of selecting a discrete value via a handle

The objective is to specify the properties of the `TextBrowser`, choose an architecture, and assemble the components

## Phase 0

Objectives of Phase 0:

- Understand the system being built in terms of its relationship with its environment
- Understand important external actors and the interactions that they can have with the system

We can accomplish this by:

1. Constructing a context diagram
2. Indicating external actors but only one activity
3. Indicating external stimuli (events) that could affect the system
4. Indicating how the system communicates its results back to the external actors (percepts)
5. Specifying behaviors we want the system to have

## Phase 1

Objective of Phase 1: divide the system being built into components (start with the analysis diagram)

We can accomplish this by:

1. Decomposing the system into components
2. Allocate responsibilities (e.g., event handling, percept delivery, and property guarantees)
3. Specify component properties as OCL invariants and pre/post conditions

## Phase 2

The object of Phase 2 is to determine the architectural style.

We can accomplish this by:

1. Choosing an architectural style (`TextBrowser` will be a layered implicit invocation)
2. Assign components to layers (user events at the bottom and percepts at the top)
3. Determine dependencies among the layers
4. Update OCL into constructive/applicative format

## Layered And Implicit Invocation

In layered and implicit invocation architecture the component is organized into layers where the higher-level components register their interest in lower-level events and are _called-back_ when the events occur. Note:

- Lower-level components do not know the identities of upper-level components consuming the events
- Propagation is implicit

## Benefits And Costs

Some of the benefits and costs of using layered and implicit invocation are:

- Pros: improved reusability and reduced complexity
- Cons: Overhead due to the extra levels of indirection

## Invariant Maintenance Strategies

A key question in going between analysis and design is how we will maintain invariants. What maintain means is how - once the invariant is broken - we will propagate the knowledge of the break to the appropriate component so that it can take steps to reestablish the invariant. Common strategies include:

- Aggregated responsibility
- Distributed responsibility
- Mediated responsibility

## Section Quizzes

### Text Browser Arch Quiz

_Can you think of three other architectural styles that might work for the web browser_?

Component Based, Model View Controller, Pipe and Filter

### Resize Window Quiz

_To which component would you assign the responsibility of resizeWindow and its indirect effects_?

`ViewPort` should have the responsibility of `resizeWindow`.

### Invariant Maintenance Quiz

_When a user event takes place, such as moving the ScrollBar handle, invariants within the TextBrowser are temporarily broken. When a user scrolls, which if the three invariants might break_?

`displaysDocument` could be broken during scrolling.

### Centralized Strategy Quiz

_Which of the 3 invariant maintenance strategies is the most centralized_?

Mediated responsibility since it can handle invariants in a single, highly cohesive location.

### Decentralized Strategy Quiz

_Which of the 3 invariant maintenance strategies is the most decentralized_?

Distributed responsibility as responsibility is spread out.

### Aggregated Responsibility Quiz

_Describe how resizeWindow would be handled if the aggregated responsibility strategy is chosen_.

Since `ViewPort` aggregates the responsibility of `resizeWindow`, that method should part of the `ViewPort` class.

### Distributed Responsibility Quiz

_Describe how resizeWindow would be handled if the distributed responsibility strategy is chosen_.

`resizeWindow` can turn into a utility method called by any class since resizing the window can be the responsibility of any of the main components for a distributed system.

### Mediated Responsibility

_Describe how resizeWindow would be handled if the mediated responsibility strategy is chosen_.

The responsibility is shifted to a mediator component which has access to `resizeWindow`. Whenever a component needs to handle the invariant, it interacts with the mediator component.

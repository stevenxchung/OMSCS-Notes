# Lesson 12

Structural models express properties that are always true but fail to convey interesting behavioral aspects of systems. UML provides alternatives for behavior modeling. In this lesson we will look into behavior modeling and state chart diagrams.

## States

**States** are abstract descriptions of system values at a given time. A state space is a set of all possible states and increases multiplicatively.

## Events

**Events** are single, instantaneous, noticeable occurrences.

## UML Event Taxonomy

UML supports the following events:

- Signal (asynchronous notification)
- Method call (synchronous operation invocation)
- State change (continuously monitored)
- Time passage

## Modeling Techniques

Systems that respond to events are called **reactive systems**. Modeling techniques include:

- Combinatorial: states but no events
- Sequential: states, linearly ordered events
- Concurrent: states, unconstrained events

## Combinatorial Modeling

**Combinatorial modeling** expresses logic of simple combinatorial systems where only inputs determine subsequent states. Some tools for this type of modeling include:

- Decision trees
- Decision tables

## Decision Tables

**Decision tables** are useful for determining system outcomes for a given configuration. For decision tables, conditions are called inputs and responses are called outputs.

## Decision Trees

The graphical form of the decision table is the **decision tree**.

## Sequential Systems

**Sequential systems** (also called **finite state systems** or FSM) have memory of previous system activities.

## State Transition Table (STT)

**STT (state transition tables)** have rows that correspond to states and contain four columns:

- Name
- Input event
- Output actions
- Next state

## State Transition Diagrams

**State transition diagrams** are graphical representation of finite state machines. However, the layout of these diagrams has no semantic import.

## Problems With State Transition Diagrams

There are several problems with state transition diagrams:

- Too many arrows
- Too many states
- No concept of abstraction/nesting

## State Charts

Improvements to state transition diagrams are included in state charts. State charts are able to address the issue of complexity and is part of UML.

## State Chart Extensions To FSMs

State charts extents FSMs by offering the following:

- Depth
- Concurrency
- Broadcast events
- Conditional transitions
- Entry/exit action/activities
- Event parameters
- History
- Default states

## Complete UML Transition Description

The complete UML transition description includes:

- Source state
- Target state
- Trigger event
- Guard
- Action
- Forks and joins

## Relationship To Class Diagram

How does the state chart relate to the class diagram? Each class has attributes and attributes form state space. Each class could have their own state chart but most have simple states. For state charts:

- Attributes are attributes of class
- Actions are methods
- Events appear as signals

## Summary

Behavioral modeling can be done with state charts. There are other methods we can use as well (shown in slides) but for the purposes of the course, state charts will be effective in representing behavior in our systems.

## Section Quizzes

### Tic Tac Toe Quiz

_The game of TicTacToe is played on a 3 x 3 grid. Each grid cell can contain an X, an O, or can be empty. In how many different states can a TicTacToe board be?_

3^9 = 19683

### State Vs Event Quiz

_Which of the following are states, events, or neither? Select the correct option from the drop down next to each of the below._

- State
- Neither
- Event
- Event
- State
- Event
- Neither
- Event

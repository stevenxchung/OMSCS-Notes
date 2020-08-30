# Lesson 19

> Connectors mediate interactions among components - that is they establish rules that govern component interaction and specify any auxiliary mechanisms required. (Shaw and Garlan)

We will look more into connectors in this lesson.

## Atomic Elements

Atomic elements in software architecture include:

- **Ducts**: provide mechanisms for transmitting data and control information among components
- **Connectors**: go beyond ducts by providing the protocol used on ducts

Connectors may include internal mechanisms such as storage or computation

## Service Categories

**Service categories** represent the broad interaction role the connector fulfils. These catagories include:

- Communication (t): transmission of data
- Coordination (o): transfer of control
- Conversion (x): converting data formats for component interaction
- Facilitation (f): mediation and optimization

## Procedure Call Connectors

**Procedure call connectors** are the basis for composite call connectors.

- Flow of control: coordination (o)
- Parameters: communication (t)

## Event Connectors

Another very common connector is the **event connector**. This connector generators message after detecting an event or pattern of events.

- Flow of control: coordination (o)
- may pass information (time stamps, source, parameters): communication (t)

These connectors are also used in distributed asynchronous applications.

## Data Access Connectors

Access to a data repository requires a **data access connector**.

- Access to a repository: communication (t)
- May perform translation: conversion (x)

## Linkage Connectors

**Linkage connectors** are responsible for establishing ducts.

- Establish ducts and enforce interaction semantics: facilitation (f)
- May disappear after setup is complete

Modules, files, and objects are managed by configuration management and make tools.

## Stream Connectors

When dealing with streams we resort to the **stream connector**.

- Data transfer: communication (t)

## Arbitrator Connectors

Conflict resolvers are the handled by **arbitrator connectors**.

- Conflict resolution: facilitation (f)
- Redirection of control: coordination (o)

## Adaptor Connectors

When components are to be connected we use an **adaptor connector**. These connectors are not designed to interpolate.

- Converting protocols and policies: conversion (x)

## Distributor Connectors

For routing we can resort to **distributor connectors**. These connectors could also be used to assist other connectors.

- Identify interaction paths and routing: facilitation (f)

## Connector Design

When designing connectors it is important to:

- Determine components and required interactions
- For each interaction determine the required services
- Select connector types that provide services
- Choose values for connector dimensions
- Validate using rules

## Validation Rules

Validation rules include:

- **Requires**: requirements placed by the value on one dimension on the value of another dimension
- **Cautions**: certain combinations may be unstable or unreliable
- **Restricts**: certain combinations may be invalid
- **Prohibits**: total incompatibility of dimensions

## Summary

The job is not finished after determining the components of a system. We still must specify connectors for each component as well. Treating connectors as part of the design process can help further the design process.

## Section Quizzes

### Pipe and Filter Quiz

_For the pipe and filter architectural style, which is the component and which is the connector?_

The _pipe_ is the _connector_ and the _filter_ is the _component_.

### Services Quiz

_Provide service types for the following example services (shown in lecture)._

1. Data buffering: f
2. Acknowledgement: o
3. Guaranteed delivery: o
4. Dynamic reconfiguration: f
5. Multiplexing: o
6. Invocation: t
7. Transactions: o
8. Load balancing: f
9. Scheduling: o
10. Synchronization: o

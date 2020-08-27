# Lesson 18

Software architecture prescribes the high-level structure of a system in terms of its components and how they interact. In this lesson we will look more into how software architecture should satisfy non-functional requirements.

## Qualities

Non-functional qualities includes **crosscutting** which is not provided by a single component but provided by many or all components. Crosscutting has a strong effect on a system's architecture.

## Quality Catalog

Below is a list of some common non-functional requirements:

- **Performance**: attribute of a computer system that characterizes the timeliness of the service delivered by the system
- **Maintainability**: extent to which enhancements can be readily added to a system (also called evolvability, flexibility, adaptability)
- **Reliability**: likelihood of failure in a given time period
- **Safety**: extent to which system protects against injury, loss of life, or property damage
- **Security**: extent to which system protects against unauthorized intrusion

## Architectural Styles

Below are some of the architectural styles we will examine:

- **Pipe and filter**: chain of processing elements called filters arranged so that the output of each element is communicated via a pipe to become the input of the next
- **Layered**: grouping of functionality into distinct layers that are stacked vertically on top of each other; communication between layers is explicit and loosely coupled
- **Blackboard**: a common knowledge base is iteratively updated by a diverse group of specialist knowledge sources
- **Object-oriented**: division of responsibilities into individual reusable and self-sufficient objects
- **Implicit invocation**: a component can broadcast events while other components in the system can register interest by associating a procedure with the event

## Pipe And Filter Qualities

Lets highlight some of the qualities of pipe and filter.

Performance:

- Pros: enhanced throughput because the filters can run in parallel
- Cons:
  - An individual filter may be slowed down if it is waiting for its supplier
  - May be a significant overhead due to context switches

Maintainability:

- Pros: enhances encapsulation
- Cons: increases coupling

Reliability:

- Pros: may be reduced due to the _weakest link_ filter

Safety:

- Pros: verification may be enhanced
- Cons: may be reduced by multiple dependencies

Security:

- Pros: simplicity increases opportunities for authentication, encryption and implementation of security levels

## Layering Qualities

Lets highlight some of the qualities of layering.

Performance:

- Cons:
  - May be reduced
  - Increased context swapping

Maintainability:

- Pros:
  - May be increased
  - May be even possible to replace an entire layer

Reliability:

- Pros: higher layers may have the oversight to provide redundancy
- Cons: reliability is reduced

Safety:

- Pros: may be easy to insert safety-monitoring layers

Security:

- Pros: security is enhanced

## Blackboard Qualities

Lets highlight some of the qualities of blackboard.

Performance:

- Cons:
  - lack of well-defined control flows may lead to redundant, administrative behavior

Maintainability:

- Pros: enhances flexibility
- Cons: changes to a common control paradigm or the repository's data format may have pervasive effects

Reliability:

- Pros: independence of the components can increase system resilience
- Cons: may be difficult to identify the cause of problems

Safety:

- Cons: can promote spreading of bad data

Security:

- Pros: access control is enhanced
- Cons: reduce confidence in overall system security

## Object-oriented Qualities

Lets highlight some of the qualities of object-oriented.

Performance:

- Cons:
  - Many small objects lead to multiple context switches
  - Can reduce responsiveness

Maintainability:

- Pros: significantly increased because of the independence of the components, both their encapsulated data and the hands-off, message-passing style of communications
- Cons: can increase system inter-component dependencies, thereby reducing maintainability

Reliability:

- Pros: encapsulation can reduce vulnerability to unintended interactions
- Cons: decentralized control reduces opportunity for oversight

Safety:

- Pros: improved intentionality and accountability

Security:

- Pros: encapsulation can reduce vulnerability
- Cons: increase system fragmentation

## Implicit Invocation Qualities

Lets highlight some of the qualities of implicit invocation.

Performance:

- Cons: extra communications can lead to reduced performance

Maintainability:

- Pros: may be increased (reuse due to independence of components)

Reliability:

- Pros: more easily able to deal with unexpected events
- Cons: overall understandability is reduced

Safety:

- Cons: increased interaction complexity may make it harder to ensure safety

Security:

- Pros: encapsulation can help mitigate fragmentation problems
- Cons: fragmentation can cause problems

## Summary

When designing a system be sure to take into account the positives and negatives of each implementation.

## Section Quizzes

### Non-functional Qualities Quiz

_There are many different non-functional qualities that a system might have. Try to name 3._

Accessibility, learnability, usability, etc.

### Functional And Non-functional Requirements Quiz

_Imagine a program that plays TicTacToe against a human opponent. Here is a list of requirements. Please choose if each is a functional or non-functional requirement._

1. Functional
2. Non-functional
3. Non-functional
4. Functional

### Applications Quiz

_The column lists the five qualities we just discussed (shown in lecture). The lists to the right contain the applications. See if you can match the quality to the application in which that quality is paramount._

- Performance: weather prediction
- Security: online banking
- Safety: cruise control
- Maintainability: Twitter API
- Reliability: traffic light controller

### Side Effects Quiz 1

_Match each architectural style with a negative side effect it can have on system design._

- Pipe and filter: increased coupling
- Blackboard: can promote spread of bad data
- Object-oriented: increase system fragmentation
- Implicit invocation: reduced system understanding

### Side Effects Quiz 2

_Now, match each non-functional requirement with the negative side effect using it might engender._

- Reusability: increased system fragmentation
- Reliability: compromised delivery schedule
- Security: increased coupling
- Performance: reduced system understanding

# Lesson 24

So far we have covered **top-down design** which begins with requirements. In this lesson we will focus on **bottom-up design** which begins with self-contained pieces of software systems called components.

## Components

**Components** are pieces we put together. Here is a quote from Clemens Szyperski:

> A component is an executable unit of independent production, acquisition, and deployment that can be composed into a functioning subsystem.

## Buy Versus Build

Often we find ourselves asking at the beginning of bottom up design: should we construct software assets ourselves or buy them from someone else?

## Build

Building means in-house custom development. The advantages and disadvantages mirror those of _buying_:

Pros:

- Tailored to specific situation
- Retain control of intellectual property

Cons:

- Costs more due to economy of scale
- Overall delivery risk is increased

## The Third Way

There is also a third way: use third-part components that can be customized during assembly.

## Characterizations Of Components

There are pre-existing and general components (making them reusable). What does it mean to manufacture a component?

- Can configure a component with respect to your needs and the target environment
- Can be easily composed with each other and with non-component code
- Conform to a software component model

## Component Life Cycle

There are three phases to a component life cycle:

1. Design time
2. Deployment time
3. Runtime

## Component Models

A component model is a component's framework. This includes:

- Component syntax
- Component semantics
- Component composition

## Issues

Issues with components may include:

1. **Configuration**
   - Components are typically configurable
   - Component vendors provide a means by which the client can tailor it to a particular solution
   - The flexibility that configuration fives comes at a cost
2. **Versioning**
   - Backward compatibility becomes a problem
   - Component vendors must keep customers up to date
3. **Extensions**
   - Components are often extended by adding new features:
     - Singleton extension
     - Parallel extension of multiple components
     - Non-orthogonal extensions
     - Recursive extension
4. **Callbacks**
   - An operation provided by the client
   - Powerful tool that components can use for interacting with clients
   - However, system integrity may be compromised during the time in which the client is in control
5. **Contracts**
   - Because components are provided by third parties, there is an increased need for a clear specification of what they are promising.
6. **Objects as components**
   - Many component technologies identify objects and components
   - Problems arise when using objects to implement components
   - It becomes much more difficult to guarantee contracts in the face of object callbacks and inter-method calls
   - Problem is even worse in the presence of multi-threading
   - Inheritance: subclass objects may violate component contracts
   - Fragile base class: occurs when a new version of a component changes one of its base classes
7. **Scaling**
   - Accounting
   - Deployment and configuration
   - Disputes
   - Quality of service
   - Fault containment and error handling
8. **Domain standards**
   - There is tension between proprietary solutions and open standards
   - Community benefits from standard solutions
   - Standards take a long time for approval and penetration

## Invariants

Modules in a system are responsible for maintaining invariants. Presence of callbacks makes invariant maintenance much more difficult. There is a danger that the client may do something that breaks the invariant.

## Callback Summary

The advantage of callbacks is that the component can provide a control regime with with the client executes. The cost of using callbacks is that the component stat is exposed to the client at a time when it may not be internally consistent.

## Levels Of Contracts

There are various levels of contracts:

1. **Signature contracts**
   - Syntactic or signature contract
   - Names and arguments of component operations are specified
2. **Correctness contracts**
   - Pre and post conditions are specified for all callable operations thus guaranteeing that component operations successfully execute
   - OCL is a good candidate
3. **Collaboration contracts**
   - Interactions are specified addressing issues such as synchronization, liveness, and deadlock
   - Set of allowed interactions for a component that compromise that component's protocol
4. **Quality of service contracts**
   - Non-functional requirements addressed (e.g., availability, throughput, latency, etc.)

## Summary Of Contracts

The bottom line is for contacts is that the customer needs to know what he or she is getting.

## Component Frameworks

Component frameworks include **shared attributes**:

- All provide late binding, persistence, encapsulation, and sub-typing
- Provide support for communication among components
- Offer some form of component transfer packaging
- All provide a way of describing deployments
- Provides a way of serving components

## Future Directions

Some ongoing concerns for components include:

- Liability
- Quality guarantees
- Contract persistence over versions

## Summary

Advent of viable component marketplace has opened up a whole new approach to building software applications. Components provide some of the flexibility that comes with building your own solution without incurring all of the associated risks.

## Section Quizzes

### Buy Quiz

_Below are some business factors to consider when deciding whether to buy a software component from a 3rd party vendor . Choose whether each is enhanced or diminished if you decide to buy._

- Your uniqueness with respect to your competitors: diminished
- The amount of staff time required to develop the product of which the component is a part: enhanced
- Your overall production costs: enhanced
- Your control over the development process: diminished

### Third Party Quiz

_In addition to buying complete applications or components , there are several other ways that 3rd parties can provide computational resources to a client. Match the example to the category:_

- PThreads: software libraries
- NIST time service: cloud-based services
- Tom-Tom GPS: turn-key equipment
- Checkstyle: IDE plugins
- PHP: open-source software

### Component Models Quiz

_Wordpress is a content management solution for blogs. Here are some requirements taken from the Wordpress codex. For each requirement, determine whether it concerns component syntax, component semantics, or component composition._

- Any text output by the 'Action' function will appear in the page source at the location where the action was invoked: **component semantics**
- Use well-structured, error-free PHP and valid HTML: **component composition**
- Actions are triggered by specific events in Wordpress, such as publishing a post, changing themes, or displaying an administration screen. Action is a custom PHP function defined in your plugin and hooked to some of these events: **component syntax**

### Automobile Components Quiz

_What are some of the 3rd party component on which automobile manufacturers rely?_

Tires, dashboards, and other parts.

### Callbacks Quiz

_Consider this sequence diagram (shown in lecture) describing a typical callback situation in which a component captures a user event and invokes a client method via a callback. The component is subject to corruption during which time period?_

Period D to E since the component method is exposed.

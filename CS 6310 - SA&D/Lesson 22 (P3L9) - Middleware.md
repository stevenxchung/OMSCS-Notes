# Lesson 22

This lesson will focus on architecture of **distributed systems**. Distributed systems typically involve multiple computers and are heterogeneous in nature (includes multiple components).

## Middleware

**Middleware** consists of _glue_ code which supports distributed heterogeneous computation. This is similar in concept to architectural connectors.

## Context

Why is distributed systems architecture relevant?

- Growth of networked machines
- Specialization of hardware resources
- Increasingly powerful applications

## Needs

What is required to support distributed applications?

- Abstractions (REST), interfaces (APIs), and standards (HTTP)
- Notations (e.g., XML)
- Tools (Spring Boot) which include design and code generation

## Exercise Application

In this lesson we will be examining distributed systems through an example application which is web-based and polls user opinion on a variety of questions. The application is able to record choices, display how others voted but keeping users anonymous.

## Characteristic Issues

We will also be examining the following issues:

1. **Network communication**:
   - Error handling/reliable delivery
   - Synchronous and asynchronous errors
   - Data representation and transport:
     - This could include machine differences, organization of constituent pieces, and self definition
   - Transactions:
     - Includes **ACID (Atomic, Consistency-preserving, Isolated, and Durable)**
     - Reliable database access with multiple readers and writers
     - Conditionally updating a record
     - Reliable transactions satisfy ACID properties
2. **Coordination**:
   - Synchronization
   - Control
   - Robustness
   - Availability
   - Persistence
3. **Reliability**:
   - Components of distributed systems sometimes fail
   - Failure to deliver or multiple delivers
   - Classic reliability/performance tradeoff
4. **Scalability**:
   - What has to be done to the system to deal with growth in users or load
   - To what extent will adding new machines change system architecture or components?
   - Transparency (e.g., access, location, migration, and replication transparency)
5. **Heterogeneity**:
   - Hardware
   - Operating systems
   - Programming languages
   - Standards, protocols, APIs
   - Access mechanisms
   - Web browsers
   - Devices

## Implications Of Heterogeneity

Some implications of heterogeneity include:

- Standard APIs (backward and forward compatibility)
- Normative architectures (model-driven architectures or MDA)
- Vendor comprehensive solutions

## Other Non-functional Issues

Other non-functional issues may include the following:

- Fault tolerance
- Flexibility
- Reuse/productivity
- Complexity management
- Quality of service

## Kinds Of Middleware

There are different kinds of middleware:

- **Transactional**: distributed transactions
  - Deals with reliability and ACID requirements
  - Two-phased commit
  - Distributed client/server with location transparency
- **Message-oriented**: message passing
  - Asynchronous message passing
  - Fault tolerant because of queues
  - Distributed event notification (push/subscribe)
  - Not very transparent (clients must implement coordination)
- **Procedural**: remote procedural call
  - RPC (remote procedural call)
  - Synchronous
- **Object/component**: remote object requests
  - Costs (e.g., object identity, inheritance)
  - Features (e.g., synchronous/asynchronous, marshalling, exception handling)

## Software Engineering Issues

There are also software engineering issues:

- **Requirements engineering**: elicitation of non-functional requirements
- **Software architecture**:
  - Derive architectures that will address non-functional requirements
  - Relationship of connections to middleware
- **Design issues**:
  - Network latency for distributed interactions
  - Activation, statefulness, persistence
  - Concurrency (e.g., synchronization, deadlock, avoidance, liveliness)

## Research Questions

Research questions in the area of distributed systems architecture might include:

- Naming (white pages) vs. trading (yellow pages)
- Use of reflection, meta-object protocols
- NoSQL
- Fat vs. thin clients (AJAX)
- Embedded systems/memory limitations

## Web Services

A **web service** is:

- W3C:

  > A software system designed to support interoperable machine to machine interaction over a network.

- Wiki:

  > An API or are APIs that can be accessed over a network, such as the internet and executed on a remote system hosting the requested services.

## Web Service Protocols

There are several web service protocols:

- **XML** - self-defining data descriptions
- **WSDL** - web services description language
- **UDDI (Universal Description, Discovery and Integration)** - directory services (yellow pages)

## SOA

**SOA (Service Oriented Architecture)** is:

- Wiki:

  > A computer systems architectural style for creating and using business processes, packages as services throughout their lifecycle.

## SOA Services

SOA services can be described as:

- Service:
  - Self-contained, self-defined, modular application
  - Defined and self-documented use protocol
- Job responsibilities or business needs of the service user
- Comprised of a suite of sub-services (published, located, and dynamically invoked)

## Characteristics Of Services

There are several characteristics of services:

- **Flexibility**: obtained by factoring
- **Meaningful**: self-contained and user oriented
- **Stateless**: however, can make use of a database
- Transparent with respect to middleware

## Summary

To summarize, middleware is a collection of technologies for addressing non-functional constraints in heterogenous distributed applications. These technologies include APIs, protocols, tools, and design patterns.

## Section Quizzes

### Voting Application Quiz 1

_For the sample application, what data needs to be transmitted from the web browser to the server?_

Vote and question number

### Voting Application Quiz 2

_Is there a need for transactions in the application?_

It depends

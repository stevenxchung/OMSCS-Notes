# Lesson 15

The second major topic in this course is software architecture. In this lesson, we will examine software architecture as well as diagrams that go along with software architecture.

## Informal Definition

**Software architecture** is the organization of a system into component subsystems or modules. It can be iteratively refined into multiple layers and often makes use of the stereotypical architectural style.

## USP Definition

Software architecture is concerned not only with structure and behavior but with usage, functionality, performance, resilience, reuse, comprehensibility, economics and technology constraints and trade-offs, and aesthetic concerns.

## Other Definitions

For representing architectures we have the following:

- Component: computational or data element interface to the rest of the system
- Connector: communication protocols among components
- Configuration: components hooked up with connectors

## Selecting Components

What are some steps to selecting components? We typically look for

- Required functionality
- Existing reusable components
- Physical machine architecture
- Expertise of staff
- Conway's Law
- Projected evolution trajectories

## APIs

**APIs (Application Programming Interface)**:

- Include names of access ports, arguments, types
- Can be described in a specific programming language; language binding
- Might be described in OCL
- Can be described using ADLs (Architectural Description Language)

## Architectural Views

The architecture of a system comprises all of the decisions controlling how a specified problem solution is realized. Because this set of decisions may be quite large and eclectic, various architectural diagrams are used to convey some portion of them.

## Architectural Styles

Different architectural styles might offer the following benefits:

- Encoded experience
- Standards (validation, selection criteria, etc.)
- Reuse
- Support of process

## Style Issues

There are various issues when it comes to architectural styles however:

- Some systems have more than one style (heterogeneous)
- Other systems might include DSSA (domain-specific software architecture) or reference architecture
- Semantics could become an issue with multiple styles

## Architecture Description Language

**ADL** is a notation for describing architecture as discussed earlier. It includes formality and precision and is a prerequisite for tool support.

## Architectural Evaluation

Architectural evaluation is a systematic assessment of architecture properties and includes:

- Architecture review boards
- SAAM (Software Architecture Assessment Method)
- ATAM (Architecture Tradeoff Analysis Method)

## Summary

The ultimate goal is to increase the quality of delivered systems and reduce the cost of producing them.

## Section Quizzes

### Analysis To Components Quiz

_Assume we want to determine the components of a software system based solely on an analysis model. Given this scenario, select true or false for each statement._

Analysis models...

- Can adapt well to changes in customer requirements
- Should **NOT** represent the approach that will be taken in design
- Are resilient to changes in hardware
- Do **NOT** include all components required by a system


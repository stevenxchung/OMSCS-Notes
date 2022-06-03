# Lesson 21

In this lesson we will cover _configuration_ which is a routine kind of design task in which all the components of the design are already known. The task of configuration is to assign values to the variables of those components so they could be arranged according to some constraints. We will cover the following:

1. Design and configuration
2. Plan refinement
3. Connections to earlier topics

## Define Design

**Design** takes in needs, goals, or functions and returns the specification and structure of some artifact that satisfies those needs, goals, and functions. The artifact does not need to a physical product, it could be a process, program, or policy.

Design is very broad, open ended, and undefined. In problem solving, typically the problem remains fixed even as the solution evolves. However in design, both the problem and the solution co-evolve (the problem evolves as the solution evolves). One of the goals of KBAI is building intelligent agents which can design.

## Defining Configuration

**Configuration** is a problem solving activity that assigns values to variables to satisfy constraints.

## The Configuration Process

The configuration process is as follows:

1. **Specification space**: which provides specification to structure mapping and receives additional specifications if arrangement model evolves
2. **Abstract and partial solutions**: the beginning state when solutioning
3. **Solution refinement and expansion**: includes pulling abstraction and component hierarchy from the configuration space
4. **Expanded and refined solutions**: the end state of solutioning
5. **Arrangement model**: the output of the configuration process which could also be refined

## Connection To Classification

Classification and configuration are both hierarchical. Configuration leverages classification's notion of prototype concepts.

We use _classification_ to make sense of the world by mapping combinations of percepts equal to its process. We use _configuration_ to act on the world by designing actions. So while _classification_ is a way to make sense of the world, _configuration_ is a way of creating the world.

## Contrast With Case-based Reasoning

_Configuration_ suggests starting with a prototype concept and assigning values to variables. _Case-based reasoning_ suggests starting from a specific chair and tweaking it as needed.

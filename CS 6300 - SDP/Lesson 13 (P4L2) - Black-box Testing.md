# Lesson 13

In this lesson we will cover one of two testing methods: _black-box testing_ which refers to functional testing.

## Black-box Testing Overview

**Black-box testing** has to do with testing a system without knowing its internal details.

Advantages:

- Focuses on the domain
- No need for the code -> early test design
- Catches logic defects
- Applicable at all granularity levels

## Systematic Functional Testing Approach

How do we get from functional specifications to test cases? There are several steps:

1. **Identify independently testable features**
2. **Identify relevant inputs**:
   - We should **not** have to test all cases
   - We should **not** test random inputs
   - Instead we should identify partitions and select inputs from each
   - We could also look at boundary values (edge cases) for each partition
3. **Derive test cases specifications**
4. **Generate test cases**

## Category Partition Method

The **Category-partition Method** (Ostrand and Balcer, CACM, June 1988) describes how to go from specifications to test cases in six steps:

1. **Identify independently testable features**
2. **Identify categories**: this involves identifying characteristics of each input element
3. **Partition categories into choices**: this involves identifying interesting cases (sub-domains)
4. **Identify constraints among choices**:
   - Eliminate meaningless combinations
   - Reduce the number of test cases
   - Three types of labels: `Property... If`, `Error`, and `Single`
5. **Produce/evaluate test case specifications**:
   - Can be automated
   - Produces test frames
6. **Generate test cases from test case specifications**:
   - Simple instantiation of frames
   - Produces set of concrete tests (final result)

## Model Based Testing

**Model-based testing** fits into the previous functional testing approach like so:

1. Identify independently testable features
2. Identify relevant inputs _or_ the model
3. Derive test cases specifications
4. Generate test cases

## Finite State Machines

One of the model-based testing approaches utilizes **FSM (finite state machines)** which can be defined by the following components:

1. Nodes -> states
2. Edges -> transitions
3. Edge labels -> events and actions

To build an FSM from specifications, we can perform the following:

1. Identify system boundaries and input and output
2. Identify relevant states and transitions
3. Identify how a system can go from one state to another

## Finite State Machines Considerations

There are some considerations for the FSM model-based testing approach:

1. **Applicability**:
   - Very general approach
   - In UML, state machines are readily available
2. **Abstraction is key**
3. **Many other approaches**: e.g., decision tables, flow graphs, historical models, etc.

## Section Quizzes

### Overview 1 Quiz

> `printSum(int a, int b)`

_How many independently testable features do we have here_?

We only have one feature, in this case `printSum()`.

### Overview 2 Quiz

_Identify three possible independently testable features for a spreadsheet_.

- Sorting
- Plotting
- Saving

### Test Data Selection Quiz

_How long would it take to exhaustively test this function_?

> `printSum(int a, int b)`

_This function takes two integers and prints the sum_.

It would take hundreds of years.

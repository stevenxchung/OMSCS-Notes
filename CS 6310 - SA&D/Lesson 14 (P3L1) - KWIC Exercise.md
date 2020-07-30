# Lesson 14

To familiarize ourselves more with software architecture, we will examine a paper by David Parnas and come up with four different architectures that address the same problem. The problem introduced is to design a program that produces a _key word in context_ index.

## Key Word In Context

The KWIC (Key Word In Context) problem is described as follows:

- KWIC index system accepts as input a sequence of text lines
- A line may be circularly shifted by removing its first word and appending it at the end of the line
- KWIC index system outputs a listing of all circular shifts of all lines

## Components

For shared data decomposition:

- Break the system into components based on the functions they compute
- All components share access to the data
- Usually contains some form of master-controller routine responsible for invoking the others

## Pipe And Filter

For pipe and filter:

- Break the system into independently executing components (filters)
- Connect the components together via FIFO queues (pipes)
- Each filter takes a single input (`stdin`) and produces a single output (`stdout`)
- The filters share the assumption that the inputs and output consist of sequential files containing lines of ASCII characters

## Abstract Data Types

For ADTs (abstract data types):

- Break the system into components based on important data structures
- Hide the representations of the data structures behind abstract interfaces
- The components holding the data structures also provide operations
- ADTs were a precursors to objects in object-oriented languages

## Implicit Invocation

Implicit invocation implies that:

- Communication is coordinated between components using registration-broadcast
- Servers do not know the identities of clients
- The unit of notification is the event

## Evaluation

Below are some advantages and disadvantages of each:

- ADT:
  - Pros: maintainability, reuse
  - Cons: Performance
- Implicit invocation:
  - Pros: enhancements, data representation changes, reuse
  - Cons: difficult to control/think about, inefficient
- Pipe and filter:
  - Pros: intuitive, reuse
  - Cons: interactivity, space efficiency

## Lessons

There are a variety of different architectural styles that can be used to solve a design problem. A given style will have advantages and disadvantages depending on the particular requirements changes it must deal with.

## Section Quizzes

### Shared Data Approach Quiz

_Each approach to solving the KWIC problem has advantages and disadvantages . For the following statements choose whether they are advantages or disadvantages of the shared data approach._

- Data Access Complexity: advantage
- Data Access Speed: advantage
- Resilience to Change: disadvantage

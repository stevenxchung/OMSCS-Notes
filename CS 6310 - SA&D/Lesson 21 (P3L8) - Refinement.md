# Lesson 21

In this lesson we will look into refining an abstract software architecture design to an implementation using a banking example.

## Levels Of Abstraction

**Abstraction** implies thinking at different levels. Work done at a lower level of abstraction must contribute to the solution at a higher level.

## Divide And Conquer

There are two types of divide and conquer, we will use a 3D picture puzzle as a metaphor:

- **Horizontal decomposition**: at any one level of abstraction, you carve out the pieces and fit them together
- **Vertical decomposition**: for each piece at that level, you have a whole picture puzzle at a lower level
  - Refinement suggests devising the puzzles at the lower level and ensuring that they satisfy the needs at the upper level
  - In summary, for vertical decomposition we have a collection of refinements at one level addressing a problem at a higher level

## Proper Refinements

**Proper refinements** move from a high-level understanding to an implementation. To execute a multilevel design properly, three properties must obtain the following:

1. The top level must faithfully represent the requirements
2. Each level must be internally consistent
3. Each lower level must faithfully represent the level above it

## Property 1

**Property 1** holds for any program we want to implement. We check this property using traditional methods such as software testing, group reviews and customer acceptance criteria.

## Property 2

**Property 2** says each level in a design must be internally consistent. We must ensure that each operation maintains all class invariants.

## Property 3

**Property 3** says each lower level in a refinement must faithfully represent the level above it.

## Adequate Representation

The lower level implementation must be rich enough that each abstract state is represented by a concrete state.

## Total Representation

The implementation cannot put us in a concrete state that does not correspond to an abstract one. We must make sure that the retrieve function is total in the mathematical sense.

## Models

Each concrete operation must faithfully reflect the intent of the abstract specification. This criterion has two parts having to do with the operations inputs and outputs.

- **Operation inputs**: inputs acceptable to an abstract specification must also be acceptable to the concrete implementation
- **Operation outputs**: outputs produced by the concrete operations, along with any changes made to class attributes must satisfy the abstract specification.

## Summary

This refinement lesson could be summarized as follows:

1. The top level specification matches the requirements document
2. Operations at each level preserve invariants
3. Each refinement is adequate
4. Each refinement is total
5. Concrete operation preconditions and post conditions model their abstract counterparts

## Section Quizzes

### Bank Account Quiz 1

_Complete the OCL constraints (OCL provided in lecture)._

- A: `>`
- B: `transactions@pre`
- C: `a`
- D: `transactions@pre`
- E: `-a`
- F: `sum`
- G: `transactions`

### Bank Account Quiz 2

_Update your OCL (OCL provided in lecture) to reflect the addition of the new attribute `runningTotal`._

- A: `runningTotal@pre`
- B: `a`
- C: `runningTotal@pre`
- D: `-`
- E: `a`
- F: `runningTotal`
- G: `0`
- H: `transactions`

### Adequacy Quiz

_If we have an abstract state that looks like the following:_

```bash
transactions: {3, -2, 4, 5, -6}
```

_What is the corresponding concrete state?_

- `transactions`: {3, -2, 4, 5, -6};
- `runningTotal`: 4

### Totality Quiz

_The following is a valid concrete state:_

```bash
transactions: {13, -12, 3, 5, -6};
runningTotal: 3
```

_What is the corresponding abstract state?_

`transactions: {13, -12, 3, 5, -6}`

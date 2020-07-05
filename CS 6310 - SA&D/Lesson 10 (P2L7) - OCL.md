# Lesson 10

Because diagrams do not tell the entire story we will need OCL to help accomplish that. OCL supports:

- Strong typing, declarative specification of system properties
- Constraints
- Collection classes
- UML diagram navigation

## Why Do We Need OCL

We need OCL because UML diagrams are limited in what they can express (structural relationships and behavioral descriptions). OCL extends UML with:

- Class invariants
- Operation pre and post conditions
- Guards on state-machine transitions

## OCL Overview

OCL has the following characteristics:

- Declarative not procedural
- Pure expression language
- No assignment statements or other side effects
- Strongly typed
- Built-in types and includes types introduced in UML diagrams

OCL also includes a high level mechanism known as a **constraint** which is a formal assertion of system properties.

## Uses Of OCL

There are multiple uses of OCL:

- Specify invariants on classes in the class model
- Describe pre and post conditions on operations and methods
- Specify derivation rules for derived attributes
- Describe guards on transitions in state chart diagrams
- Specify targets for messages and actions
- Specify type invariants for stereotypes
- Query language

## Syntax

Here is an example of syntax in OCL: `context <identifier> <constraintType>: <Boolean expression>`

## Invariants

**Invariants** are statements of a property that is always true:

```java
context LargeCompany
inv: numberOfEmployees > 50
```

## Role Of Invariants

Role of invariants include concept of integrity constraints e.g., properties of the data in the database that describe whether the database is sound.

## Pre And Post Conditions

Both `pre` and `post` conditions are used to express the meaning of UML operations. A `pre` condition specifies what must be true for the operation to meaningfully take place. A `post` condition specifies what is guaranteed to be true after the operation completes.

## OCL Built In Types

[OCL also includes built in types](https://www.youtube.com/watch?v=o5Rih1sBEuQ) as well as literals and operations.

## OCL Keywords

[There are also keywords we can use in OCL](https://www.youtube.com/watch?v=6_YE18LdtC4). We already have seen `inv`, `pre`, and `post`.

## Navigation

Recall that OCL constraints are associated with class model diagrams. Each constraint specifies a context. **Navigation** is done by walking through a diagram from the context class to the other class using intermediary relationship lines and class rectangles.

## Navigation: Multiplicity

Associations can be multiplicity (e.g., 1-1, 1-m, n-m). When an association has multiplicity greater than one, the result is a collection rather than an individual object. If an operation is performed, then the `->` symbol is used to separate the collection name from the operation name.

## Collections

OCL features four kinds of collections that support associations with n-m and 1-m multiplicities:

- `Collection` provides features that hold true for all collections
- Collections can also provide specialized operations e.g., `Set`, `Bag`, and `Sequence`

## Summary

OCL gives us the ability to properly specify the properties of our system.

## Section Quizzes

### Invariant Constraint Quiz

_See if you can come up with another invariant constraint for the LargeCompany class. Express an invariant that satisfies this requirement for large companies... "A company is considered large if it has a market capitalization of over one million dollars."_

```java
context LargeCompany inv:
marketCapitalization > 1000000
```

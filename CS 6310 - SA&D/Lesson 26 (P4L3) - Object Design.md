# Lesson 26

Previously we focused on OOA. In this lesson we will examine the next steps in architecture design with **OOD (Object-oriented Design)**.

## OOD

Some topics to consider before jumping into OOD include:

1. **Inter-model consistency**
   - May have produced multiple diagrams
   - May include uses cases, sequence diagrams, state charts, etc.
2. **From analysis to design**
   - Treat the entire system as an object
   - Implementing associations and invariants is key
3. **System design**
   - May include architecture, concurrency, physical design, data stores, control, and error handling
4. **Abstraction mechanisms**
   - May include idioms, classes, patterns, aspects, frameworks, and architectural styles
5. **Collaboration-based design**
   - Also known as role-based design and is alternative to strict OOD
   - May include user stories, collaboration and role identification, sequence or collaboration diagrams, role abstraction, and synthesis of classes from roles

## Object Design

There are several elements of object design we should examine:

1. **Methods**
   - Can come from operations
   - May include constructors, getters and setters, etc.
2. **New classes**
   - Should implement relationships, intermediate results, and invent new abstract classes
3. **Generalization**
   - Can occur through inheritance via sub-classing
   - Occurring between two instances means all instances of the derived class are also instances of the parent class
4. **Associations**
   - One way associations:
     - For 1-1 associations, use a simple pointer
     - For 1-n, use a vector of pointers
   - Two-way associations require pointers in both directions:
     - Use two-way associations if access outnumber updates
     - Use if one direction is much more prevalent than the other
   - Associations as objects:
     - Looping through all of the links in a two-way association can be cumbersome and costly
5. **Dependencies**
6. **Implementing control**
7. **Abstract classes, interfaces, and types**
   - There are various mechanism available for abstract classes: abstract methods, abstract classes, and interfaces

## Implementing Generalization

There are many approaches to implement generalization:

1. Inheritance that follows specific rules
2. A single class with flags
3. Hide child data in parent
4. Java interfaces or enums
5. Use state pattern for dynamic inheritance
6. Use multiple inheritance

## Implementing Associations

Unlike generalizations, it takes a bit more thinking to implement associations:

1. OO programming languages do not directly support associations
2. Factors to consider include directionality, cardinality, access (CRUD)
3. Invariant maintenance

## Implementing Dependencies

How do we go about implementing dependencies (most common and varied relationship)?

1. Use an attribute or global object having the type of the target class
2. Receive arguments of the target class
3. Make a method or constructor call to the target
4. Import the target

## Implementing Control

How do we go about implementing control?

1. A class's attribute values comprise its state
2. When needed, code specifically manages event handling and state update on a case-by-case basis
3. Implement some form of state machine

## OOD Summary

OOA goes a long way. However, the OOD process allows us to address how to best deal with UML elements in a OOP setting. We should think through the tradeoffs involved before choosing a solution.

## Section Quizzes

### OOA To OOD Quiz

_What UML elements, used in OOA models do not have direct equivalents in object-oriented programming languages_?

Associations, aggregations, invariants, and state charts to name a few.

### Generalization Quiz

_If you were implementing generalization between squares and rectangles, would you make Square a subclass of Rectangle in which both sides are equal? Or would you make Rectangle a subclass of Square with an additional attribute_?

Either implementation could work, it depends on which class is defined first and how it is defined.

### Associations Quiz

_Consider the problem of implementing the Takes association between Students and Courses. For each of the following 4 options (provided in lecture), match each with its major disadvantage_.

- In each student, create a reference that refers to the `Course` that student is taking: a student can take only one course
- In each course, create a `Vector` of references to students: hard to find the courses taken by students
- Create a `Takes` association class that contains an attribute for `Student` and `Course`: extra step involved in each query
- Use symmetric `Vectors` in `Student` and `Course`: referential integrity maintenance

### Modeling To Implementation Quiz

_Match each OOA modeling concept (provided in lecture) with a Java concept that might be used for its implementation_.

- Generalization: sub-classing
- Aggregation: collection classes
- Invariant: methods and constructors
- State: enumerations

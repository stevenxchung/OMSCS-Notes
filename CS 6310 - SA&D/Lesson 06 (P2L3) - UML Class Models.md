# Lesson 6

In this lesson, we will cover how to express the results of OOA using **UML (Unified Modeling Language)**. We will mainly be focusing on the Class Model Diagram (also called Static Structure Diagrams) which is the most popular and most complex of the diagrams (although there is no need to use all of its features). This type of diagram contains representations for:

- Classes
- Interfaces
- Objects
- Relationships

## Classes

**Classes** are a description of a similar set of instances. Candidates for classes include:

- Domain objects
- Roles
- Events
- Relationships

Nouns are good candidates. Classes are typically represented by a rectangle and are broken down into three parts:

1. Class name
2. Attributes
3. Operations

## Name Compartment

The class name should be a noun. On the other hand, abstract classes describe properties of subclasses and should never have their own instances.

Q: Why use an abstract class?
A: We can factor related classes with common features up to the abstract class.

Other affordances include stereotypes which extend base UML.

## Class Features

Classes have features e.g., attributes and operations. While classes exist in the real world, features exist inside the computer. For class features:

- Attributes are implemented by instance variables
- Operations are implemented by methods

## Attributes Compartment

Attributes include symbols for visibility:

- Public: `+`
- Private: `-`
- Protected: `#`
- Package: `~`

Attributes can also include:

- Name
- Type
- Optional multiplicity and ordering
- Optional initial value
- Optional derivation

## Operations Compartment

The operations compartment is similar to the attributes compartment. It includes a parameter list which may highlight:

- Name
- Type
- Default value
- Kind

There are also properties:

- Query (expressed by `{}`)
- Concurrency (expressed by `{}`)
- Abstract (expressed by `{}`)
- Class scope (shown by underline on the operation name)

## Advanced Features

Advanced features for class models include:

- Interfaces: icons for requires and provides
- Parameterized classes: describe collection classes
- Nested classes: suitable for inner classes
- Composite objects: class diagrams within class rectangles

## Relationships

Verbs describe relationships. There are three types of relationships in UML:

1. Association
2. Generalization
3. Dependency

## Associations

For associations, we can have:

- Name
- Association classes
- Aggregation or composition

## Association Class

Association the has some class properties e.g., attributes

## Aggregation And Composition

Aggregation association is to show that an instance of one class is made up of instances of another class. Aggregation does not say much about the lifetimes of the participant objects.

## Qualifiers

Another refinement of associations is qualifiers. Qualifiers are indicated by small rectangles that are on the sides or edges or class rectangles.

## Links

Just like classes can have instances, associations can have links.

## Generalizations

The second way to indicate a relationship is through generalizations. Generalizations are indicated by a solid line but ends with a triangle.

All instances of the subclass are also instances of the parent class (there is a subset relationship such that **the properties of the subclass have to have all of the properties of the parent class**). Note that generalizations are not the same as inheritance in OOP (object-oriented programming).

## Summary

UML provides a rich vocabulary for modeling system structure. However there is no need to use all of its affordances.

## Section Quizzes

### Abstract Class Quiz

_Fill in the following text boxes for an abstract vehicles class:_

- Subclasses: car
- Attributes: VIN
- Operations: carry passengers

### Class Description Quiz

_For 'Name': Enter a single word answer into the text box. For 'Attributes' and 'Operations', provide comma-separated answers._

- Name: Account
- Attributes: Current balance
- Operations: Deposit

### Aggregation & Composition Quiz

_For the pairs of classes, select whether the each is a composition, an aggregation, or a general association._

- Courses and students: aggregation
- Person and spouse: general associations
- Bank account and patron: aggregation
- Fonts and glyphs: composition

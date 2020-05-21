# Lesson 2

> Design is better learned than taught

## TextBrowser Exercise

There are several of elements for the TextBrowser:

1. **FileManager**:

   - Some way to access the file's contents
   - Provide a module that can retrieve a limited length, consecutive subsequence of the file's lines

2. **ViewPort**: need to be able to display the textual content graphically
3. **ScrollBar**: need to give the user some way to access different parts of the file

## Analysis Model

The analysis model will consist of various parts:

- UML class-model diagram
- Rectangles for classes
- Each rectangle is divided vertically
- Lines between the components denote relationships

## Operations

Operations comprise those actions that the user can undertake to interact with the TextBrowser.

## Relationships

In a UML analysis model, you should be concerned with three types of relationships:

1. Associations
2. Aggregations
3. Generalizations

## Summary

What is the key design question with which any implementation of the TextBrowser must deal?

## Section Quizzes

### GUI Elements Quiz

_Assume that you had a GUI library, such as Swing or SWT. At a minimum, what atomic GUI components would you need to build your TextBrowser?_

- Window
- Scroll bar

### Use Cases Quiz

_What use cases apply for the TextBrowser application?_

We can read text, move handle, and adjust view port size.

### Classes Quiz

_Create a diagram with classes for the three components that we have already identified:_

- Name: ViewPort
  - Attributes:
  - Operations:
- Name: ScrollBar
  - Attributes:
  - Operations:
- Name: FileManager
  - Attributes:
  - Operations:

### Operations Quiz

_Add the two externally visible operations, `resizeViewPort` and `moveHandle`, to the correct classes within the diagram._

- Name: ViewPort
  - Attributes:
  - Operations: resizeViewPort
- Name: ScrollBar
  - Attributes:
  - Operations: moveHandle
- Name: FileManager
  - Attributes:
  - Operations:

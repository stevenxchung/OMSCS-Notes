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

### Visible Attributes Quiz

_We must translate what the user can see in the GUI into explicit attributes. We call these attributes percepts. Can you think of what those percepts should be (for the TextBrowser)?_

Text, size of the handle, handle position, and size of the view port.

### Relationships Quiz

_In our TextBrowser, what components are affected by the two user actions `moveHandle` and `resizeViewPort`? Indicate the components involved (check all that apply) for each action and describe the relationship._

- When `moveHandle` is triggered, the ScrollBar position will be updated where what the user sees will also have to be updated via ViewPort. To obtain this information, we will need to use the file manager
- When `resizeViewPort` is triggered, the ViewPort will be resized where the ScrollBar size will adjust as well. To obtain new lines, we will need to use the file manager

### Number Of Lines Quiz

_At any given moment in time, what is the number of lines actually displayed in the ViewPort as a function of the window's size and the number of lines in the file?_

`numberOfLinesDisplayed = minimum(windowSize, numberOfLinesInFile)`

### Another Association Quiz

_LinesVisible indicates the contents of the ViewPort that must come from the FileManager. Those lines are determined by the position of the ScrollBar handle. How might this be expressed?_

`linesVisible` = from `topPositionHandle` to (`topPositionHandle` + `windowSize`)

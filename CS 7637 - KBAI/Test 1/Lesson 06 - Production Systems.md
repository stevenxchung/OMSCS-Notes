# Lesson 6

We will discuss **production systems** in this lesson. Production systems are a kind of cognitive architecture in which knowledge is represented in the form of rules. This is the last topic under the fundamental topics. We will also cover the following:

- Cognitive architectures
- Production systems
- Chunking

## Function Of A Cognitive Architecture

A **cognitive agent** is a function that maps a perceptual history into an action.

## Levels Of Cognitive Architecture

There are various levels of cognitive architecture:

- Low: hardware/implementation level (e.g., brain, transistor)
- Medium: algorithm/symbol level (e.g., means-ends analysis, semantic networks)
- High: task/knowledge level (e.g., selecting a pitch, playing baseball)

The lower levels provide an _architecture_ for higher levels and the higher levels provide _content_ for lower levels.

## Assumptions Of Cognitive Architectures

There are several of assumptions for cognitive architectures:

1. Goal-oriented
2. Rich, complex environment
3. Significant knowledge
4. Symbols and abstractions
5. Flexible and function of the environment
6. Learning

## Architecture, Content, and Behavior

In general, it could be said that `architecture + content = behavior`. Suppose that our architecture is fixed, then the behavior of agents could be directly mapped to the knowledge content.

## A Cognitive Architecture For Production Systems

The **SOAR** architecture is one of the architectures for deliberation (recall the diagram of a cognitive system from the first lesson). SOAR can also cover certain aspects of reaction as well as meta-cognition.

SOAR consists of long-term memory and a working memory, where long-term memory contains different kinds of knowledge:

1. **Procedural**: has to do with how to do accomplish certain tasks (e.g., how to cook a specific dish?)
2. **Semantic**: includes generalizations in the form of concepts and models of the world (e.g., how does food get its flavor?)
3. **Episodic**: includes specific events (e.g., what did you cook last weekend?)

## Chunking

Referring to our baseball example, what if we have two rules that the SOAR agent cannot decide on? The agent will attempt to draw from the episodic knowledge to decide what rule should be used. This process of drawing from previous knowledge to fulfill a goal or make a decision when two or more decisions are presented is called **chunking**.

## Fundamentals Of Learning

The theory of reasoning states helps us address questions such as:

1. What to learn?
2. When to learn?
3. Why do we learn?
4. How do we learn?

We start with reasoning first then work backwards to learning. This occurred for our production system with the baseball example. When the logic was blocked, the system had to refer to its episodic knowledge into order to fulfill the goal.

## Section Quizzes

### Levels Of Architectures Quiz

_What are the layers of Watson_?

1. The physical computer
2. Searching and decision-making
3. Answering the inputted clue

### Production System In Action I Quiz

_What operator is selected (provided)_?

Intentional walk based on the goal, _r1_ then _r3_ is activated.

### Production System In Action II Quiz

_What operator is selected (provided)_?

Throw curve-ball based on the goal, _r1_ is skipped then _r2_ is activated which leads to _r5_.

### Production System In Action III Quiz

_What operator is selected (provided)_?

None since the goal is to pitch (_r2_ -> _r4_ -> _r5 or r6_) but the system cannot decide between _r5 or r6_.

### Chunking Quiz

_What operator is selected (provided)_?

Throw curve-ball since _r8_ will dismiss _r6_.

### Final Quiz

_What did you learn in this lesson_?

- Generally, `architecture + content = behavior` and if the architecture is fixed then the behavior will be based on the knowledge content
- SOAR architecture in this lesson covered deliberation in the cognitive model which depicts agents having working memory and the ability draw three different kinds of knowledge: procedural, semantic, and episodic
- Production systems were initially purposed as a model for human cognition (e.g., working memory translates to short-term memory for humans) but human cognition are much more complex than architectures like SOAR which mainly captures cognition in a closed-world environment

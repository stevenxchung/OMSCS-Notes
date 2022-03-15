# Lesson 14

In this lesson we will examine an intelligent agent's _understanding_ of events and stories in the world which will build on our frame concepts. We cover the following:

1. Thematic role systems
2. Ambiguity
3. Constraints

## Thematic Role Systems

A **thematic role system** is a type of frame representation system where the frame represents an action or event identified by a verb. In these frames, the verb is able to establish expectations about the roles that are connected to that particular event.

Consider the following sentence:

> Ashok made pancakes for David with a griddle

The frame representation could be as follows:

Thematic Role:

- Verb: make
- Agent: Ashok
- Beneficiary: David
- Thematic object: pancakes
- Instrument: griddle

This frame will allow us to draw inferences which will allow an agent to understand the meaning of the sentence.

## Constraints

**Constraints** also allow an agent to understand the meaning of a sentence. Below are some prepositional constraints:

| Preposition | Thematic Roles              |
| ----------- | --------------------------- |
| by          | agent, conveyance, location |
| for         | beneficiary, duration       |
| from        | source                      |
| to          | destination                 |
| with        | co-agent, instrument        |

## Resolving Ambiguity In Prepositions

However, there may exist ambiguity in sentences such as below where the word _by_ has different thematic roles:

> That was written by Ashok.
> David went to New York by train.
> David stood by the statue.

How to resolve these issues? The agent should have an _ontology_ of the world. That is, it has a conceptualization or model of the world (in lecture it looks like a tree with multiple branches) such that it is able to determine which thematic role _by_ takes in each sentence above.

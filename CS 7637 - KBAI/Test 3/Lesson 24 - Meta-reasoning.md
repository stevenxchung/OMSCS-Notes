# Lesson 24

In this lesson we discuss **meta-reasoning** which is thinking about thinking (or knowledge about knowledge). Meta-reasoning is not concerned about an agent reasoning to determine an output to the world. Instead, meta-reasoning focuses on an agent's own internal knowledge, reasoning, and learning. We will cover the following:

1. Mistakes in knowledge, reasoning, and learning
2. Gaps in knowledge and reasoning
3. Strategy selection and integration
4. Meta-meta reasoning?
5. Goal-based autonomy

## Mistakes In Reasoning And Learning

Meta-reasoning allows an agent to explore the following:

1. How was this particular knowledge learned?
2. What was wrong in the learning process that led to that particular error?
3. How to fix the learning process such that the same mistakes are not made again?

## Beyond Mistakes: Knowledge Gaps

While an agent might discover an error (_incorrectness_) in the knowledge, reasoning, or learning, the agent should also consider gaps (_incompleteness_) in the knowledge, reasoning, or learning.

Gaps allow an agent to trigger a search (or spawn a goal) to find the link which will enable connection between concepts. The ability to spawn learning goals and find a way to achieve learning goals is another aspect of meta-cognition.

## The Blurred Line Between Cognition And Metacognition

The lines between deliberation (cognition) and metacognition are actually quite blurred as a considerable amount of processes overlap. In terms of KBAI, we should not be overly concerned about whether some processes occur in the deliberation or metacognition space. Instead, we should focus on:

1. What is the content that is needed for an agent to carry out a process?
2. What is the process that the agent needs to carry out?

## Strategy Selection

**Strategy selection** is facilitated by metacognition. Recall that some examples of reasoning strategies or methods are:

- Case-based reasoning
- Analogical reasoning
- Constraint propagation
- Planning
- Generate and test
- Problem reduction
- Means-ends analysis

Also recall that some examples of learning strategies or methods are:

- Explanation-based learning
- Learning by recording cases
- Incremental concept learning
- Classification
- Version spaces

Given a problem, the agent's metacognition selects a strategy based on the following criteria:

1. The agent will select an method based on knowledge of the world
2. If knowledge exists for competing methods, the agent must select the method which satisfies the most criteria for the given problem
3. The agent may evaluate the quality of solutions as well to select the proper strategy

## Strategy Integration

**Strategy integration** allows an agent to shift to another strategy when needed as the given problem evolves.

## Process Of Meta-reasoning

Metacognition could be used to:

1. Fix errors in knowledge, reasoning, or learning
2. Fill gaps in knowledge, reasoning, or learning
3. Strategy integration

However, what is the process or strategy that metacognition uses? Metacognition can use the **same** processes and strategies that deliberation uses. In this way, an agent can achieve _goal-based autonomy_ as metacognition is able to provide continuous robustness and flexibility by allowing an agent to achieve new goals.

## Section Quizzes

### Meta-meta Reasoning Quiz

_Is this (diagram provided) a good way to think about levels of metacognition_?

No, because each level of metacognition is conceptually identical, so they are better represented as self-referential.

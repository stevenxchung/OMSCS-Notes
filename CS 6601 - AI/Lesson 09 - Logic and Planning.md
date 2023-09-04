# Lesson 9

In this lesson we cover planning in terms of AI. **Planning** is the study and process of finding appropriate actions for an agent. Consequently, planning could be thought of as the core of all AI techniques we have examined so far.

Previously, we examined search techniques such as A\* which is able to find an optimal path given a state space and problem description. However, these techniques only work when the environment is deterministic and fully observable. Planning allows use to relax some of those constraints.

We will also examine:

- [Resolution algorithnm](http://web.csulb.edu/~tebert/teaching/lectures/528/resolution/resolution.pdf) which allows inference of new knowledge given a knowledge base
- [Graphplan](https://en.wikipedia.org/wiki/Graphplan) which allows planning to be practical for a whole new range of problems
- [Value iteration](https://en.wikipedia.org/wiki/Markov_decision_process#Value_iteration) which is a key part of MDPs

## Logic

**Logic** is a way of describing the world. When we make logical statements we capture part of what we want to know about the world and ignore other parts (any description is only partial). However, once we have made some statements about the world we could then reason completely within the logic without having to go back to reference the world to come to some conclusions (guaranteed as long as the description is an accurate representation of the world).

Historically, researchers have designed AI only in boolean logic. However, as we have learned in this class so far, the world is uncertain and therefore it is much more accurate to represent the world with probability logic.

Today, researchers have AI learn about the world from data instead of hard-coding rules since writing rules by hand is much more laborious that aggregating data from the world.

Examples of logic problems include:

- FedEx planning deliveries of all it's packages using it's fleet of vehicles
- The most optimal location to place a supply base during a war

Current exploratory domains include:

- Learning by examples
- Transfer of learning across domains
- Interactive planning (human and machine planning)
- Problem explanation

## AI Complexity And Uncertainty

So far we have talked about how AI can manage complexity and uncertainty with techniques from the following domains:

- Search: discover sequences of actions to solve problems
- Probability: represent and reason with uncertainty
- Machine learning: iteratively learn and improve

AI is dynamic and complex because it involves increasing complexity in at least three key areas:

1. **Agent design**: reflex-based agents and move into goal-based agents
2. **Environmental complexity**: simple case to partially observable, stochastic actions, multiple agents, etc.
3. **Representation**: the agent's model of the world becomes increasingly complex

## Propositional Logic

A propositional logic statement is only true or false with respect to the model of the world where the model is a set of true or false values for all the propositional symbols (e.g., events $A$, $B$, $C$, etc.).

Relevant connectors include:

- `OR`: $\bigvee$
- `AND`: $\bigwedge$
- `NOT`: $\neg$
- _Implies_: $\Rightarrow$
- _If and only if_: $\Leftrightarrow$

The _truth_ of a sentence can be defined in terms of the truth of the symbols with respect to the models using truth tables as follows:

| $P$   | $Q$   | $\neg P$ | $P \bigwedge Q$ | $P \bigvee Q$ | $P \Rightarrow Q$ | $P \Leftrightarrow Q$ |
| ----- | ----- | -------- | --------------- | ------------- | ----------------- | --------------------- |
| False | False | True     | False           | False         | True              | True                  |
| False | True  | True     | False           | True          | True              | False                 |
| True  | False | False    | False           | True          | False             | False                 |
| True  | True  | False    | True            | True          | True              | True                  |

There are different types of propositional sentences:

- **Valid**: true in every possible model for every combination of values of the propositional symbols
- **Satisfiable**: true in some moles but not necessarily for all models
- **Unsatisfiable**: false for all models

Limitations of propositional logic include:

- Cannot handle uncertainty (or probabilities)
- Cannot talk about objects which have properties (e.g., size, weight, color, etc.)
- No shortcuts to talk about many events occurring simultaneously

## First-order Logic

First-order logic resolves the two issues of propositional logic (cannot handle objects or talk about many events). We can compare both as follows:

- First-order logic:
  - World: includes relations, objects, and functions with respect to the world
  - Belief: the output can be true, false, or unknown
- Propositional logic:
  - World: includes only facts about the world
  - Belief: the output can be true, false, or unknown
- Probability theory:
  - World: includes only facts about the world
  - Belief: can be any real number $[0, 1]$

There are various ways to represent our world as we have seen:

- **Atomic**: representation of a state is just an individual state (no internal components as in search problems)
- **Factored**: representation of an individual state of the world is factored into several variables (e.g., events $A$, $B$, $C$, etc.)
- **Structured**: representation of an individual state with a set of values for variables as well as relationships between objects, branching structures, etc. (e.g., relational databases)

The syntax of first-order logic is as follows:

- Sentences: composed of atomic sentences (predicates corresponding to relations, e.g., `above(a, b)`)
- Terms: describes objects and includes constants, variables, and functions
- Quantifiers:
  - _For all_: $\forall$ (typically goes with a conditional statement about an object)
  - _There exists_: $\exists$ (typically goes with just an object and not a conditional statement)

Note that first-order logic relations are only on objects and **not** relations (which would be higher-order logic).

## Solving PL And FOL Problems

**Note**: this section is from the [Stanford CS221 lectures on first-order logic](https://youtu.be/_Iz83hfkFds?t=1100) which I felt did a better job of covering how to actually solve propositional logic and first order logic problems with the resolution algorithm as well as covering [CNF (conjunctive normal form)](https://en.wikipedia.org/wiki/Conjunctive_normal_form) tricks.

Recall the logic identities we may use when solving logic problems (see AIMA Chapter 7, Figure 7.11 for more logic identities):

- $p \Rightarrow q$ is equivalent to $\neg p \bigvee q$
- $\neg (p \bigwedge q)$ is equivalent to $\neg p \bigvee \neg q$ (via [de Morgan's law](https://en.wikipedia.org/wiki/De_Morgan%27s_laws))
- $\neg (p \bigvee q)$ is equivalent to $\neg p \bigwedge \neg q$ (via de Morgan's law)

The rewritten form of [modus ponens](https://en.wikipedia.org/wiki/Modus_ponens) is given as: 

$\frac{A, \neg A \bigvee C}{C}\\$

Which leads us to the [resolution inference rule](http://logic.stanford.edu/intrologic/notes/chapter_05.html) where $A$ and $\neg A$ cancel out.

However, resolution inference only works on clauses. The good news is, we may convert any propositional logic or first-order logic (although requiring a few more steps - namely unification and substitution - than propositional logic) into an equivalent CNF formula. Consider the following example:

Given $(Summer \Rightarrow Snow) \Rightarrow Bizzare$:

1. Remove implication $\Rightarrow$: $\neg (\neg Summer \bigvee Snow) \bigvee Bizzare$
2. Push $\neg$ inwards (via de Morgan's law): $(\neg\neg Summer \bigwedge \neg Snow) \bigvee Bizzare$
3. Remove double $\neg$: $(Summer \bigwedge \neg Snow) \bigvee Bizzare$
4. Distribute $\bigvee$ over $\bigwedge$: $(Summer \bigvee Bizzare) \bigwedge (\neg Snow \bigvee Bizzare)$

For a more general conversion rules see the [Stanford CS221 first-order logic lecture at this timestamp](https://youtu.be/_Iz83hfkFds?t=1830).

We can combine CNF and the resolution inference rule to come up with a resolution algorithm as follows:

- Add $\neg f$ (formula) into $KB$ (knowledge base)
- Convert all formulas into CNF
- Repeatedly apply resolution inference rule
- Return entailment ($KB$ entails $f$) $\Leftrightarrow$ we derive false (e.g., $\neg A$ eliminates $A$)

In general, [Horn clauses](https://en.wikipedia.org/wiki/Horn_clause) can make use to _modus ponens_ to solve logic problems in _linear_ time but they are _less_ expressive. All clauses may use _resolution_ to solve logic problems in _exponential_ time but they are _more_ expressive

The above methods may extend to first-order logic. Identities for first-order logic include:

- Conjunction $\forall x P(x)$ is equivalent to $P(A) \bigwedge P(B) \bigwedge ...$
- Disjunction $\exists x P(x)$ is equivalent to $P(A) \bigvee P(B) \bigvee ...$
- $\neg \forall x P(x)$ is equivalent to $\exists x \neg P(x)$
- $\forall x \exists y Knows(x, y)$ is **not** equivalent to $\exists y \forall x Knows(x, y)$$

Recall that we first-order logic allows more expressiveness via $\forall$ and $\exists$ quantifiers (note the different connectives $\Rightarrow$ and $\bigwedge$). For instance:

- _Every student knows arithmetic_:
  - $\forall x Student(x) \Rightarrow Knows(x, arithmetic)$
- _Some student knows arithmetic_:
  - $\exists x Student(x) \bigwedge Knows(x, arithmetic)$

A useful trick for first-order logic is using [unification and substitution](https://youtu.be/_Iz83hfkFds?t=3730) which takes two formulas $f$ and $g$ and returns a substitution $\theta$ which is the most general unifier. For instance, focusing on variables $alice$ and $x$ in an example:

$Unify[Knows(alice, arithmetic), Knows(x, arithmetic)] = \{x/alice\}$ where $\theta = \{x/alice\}$.

## Planning Problems

We typically have to interleave planning and execution due to the following properties of real-world environments:

- **Stochastics**: we cannot know for sure what any particular action is going to do
- **Multi-agent**: we have to react to other agents in the environment which can only occur during execution and not planning
- **Partial observability**: we cannot know for sure what state we are in when we start off until we get to a particular state

Additionally, we can encounter:

- Unknowns: knowledge regarding some parts of the world are incomplete
- Hierarchical planning issues: we can only plan at a high-level and the lower-level details only occur during execution

However, most of these issues above can be addressed by shifting the point-of-view from _world_ states to _belief_ states (e.g., if a sensor malfunctions and we can know longer sense the world, we should navigate based on incremental beliefs).

Note that is possible to construct a plan that reaches a goal without ever observing the world via [conformant planning](https://arxiv.org/ftp/arxiv/papers/1401/1401.3468.pdf) which determines a goal when the initial situation is not fully known and actions may have non-deterministic effects.

## Planning As Belief State Space

The _act-observe cycle_ differs depending on the world:

- **Deterministic and partially observable**:
  - Act: each individual belief state maps into exactly another belief state (the size of the belief state remains the same or decreases)
  - Observe: partition the current belief into pieces for new observations (observations alone cannot introduce a new world state into the belief state)
- **Stochastic and partially observable**:
  - Act: results of actions are always larger than they were before due to uncertainty (increase uncertainty)
  - Observe: observations still partition current belief into pieces (decrease uncertainty)

Any plan that works in the deterministic world might work in the stochastic world but there are no guarantees with a finite set of actions. However, it is possible to represent an infinite number of moves via tree structure where we can say that as the limit approaches infinity, the goal state is guaranteed to be found.

## Classical Planning

**Classical planning** is a representation language for dealing with states, actions, and plans. It is also an approach for dealing with the problem of complexity by factoring the world into variables.

Under classical planning:

- State space: consists of all the possible assignments to $k$ boolean variables ($2^k$ states)
- World state: consists of a complete assignment (true or false) to each of the variables (states)
- Belief state: depends on the problem
  - Complete assignment: useful when dealing with deterministic and fully observable domains
  - Partial assignment: useful when some variables have values while other variables do not
  - Arbitrary formula: formula in boolean logic to represent any belief state

We also have to determine what actions and results look like which are typically represented in classical planning via _action schema_ which represents many possible actions that are similar to each other:

- `Action(action(), pre(), effect())`
  - `action()`: action operator based on the type of action
  - `pre()`: preconditions that need to be true in order to execute `action()`
  - `effect()`: the effects of taking `action()`

How to do planning with the tools above? We can implement _progression state space search_ (forward search) which searches through the space of exact states where each state is an individual world state. Another way is through _regression search_ (backward search) which starts at a goal with a description of the goal state (many world states) and works backwards to the initial state by traversing backwards through possible actions (all possible actions).

Note that regression search can be much more efficient than progression search for some problems (e.g., trying to buy a book by ISBN where the ISBN is known).

## Plan Space Search

Instead of searching through the state space we can search through _plan space_ or search through plans. In general, we start off with a incomplete plan (initial plan) and incrementally refine our plan by adding on operators in between the initial and goal state (which is within the plan) with each step until a satisfactory plan is achieved.

However, this method is still not as popular as forward or backward search since we can use heuristics (provided we have good heuristics) with forward search techniques.

## Situation Calculus

Suppose we wanted to have the goal of moving all of the cargo from airport $A$ to airport $B$, regardless of how many pieces of cargo there are. In this problem, we cannot express the notion of _all_ in propositional languages such as classical planning but we can in first-order logic.

[Situation calculus](https://en.wikipedia.org/wiki/Situation_calculus) then is just a set of conventions for how to represent states and actions using first-order logic. The convention is as follows:

- **Actions**: represented by objects which correspond to states
- **Situation**: represented by objects which correspond to paths of actions we have in the state space search (e.g., $S_0$ and $S' = Result(S, A)$)
- **Predicate**: conditions that describe the state of the world
  - $Poss(A, S)$, where we have the actions $A$ possible in a state $S$
  - To describe the predicate we can have the form $Pre(S) \Rightarrow Poss(A, S)$

In classical planning we had action schemas where we describe one action at a time and what changed. However, in situation calculus we write one action schema for each _fluent_ (or predicate) condition that can change via _successor state axioms_.

Successor state axiom example: $\forall_{A, S} Poss(A, S) \Rightarrow (+fluent \Leftrightarrow +A \bigvee -A)$ where $+A$ is the action that caused $+fluent$ state and $-A$ is the action that did not undo $+fluent$ state.

Advantages of situational calculus include:

- Has all the functionality and tools of first-order logic to represent anything we want
- Once the problem is described in first-order logic we do not need any programs to come up with a further solution
- Can apply theorem provers for first-order logic (we can just state our logic as a problem) to find a path (situations) that satisfies the goal given initial states and descriptions of the actions

However, one weakness in all of these planning approaches is that we are not able to distinguish between probable and improbable solutions (planning under uncertainty).

## Section Quizzes

**Note**: will be somewhat limited for this semester.

### Truth Tables 1 Quiz

_Given the truth table and the following, are the statements true or false_?

- $O \Rightarrow P = True$, by propositional logic since 5 is an odd number (true) and Paris is the capital of France (true)
- $E \Rightarrow M = True$, by propositional logic since 5 is **not** and even number (false) and Moscow is **not** the capital of France (false)

### Truth Tables 2 Quiz

_Given the truth table, fill in the blanks_.

| $P$ | $Q$ | $P \bigwedge (P \Rightarrow Q)$ | $\neg (\neg P \bigvee \neg Q)$ | $(P \bigwedge (P \Rightarrow Q)) \Leftrightarrow (\neg (\neg P \bigvee \neg Q))$ |
| --- | --- | ------------------------------- | ------------------------------ | -------------------------------------------------------------------------------- |
| F   | F   | F                               | F                              | T                                                                                |
| F   | T   | F                               | F                              | T                                                                                |
| T   | F   | F                               | F                              | T                                                                                |
| T   | T   | T                               | T                              | T                                                                                |

### Propositional Statements Quiz

_Given the following propositional statements_:

$(E \bigvee B) \Rightarrow A\\$
$A \Rightarrow (J \bigwedge M)\\$
$B\\$

_Determine whether each symbol (event) is true, false or unknown_.

- $B$: True, by the third statement (given)
- $E$: Unknown, since the information given does not help us determine $E$
- $A$: True, by the first statement
- $M$: True, by the second statement
- $J$: True, by the second statement

### Propositional Sentence Quiz

_Given several propositional sentences (provided), determine if it is valid, satisfiable, or unsatisfiable_.

1. Valid, since we have an `OR` relationship
2. Unsatisfiable, since it can not be both true and false at the same time
3. Valid, since we have an `OR` relationship
4. Valid, since we have an `OR` relationship
5. Valid, since we have an `OR` relationship

### Atomic Sentence Quiz

_Given several first-order atomic sentences (provided), determine if it is valid, satisfiable, or unsatisfiable_.

1. Valid, since every model has to have at least one object
2. Valid, since the first and second statements are true
3. Valid, since we have an `OR` relationship
4. Satisfiable, since there _could_ be an $x$ in $P(x)$ but it is not required

### First-order Logic Quiz

_Given several first-order sentences (provided), determine if it correctly represents the problem_.

1. Yes, since the sentence is correct since we have $x$ representing one job and $y$ representing another job
2. No, this should require an $\Leftrightarrow$ such that we only know that this sentence holds true for particular cases
3. No, this should require an $\Leftrightarrow$ such that we only know that this sentence holds true for particular cases

### Planning 1 Quiz

_Given the belief state space diagram (provided) determine if the actions will lead to a goal all the time or sometimes_.

1. Maybe
2. Maybe
3. Maybe
4. Maybe

This is because any plan that works in the deterministic world might work in the stochastic world but there are no guarantees.

_Additionally, what is a plan that would always or sometimes achieve the goal_? Since we cannot have a finite number of moves guarantee a goal, the answer is any finite number of linear moves may work sometimes. While it is **not** possible to represent an infinite set of moves with a linear sequence, it is possible to represent an infinite number of moves via tree structure.

### Planning 2 Quiz

_Given a tree that represents a single plan. Determine the tree requirements to guarantee an unbounded and bounded (unbounded or bounded number of steps) solution_.

- Unbounded: we are guaranteed an unbounded solution if every leaf in the plan ends in a goal state
- Bounded: we can have branches but we **cannot** have any loops (since we have a finite number of steps)

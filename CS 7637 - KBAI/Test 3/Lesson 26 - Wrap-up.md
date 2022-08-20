# Lesson 26

In this lesson we will reflect on some of the main themes covered in this course and other upcoming themes and topics in the AI community. We will cover:

1. Major topics revisited
2. Principles of KBAI revisited
3. Modern KBAI research
4. Final thoughts

## Cognitive Systems Revisited

Recall our model of the cognitive system which can be broken down into three main spaces:

1. **Metacognition**: monitors the deliberative reasoning and acts on the deliberative reasoning. Can also monitor and act on itself as well
2. **Deliberation**: maps percepts into actions where mappings are mediated by reasoning, learning, and memory (_see, act, and think_ cycle)
3. **Reaction**: directly maps percepts from the environment into actions on the environment (_see and act_ cycle)

Each space may overlap with each other and are not disjoint in practice. _Metacognition_ acts primarily within the cognitive space while _deliberation_ and _reaction_ acts in the world. Additionally, the cognitive system is always situated in the world (cannot be separate from the world).

Also recall that intelligence is a function that maps perceptual histories into actions to the world. Depending on the input to the cognitive system, the output may vary:

- If input is a _goal_ -> output may be a _plan_ or _action_
- If input is _knowledge_ -> output may be learned and stored in _memory_
- If input is a _percept_ -> output may be an _action_ based on the percept

The _world_ is not just a physical world but a social world as well. Cognitive systems do not just monitor and observe the world but also inputs and outputs from other cognitive systems.

## Principles Of KBAI

We have covered several principles of KBAI in this course:

1. **Represent, organize, and reason**: KBAI agents represent and organize knowledge into knowledge structures to guide and support reasoning
2. Learning in KBAI agents is often incremental (KBAI agents do not learn a ton of information at once)
3. Reasoning in KBAI is top-down as well as bottom-up
4. KBAI agents match _methods_ to _tasks_ (as well as sub-methods to sub-tasks):
   - **Methods**: generate and test, means-ends analysis, problem reduction production systems, case-based reasoning, planning, analogical reasoning -> - **Tasks**: configuration, diagnosis, design, meta-reasoning, creativity, classification, systems thinking
5. KBAI agents use heuristics to find solutions that are good enough, though not necessarily optimal (due to computational tradeoffs)
6. KBAI agents make use of reoccurring patterns in the problems they solve
7. The architecture of KBAI agents enables reasoning, learning, and memory to support and constrain each other

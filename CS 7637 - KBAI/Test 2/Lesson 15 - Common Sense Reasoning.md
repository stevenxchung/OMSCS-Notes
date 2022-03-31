# Lesson 15

In this lesson we will examine how we could make an AI agent have common sensical inferences about the world. This wil involve pulling concepts from frame representation. We will also cover the following:

1. Primitive actions
2. Actions and sub-actions
3. State changes

## Primitive Actions

We can start examining how an AI agent might interpret very structurally different sentences that have the same meaning by noting **primitive actions**. These set of basic actions (e.g., move-body-part, move-object, etc.) could help an agent interpret a message as each primitive action has a frame representation associated with it which allows for stereotyping.

## Thematic Roles And Primitive Actions

As mentioned earlier, an agent may map actions in a sentence to a store containing primitive actions. These primitive actions may be represented in a thematic role frame which will allow the agent to perform top-down processing(generating expectations and interpretations).

## Implied Actions

Oftentimes a sentence might be difficult to interpret because the action does not readily map to any primitive action. In this scenario an agent might modify the sentence such that it could map to a primitive action.

## Actions And Sub-actions

What knowledge must an AI agent have such that it could make common sense inferences? Referring back to the thematic role frames, we would add to the frame not only the primitive action, agent, and object but also sub-actions.

## State Changes

A **state-change frame** may highlight different events that may occur in a given sentence. This may be inserted into a thematic role frame as a result (e.g., the result of _Ashok ate a frog_ may contain a state-change frame representing the result: _Ashok is happy_)

## Implied Actions And State Changes

Sometimes a sentence might be vague (e.g., _Susan comforted Jing_) and so the best we can do with primitive actions, thematic role frames, and state-change frames is to generalize an action.

## Actions And Resultant Actions

Thematic role frames are not limited to chaining results to state-change frames but also results to another thematic role frame (action result to another action). This is useful for sentences which contain more than one action (e.g., _Maria told Ben to throw the ball_).

## Section Quizzes

### Primitive Actions Quiz

_Write the primitive action that subsumes the verbs in the following sentences (given)_.

1. Ran
2. Pushed
3. Took
4. Ate

### Roles And Primitive Actions Quiz

_Write the action frame corresponding to the above sentence (given) using a primitive action_.

1. Move-possession
2. John
3. Mary
4. Book

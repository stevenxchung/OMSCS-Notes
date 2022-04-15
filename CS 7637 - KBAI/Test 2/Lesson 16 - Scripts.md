# Lesson 16

In this lesson we cover another knowledge representation known as _scripts_ which allow us to make sense of discourses, stories, and scenes using previous concepts (e.g., frames, understanding, and common sense reasoning). We will cover the following:

1. Defining scripts
2. Form vs. content
3. Generating expectations
4. Hierarchies of scripts

## Story Understanding For AI Agents

Stories can help agents make sense of the world and generate expectations. Stories also allows an agent to make connections between events that otherwise might appear separate.

## Definition Of Scripts

A **script** is a knowledge representation for capturing a causally coherent set of events. There are three parts to this definition:

1. **Causally**: each event sets off or causes the next event
2. **Coherent**: the causal connections between events make sense
3. **Events**: the parts are actions or scenes in the world

## Parts Of A Script

There are six parts to a script:

1. **Entry conditions**: conditions necessary to execute the script
2. **Result**: conditions that will be true after the script has taken place
3. **Props**: objects involved in the execution of the script
4. **Roles**: agents involved in the execution of the script
5. **Track**: variations or _sub-classes_ of the particular script
6. **Scenes**: the sequence of events that occurs during execution of the script

## Using A Script To Generate Expectations

A script can be used to generate expectations since a script may generate a chain of thematic role frames (a scene) which captures a causally coherent set of events. If any of the events in the scene do not occur the agent will know that the outcome is unexpected.

These types of surprises lends itself to the theory of creativity where a situation is creative if it is:

1. Novel
2. Useful or valuable
3. Unexpected or surprising

## Tracks

For each script, there may be different _tracks_ i.e., for a script that is written for _going to a restaurant or food establishment_ there may be a script for going to a coffeehouse, fast food, causal dining, formal dining, etc. Additionally, there may also be a higher level of abstraction for these events, e.g., _going to different types of social events_ not just restaurants.

## Learning A Script

The following prior topics may help an agent learn a script:

- **Semantic networks**: can help an agent store knowledge in the form of structured representation
- **Frames**: same as semantic networks but the structure for storing information is different
- **Incremental concept learning**: an agent which constantly interacts with the world could use this technique to develop a categorization scheme for different experiences
- **Planning**: can help an agent realize a path from initial state to the goal state and translate that path into a script such that the same script could be used for other scenarios
- **Common sense reasoning**: can help an agent process a script with primitive actions

## Using A Script

The following prior topics may help an agent use a script:

- **Problem reduction**: this technique can help an agent break down a scene into smaller scenes (collection of frames) and actions such that exceptions and violations are caught
- **Classification**: can help an agent determine what script to use given a particular situation
- **Logic**: since a plan can discussed in formal logic an agent could use this technique to determine what the script asserts about the state of the world at certain points of execution
- **Understanding**: can help an agent disambiguate similar events in different situations

## Section Quizzes

### Final Quiz

_What did you learn in this lesson_?

- Stories can help agents make sense of the world and generate expectations. This possible as scripts are a knowledge representation for capturing a causally coherent set of events
- Some theories say that our brain is a predictor machine. We do quick bottom-up processing followed by top-down processing. We also generate expectations of the world and then act on those expectations
- One of the questions is _do we carry these scripts in our head or do we generate them at runtime_?
- Scripts are analogous to mental models and are culturally specific (e.g., the script for tipping in the US is different than in other countries)

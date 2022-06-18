# Lesson 23

Another method of learning is _learning by correcting mistakes_. We will also cover the following:

1. Explanation-based learning revisited
2. Isolating mistakes
3. Explaining mistakes
4. Correcting mistakes

## Questions For Correcting Mistakes

How might an agent learn to correct its mistakes? There are three relevant follow-up questions to determine:

1. How can the agent isolate the error in its former model?
2. How can the agent explain the problem that led to the error?
3. How can the agent repair the model to prevent the error from recurring?

The problem of identifying the error in one's knowledge that led to a failure is called **credit assignment** (or _blame assignment_). This assignment is concerned about: when a failure occurs, what _gap_ in one's knowledge was responsible for the failure?

Generally an error could be in one's reasoning or architecture. Some experts consider credit assignment to be the central problem in learning since the world is dynamic and so what is learned today will need to be re-learned tomorrow.

## Visualizing Error Detection

Generally, errors for agents may lie in:

1. Knowledge
2. Reasoning
3. Architecture

In this class, we will be focusing primarily on errors in _classification knowledge_.

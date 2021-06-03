# Lesson 15

The **agile development process** (also known as **test driven development** or **TDD**) is a software development process which is heavily based on testing. We will also look into two principles of agile software development commonly used in practice:

1. XP (extreme programming)
2. Scrum

## Cost Of Change

In waterfall development processes the cost of change grows exponentially with time. How to combat this issue? Back in the day, one way was to discover errors early with upfront planning.

However, this was around 30 years ago, many things have changed since then and in general the software development process became much faster. Using modern tools, practice, and principles we might be able to _flatten_ out the curve for the cost of change over time.

## Agile Software Development

If cost is flat then upfront work becomes a liability and with ambiguity it may be good to delay, therefore there is value in waiting. There are six principles of agile software development that aim at flat cost:

1. Focus on the code
2. People over process
3. Iterative approach
4. Customer involvement
5. Expectation that requirements will change
6. Simplicity

## XP Extreme Programming

**XP** is a lightweight methodology for small to medium size teams developing software in the face of vague or rapidly changing requirements. XP focuses on four main key points:

1. Lightweight
2. Humanistic
3. Discipline
4. Software Development

Additionally, XP embodies the following values and principles:

1. Communication
2. Simplicity
3. Feedback
4. Courage

In practice, XP advocates for:

1. **Incremental planning**: which could be broken down into the following:
   1. Select user stories for release
   2. Break stories into tasks
   3. Plan release
   4. Develop, integrate, and test
   5. Release software
   6. Evaluate system and iteration
2. **Small releases**: there many advantages of small releases:
   1. Deliver value quickly
   2. Rapid feedback
   3. Sense of accomplishment for the developments
   4. Reduces risk
   5. Quickly adapt to new requirements
3. **Simple design**: which advocates for design that:
   1. Is enough to meet the requirements
   2. Includes no duplicated functionality
   3. Has the fewest possible classes and methods
4. **Test first**: write tests early before developing a feature
5. **Refactoring**: restructuring code such that code is more clean and simple
6. **Pair programming**: a technique that leverages two developers where one may take on the role of programming and one may take on the role of strategizing
7. **Continuous integration**: process that advocates for continuously checking the following:
   1. Local tests
   2. Integration tests
   3. System tests
8. **On-site customer**: the customer is an actual member of the team (not very common in practice)

## Testing Strategy

The testing strategy in agile is that testing is coded confidence. There are various types of tests we should implement for meaningful features and functionality:

- Unit tests
- System tests

## Scrum Intro

**Scrum** is another agile development process similar to XP. There are various kinds of actors in a scrum setup:

1. Product owner (customer): the person in charge of product intent
2. Team: group in charge of shipping features
3. Scrum master: the person in charge of overseeing the scrum processes and ensuring team fluidity

There are several of high-level scrum process:

1. Product backlog
2. Sprint planning
3. Sprint backlog
4. Daily scrum (iterative)
5. Sprint review and retrospective (iterative)
6. Potentially shippable product increment

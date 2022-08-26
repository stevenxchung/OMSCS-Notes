# Lesson 1

In this lesson we will examine a classic problem in AI and robotics: how to we determine a robot's position in an environment? This problem is also known as **localization**:

> ... the robot's ability to establish its own position and orientation within the frame of reference. -Wiki

## Total Probability

Imagine a robot is in a one dimensional world. Imagine a that robot has a map of the world and knows what a door looks like.

How might a robot determine where it is locally?

1. The robot starts out by not knowing where it is (it has a _belief_ modeled by _uniform maximum confusion_)
2. A robot can determine it's _posterior belief_ after measurements are taken of where possible objects are (e.g., doors)
3. When a robot moves, a _convolution_ of the posterior belief occurs a creates a _prior belief_
4. If we multiply the posterior belief with the prior belief, we get a brand new posterior belief that allows the robot to localize itself

This is the general idea of a [histogram filter](https://www.deepideas.net/robot-localization-histogram-filter/).

# Lesson 6

In this lesson we will examine how to combine the previous topics (localization, tracking, planning, control, probabilities, filters, A\*, DP, and PID control) to create a truly autonomous robot.

## Segmented CTE

During navigation, it is important to segment CTE since the robot paths are not
always straight. Segmenting CTE includes having the robot detect when the local environment (the track that the robot uses to compute CTE) changes. We can take into account environment change by comparing normalized vectors (as shown in lecture) and checking if the ratio is greater than one (indicating that the segment has changed).

## SLAM

**SLAM (simultaneous localization and mapping)** is a method that allows a robot to both determine its position and building a map of its environment.

## Graph SLAM

One of the techniques used to perform SLAM is [Graph SLAM](http://www2.informatik.uni-freiburg.de/~stachnis/pdf/grisetti10titsmag.pdf) which:

> constructs a simplified estimation problem by abstracting the raw sensor measurements. These raw measurements are replaced by the edges in the graph which can then be seen as “virtual measurements”.
> -G. Grisetti, R. Kummerle, C. Stachniss, W. Burgard

Since robot location is uncertain (as given by Kalman Filters), the localization problem must utilize the Gaussian uncertainties and sensor measurements (e.g., Gaussian product of x and y) to define probabilities using a sequence of these Gaussian uncertainties or constraints. Graph SLAM works by collecting three sets of constraints:

1. Initial location
2. **Relative motion** - robot poses (current and previous robot locations)
3. **Relative measurement** - sensed landmarks and specific locations

By collecting information on each of these constraints in real-time, the robot is able to perform SLAM and determine the most likely configuration of the robot path with landmark locations.

## Omega And Xi

Once we fill out the Graph SLAM matrix, how might we use the robot's initial location, relative motion, and relative measurement constraints to estimate the robot and landmark locations? If we define the _A matrix_ as $\Omega$ and the _B matrix_ as $\xi$, then we may determine the best estimate of the robot and landmark location ($\mu$) by:

$\mu = \Omega^{-1} \cdot \xi\\$

To account for uncertainties we multiply the $\Omega$ and $\xi$ by the strength $1/\sigma$ which is the measurement uncertainty _before_ computing $\mu$.

## Section Quizzes

### Localization Quiz

_Fill in the fields below (provided) with true or false. True is equivalent to selecting a radio button shown in the intro video_.

|                   | Multi-modal | Exponential | Useful For Robots |
| ----------------- | ----------- | ----------- | ----------------- |
| Kalman Filters    | False       | False       | True              |
| Histogram Filters | True        | True        | True              |
| Particle Filters  | True        | True        | True              |

### Planning Quiz

_Fill in the fields below (provided) with true or false. True is equivalent to selecting a radio button shown in the intro video_.

|                     | Continuous | Optimal | Universal | Local |
| ------------------- | ---------- | ------- | --------- | ----- |
| Breadth First       | False      | True    | False     | False |
| A\*                 | False      | True    | False     | False |
| Dynamic Programming | False      | True    | True      | False |
| Smoothing           | True       | False   | False     | True  |

### PID Quiz

_Fill in the fields below (provided) with true or false. True is equivalent to selecting a radio button shown in the intro video_.

|     | Avoiding Overshoot | Minimizing Error | Compensating Drift |
| --- | ------------------ | ---------------- | ------------------ |
| P   | False              | True             | False              |
| I   | False              | False            | True               |
| D   | True               | False            | False              |

### Is Localization Necessary Quiz

_When mapping an environment with a mobile robot, uncertainty in robot motion forces us to also perform localization_. True.

### Graph SLAM Quiz

_How many total constraints do you have, if you count each of the constraints as exactly one constraint_? 14 since there are 6 poses and 8 landmarks.

### Implementing Constraints Quiz

_What would the new values be for the matrix? Note: The 2x2 grid of input field below corresponds to the left area outlined in purple in the video, while the 1x2 grid corresponds to the right area outlined in purple (these can be seen in the image above)_.

The A matrix would contain:

| X1  | X2  |
| --- | --- |
| 2   | -1  |
| -1  | 1   |

While the B matrix would contain:

|     | Values |
| --- | ------ |
| X1  | 9      |
| X2  | -4     |

### Adding Landmarks Quiz

_Fill out the matrix and vector_.

The A matrix should be updated to:

|     | X0  | X1  | X2  | L0  | L1  |
| --- | --- | --- | --- | --- | --- |
| X0  | -1  | -1  |     |     |     |
| X1  | -1  | 3   | -1  | -1  |     |
| X2  |     | -1  | 1   |     |     |
| L0  |     | -1  |     | 1   |     |
| L1  |     |     |     |     |     |

While the B matrix should be updated to:

|     | Values |
| --- | ------ |
| X0  | 5      |
| X1  | 0      |
| X2  | -4     |
| L0  | 9      |
| L1  |        |

### SLAM Quiz

_Check the answers that apply to Graph SLAM_.

- All about local constraints
- They require additions

### Matrix Modification Quiz

_Which fields will be modified by Graph SLAM? Fill out the answer grid below corresponding to the cells in the matrix and vector_.

The A matrix should be:

|     | X0    | X1    | X2    | L     |
| --- | ----- | ----- | ----- | ----- |
| X0  | True  | True  | False | True  |
| X1  | True  | True  | True  | False |
| X2  | False | True  | True  | True  |
| L   | True  | False | True  | True  |

While the B matrix should be:

|     | Values |
| --- | ------ |
| X0  | True   |
| X1  | True   |
| X2  | True   |
| L   | True   |

### Untouched Fields Quiz

_Given the scenario, how many fields will never be touched_? 8 if we fill in the A and B matrix according to the given robot motion and landmarks.

### Landmark Position Quiz

_What is the landmark position_? We may determine the position by:

- Initial: -3 + 10 = 7
- Move 1: -3 + 5 + 5 = 7
- Move 2: -3 + 5 + 3 + 2 = 7

### Introducing Noise Quiz

_Given the scenario, answer the following_:

1. _After the modification, what is the effect on $X_2$_? $X_2 > 5$ since the landmark location decreased
2. _After the modification, what is the effect on $X_0$_? $X_0 = -3$ since the initial location is known

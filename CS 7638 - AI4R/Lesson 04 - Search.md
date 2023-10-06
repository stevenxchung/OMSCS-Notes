# Lesson 4

In this lesson we will examine how a robot performs motion planning with the goal of reaching a target location.

## Motion Planning

**Motion planning** is the process of finding a motion path from a start to goal location by breaking up the world into discrete chunks (as done in previous localization problems). The planning problem may be broken up as follows:

- Given:
  - Map
  - Start location
  - Goal location
  - Cost (e.g., the time it takes to drive a certain route)
- Goal: find the minimum _cost_ path

## A\*

The **A\* search algorithm** is:

> an informed search algorithm, or a best-first search, meaning that it is formulated in terms of weighted graphs: starting from a specific starting node of a graph, it aims to find a path to the given goal node having the smallest cost (least distance travelled, shortest time, etc.). It does this by maintaining a tree of paths originating at the start node and extending those paths one edge at a time until its termination criterion is satisfied. -Wiki

The A\* algorithm does better than the previous search algorithm discussed in class in that it utilizes a **heuristic function** (a table of values) which provides an optimistic guess of the number of steps it takes to get to the goal if there was no obstacle. The heuristic function may be represented as:

$H(x, y) \leq d$

Where $d$ is the distance to goal from (x, y). The search algorithm would now include:

- State (current location)
- g-value (steps moved)
- f-value (g-value plus heuristic value)

## Dynamic Programming

Because the world is stochastic, we may need other paths other than the most optimal path. Another search technique may leverage **dynamic programming** to find the best path from anywhere. The dynamic programming search problem may be broken up as follows:

- Given:
  - Map
  - Goal
- Goal: find the best path from anywhere

The dynamic programming search algorithm works by defining a **policy function** which maps discrete points in the world to an action. This allows a robot to have an optimal action at every discrete point in the world.

## Computing Value

Dynamic programming leverages the **value function** (a table of values similar to the heuristic function) to associate each grid cell with a length (shortest path to the goal). The value function is given as follows:

$f(x, y) = min_{x', y'} f(x', y') + c$

Where $min_{x', y'}$ is the nearest neighbor, $f(x', y')$ is the value, and $c$ is the cost to get to the goal. Once the value function is determined, we can obtain the optimal control action my minimizing the value.

## Section Quizzes

### Compute Cost 1 Quiz

_Given actions of moving forward and turning, in the discrete world defined above (provided, which has been divided into grid cells for convenience), how many steps does it take to reach the goal_? 7 steps since it takes 6 moves and 1 turn (which is also costly).

### Compute Cost 2 Quiz

_Using the same world as the previous question, but with the following action set, (provided, each with a cost of 1). How many steps does it take to reach the goal_? 6 steps since the problem specified that a turn and move is one step.

### Optimal Path 1 Quiz

_Using the same world as the previous questions, but with the following actions and costs, with a penalty applied to left turns (provided). What is the cost of the optimal path_? 15 steps since we penalize left turns more heavily but it is still more optimal than the other path (16 steps).

### Optimal Path 2 Quiz

_Using the same world as the previous questions, but with the following actions and costs, with a penalty applied to left turns (provided). What is the cost of the optimal path_? 16 steps since the penalty for left turns is very costly (20 steps).

### Maze 1 Quiz

_Given a different world from the previous questions in the maze shown above (provided), and a robot which can move as shown in each direction (up, left, right, down), how many steps does it take to reach the goal_? 7 steps.

### Maze 2 Quiz

_For this new given world (provided), what is the shortest number of actions (moving up, left, right, or down) to reach the goal_? 11 steps.

### Computing Value 1 Quiz

_What is the value of the grid square in the bottom right corner (provided)_? 15 steps.

### Computing Value 2 Quiz

_What is the value of the grid square in the bottom left (provided)_? 3 steps.

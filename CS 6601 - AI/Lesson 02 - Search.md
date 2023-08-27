# Lesson 2

In this lesson we will examine one of the most fundamental problems in AI - search. Specifically we will examine [A\*](https://en.wikipedia.org/wiki/A*_search_algorithm) search which is an efficient graph traversal and path search algorithm.

## Definition Of A Search Problem

A search problem may be broken down into the following parts:

1. **Initial** state: where an AI is initially located
2. **Actions**: set of possible actions given a state
   - E.g., $actions(s) \rArr {a_1, a_2, a_3}$
3. **Result**: resulting state after applying an action at a specific state
   - E.g., $result(s, a) \rArr s'$
4. **Goal test**: testing whether or not an AI is in the goal state or not
   - E.g., $test(s) \rArr T | F'$
5. **Path cost**: the total cost of any particular path from starting to end state
   - E.g., $path_{cost}(s_0 \rArr s_1 \rArr s_2) \rArr n$
   - **Step cost**: the cost of any particular step from starting to end state (so we can just sum up all the step costs to determine the cost of a path
     - E.g., $step_{cost}(s, a, s') \rArr n$

## Tree Search Algorithm

The pseudo-code for tree search (which is a family of algorithms which super-imposes the search tree of the state space) is as follows:

```python
def tree_search():
    frontier = self.initial_state
    while frontier not None:
        if frontier is None:
            return 'Fail'
        path = self.remove_choice(fronter)
        s = path.end
        if self.goal_test(s):
            return path
        # Otherwise, we expand the path if goal not found
        for a in self.actions(s):
            # Add [path + a -> result(s, a)] to frontier
            path += a + self.result(s, a)
            frontier.append(path)
```

**Note**: the _frontier_ means the latest visited node or the current state of the AI. However, the problem with tree search is that the paths have a possibility of going backwards.

## Graph Search Algorithm

To address the tree search algorithm going backwards we have to keep track of the explored states and so the algorithm then becomes a _graph search_ algorithm as follows:

```python
def graph_search():
    frontier = self.initial_state
    # Keep track of explored states
    explored = []
    while frontier not None:
        if frontier is None:
            return 'Fail'
        path = self.remove_choice(fronter)
        s = path.end
        explored.append(s)
        if self.goal_test(s):
            return path
        # Otherwise, we expand the path if goal not found
        for a in self.actions(s):
            # Only add unexplored states
            if self.result(s, a) not in explored and not in frontier:
                # Add [path + a -> result(s, a)] to frontier
                path += a + self.result(s, a)
                frontier.append(path)
```

**Note** graph search does **not** terminate when the goal state is added (the `goal_test()` is triggered only when we remove a path from the frontier) because it might not be the best path to the goal. However, this could be modified such that BFS terminates as soon as the goal is found by checking the goal state as soon as it is added to the frontier.

Another important note is that BFS can determine the least number of _steps_ (branches) to get to the goal but **not** the _minimum cost_ it takes to get to the goal.

## Uniform-cost (Cheapest-first) Search

How do we find the shortest path if BFS only yields the least number of steps? We can utilize the **uniform-cost (cheapest-first)** search whereby the path with the lowest cost is expanded first.

In general, if we want to find the goal faster, we need to add more knowledge via path estimates to the goal state. One algorithm to accomplish this may be _greedy best-first search_ but this is limited when there are barriers to the goal. This is where A\* comes into play.

## A\* Search

A\* achieves better performance than an algorithm like Dijkstra's by using _heuristics_ to guide its search. The A\* algorithm can be summarized into three main parts:

1. $f = g + h$, where $h$ is the heuristic function
2. $g(path) = path_{cost}$
3. $h(path) = h(s) = distance_{goal}$, where $distance_{goal}$ is an estimate

The function $f = g + hg$ allows A\* to find the shortest path while expanding the minimum number of paths possible.

**Note**: the heuristic function $h(s)$ will find the lowest cost path **only** if $h(s) < true cost$. Consequently, we never want $h$ to overestimate the goal (i.e., $h$ is optimistic and admissable).

## Search Problem Assumptions

Search works for problems which are:

- **Fully observable**: must be able to see the initial state
- **Known**: we have to know the set of actions available in the domain
- **Discrete**: there must be a finite number of actions to choose from
- **Deterministic**: we have to know the result of taking an action
- **Static**: there must be nothing else in the world that can change the world except our own actions

## Section Quizzes

**Note**: will be somewhat limited for this semester.

### Challenge 1: Tri-City Search Quiz

_How did Sally write her program such that it had minimal runtime and memory overhead_? None of the above, the preferred algorithm is a tri-directional A\* search.

### Challenge 2: Rubik's Cube Quiz

_Design a search algorithm for Rubik's Cube that guarantees the least number of moves required to finish from any starting state. We will consider each 1/4 (90-degree) turn to be a move_. Iterative deepening A\* is the preferred algorithm.

### BFS Vs. DFS Vs. CFS Optimally Quiz

_Given BFS, DFS, and CFS (cheapest-first search), which of the algorithms are optimal (i.e., guaranteed to find the shortest path)_? Only BFS and CFS are optimal not DFS since DFS searches by depth first.

### BFS Vs. DFS Vs. CFS Completeness Quiz

_Given BFS, DFS, and CFS (cheapest-first search), which of the algorithms are complete (i..e, if there is a goal somewhere, will the algorithm find it)_? Only BFS and CFS are complete but not DFS since DFS searches by depth first and may keep going downhill for an infinite tree.

### A\* Shortest Path Quiz

_Will A\* always find the shortest path_? No, it depends on the heuristic function $h$.

### Other State Spaces 1 Quiz

_The state spaces can represent many varieties of spaces not just discrete 2D planes. Given two states (provided), how many states do we need to represent the problem_? We need `2 (vacuum or no vacuum) * 2 (dirt or no dirt) * 2 (position A or B) = 8`.

### Other State Spaces 2 Quiz

_Given two states (provided) and adding options (power, camera, brush height, and 10 more possible positions), how many states do we need to represent the problem_? We need `3 (on, off, sleep) * 2 (on, off) * 5 (1, 2, 3, 4, 5) * 2**10 (2 dirt positions for each of the 10 positions) * 10 (10 positions) = 307200`.

### Sliding Blocks Puzzle Quiz

_Given the sliding block puzzle, which of the following heuristics are admissible_?

- $h_1 = n_{blocks}$
- $h_2 = \sum distance_{blocks}$

Note that since $h2 \geq h_1$, $h_2$ will always expand fewer paths than $h_1$.

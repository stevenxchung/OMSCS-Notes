# Lesson 4

How do airports schedule so many different flights simultaneously? How are maps properly colored so that no neighboring country is the same color? Turns out these problems are a classic example of AI **CSP (constraint satisfaction problem)**.

## Backtracking Search

Given a map coloring problem where:

- Variables: territories
- Domains: set of colors
- Constraints: adjacent regions must have different colors

How do we solve this problem? One way to solve constraint satisfaction problem (pseudo-code) is as follows:

1. Initialize an empty state
2. Check if current assignment is the goal
3. Assign value to unassigned variable that does not conflict with current assignment
4. If there are no legal assignments then we have reached a dead-end
   - Back up to a previous node (or state) and try another assignment
5. Recurse until we found the goal or have tried all possible assignments

## Improving Backtracking Efficiency

There are several ways to improve backtracking by adding some heuristics (intelligence) to our AI:

- **Least constraining value**: choosing the variable that rules out the fewest values in the remaining variables
- **MRV (minimum remaining values)**: choosing the variable with the fewest legal values
- **Degree heuristic**: choosing the variable with the most constraints on remaining variables

By combining some of these heuristics we can solve very complex problems such as the 1000-Queens problem (enhanced 8-Queens problem) via heuristics such as least constraining value and MRV.

## Forward Checking

Another addition to backtracking is **forward checking**:

- For each unassigned variable, keep track of the remaining legal values
- If an unassigned variable cannot be assigned to a value
  - Stop searching and back up to previous node (or state)

This allows us to backtrack instead of going down the wrong branch

## Constraint Propagation And Arc Consistency

Forward checking provides information from assigned to unassigned variables but does **not** provide information for all failures. Instead, a better approach is to use **constraint propagation** whereby all local constraints are enforced at each step of the search.

Another approach is to leverage **arc consistency** (simple version of constraint propagation) which states that:

> A variable in a constraint satisfaction problem is arc consistent with respect to another variable if there is some value still available for the second variable after we assign a value to the first variable.

If all variables in a graph satisfy the arc consistency condition, then the network is arc consistent.

## Structured CSPs

Another method to solve CSPs is through **structured CSPs** whereby the problem is deconstructed into smaller independent problems. For tree-structured CSPs (CSPs with no loops), the problem can be simplified such that the time efficiency drops from $O(n^d)$ to $O(n * d^2)$ where $n$ is the number of variables and $d$ are the possible values. This can be accomplished as follows:

1. Choose a variable as root, order variables from root to leaves such that every node's parent preceded it in the ordering
2. We then make each parent arc consistent from the bottom to top of the tree
   - For `i` from `n` down to `2`, apply `remove_inconsistent(parent(x[i]), x[i])`
   - For `i` from `1` to `m`, assign `x[i]` consistently with `parent(x[i])`

For constraint graphs that are not a tree, we might be able to transform a the graph problem into a tree by assigning values to some variables.

## Section Quizzes

**Note**: will be somewhat limited for this semester.

### Map Coloring Quiz

_Given a map (provided), color each region by typing a number. What is the minimum number of colors needed for this map_? At least 4 colors are needed.

### Backtracking Optimization Quiz

_Given a map (provided), check the boxes to indicate which region(s) we should fill in next. Try to minimize backtracking. Which optimization did you use_? We can use either least constraining value or MRV.

### Constraint Propagation Quiz

_Which color(s) are possible in each region? Is the entire network arc consistent_?

- Possible colors:

  - H: blue, orange, green
  - T: orange, green
  - K1: orange, green
  - K2: green
  - S: blue, orange, green
  - K3: blue, orange, green
  - O: blue, orange, green

- Yes, because we do not have any regions without a possible color.

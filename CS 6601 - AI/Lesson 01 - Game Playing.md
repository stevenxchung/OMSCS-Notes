# Lesson 1

In this lesson we will examine the game playing problem where the goal is to build an AI which can play a game better than a human. The following topics will be covered:

1. Adversarial search
2. Minimax algorithm
3. Alpha-beta pruning
4. Isolation game player
5. Multi-player probabilistic games

## Isolation Game Player Steps

To construct an isolation game player we need to implement:

- **Minimax**: process of computing scores at each node from bottom to top
  - For each max node, pick the max score among child nodes (opponent will pick the min node since they are trying to win as well)
  - If there is at least one `+1` child node, the AI can always pick that to win
  - Favors the left-most branch
- **Alpha-beta pruning**: an _adversarial_ technique where we may ignore whole section of the game tree while still arriving at the same answer as minimax by stopping evaluation once at least one possibility has been found that proves the move to be worse than a previously examined move
  - Can run in $b^{d/2}$ time if nodes are ordered best moves first (optimal)
  - Can run in $b^{3d/4}$ time if nodes are ordered randomly

## Depth-limited Search

Our AI will take too long to determine the most optimal move to win the game if it searches until the _end game_ move. Therefore, the AI should limit the depth of the search to meet the time restriction criteria via **depth-limited search** as part of minimax.

E.g., given there are on average 8 legal moves, we can search $10^9$ nodes per second and the time restriction was 2 seconds, then the maximum depth we can go while meeting our deadline is:

$x < \frac{log_{10}(2e9)}{log_{10}(8)} \rArr x < 10$

## Evaluation Function

Once we get to a specific depth via depth-limited search, we need an evaluation function which will count the total amount of legal moves the AI has at that level. The preferred move will be one where the AI has the most number of legal moves.

## Quiescent Search And Iterative Deepening

To reach a state of _quiescent_, the AI player has to search deep enough until the nodes at the top-level of the tree are not changing much. However, we do not have to use quiescent search all the time especially of our evaluation function is giving back consistent results.

**Iterative deepening** is when the AI goes through each level of the tree and selects the node with the highest number of legal moves and stores them (just incase it runs out of time). The amount of time the AI takes to execute iterative deepening is dependent on the last level searched. The number of nodes at each level of the tree is given by:

$n = 2^{d + 1} - 1$

Consequently, iterative deepening expands less than 2 times the number of nodes a depth-limited search would have done at the same level. We can generalize the number of nodes $n$ searched by iterative deepening with a branching factor of $b$ as follows:

$n = \frac{b^{d + 1} - 1}{b - 1}$

## Section Quizzes

**Note**: will be somewhat limited for this semester.

### Nodes In A Game Tree Quiz

_How many nodes do you think Minimax will need to visit_? $b^d$ nodes where $b$ is the branching factor (average number of children of each node or _average number of legal moves in a position_) and $d$ is the depth of the tree.

### Good Evaluation Functions Quiz

_Which of the following may be considered good evaluation functions_? `n_my_moves - n_opponent_moves` since we can determine how many moves an AI has over the opponent or vice versa.

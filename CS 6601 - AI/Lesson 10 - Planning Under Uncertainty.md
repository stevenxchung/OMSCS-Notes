# Lesson 10

So far we have discussed planning, uncertainty, and learning separately. In this lesson we will examine techniques (e.g., MDPs, POMDPs) which utilize planning and uncertainty to examine how we can build AI to plan under uncertainty.

RL techniques combine aspects of planning, uncertainty, and learning.

## Content Review

To review, some of the core techniques we have previously discussed could be categorized into:

|                      | Deterministic | Stochastic |
| -------------------- | ------------- | ---------- |
| Fully observable     | A\*, DFS, BFS | MDP        |
| Partially observable | ?             | POMDP      |

Where, the term definitions for each category is:

- **Deterministic**: results of actions are predictable
- **Stochastic**: results of actions are not always predictable
- **Fully observable**: we know all states of the environment and can make all decisions based on the momentary sensor input
- **Partially observable**: we do not know the entire state of an environment and therefore would require memory to add information to the AI agent

## MDPs (Markov Decision Processes)

MDPs are fully observable processes which include stochastic outcomes may defined mathematically as a 4-tuple $(S, A, P_a, R_a)$, where:

- $S$: set of states called the _state space_
- $A$: set of actions called the _action space_
- $P_a(s, s') = P(s_{t+1} = s' | s_t = s, a_t = a)$: probability that action $a$ in state $s$ at time $t$ will lead to state $s'$ at time $t + 1$
- $R_a(s, s')$ is the immediate reward (or expected immediate reward) received after transitioning from state $s$ to state $s'$ due to action $a$

Consider a path finding problem in a grid world. One challenge with MDPs is accounting for the stochastic outcomes during path finding. Problems with stochastic environments include:

- Deep trees
- Large branching factor
- Many states reoccur (can revisit the same state)

Consequently, instead of finding the most optimal deterministic path to the goal, the AI should find the _optimal policy_ which takes the optimal path to the goal at any point.

How do we get the optimal policy? We want to _minimize_ the costs and _maximize_ the sum of all future rewards:

$E[\sum \gamma R_t] \rightarrow R_{max})\\$

Where we seek to maximize the expectation $E$ (expectation is needed since the problem is stochastic) on all future cumulative and discounted rewards $R_t$. The discount factor $\gamma$ (typically with a value of `0.9`) decays future rewards relative to immediate rewards and bounds the expectation by:

$E \leq \frac{1}{1 - \gamma} * |R_{max}| \\$

How do we know the value of any state? We can compute the _value function_:

$V(s) = E[\sum \gamma R_t | S_0 = S]$

This allows us to iteratively find better plans using methods such as _value iteration_.

## Value Iteration

**Value iteration** (a.k.a. backward induction) is a recursive algorithm which iteratively improves the optimal policy. Mathematically denoted as:

$V(s) \leftarrow [max_a(\gamma \sum P(s'|s, a) * V(s'))] + R(s)\\$

Which computes a value recursively based on successor values $V(s')$ (with a probability distribution $P(s'|s, a)$) plus the reward $R(s)$ (minus the cost) it takes to get to a specific state. Because we can select our action $a$ we select the optimal $max_a()$ of all possible actions. If we are in the terminal (goal) states then we simply assign $V(s) \leftarrow R(s)$.

[Bellman (1957)](https://en.wikipedia.org/wiki/Bellman_equation) has shown that the value iteration algorithm converges over time as updates occur. Since the goal of value iteration is to find the optimal policy $\pi(s)$, once value iteration converges, the optimal policy is:

$\pi(s) = argmax_a(\sum P(s'|s, a) * V(s'))\\$

Which gives the best action to take at any state.

## POMDPs

POMDPs are MDPs for a special case of partially observable environments (requires memory as mentioned above). In these cases, simply using MDP and value iteration will not guarantee an optimal path since it would need to retrieve information about the environment first.

Consequently, one solution is to switch from state space representation to _belief space_ representation such that planning is done on beliefs instead of known physical states. In this way, belief states may be modeled as being stochastic and MDPs could be used to solve the problem and find the optimal policy.

## Section Quizzes

**Note**: will be somewhat limited for this semester.

### Stochastic Environments Quiz

_Given the MDP grid navigation problem (provided). How many states can we reach in cell $b3$_? There are eight possible states we can reach including remaining in the same position.

### Optimal Action 1 Quiz

_Given the MDP grid navigation problem (provided). What is the optimal action if the AI agent is in cell $a1$_? Moving east.

### Optimal Action 2 Quiz

_Given the MDP grid navigation problem (provided). What is the optimal action if the AI agent is in cell $b1$_? Moving north.

### Optimal Action 3 Quiz

_Given the MDP grid navigation problem (provided). What is the optimal action if the AI agent is in cell $c4$_? Moving south (which is not physically possible) to reduce the probability of moving north and increase the probability of moving west.

### Optimal Action 4 Quiz

_Given the MDP grid navigation problem (provided). What is the optimal action if the AI agent is in cell $b3$_? Moving west (which is not physically possible) to reduce the probability of not getting the reward.

### Deterministic Value Iteration 1 Quiz

_Given a grid world (provided), what is the value in cell $a3$ if the transition probability is deterministic, $\gamma = 1$ and $R(s) = -3$ _?

For state $a3$: $V(s) = V(s') + R(s) = 100 - 3 = 97$.

### Deterministic Value Iteration 2 Quiz

_Given a grid world (provided), what is the value in cell $b3$ if the transition probability is deterministic, $\gamma = 1$ and $R(s) = -3$ _?

For state $b3$: $V(s) = \sum V(s') + R(s) = 97 - 3 = 94$.

### Deterministic Value Iteration 3 Quiz

_Given a grid world (provided), what is the value in cell $c1$ if the transition probability is deterministic, $\gamma = 1$ and $R(s) = -3$ _?

For state $c1$: $V(s) = \sum V(s') + R_{c}(s) = 94 - 3 - 3 - 3 = 85$.

### Value Iteration 1 Quiz

_Given a grid world (provided), what is the value in cell $a3$ if the transition probability is stochastic with $P(s'|s, a) - 0.8$, $\gamma = 1$ and $R(s) = -3$ _?

For state $a3$: $V(s) = \sum P(s'|s, a) * V(s') + R_{c}(s) = 0.8 * 100 - 3 = 77$.

### Value Iteration 2 Quiz

_Given a grid world (provided), what is the value in cell $b3$ if the transition probability is stochastic with $P(s'|s, a) - 0.8$, $\gamma = 1$ and $R(s) = -3$ _?

For state $b3$: $V(s) = \sum P(s'|s, a) * V(s') + R_{c}(s) = 0.8 * 77 + 0.1 * (-100) - 3 = 48.6$.

# Lesson 3

It turns out that there are a whole class of problems where just adding a little bit of intelligence and iteratively improving the solution can get us very lose to an optimal solution. In this lesson we examine these problems and how we can use iterative improvement algorithms (e.g., random restart, simulated annealing, or genetic algorithms) to solve them.

## Random Restart

How do we find the global maximum for a particular problem? We might try **random restart** _hill-climbing_ where we randomly restart and follow a positive gradient. As the number of random restarts reaches infinity, the global maximum will be found (although inefficient). Some ideas to improve efficiency may include:

- Keeping track of previous restart states so that our AI does not restart at the same place and generate redundant results
- Estimating the shape of the problem by keeping track of all local maxima found

Some further problems with hill-climbing include:

- Step size is too small
- Step size is too large

## Simulated Annealing Algorithm

**Simulated annealing** takes the analogy of _heating_ and _cooling_ from physics to apply more heat (randomness) or cool (less randomness) to help AI converge to a global maxima. Simulated annealing looks at points close to the current position that might have an improved value. The simulated annealing algorithm (pseudo-code) is as follows:

```python
while not self.infinity:
    T = schedule(t)
    if T = 0:
        return current
    # Randomly select a successor of current from a nearby region
    next = self.randomly_select_successor()

    if delta_e > 0:
        current = next
    else:
        # Set current to next with probability e^(delta_e/T) of selecting
        current = self.next_by_probability()
```

Note that we start with $T$ being very high which will cause $e^{\frac{\delta E}{\infty}} = e^0 = 1$. Simulated annealing is **guaranteed** to find the **global** maxima provided that $T$ starts with a high value and slowly decreases over time.

## Local Beam Search

Building on simulated annealing where we examine only one particle, we may apply **local beam search** which examines $k$ particles and their randomly generated neighbors and keep the best results for the next iteration. Local beam search will terminate when any of the $k$ particles have found the global maxima.

## Genetic Algorithms

Genetic algorithms is really another version of stochastic beam search and an analogy to natural selection in biology, it uses _breeding_ and _mutation_ to find the optimal answer to the problem. The fitness function (which measures how likely a given state will survive into the next iteration) in the genetic algorithm naturally reduces randomness as each generation gets closer to the optimal solution.

Some ideas to make genetic algorithms more efficient include tuning parameters such as:

- Crossover
- Mutations
- Number of parents

## Section Quizzes

**Note**: will be somewhat limited for this semester.

### Hill Climbing 1 Quiz

_Given the hill climbing chart (provided), what is the final value of each particle_?

- Particle 1 starts at `x = 1`: 2
- Particle 2 starts at `x = 8`: 6
- Particle 3 starts at `x = 9`: 8
- Particle 4 starts at `x = 14`: 8
- Particle 5 starts at `x = 20`: 12

### Hill Climbing 2 Quiz

_Given the hill climbing chart (provided), what is the final value of each particle (with larger step-size)_?

- Particle 1 starts at `x = 7`: 10
- Particle 2 starts at `x = 8`: Unknown since it will oscillate around the peak
- Particle 3 starts at `x = 10`: 4

### 8-Queens Representation Quiz

_Given the following 8-Queens board (provided), determine the string that represents the position of each piece_. The string is `16257483`

### Challenge Question Quiz

_Mark the given methods which can be used to unstick us and find the global maximum_.

- Random restart
- Genetic algorithms
- Simulated annealing

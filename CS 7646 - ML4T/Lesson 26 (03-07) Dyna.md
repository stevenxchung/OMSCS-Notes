# Lesson 26

One of the problems with Q-learning is that it takes many experience tuples to converge. This is not practical for trading purposes since we have to execute many trades to gather experience tuples (very costly).

To address this issue, Richard Sutton invented the Dyna-Q learner which leverages a transition matrix $T$ and a rewards matrix $R$. After some real interactions with the world the Dyna-Q learner can generate additional _hallucinated_ experiences (synthetic data) to update the Q-table.

## Dyna-Q Big Picture

Recall that Q-learners are _model-free_ learners by default (they do not know $T$ or $R$ matrices). Because Dyna-Q can generate additional experiences, it adds a model-based element to Q-learning.

Currently Q-learners are structured as:

1. Initialize Q-table
2. Observe S
3. Execute $a$, observe $s$ and $r$
4. Update $Q(s, a, s', r)$

When adding Dyna-Q the following steps are defined:

5. Learn models $T'(s, a, s')$ and $R'(s, a)$
6. Hallucinate experiences:
   - Randomly select a $s$
   - Randomly select an $a$
   - Infer $s'$ from $T'(s, a, s')$
   - Infer $r$ from $R'(s, a)$
7. Update $Q(s, a, s', r)$

During the Dyna-Q steps we may iterate through steps 6 and 7 hundreds of times (which is still much cheaper than interacting with the real world). Once the Dyna-Q is done iterating through steps 6 and 7 it returns back to the Q-table process at step 1.

## Learning T

How does Dyna-Q learn $T(s, a, s')$? Recall that $T(s, a, s')$ contains the probably that taking action $a$ in state $s$ will result in state $s'$. We may utilize another matrix ($T_{count} = 0.00001$) to keep track of how many times did $s'$ occur given an action $a$ at state $s$ as follows:

1. Initialize $T_{count} = 0.00001$
2. While executing, observe $s$, $a$, and $s'$
3. Increment $T_{count}(s, a, s')$

## Learning R

Recall that $R(s, a)$ is a model of the _expected reward_ for $s$ given $a$. Our _immediate reward_ $r$ is from our experience tuple so we can leverage $r$ to update our model $R(s, a)$ as follows:

$R'(s, a) = (1 - \alpha) R(s, a) + \alpha * r$

Where $\alpha * r$ is the new best estimate of the reward.

## Section Quizzes

### How To Evaluate T

_How would we evaluate $T_{count}$_? We use $T_{count}[s, a, s'] = \frac{T_{count}[s, a, s']}{\sum_i T_{count}[s, a, i]}$ to indicate the probability that we are in state $s'$ after taking action $a$ in state $s$.

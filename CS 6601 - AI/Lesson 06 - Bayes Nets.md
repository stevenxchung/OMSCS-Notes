# Lesson 6

Previously, we introduced the fundamental building blocks of Bayes networks e.g., Bayes' Rule. In this lesson we will examine how to construct Bayes networks which will allow AI to observe events in the world and compute probabilities of specific hypotheses.

## Bayes Network Visualized

A classical Bayes network is one where event $A$ is not observable but event $B$ is. We may say that event $A$ causes $B$ or $P(B | A)$ and $P(B | \neg A)$. Therefore, the _diagnostic reasoning_ may be given as $P(A | B)$ and $P(A | \neg B)$

## Bayes' Rule Normalizer Trick

Suppose we are trying to compute:

$P(A | B) = \frac{P(B | A) * P(A)}{P(B)}\\$
$P(\neg A | B) = \frac{P(B | \neg A) * P(\neg A)}{P(B)}\\$

Where $P(A | B) + P(\neg A | B) = 1$. How do we compute $P(A | B)$ and $P(\neg A | B)$ more efficiently?

We can compute both numerators ($P(B | A) * P(A)$ and $P(B | \neg A) * P(\neg A)$) and then normalize both numerators with the sum of both numerators $n = P(B | A) * P(A) + P(B | \neg A) * P(\neg A)$

## Conditional Independence

If we have a Bayes network where $A$ is the parent and $B$ and $C$ are child nodes. Then, by conditional independence, $B$ is independent from $C$ ($B \perp C$) given $A$.

## Different Type Of Bayes Networks

Before we seen that one hidden cause $C$ can affect the results of observations $A$ and $B$. Now let's examine the opposite where _two_ independent hidden causes affect the results of a _single_ observation.

From the sunny and raise affecting happiness exercise. We observed that:

- $P(R | H, S) = 0.0142$ which $\not = {P(R | H)}$
- $P(R | S) = P(R) = 0.01$ (no effect)
- $P(R | H, \neg S) = 0.0833$

Therefore, absolute independence does **not** imply conditional independence.

## General Definition Of Bayes Networks

Given that we have causes $A$ and $B$ affecting observation $C$ and $C$ affecting observations $D$ and $E$, we can represent as a Bayes network as a joint probability:

$P(A, B, C, D, E) = P(A) * P(B) * P(C |A, B) * P(D | C) * P(E | C)$

The advantage is that we can represent the graph as a Bayes network with only 10 probability values (note that there are 4 for $P(C |A, B)$ and 2 for $P(D | C)$ and $P(E | C)$) versus $2^5 - 1 = 31$ probability values for a normal graph. This means that Bayes networks representation are much more scalable.

## D-separation

**D-separation** is also known as _reachability_ and can help determine conditional independence by:

- **Active triplets** - triplet Bayes network configuration which renders variables _dependent_ if all variables are unknown
  - However, note that when two _independent_ variables (or causes) point to a _known_ variable, then both of the variables become _dependent_ (as in the given raise and sunny causes happiness example via _explain away effect_)
  - Additionally, the above _explain away effect_ also applies when a successor down the chain is _known_
- **Inactive triplets** - triplet Bayes network configuration which renders variables _independent_ if the middle variable is known
  - However, note that when two _independent_ variables (or causes) point to a _unknown_ variable, then both of the variables remain _independent_

For more information on D-separation see [d-separation Wiki](https://en.wikipedia.org/wiki/Bayesian_network#d-separation). The rules for D-separation are as follows: any two variables are independent if they are **not** linked by unknown variables (see [slide 17 - Reachability](https://courses.cs.washington.edu/courses/cse473/14sp/slides/21-BN-Independence.pdf)).

## Probabilistic Inference

Previously, we learned about:

- Probability theory
- Bayes networks
- Independence

Let's examine [probabilistic inference](http://deepdive.stanford.edu/inference) which is:

> the task of deriving the probability of one or more random variables taking a specific value or set of values. For example, a Bernoulli (Boolean) random variable may describe the event that John has cancer. Such a variable could take a value of 1 (John has cancer) or 0 (John does not have cancer).

Some questions or inferences we can make:

- Given some inputs (evidence variables) what are the outputs (query variables)?
  - $P(Q_1, ..., Q_i | E_1 = e_1, ..., E_j = e_j)$
- Given all query values for all query variables, which combination has the highest probability (i.e., find max $q$ given $E$)?
  - $argmax_q(P(Q_1 = q_1, ..., Q_i = q_i | E_1 = e_1, ..., E_j = e_j))$

Nodes can be one of three types:

- Evidence (input variables)
- Hidden (unknown variables)
- Query (output variables)

## Enumeration

How do we perform inference on Bayes networks? We use an **enumeration** method which goes through all the possibilities, adds them up, and comes out with an answer. E.g., to solve for $P(+b | +j, +m)$ given the in-class example:

1. Use conditional probability where $P(Q | E) = \frac{P(Q, E)}{P(E)}$
2. Enumerate all possible values for hidden variables in numerator
3. Enumerate all possible values for hidden variables in denominator

Therefore, the numerator in the example would be:

$P(+b, +j, +m, e, a) = P(+b) * P(e) * P(a | +b, e) * P(+j | a) * P(+m | a) = P(+e, +a) + P(+e, \neg a) + P(\neg e, +a) + P(\neg e, \neg a)$.

We fill in values by referencing the conditional probability tables. Note that we do this for all possible values of $e$ and $a$ (true or false for both so four times total).

## Pulling Out Terms

While enumeration may help solve some Bayes networks, more complex networks can reduce the efficiency of enumeration very quickly. Consequently, we may need more creative methods such as:

- _Pulling out terms_ whereby terms are pulled out or rearranged such that we do not add terms redundantly (however, this does **not** reduce the number of rows in the table)
- _Maximize independence_ whereby the Bayes network is structured in a more efficient manner via independence between variables

## Causal Bayes Networks

Bayes networks tend to be more compact and easier to work with when they are constructed in the _causal direction_ whereby the network flows from causal nodes to effect nodes.

## Variable Elimination

Although inference over Bayes networks is still a [NP-hard](https://en.wikipedia.org/wiki/NP-hardness) computation in general, _variable elimination_ works faster than inference by enumeration in most cases by utilizing algebra to eliminate variables. The steps are as follows:

- _Joining factors_ by multiplying values of one factor with values from another factor where a factor is one or more probability tables (multi-dimensional matrix of probability values)
- _Elimination_ (also called summing out or marginalization) by reducing the joined factor table by summing like values (e.g., add values of factor where $+A$ or $-A$)

## Approximate Inference

We can conduct **approximate inference** via sampling where the advantages are:

- We know the procedure for coming up with an approximate value for the joint probability distribution as opposed to exact inference where the computation may be more complex
- If we did not know the conditional probability tables (the factors as discussed in the earlier example above), then we can simply proceed with sampling to determine those values

Note that over an infinite number of samples, sampling produces the true joint probability distribution which means that the sampling method is **consistent**.

If a new probability of an event $P(B | -A)$ needed to be evaluated we would just reject all samples (e.g., $+A$) not matching the conditional probabilities (e.g., $-A$) of the event $P(B | -A)$ via **rejection sampling** and keep the samples which match the conditional probability.

## Likelihood Weighting

Unfortunately, with rejection sampling, we can end up rejecting many samples before a valid example is found. We can address this with **likelihood weighting** which only generates samples that we need by fixing the evidence variables (e.g., $A$ in $P(B | A)$ is always positive). However, this causes our sampling method to be **inconsistent**. How to fix?

We can assign probabilities to each sample and weigh them correctly which results in a consistent sampling method.

Note that sampling does not work in all cases, if we try to determine the probability of a parent event which has no influences, we will obtain probability values which may not go well with the evidence.

## Gibbs Sampling

[Gibbs sampling](https://en.wikipedia.org/wiki/Gibbs_sampling) is a **MCMC (Markov chain Monte Carlo)** algorithm that we randomly resample one variable at a time conditioned on all the other variables.

Note that:

- Gibbs sampling consists of samples dependent and similar to adjacent samples while maintaining consistency
- Rejection and likelihood sampling consists of samples which were independent of each other

## Section Quizzes

**Note**: will be somewhat limited for this semester.

### Bayes Network Visualized Quiz

_Given a Bayes net between $A$ and $B$ (provided), how many parameters does it take to specify the entire joint probability of $A$ and $B$ (or the entire Bayes network)_? It takes three, $P(A)$, $P(B | A)$, and $P(B | \neg A)$ (which makes up Bayes' Rule).

### Test Cancer Example 1 Quiz

_Given the following_:

$P(c) = 0.01\\$
$P(\neg c) = 0.99\\$
$P(+ | c) = 0.9\\$
$P(- | c) = 0.1\\$
$P(+ | \neg c) = 0.2\\$
$P(- | \neg c) = 0.8\\$

_Determine $P(c | T_1 = +, T_2 = +)$_.

|          | Prior | $T_1 = +$ | $T_2 = +$ | P'     |
| -------- | ----- | --------- | --------- | ------ |
| $c$      | 0.01  | 0.9       | 0.9       | 0.0081 |
| $\neg c$ | 0.99  | 0.2       | 0.2       | 0.0396 |

Therefore, $P(c | T_1 = +, T_2 = +) = \frac{0.0081}{0.0081 + 0.0396} = 0.1698$

### Test Cancer Example 2 Quiz

_Given the following_:

$P(c) = 0.01\\$
$P(\neg c) = 0.99\\$
$P(+ | c) = 0.9\\$
$P(- | c) = 0.1\\$
$P(+ | \neg c) = 0.2\\$
$P(- | \neg c) = 0.8\\$

_Determine $P(c | T_1 = +, T_2 = -)$_.

|          | Prior | $T_1 = +$ | $T_2 = -$ | P'     |
| -------- | ----- | --------- | --------- | ------ |
| $c$      | 0.01  | 0.9       | 0.1       | 0.0009 |
| $\neg c$ | 0.99  | 0.2       | 0.8       | 0.1584 |

Therefore, $P(c | T_1 = +, T_2 = -) = \frac{0.0009}{0.0009 + 0.1584} = 0.0056$

### Conditional Independence 1 Quiz

_We discussed that conditional independence implies $B \perp C$ | $A$ ($B$ is independent of $C$ given $A$). However, if we are not given $A$, are $B \perp C$ still independent_? No, because results of child $A$ can affect the parent $C$ which influences child $B$.

### Conditional Independence 2 Quiz

_Given the following_:

$P(c) = 0.01\\$
$P(\neg c) = 0.99\\$
$P(+ | c) = 0.9\\$
$P(- | c) = 0.1\\$
$P(+ | \neg c) = 0.2\\$
$P(- | \neg c) = 0.8\\$

_Determine $P(T_2 = + | T_1 = +)$_.

$P(T_2 = + | T_1 = +) = P(T_2 = + | T_1 = +, c) * P(c | T_1 = +) + P(T_2 = + | T_1 = +, \neg c) * P(\neg c | T_1 = +)$.

From conditional independence we know that $P(T_2 = + | T_1 = +, c) = P(T_2 = + | c)$ and $P(T_2 = + | T_1 = +, \neg c) = P(T_2 = + | \neg c)$.

Therefore, $P(T_2 = + | T_1 = +) = P(T_2 = + | c) * P(c | T_1 = +) + P(T_2 = + | \neg c) * P(\neg c | T_1 = +) = 0.9 * 0.043 + 0.2 * 0.957 = 0.2301$. Additionally, $P(T_2 = +) = 0.207$, which means that observing $T_1 = +$ increases the probability that $T_2 = +$.

### Conditional Independence 3 Quiz

_Answer the following_:

1. _Does absolute independence imply conditional independence_? False
2. _Does conditional independence imply absolute independence_? False, since results of child $A$ can affect the parent $C$ which influences child $B$.

### Different Type Of Bayes Networks 1 Quiz

_Given the following_:

$P(S) = 0.7\\$
$P(R) = 0.01\\$
$P(H | S, R) = 1\\$
$P(H | \neg S, R) = 0.9\\$
$P(H | S, \neg R) = 0.7\\$
$P(H | \neg S, \neg R) = 0.1\\$

_Determine $P(R | S)$_.

$P(R | S) = 0.01$ since $S$ and $R$ are independent of each other and we do not know anything about $H$.

### Different Type Of Bayes Networks 2 Quiz

_Given the following_:

$P(S) = 0.7\\$
$P(R) = 0.01\\$
$P(H | S, R) = 1\\$
$P(H | \neg S, R) = 0.9\\$
$P(H | S, \neg R) = 0.7\\$
$P(H | \neg S, \neg R) = 0.1\\$

_Determine $P(R | H, S)$_.

$P(R | H, S) = \frac{P(H | R, S) * P(R | S)}{P(H | S)} = \frac{P(H | R, S) * P(R)}{P(H | R, S) * P(R) + P(H | \neg R, S) * P(\neg R)} = 0.0142$.

### Different Type Of Bayes Networks 3 Quiz

_Given the following_:

$P(S) = 0.7\\$
$P(R) = 0.01\\$
$P(H | S, R) = 1\\$
$P(H | \neg S, R) = 0.9\\$
$P(H | S, \neg R) = 0.7\\$
$P(H | \neg S, \neg R) = 0.1\\$

_Determine $P(R | H)$_.

We need the following:

- $P(H) = P(H | S, R) * P(S, R) + P(H | \neg S, R) * P(\neg S, R) + P(H | S, \neg R) * P(S, \neg R) + P(H | \neg S, \neg R) * P(\neg S, \neg R) = 0.5245$
- $P(H | R) = P(H | R, S) * P(S) + P(H | R, \neg S) * P(\neg S) = 0.97$

Finally, $P(R | H) = \frac{P(H | R) * P(R)}{P(H)} = 0.0185$.

### Different Type Of Bayes Networks 4 Quiz

_Given the following_:

$P(S) = 0.7\\$
$P(R) = 0.01\\$
$P(H | S, R) = 1\\$
$P(H | \neg S, R) = 0.9\\$
$P(H | S, \neg R) = 0.7\\$
$P(H | \neg S, \neg R) = 0.1\\$

_Determine $P(R | H, \neg S)$_.

$P(R | H, \neg S) = \frac{P(H | R, \neg S) * P(R | \neg S)}{P(H | \neg S)} = \frac{P(H | R, \neg S) * P(R)}{P(H | \neg S, R) * P(R) + P(H | \neg S, \neg R) * P(\neg R)} = 0.0833$

### Required Probability Values 1 Quiz

_Given the Bayes network (provided), how many probability values are required_? 13 probability values since any variable that has $k$ inputs requires $2^k$ probability values.

### Required Probability Values 2 Quiz

_Given the Bayes network (provided), how many probability values are required_? 19 probability values.

### Required Probability Values 3 Quiz

_Given the Bayes network (provided) from the initial car example, how many probability values are required_? 47 probability values.

### D-separation 1 Quiz

_Given the Bayes network (provided), answer the following_:

1. $C \perp A$: no, since $C$ is influenced by $B$ which is influenced by $A$
2. $C \perp A | B$: yes, if we know $B$ for sure
3. $C \perp D$: no, since $C$ or $D$ can affect $A$
4. $C \perp D | A$: yes, if we know $A$ for sure
5. $E \perp C | D$: yes, if we know $D$ for sure

### D-separation 2 Quiz

_Given the Bayes network (provided), answer the following_:

1. $A \perp E$: no
2. $A \perp E | B$: no
3. $A \perp E | C$: yes
4. $A \perp B$: yes
5. $A \perp B | C$: no, due to the _explain away effect_

### D-separation 3 Quiz

_Given the Bayes network (provided), answer the following_:

1. $F \perp A$: yes
2. $F \perp A | D$: no
3. $F \perp A | G$: no
4. $F \perp A | H$: yes

### Probabilistic Inference Quiz

_Given the Bayes network (provided), select whether the node is an evidence, hidden, or query node_:

- B: Query
- E: Hidden
- A: Hidden
- J: Hidden
- M: Evidence

### Maximize Independence 1 Quiz

_Given the Bayes network (provided), is $M$ dependent on or independent of $J$_? It is dependent since $A$ is unknown in our Bayes network.

### Maximize Independence 2 Quiz

_Given the Bayes network (provided), which nodes is $A$ dependent on_? It is dependent on $J$ and $M$.

### Maximize Independence 3 Quiz

_Given the Bayes network (provided), which nodes is $B$ dependent on_? It is dependent on $A$.

### Maximize Independence 4 Quiz

_Given the Bayes network (provided), which nodes is $E$ dependent on_? It is dependent on $A$ and $B$.

### Join And Elimination 1 Quiz

_Given the factor tables (provided), fill in the following table for elimination_:

We look up in $P(R, T)$ where $+T$ and $-T$ and add like terms:

|      | $P(T)$ |
| ---- | ------ |
| $+T$ | 0.17   |
| $-T$ | 0.83   |

### Join And Elimination 2 Quiz

_Given the factor tables (provided), fill in the following table for joining_:

We look up in $P(L, T)$ where $+T$ and $-T$ and multiply like terms:

| T   | L   | $P(L \| T)$ |
| --- | --- | ----------- |
| +   | +   | 0.051       |
| +   | -   | 0.119       |
| -   | +   | 0.083       |
| -   | -   | 0.747       |

### Join And Elimination 3 Quiz

_Given the factor tables (provided), fill in the following table for elimination_:

We look up in $P(T, L)$ where $+L$ and $-L$ and add like terms:

|      | $P(L)$ |
| ---- | ------ |
| $+L$ | 0.134  |
| $-L$ | 0.866  |

### Sampling Quiz

_Given the factor tables and sampled values (provided), which of the rows are relevant and what is $+W$ and $-W$_? We should look at the $-S \rArr +R \Rarr +W and -W$ rows where $+W$ is more likely.

### Likelihood Weighting Quiz

_Given the factor tables and sampled values (provided), what is the value of the weight we should add_? We should multiply the previous weights with $P(+W | +S, +R) = 0.99$ to get a final value of 0.099 for the weight on samples $+C$, $+S$, $+R$, and $+W$.

### Monty Hall Problem Quiz

_Given the [Monty Hall Problem](https://en.wikipedia.org/wiki/Monty_Hall_problem) what is the probability of winning if door 1 or 2 are selected_?

- Door 1 win probability: 1/3 or ~33%
- Door 2 win probability: 2/3 or ~66%

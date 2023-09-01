# Lesson 7

In this lesson we cover topics on machine learning including supervised and unsupervised learning.

## K-nearest Neighbor

As covered previously in ML4T:

> The **kNN (k-nearest neighbor)** approach utilizes data (instance based approach) to find the mean value of the nearest $k$ data points to produce a $y$ output.
>
> A similar approach is **kernel regression** which utilizes weights on each kNN based on distance (evaluating contributions based on distance). The kNN approach only assigns equal weights to all kNN.

## Cross Validation

As covered previously in ML4T:

> Often researchers do not have enough data to analyze their algorithm. This can be remedied by **cross validation** whereby data is sliced into multiple chunks of training and testing. In this way, one set of data could be used for multiple trials by switching chunks of training and testing data for each trial.

## Gaussian

As covered previously in AI4R:

> The Gaussian distribution has the following characteristics:
>
> - The shape of the Gaussian is unimodal
> - The area underneath a Gaussian sums to 1
> - Mean $\mu$: the average of all data points in the distribution
> - Width $\sigma^2$: the variance of a specific data point from the mean
>
> A 1-D Gaussian is characterized by $\mu \sigma^2$ which is the estimation of the location of a point of interest. The formal definition of the Gaussian function is as follows:
>
> $f(x) = \frac{1}{\sqrt{2\pi\sigma^2}} e^-\frac{(x - \mu)^2}{2\sigma^2}$

By **CLT (central limit theorem)** if we have enough independent random variables, their properly normalized sum tends toward a normal distribution (or Gaussian) even if the original variables themselves are not normally distributed. Note that while this might hold true in theory, in practice this tends to vary. However, using the Gaussian distribution as an initial assumption is a common starting point.

**Decision boundaries** are where two boundaries (in this case Gaussians or two sets of data normally distributed) overlap. Decision boundaries can also be applied to 2-D, 3-D, or higher dimensions as well. Additionally,

> the classifier will classify all the points on one side of the decision boundary as belonging to one class and all those on the other side as belonging to the other class. -Wiki

## Error

We can also use Gaussians to understand errors. If we can determine error at decision boundaries by either integrating the Gaussian (finding the area under the curve) or looking up the area under the curve for a Gaussian distribution at specific standard deviations.

If we do not want to risk misclassifying specific data then we need to move the decision boundary in the direction (left or right for 1-D Gaussians) according to whichever error we want to lower.

## Bayes Classifier

Building on Bayes' Rule, we can specify a **Bayes classifier** which minimizes the probability of misclassification as:

$P(C_j | D) = \frac{P(D | C_j) * P(C_j)}{P(D)}\\$

- Where $C_j$ is the class and $D$ is the event (or data point)
- $P(D | C_j)$ is probability of generating $D$ given $C_j$
- $P(C_j)$ is probability of occurrence of $C_j$ (prior)
- $P(D)$ is probability of event $D$ occurring

## Naive Bayes

Bayes classifier is a powerful tool and so far we've use it to classify 1-D data. However, what happens when our data is multi-variable? We make the assumption that the data is _independent_ of each other which allows us to use the **naive Bayes classifier** which requires a number of parameters linear in the number of variables (features/predictors) in a learning problem.

Sometimes the naive Bayes classifier is known as **simple Bayes** because it can be represented as a Bayes network where the class $C_j$ (cause) points to the feature distributions $P(D_1 | C_1), ..., P(D_m | C_J)$ (effects). Once a class is established, each node in the net is independent (each node has conditional independence based on the class).

Because of the simple Bayes network for naive Bayes, calculations become much simpler:

- _Maximum likelihood_: $P(D | C_j) = P(D_1 | C_j) * ... * P(D_n | C_j) = \prod P(D_i | C_j)$

Other advantages of naive Bayes:

- Space efficient since we only have to store tables for each feature instead of a combination of features
- Computing metrics only require using look-up tables and multiplying values
- Not sensitive to irrelevant features

If features are **not** independent we can always switch back to using inference on Bayes networks.

## No Free Lunch

The **NFL (no free lunch) theorem** states that no particular algorithm is optimal for all problems, that is for any elevated performance over one class of problems is offset over another class of problems.

We may try to improve our performance for our algorithm by using **KDE (kernel density estimation)** to estimate the class-conditional marginal densities of data when using naive Bayes classifier to improve prediction accuracy. KDE works by using inferences about the population are made based on a finite data sample. KDE can be tuned via tuning (selecting the number of Gaussians give the best results).

The goal is to tune the classifier such that:

- Maximizes accuracy
- Minimizes overfitting
- Generalizes well from training to testing

## Selecting ML Algorithms

Given that there are many classes of problems, how do we select an effective ML algorithm? We might try to first visualize the data and note:

- Clusters of data without much concavity may be modeled with Gaussians
- Clusters of data overlap but still have distinct boundaries: k-nearest neighbors or applying a kernel method

However, higher dimensional data may require other methods such as decision trees or boosting to determine best features.

## Decision Trees

To use a decision tree, we can tabulate the sample values of the decision tree and start traversing the tree from the root down to come to an answer. If values are continuous, we can set a threshold for when to make a decision such that the results are binary leaf nodes.

Selecting attributes to construct a simple tree is key. We want to select attributes which can split our data into positive and negative examples. Effectively we want to ask a question that results in an answer that provides the most information towards the problem.

## Entropy

**Entropy** is the measure of uncertainty or _error_ in a random variable. It can be represented as:

$H(X) = - \sum P(X_i) * log_2(P(X_i))\\$

For binary cases we have:

$B(Q) = - (Q * log_2(Q) + (1 - Q) * log_2(1 - Q))\\$
$B(\frac{P}{P + N})\\$

where $P$ are the number of positive examples and $N$ is the number of negative examples and $B$ is the number of successes in our sample. Note that `log` is in base 2.

## Information Gain

What attribute should we use first? We can use _information gain_ to determine the initial attribute as follows:

$Remainder(A) = \sum \frac{P_k + N_k}{P + N} * B(\frac{P_k}{P_k + N_k})\\$
$Gain(A) = B(\frac{P}{P + N}) - Remainder(A)\\$

By using data from our tree, we can apply the information gain for prospective attributes and select the attribute that has the highest information gain (most bits of information).

Note that $B(\frac{P_k}{P_k + N_k})$ is the number of samples which are positive over the total number of samples (positive and negative). For more information see [slide 7 - Calculating Information Gain](https://homes.cs.washington.edu/~shapiro/EE596/notes/InfoGain.pdf).

## Random Forests

We can build on decision trees with an ensemble of decision trees e.g., _random forests_ where the results of all decision trees are averaged via **boostrap aggregation (a.k.a. bagging)**. The algorithm is as follows:

1. Input is a data set of size $N$ with $M$ dimensions
2. Sample $N$ times fom data
3. Sample $M$ times from attributes
4. Learn tree on sampled data and attributes
5. Repeat until $k$ trees

Decision trees and forests can help with determining which features we should investigate more and which features we should select in machine learning.

What if trees are large and hard to read? We can specify the decision tree leaves and set it to a small number to reduce the size of the tree.

Random forests can help determine:

- Feature stability
- Complementary features
- Percent contribution each tests makes in the tree

With **boosting** we can combine many weak classifiers to form an ensemble that can do the classifier task with the following equations:

$\alpha_t = \frac{1}{2} * ln(\frac{1 - \epsilon_t}{\epsilon_t} \gt 0)\\$
$H_{final}(x) = sign(\sum \alpha_t * h_t(x))$

Where $\alpha_t$ is the voting weights for weak classifiers and $\epsilon_t$ and $h_t(x)$ represent errors (misclassified examples).

## Neural Networks

A neural network is a:

> network or circuit of neurons, or in a modern sense, an artificial neural network, composed of artificial neurons or nodes... The connections of the biological neuron are modeled as weights. A positive weight reflects an excitatory connection, while negative values mean inhibitory connections. All inputs are modified by a weight and summed. This activity is referred to as a linear combination. Finally, an activation function controls the amplitude of the output. -Wiki

Some key components of a neuron include:

- Bias weight $W_{0, i}$
- Input links (e.g., $W_{j, i}$, $a_j$)
- Input function
- Activation function (typically non-linear, e.g., step or sigmoid)
- Output $a_i = g(in_i)$
- Output links

A **feed-forward network** is one without internal state, that is they implement functions on their inputs. A **recurrent network** does have internal state and have directed cycles with delays.

What if the output function is linear? Then the entire network can be reduced to the combination of the weights. However, the non-linearity of the activation function allows each neuron to make an individual contribution to the decision boundary. By slowly changing the weights through training, we can iteratively improve the decision boundary (which can improve prediction accuracy).

## Perceptron Learning

**Perceptron** is one component of a neural net and is:

> an algorithm for supervised learning of binary classifiers. A binary classifier is a function which can decide whether or not an input, represented by a vector of numbers, belongs to some specific class. It is a type of linear classifier, i.e. a classification algorithm that makes its predictions based on a linear predictor function combining a set of weights with the feature vector. -Wiki

The key components of perceptron learning could be highlighted as follows:

- The squared error for an example with input $x$ and true output $y$: $E = \frac{1}{2} * (y - h* W(x))^2$
- Perform optimization search by gradient descent: $\frac{\partial E}{\partial W_i} = -E \times g'(in) \times x_j$
- Simple weight update rule: $W_j = W_j + \alpha \times E \times g'(in) \times x_j$

The learning weight $\alpha$ will be slowly tuned during training such that each example will be able to contribute to the weights over time and until the perceptron converges on a set of weights (the decision boundary) which provide the least error.

Note that a single-layer perception can only produce a linear decision boundary (can perform `AND()` and `OR()` but not `XOR()`). We would need to add more hidden units (or layers) to the neural network which will allow us to model more types of functions.

## Back-propagation

We can train neural networks with **back-propagation** which:

> computes the gradient of the loss function with respect to the weights of the network for a single input–output example, and does so efficiently... This efficiency makes it feasible to use gradient methods for training multilayer networks, updating weights to minimize loss; gradient descent, or variants such as stochastic gradient descent, are commonly used. -Wiki

Back-propagation includes the following steps:

- Output layer: same as single-layer perceptron
  - $W_{j, i} = W_{j, i} + \alpha \times a_j \times \Delta_i$ where $\Delta_i = E_i \times g'(in_i)$
- Hidden layer: back propagate the error from the output layer
  - $\Delta_j = g'(in_j) \sum W_{j, i} * \Delta_i$
- Update rule for weights in hidden layer
  - $W_{k, j} = W_{k, j} + \alpha \times a_k \times \Delta_j$

In essence, back-propagation works by:

> computing the gradient of the loss function with respect to each weight by the chain rule, computing the gradient one layer at a time, iterating backward from the last layer to avoid redundant calculations of intermediate terms in the chain rule; this is an example of dynamic programming. -Wiki

An **epoch** refers to the process of updating the weights and summing the gradient updates for all the training examples. Researchers can gauge the difficulty of a problem by the number of epochs it takes for the model to converge and yield minimum error on the training set.

Neural networks with more than one hidden layer are also known as [deep learning networks](https://en.wikipedia.org/wiki/Deep_learning). This class of machine learning algorithm is able to utilize multiple hidden layers to extract higher-level features from raw input.

## Pros And Cons Of Neural Networks

Some benefits and drawbacks of neural networks include:

- Pros:
  - Can discover new features in data which can improve performance
  - Can visualize outputs of various layers of the network for some problems to gain intuition on how well the neural network is doing
- Cons:
  - Very difficult to understand how a neural network arrives at a result compared to a decision tree
  - Difficult to use the neural network to gain a better understanding of the problem domain

However, researchers are constantly finding ways to pull meaningful structures at multiple levels such that neural networks can be better understood.

## Unsupervised Learning

**Unsupervised learning** is a type of algorithm that learns patterns from untagged data and attempts to determine what classes are in the data and what data belongs to which class.

One unsupervised learning algorithm is **k-means clustering** which:

> is a method of vector quantization, originally from signal processing, that aims to partition n observations into k clusters in which each observation belongs to the cluster with the nearest mean (cluster centers or cluster centroid), serving as a prototype of the cluster. -Wiki

Previous iterative improvement techniques such as _random restart_ (in this case restarting to different initial conditions) will allow k-means clustering to work even if k-means appears to not converge.

In general, good clustering is characterized by _high_ inter-cluster variance and _low_ intra-cluster variance (well-separated clusters are desirable). Human activity tends to separate well in clusters in both time and space.

Another unsupervised learning algorithm is **EM (expectation-maximization)** which - similar to k-means - is:

> an iterative method to find (local) maximum likelihood or maximum a posteriori (MAP) estimates of parameters in statistical models, where the model depends on unobserved latent variables. -Wiki

EM works by iteratively alternating between two steps:

1. **E (expectation)**: creates a function for the expectation of the log-likelihood evaluated using the current estimate for the parameters
2. **M (maximization)**: computes parameters maximizing the expected log-likelihood found on the E step

The parameter estimates from the previous M step are then used to determine the distribution (e.g., Gaussian mixture) of the latent variables in the next E step. Since there are more parameters to estimate, EM typically takes longer than k-means to converge.

EM can be used in applications such as recognition of speech, handwriting, sign-language, and many other time-series.

## Section Quizzes

**Note**: will be somewhat limited for this semester.

### Challenge Question Quiz

_Given tabular data on AI students from last semester (provided), pick the most appropriate decision tree from these choices that predicts the student's grades this semester_. C, since it is the most compact and accurate representation (D is a fair choice but is not as compact) since we don't need the _reads book_ attribute based on the table.

### Cross Validation Quiz

_Suppose you are given a top secret project: design a system to identify when something important is happening at the Kremlin by observing the automobile traffic outside. To get you started, the government gives you 100 days worth of observations which are annotated as `important` or `unimportant`. Which of the following ways seems reasonable to create the best system possible_?

We want to randomly choose 80 days as training data and 10 days as test data. Train and test our system. Repeat the cycle until we have satisfactory results. At the beginning of the experiment, we can reserve 10 random days as a final test set which we will not include in our experiment until we believe our system is finished.

### Gaussians Quiz

_What is the probability for each of these distributions (provided), given an antenna length of 7_?

|        | Katydid | Grasshopper |
| ------ | ------- | ----------- |
| Mean   | 7.5     | 3.3         |
| STD    | 1.5     | 1.5         |
| $P(7)$ | 0.25    | 0.01        |

### Recognition Quiz

_Given data consisting of 10% positive examples and 90% negative examples, should you believe that a recognizer that works 90% of the time is working_? No, because it only works 90% of the time.

### Bayes' Rule Quiz

_Given a table based on name and gender (provided), is it likely for a person named Drew to be male or female_?

We can frame the problem as follows:

$P(Male | Drew) = \frac{P(Drew | Male) * P(Male)}{P(Drew)}\\$
$P(Male | Drew) = \frac{(1/3) * (3/8)}{(3/8)} = \frac{1}{3}\\$
$P(Female | Drew) = \frac{(2/5) * (5/8)}{(3/8)} = \frac{2}{3}\\$

Therefore, Drew is more likely to be female.

### Naive Bayes Quiz

_Given the following_:

$P(S) = 0.3\\$
$P(P | S) = 0.001, 0.25\\$
$P(B | S) = 0.1, 0.1\\$
$P(D | S) = 0.3, 0.01\\$

_Determine $P(S | \neg P, B, \neg D)$_

Applying Bayes' Rule:

$P(S | \neg P, B, \neg D) = \frac{P(\neg P, B, \neg D | S) * P(S)}{P(\neg P, B, \neg D)} = \frac{P(\neg P | S) *  P(B | S) * P(\neg D | S) * P(S)}{P(\neg P, B, \neg D | S) * P(S) + P(\neg P, B, \neg D | \neg S) * P(\neg S)}$

Now we can fill in the values from the look-up table to get $P(S | \neg P, B, \neg D) = \frac{0.999 * 0.2 * 0.7 * 0.3}{(0.999 * 0.2 * 0.7 * 0.3) + (0.75 * 0.1 * 0.99 * 0.7)} = 0.447$

### Decision Tree 1 Quiz

_Given the decision tree table (provided), what is the decision for the last situation? Will we play tennis_? Yes, since the outlook is _rain_ and the wind is _weak_.

### Decision Tree 2 Quiz

_Given the decision tree table (provided), determine the following information gains_:

First we calculate $B(\frac{9}{14}) = - (\frac{9}{14} _ log(\frac{9}{14}) + (1 - \frac{9}{14}) _ log(1 - \frac{9}{14})) = 0.94$

- $Gain(Outlook) = 0.94 - (\frac{5}{14} * B(\frac{2}{5}) + \frac{4}{14}*B(\frac{4}{4}) + \frac{5}{14} * B(\frac{3}{5})) = 0.246$
- $Gain(Temperature) = 0.94 - (\frac{4}{14} * B(\frac{2}{4}) + \frac{6}{14}*B(\frac{4}{6}) + \frac{4}{14} * B(\frac{3}{4})) = 0.028$
- $Gain(Humidity) = 0.94 - (\frac{7}{14} * B(\frac{3}{7}) + \frac{7}{14}*B(\frac{6}{7})) = 0.151$
- $Gain(Wind) = 0.94 - (\frac{8}{14} * B(\frac{6}{8}) + \frac{6}{14}*B(\frac{3}{6})) = 0.047$

### Boosting Quiz

_Given the classifier examples, calculate $\alpha_t$ for each boundary and pick the one that best classifies these samples_.

Using the equations:

$\alpha_t = \frac{1}{2} * ln(\frac{1 - \epsilon_t}{\epsilon_t} \gt 0)\\$
$H_{final}(x) = sign(\sum \alpha_t * h_t(x))$

1. $\alpha_t = 0.31$ since $\epsilon_t = \frac{7}{20}$
2. $\alpha_t = 0.20$ since $\epsilon_t = \frac{8}{20}$
3. $\alpha_t = 0.10$ since $\epsilon_t = \frac{9}{20}$
4. $\alpha_t = 0.42$ since $\epsilon_t = \frac{6}{20}$
5. $\alpha_t = 0.20$ since $\epsilon_t = \frac{8}{20}$
6. $\alpha_t = 0.88$ since $\epsilon_t = \frac{3}{20}$

The best classifier is when $\alpha_t = 0.87$ (highest value) so we select the last classifier.

### Neural Networks Quiz

_Fill in the provided truth table for a `NOR()` function. What type of activation function is this? Also what are the bias weight and the input weights_?

| $i_1$ | $i_2$ | $a$ |
| ----- | ----- | --- |
| 0     | 0     | 1   |
| 0     | 1     | 0   |
| 1     | 0     | 0   |
| 1     | 1     | 0   |

Therefore, $W_0 = 0.5$, $W_1 = -1$, and $W_2 = -1$. The activation function is the step function.

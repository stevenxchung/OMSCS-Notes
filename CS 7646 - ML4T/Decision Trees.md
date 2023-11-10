# Decision Trees

In this lesson we will cover how to build a decision tree learner from some factors, features, or attributes (things we can measure from a system typically denoted by $X$). These decision tree learners will help us predict (an output typically denoted by $Y$) what will happen based on our model.

## How To Build A Decision Tree

To build a decision tree we need the following:

- List of factors or attributes $X_1 ... X_N$
- Labels $Y$
- Decision nodes (e.g., binary decision at _split values_)
- Outgoing edges
- Leaves are values

We typically build from data examples (e.g., $X_1, ... X_N$). We split the tree at decision nodes which typically consist of a binary decision and a _split value_ (the value at which a decision is made).

## Decision Tree Code

A decision tree could be written as follows in Python (by JR Quinlan):

```python
build_tree(data):
    if data.shape[0] == 1:
        return [leaf, data.y, NA, NA]
    if all data.y same:
        return [leaf, data.y, NA, NA]
    else:
        # Determine best feature to split on
        split_val = data[:, i].median()
        left_tree = build_tree(data[data[:, i] <= split_val])
        right_tree = build_tree(data[data[:, i] > split_val])
        root = [i, split_val, 1, left_tree.shape[0] + 1]
        return append(root, left_tree, right_tree)
```

## How To Determine The Best Feature

How do we go about determining the best feature? We want to divide and conquer so we group data into most similar groups. Some approaches may include:

- Information gain: entropy
- Information gain: correlation
- Information gain: Gini index

In this class we will examine each feature $X$ and determine the best feature based on the correlation of the feature to the output $Y$.

## Random Trees

There are at least two drawbacks to the decision tree algorithm we have discussed so far:

1. Determining the best feature to split on requires determining the feature $X$ with the highest correlation with $Y$. This can be expensive if we have thousands of columns of features
2. Determining the median split value can also be expensive with more data

Therefore, we could leverage a **random tree** algorithm. The random tree algorithm adjustment can be given as follows (by A Cutler):

```python
build_tree(data):
    if data.shape[0] == 1:
        return [lead, data.y, NA, NA]
    if all data.y same:
        return [leaf, data.y, NA, NA]
    else:
        # Determine random feature to split on
        split_val = (data[random, i] + data[random, i]) / 2
        left_tree = build_tree(data[data[:, i] <= split_val])
        right_tree = build_tree(data[data[:, i] > split_val])
        root = [i, split_val, 1, left_tree.shape[0] + 1]
        return append(root, left_tree, right_tree)
```

But wait... Doesn't the addition of randomization make the tree worse and consequently the results of the tree? Yes, however we may leverage _ensemble learners_ techniques such as _bagging_ where various parts of the data are selected at random to create _bags_ of data. This technique allows a set of decision tree learners to train and output results which are then averaged - effectively reducing bias and overfitting.

## Strength And Weaknesses Of Decision Tree Learners

Below are the strengths and weaknesses of decision tree learners:

- Strengths:
  - Do not have to normalize your data
- Weaknesses:
  - Cost of learning is slower than linear regression and kNN (e.g., building decision forest is costly)
  - Cost of query is between linear regression (fastest) and kNN (slowest)

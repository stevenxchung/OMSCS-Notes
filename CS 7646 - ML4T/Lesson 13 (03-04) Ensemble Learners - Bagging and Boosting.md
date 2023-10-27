# Lesson 13

In 1988 Michael Kearns and Leslie Valiant asked:

> Can a set of weak learners be combined to created a single strong learner?

This question was answered in 2009 following a Netflix 2006 challenge: create a ML algorithm which can perform 10% better than their current algorithm for predicting movies the user may like to watch. The winning algorithm was comprised of an _ensemble_ of ML algorithms which were able to solve the challenge. In this lesson we will examine ensemble learners.

## Ensemble Learners

**Ensemble learners** are just many different types of learners combined together to produce an output where the output is the average of all learner outputs. What are some benefits of using ensemble learners?

- Lower error
- Less overfitting

These are possible since each learner inherently has their own biases. We may reduce these biases and mitigate overfitting by averaging the outputs of each learner.

## Bootstrap Aggregating (Bagging)

**Bootstrap aggregating (bagging)** may be accomplished by using the **same** learner and training each learner on a different set of the data (taking the data and creating new random _bags_ of data through _bagging_). After training, we average the outputs of each learner. This technique is able reduce bias and overfitting even with the **same** learner due to training on separate data sets and averaging results.

Note: We still want to separate the training _bags_ of data with the testing _bags_ of data.

## Boosting

**Boosting** or AdaBoost is a technique which takes the bootstrap bagging technique one step further by adding the following steps:

- Random _bag_ of data is created from the training set
- Learner is trained on the training set and tested using the **training** set again
- Training data outside of an RMSE limit will be weighted such that the next learner has a higher chance of being trained with a _bag_ of data consisting of the outlier data points

This process is repeated for all subsequent learners until the last learner and the result is that the average of all learners are _boosted_ in such a way that the output fits the test data more closely.

## Ensemble Learners: Bagging And Boosting Summary

In summary, ensemble learners are wrappers around existing methods which may benefit financial researchers as it is able to create models which reduces error and overfitting.

## Section Quizzes

### How To Build An Ensemble Quiz

_Given the following, what is the best way of going about building an ensemble_? D, we can train several parameterized polynomials of differing degrees then train several kNN models using different subsets of data thereby reducing bias.

### Which Is Most Likely To Overfit Quiz

_Given the following, which model is most likely to overfit_? Single 1NN model trained on all the data.

### Overfitting Quiz

_Given the following,, which is more likely to overfit as m increases_? AdaBoost since it assigns more specific data to subsequent learners in the ensemble.

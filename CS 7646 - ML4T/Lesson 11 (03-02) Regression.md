# Lesson 11

In this lesson we will learn more about supervised regression learning which utilizes regression algorithms to produce numerical outputs based on a set of numerical inputs.

## Parametric Regression

**Parametric regression** utilizes a line of best fit (e.g., linear, polynomials, etc.) to estimate our data and then finds the parameters (coefficients of the equation) to describe our overall model.

## K-nearest Neighbor

The **kNN (k-nearest neighbor)** approach utilizes data (instance based approach) to find the mean value of the nearest $k$ data points to produce a $y$ output.

A similar approach is **kernel regression** which utilizes weights on each kNN based on distance (evaluating contributions based on distance). The kNN approach only assigns equal weights to all kNN.

## Parametric Vs. Non-parametric

Comparing parametric vs. non parametric approach:

- Parametric:
  - Pros: we do not have to store the original data (space efficient - faster queries)
  - Cons: cannot update the model as more data is gathered (slower training)
- Non-parametric:
  - Pros: new data can be added easily (no parameters needed - faster training)
  - Cons: have to store all data points (huge data set - slow queries)

## Training And Testing

We should split up training and testing sets (out-of-sample testing) in order to evaluate that the trained model does in fact predict prices with some level of confidence and uncertainty.

Since we are examining stock prices over time in this class we should split up training and testing sets based on different time periods. Typically, training data is based on _older_ time periods while testing data is based on more _recent_ time periods.

## Learning APIs

The learning APIs may be structured for parametric and non-parametric approaches as follows:

- Linear regression:

  ```python
  learner = linear_regression_learner()
  learner.train(x_train, y_train)
  y = learner.query(x_test)
  ```

- kNN:

  ```python
  learner = knn_learner(k = <int>)
  learner.train(x_train, y_train)
  y = learner.query(x_test)
  ```

Essentially, the `learner` should first be trained with training sets (`x_train`, `y_train`), then be fed an input of `x_test` which would yield an output of `y`.

## Example For Linear Regression

The pseudo-code for linear regression may look something like this:

```python
class linear_regression_learner:
    def __init__():
        pass
    def train(x, y):
        self.m, self.b = <linear regression equation of choice>(x, y)
    def query(x):
        y = self.m * x + self.b
        return y
```

The API for kNN will be nearly identical.

## Section Quizzes

### How To Predict Quiz

_What should we do with these points (provided)_? Find the mean of their $y$ values such that an observed $y$ may be determined.

### Parametric Vs. Non-parametric Quiz

> Determine whether we should use a parametric or non-parametric regression approach for the following scenarios.

1. Parametric, since it is more obvious how $x$ and $y$ may be related (biased)
2. Non-parametric, since it is not obvious what happens when $x$ increases (unbiased)

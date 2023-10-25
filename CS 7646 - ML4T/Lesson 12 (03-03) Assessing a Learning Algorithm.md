# Lesson 12

Previously we learned about parametric (linear regression) and non-parametric (kNN) methods. In this lesson we will learn more about how to assess the pros and cons of each algorithm.

## Metric 1: RMS Error

How do we quantify how well our model fits the data? We may use the **RMSE (root mean squared error)** is the standard deviation of the residuals which is mathematically defined as follows:

$RMSE = \sqrt{\frac{\sum(y_(test) - y_(predict))^2}{N}}\\$

The RMSE tells us how far (on average) the model (prediction) is away from the actual (test) data. It is important to note that the _in-sample_ (training set) RMSE is different than the _out-of-sample_ (testing set) RMSE since the two sets of data are separate in practice.

## Cross Validation

Often researchers do not have enough data to analyze their algorithm. This can be remedied by **cross validation** whereby data is sliced into multiple chunks of training and testing. In this way, one set of data could be used for multiple trials by switching chunks of training and testing data for each trial.

## Roll Forward Cross Validation

An important note is that cross validation is not as effective in financial research if a trial includes the testing set before the training set (no peeking into the future). Consequently, a best practice is to always have our training set **before** our testing set and _rolling forward_ each pair of train and testing data sets until we run out of data.

## Metric 2: Correlation

Another metric we may use to evaluate our model is through **correlation**. This may be done by generating a set of $y_(predict)$ using the test set and then plotting the $y_(test)$ outputs on the same plot.

Correlation may be evaluated using the NumPy method `np.corrcoef()` where the coefficient of correlation may be in a range of -1 to 1 or 0 (no correlation).

Note that the correlation coefficient is **not** related to the slope of the correlation line.

## Overfitting

**Overfitting** occurs when the in-sample (training set) error is low but the out-of-sample (testing set) error is high. Given a parametric model, if the in-sample error decreases while the out-of-sample error increases, then our model is likely overfitting.

## Section Quizzes

### What Happens As K Varies Quiz

_Select the correct corresponding chart for each given $k$ value_.

1. The second chart since $k = 1$ averages over exactly one point
2. The first chart since $k = 3$ averages over three point
3. The second chart since $k = N$ averages over all points
4. False, as we increase k, we are _less_ likely to overfit (since we have more neighbors)

### What Happens As D Varies Quiz

_Select the correct corresponding chart for each given $d$ value_.

1. The second chart since $d = 1$ is linear
2. The first chart since $d = 2$ is quadratic
3. The second chart since $d = 3$ is polynomial
4. True, as we increase k, we are _more_ likely to overfit

### Which Is Worse Quiz

_Given RMSE of training and test set, which would you expect to be larger_? The out-of-sample (test set) error since it is data not previously seen.

### Correlation RMS Error Quiz

_In general as RMS error increases correlation.._. decreases since the trend line (prediction) does not match the data as closely.

### Overfitting Quiz

_Given the kNN plots, which depicts the model overfitting_? B, since the in-sample error decreases while the out-of-sample error increases (plot is independent on k so overfitting is observed at the beginning of the plot where $k = 1$).

### A Few Other Considerations Quiz

> Given the following additional considerations, select the best answer.

1. _Which is better on space saving for the model_? Linear regression
2. _Which is better on compute time to train_? kNN
3. _Which is better on compute time to query_? Linear regression
4. _Which is better on ease to add new data_? kNN

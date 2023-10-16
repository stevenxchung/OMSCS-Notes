# Lesson 3

**NumPy** is a numerical library that acts as a wrapper around underlying C and Fortran code (consequently, the runtime is optimal). NumPy's claim to fame is having ability to quickly vectorize, index, and broadcast n-dimensional arrays. It is a primary reason why many researchers decide to use Python for financial research.

## Relationship To Pandas

We previously discussed that NumPy is a wrapper around C and Fortran. Pandas is a wrapper around NumPy. This could be observed as the data in the dataframe is really an n-dimensional (`ndarray`) array surrounded by stock symbols (first row) and dates (first column).

When we treat a dataframe as an `ndarray`, we get many more methods which will enable us to do more with given data.

## Notes On Notation

To utilize `ndarray` we may specify certain values with:

```python
ndarray[row index, col index]
```

You may be familiar with accessing ranges from previous lessons. We may access ranges of values by specifying the starting indices (row or column) and ending indices (row or column) separated by a `:` to denote a range:

```python
ndarray[starting row index:ending row index, starting col index:ending col index]
```

## Section Quizzes

### Replace A Slice Quiz

_Which statement does the job_? The line:

```python
 nd1[0:2, 0:2] = nd2[-2:, 2:4]
```

### Specify The Datatype Quiz

_Specify the datatype for the given code (provided)_. `dtype = int`.

# Module 2

This module covers lessons 6 through 11. Notes will be primarily from the main lecture content rather than external resources.

In the following lessons, we will go over the underlying components of big data and statistical techniques. We will also cover issues that occur when learning from Big Data.

## Lesson 6 Overview

### Why Statistics

Data is everywhere and statistical techniques are used to make decisions that affect our lives. **Statistics** is:

> The science of collecting, organizing, presenting, analyzing, and interpreting data to assist in making more effective decisions

Consequently, **statistical analysis** is used to manipulate, summarize, and investigate data so that useful decision-making information results. The term statistics, derived from the word state, was used to refer to a collection of facts of interest to the
state.

### How To Mislead Through Poor Sampling

In order to analyze and interpret data, we must first collect it. The data that is collected is known as a **sample**. The sample is collected from a **population**.

### How To Mislead Through Poor Analysis

**Data analysis** is a process of gathering, modeling, and transforming data with the goal of highlighting useful information, suggesting conclusions, and supporting decision making. If we aren’t careful, data analysis could mislead by miscalculating trends.

### How To Mislead Through Interpretation

Interpreting data often involves displaying it in some useful way (e.g. chart, graphs, etc.). Unfortunately it is fairly easy to lie, cheat, manipulate, or mislead the public with graphical displays.

## Lesson 7 Python And Stats 101

### Defining Data Analytics

There are two types of analytics:

1. **Descriptive analytics**: methods of organizing, summarizing, and presenting data in an informative way
2. **Inferential analytics**: the methods used to determine something about a population on the basis of a sample

**Big data** focuses on issues with handling non-traditional _big_ data whereas **data analytics** focuses on gaining meaningful insight regardless of the size of the data. Data analytics depends heavily on machine learning.

### All About The Data

Stats starts with data, the facts and figures are collected summarized, analyzed, or interpreted. Data can come in various flavors:

- **Quantitative/qualitative**
- **Continuous**: data is infinitely divisible into whatever units a researcher may choose
- **Ordinal/rank**: in order but not necessarily equal
- **Categorical/discrete**: data consists of indivisible categories

### Introduction To Python And Jupyter

Objective for this section is to cover key concepts in statistics and
Python data analytics:

- Python basics for stats/data analytics
- Python data analytics libraries
- Jupyter Notebook

### Basic Statistical Measures And Data Analytics Using Python

**Jupyter Notebook** is an open source web-based interactive data analysis environment that supports iPython, a Python command shell for interactive computing.

### Hands On Tutorial: Pandas Basics 1

Optional tutorial for Pandas basics: [Pandas Tutorial 1: Pandas Basics (Reading Data Files, DataFrames, Data Selection)](https://data36.com/pandas-tutorial-1-basics-reading-data-files-dataframes-data-selection/).

## Lesson 8 Descriptive Statistics

### Types Of Studies And Sampling Errors

Recall that descriptive analytics may include:

- Frequency tables
- Histograms
- Mean
- Variance

While inferential analytics may include:

- **Population**: the entire set of individuals or objects of interest or the measurements obtained from all individuals or objects of interest
- **Sample**: a portion, or part, of the population of interest

There are various types of studies:

- **Experimental**: one variable is manipulated. A second variable is observed and measured to determine effect of manipulated variable. The measurements are then compared to see if there are differences between conditions
- **Correlation**: determine whether there is a relationship between two variables and to describe the relationship. A correlational study simply observes the two variables as they exist naturally
- **Quasi-experimental**: compares groups based on a variable that differentiate the groups (e.g., male/female)

The discrepancy between a sample statistic and its population parameter is called **sampling error**. We will look at this later through the lens of **sampling bias**.

### Median, Mean, And Mode

Recall the following definitions:

- **Mean**: the arithmetic average which is best for symmetric distributions
- **Median**: the middle value in an ordered sequence of observations which is _less_ sensitive to outliers (extreme scores) than the mean and thus a better measure than the mean for highly skewed distributions
- **Mode**: the most frequently occurring number

### How To Mislead With Averages

Since it is fairly easy to mislead with poor sampling, analysis, and interpretation, it should be no surprise that it would be easy to mislead with averages which can tell a completely different story when broken down (see real-estate example in lecture).

### Frequency Distribution

A **frequency distribution** keeps count of the number of times a data item occurs by keeping a tally. The number of times the item occurs is called the frequency of that item. With a _cumulative_ frequency distribution, you can also find a _running total_ of frequencies. It is useful to know the running total of the frequencies as this tells you the total number of data items at different stages in the data set.

### Variability

**Variability** (or dispersion) measures the amount of scatter in a dataset. Gives us an indication of indicate how well the average characterizes the data as a whole.

Commonly used variability methods include: range, variance, standard deviation, inter-quartile range, coefficient of variation, etc. The **five number summary**: is a summary of a distribution which consists of:

1. Min
2. Q1 (first quartile or min to 25% of the data)
3. Q2 (second quartile or 25% to 75% of the data where the upper bound is the median)
4. Q3 (third quartile or 75% to max of the data)
5. Max

**Anscombe's quartet** comprises four datasets that have nearly identical simple statistical properties, yet appear very different when graphed (see [Anscombe's Quartet Worksheet](https://www.geogebra.org/m/PNg789TK) for more information).

### Descriptive Statistics In Pandas

This section covers general Pandas methods and examples for descriptive statistics (see lecture for more details).

### Hands On Tutorial: Pandas Basics 2

Optional tutorial for Pandas basics: [Pandas Tutorial 2: Pandas Basics (Aggregation and Grouping)](https://data36.com/pandas-tutorial-2-aggregation-and-grouping/).

## Lesson 9 Inferential Statistics: Sampling Bias

### Inferential Statistics Introduction

Recall that inferential statistics provide numerical indications of how likely it is that a given event will occur.

**Statistical probability** is the odds that what we observed in the sample did not occur because of errors (random and/or systematic). In other words, the probability associated with a statistics is the **level of confidence** we have that the sample group that we measured actually represents the total population.

### Warm-up Exercise

This section includes a warm-up exercise (see lecture for more details).

### Simpson’s Paradox

**Simpson’s paradox** is a phenomenon in probability and statistics in which a trend appears in several different groups of data but disappears or reverses when these groups are combined.

### Biased Sampling

The equation to measure statistical bias can be summarized as:

$Bias = E(x) - Mean$

Where $E(x)$ is the [expected value](https://en.wikipedia.org/wiki/Expected_value) (or mean of the means) of our data and $Mean$ corresponds to the true mean. If the expected value is the same as the true mean then we may say that the estimator is _unbiased_ (unlikely in practice).

Since we can’t have a boundless survey that covers all data points. There are many different types of sampling bias:

- **Area bias**: introduced by conducting the study in a specific area that does not include a representative sampling of the population being studied
- **Selection bias**: introduced by the selection of individuals, groups or data for analysis in such a way that proper randomization is not achieved, thereby ensuring that the sample obtained is not representative of the population intended to be analyzed
- **Self-selection bias**: when a participants' decision to participate may be correlated with traits that affect the study, making the participants a non-representative sample
- **Leading question bias**: biases respondents by giving them a clue to the desired answer or leads respondents to answer a certain way, resulting in the tendency for respondents to agree with the direction of the leading question
- **Social desirability bias**: type of response bias that is the tendency of respondents to answer questions in a manner that will be viewed favorably by others

### Biased Sampling Example

_What seems to be a good sampling method (provided in lecture)_?

- B, since the distribution is normal and the population parameter is right in the middle of the distribution

### Types Of Randomized Sampling

Benefits of **randomized sampling** include:

- Reduces issues with sampling bias
- Ensures hat on the average the sample looks like the rest of the population
- Enables us to make rigorous probabilistic statements concerning possible error in the sample

Randomization methods include:

- Random sampling
- Simple random sampling

In **systemic sampling**, all data is sequentially numbered and every $n$ piece of data is chosen. We can combine this technique with random sampling to systematically generate a randomized sample.

Additionally, data may be divided into subgroups (strata) as in **stratified random sampling** or clustered as in **cluster random sampling** where each cluster is a miniature version of the entire population (useful when it is difficult and costly to develop a complete list of the population members).

The high cost of obtaining data has some companies looking for data on the internet. On the internet a common sampling method is **non-probability sampling** where participants are chosen or choose themselves so that the chance of being selected is not known.

### Sampling Bias Example Experiments

This section includes sampling bias examples (see lecture for more details).

## Lesson 10 Inferential Statistics: Causation Vs. Correlation

### Correlation Vs. Causation

Correlation tells us two variables are _related_. Types of relationship reflected in correlation:

1. $X$ causes $Y$ or $Y$ causes $X$ (**causal relationship**)
2. $X$ and $Y$ are caused by a third variable $Z$ (**spurious relationship**)

Of course, correlation does not imply causation!

### Correlation Vs. Causation Examples

This section includes correlation vs. causation examples (see lecture for more details).

### Relationships

A strong relationship between two variables does **not** always mean that changes in one variable causes changes in the other. The relationship between two variables is often influenced by other variables which are lurking in the background.

There are two relationships which can be mistaken for causation:

1. **Common response**: refers to the possibility that a change in a _lurking variable_ is causing changes in both our explanatory variable and our response variable
2. **Confounding**: refers to the possibility that either the change in our explanatory variable is causing changes in the response variable OR that a change in a _lurking variable_ is causing changes in the response variable

### Additional Material: Measuring Linear Correlation In Python

This section includes materials for measuring linear correlation in Python (see lecture for more details).

## Lesson 11 Inferential Statistics: Confidence

### Empirical Rule

The [empirical rule](https://www.investopedia.com/terms/e/empirical-rule.asp) or three-sigma rule states that 99.7% of data observed following a normal distribution lies within 3 standard deviations of the mean. Additionally, 68% of the data falls within one standard deviation, 95% percent within two standard deviations, and 99.7% within three standard deviations from the mean.

### Population Proportions And Margin Of Error

When sampling from the population, we could say with a certain degree of confidence - if the sample was _large enough and representative_, then the proportion of the sample would be approximately the same as the proportion of the population.

Since we are 95% certain that the population proportion is within 2
standard deviations of the sample proportion (by the empirical rule), the **margin of error** in this scenario is:

$MOE = \frac{1}{\sqrt{n}}$

Where $MOE# is margin of error and $n$ is the sample size.

### Sample Size Vs. Margin Of Error

The size of the population does not matter. Margin of error estimates how accurately the results of a poll reflect the _true_ feelings of the population. In general, as sample size _increases_, margin of error _decreases_.

# Lesson 22

In this lesson we will cover _diagnosis_ which identifies the faults responsible for a malfunctioning system. We will cover the following:

- Defining diagnosis
- Data and hypothesis spaces
- Mapping data to hypothesis
- Two views of diagnosis

## Defining Diagnosis

**Diagnosis** is to determine what is wrong with a malfunctioning device or what is the fault that causes a device to malfunction.

## Data Space And Hypothesis Space

We can think of diagnosis as a process that maps data from a _data space_ to a _hypothesis space_. In diagnosis the mapping between data from the data space to hypotheses in the hypothesis space is `N * N`. This can be very complicated very quickly.

Consequently, the data space is abstracted such that it could be mapped to an abstract hypothesis (bottom-up classification). Once an abstract hypothesis has been created, the next process is to refine the hypothesis such that the finalized hypothesis will maximize all data available in the data space (top-down classification).

## Problems With Diagnosis As Classification

There are several problems with diagnosis however:

1. One data point may map to multiple hypotheses
2. One hypothesis may map to multiple sets of data
3. Multiple hypothesis may map to multiple sets of data
4. Hypotheses may be mutually exclusive
5. Data points may interact

Point 5 is difficult to account for in practice so it is useful to shift from a sole classification approach to diagnosis to an abduction approach.

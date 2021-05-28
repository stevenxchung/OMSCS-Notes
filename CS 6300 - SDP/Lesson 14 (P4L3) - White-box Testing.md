# Lesson 14

In _black-box_ testing we tested a system without knowing the internal details of the system. This lesson will examine _white-box_ (structural) testing which involves the internal details of a system as wells as benefits and drawbacks.

## White-box Testing Overview

In **white-box testing**, the basic assumption is that executing the faulty statement is a necessary condition for revealing a fault.

Some advantages of white-box testing include:

- Can be measured objectively
- Can be measured automatically
- Can be used to compare test suites
- Allows for covering the coded behavior

There are also different kind of white-box testing:

- Control-flow based
- Data-flow based
- Fault based

## Statement Coverage

**Statement coverage** refers to the number of statements in the program (e.g., _expect a + b to be > 0_) and the coverage should measure the number of executed statements versus the total number of statements.

Statement coverage in practice is typically 80-90% with but not 100%.

## Control Flow Graphs

**Control flow graphs** are ways to visualize the control flow of a particular block of code.

## Branch Coverage

Similar to statement coverage, **branch coverage** refers to the number of branches in the program (a group of tests based on the control flow for a particular block of program) and the coverage should measure the number of executed branches versus the total number of branches.

## Condition Coverage

**Condition coverage** refers to the individual conditions in the program and are measured based on the number of conditions that are both true and false versus the total number of conditions.

## Modified Condition/Decision Coverage

**MC/DC (modified condition/decision coverage)** refers to testing important combinations of conditions and limiting test costs. This type of testing extends branch and decision coverage with the requirement that _each_ condition should affect the decision outcome independently.

## Section Quizzes

### Coverage Criteria Intro 1 Quiz

_Given the following code block_:

```java
printSum(int a, int b) {
   int result = a +b;
   if(result > 0)
      printcol("red", result);
   else if(result < 0)
      printcol("blue", result);
}
```

_What are some possible test specifications that will satisfy some of the requirements we just saw? What constraint must be specified for line 4 and 6 to be executed_?

1. Line 4: `a + b > 0`
2. Line 6: `a + b < 0`

### Coverage Criteria Intro 2 Quiz

_Implement the test cases matching the following specifications_:

1. `a + b` needs to be positive and the result should be red
2. `a + b` needs to be negative and the result should be blue

### Statement Coverage Quiz

_Given statement coverage is mostly used in industry and "typical coverage" target is 80-90% why don't we aim at 100%_?

That is not possible and would take too much time to reach that goal since almost always more lines of code are added to an active repository than can be covered.

### Subsumption 1 Quiz

_Does condition coverage imply branch coverage_? No, branch coverage covers branches while condition coverage covers conditions.

### Subsumption 2 Quiz

_Does branch and condition coverage imply branch coverage_? Yes, because it implies that branch and condition coverage needs to be met.

### Branch And Condition Coverage Quiz

_Add a test case (to provided code) to achieve 100% branch and condition coverage_.

Set `x = 1` and `y = -1`.

### Review 1 Quiz

_Given the following code block_:

```java
int i;
read(i);
print(10 / (i - 3));
```

_Test if test suite (1, -5), (-1, 2.5), (0, -3.333), does this test suite achieve path coverage_? Yes, since there is only one path.

### Review 2 Quiz

_Referring to the previous path coverage test, does this test suite reveal the fault at line 3_? No, because there is no input that causes it to `print(10/0)`.

### Review 3 Quiz

_Given the following code block_:

```java
int i = 0;
int j;
read(j);
if ((j > 5) && (i > 0))
   print(i);
```

_Can you create a test suite to achieve statement coverage_? No, because `i = 0` is always true

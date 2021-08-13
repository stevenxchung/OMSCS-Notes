# Lesson 12

In this lesson we will cover software testing which includes software verification and validation. We will also cover some techniques for software testing, TDD (test-driven development), and agile methods which will allow more flexibility in the previously discussed RUP activities.

## General Concepts Introduction

Software is buggy, in fact experts argue that software bugs cost the US economy around $60B a year. On average, there are about 1-5 bugs/1000 lines of code. The idea of 100% correct mass-market software is impossible. Therefore, we need to verify the software as much as possible.

## Failure, Fault, and Error

There are three main concepts we should know when testing software:

1. **Failure**: an observable incorrect behavior
2. **Fault**: incorrect code
3. **Error**: cause of a fault

## Verification Approaches

How can we verify software? There are several approaches:

1. **Testing**: testing if a piece of software returns an expected output given an input
   - Pros: does not generate false positives
   - Cons: is incomplete
2. **Static verification**: considers all possible inputs
   - Pros: considers all program behaviors
   - Cons: generates false positives
3. **Inspections**: a manual and typically group activity that involves reviewing a piece of software for correctness
   - Pros: systematic and thorough
   - Cons: informal and subjective
4. **Formal proofs of correctness**: a proof (e.g., simulation that verifies physics or mathematics) that piece of software correctly implements what is specified in the specification document
   - Pros: strong guarantees
   - Cons: complex and expensive

## Testing Introduction

Testing means to execute a program on a tiny sample of the input domain. More generally, testing is a:

- Dynamic technique
- Optimistic approximation

## Testing Granularity Levels

There are different levels of testing:

1. **Unit**: testing one unit of software (e.g., if a variable is doubled)
2. **Integration**: testing a particular software feature (e.g., does the home page load the correct user data in order)
3. **System**: testing the whole software (e.g., do the various application features work?)
4. **Acceptance**: testing if the software system meets the customer's specifications
5. **Regression**: testing if the new features and unchanged features work as expected

## Alpha And Beta Testing

We previously discussed developer testing but there are also different types of testing by organization:

- **Alpha**: testing done by users internal to the developing organization
- **Beta**: testing done by users external to te developing organization

## Black And White Box Testing Introduction

There are also testing techniques such as:

- **Black-box testing**: testing a piece of software based on a description of the software (specification). The goal is to cover as much specified behavior as possible. However, it cannot reveal errors due to implementation details
- **White-box testing**: testing that looks at software implementation and is design to covered as much coded behavior as possible. However, it cannot reveal errors due to missing specifications

## Section Quizzes

### Failure, Fault, and Error 1 Quiz

_Given the following code_:

```java
int doubleValue(int i) {
   int result;
   result = i*i;
   return result;

```

_A call to doubleValue(3) returns 9. This is_: a failure.

### Failure, Fault, and Error 2 Quiz

_Where is the fault that causes the failure in the program (provided previously)? Write the line number of the code that contains the fault_.

In line 3 where `result = i*i;`.

### Failure, Fault, and Error 3 Quiz

_What is the error the caused the fault (given previously)_?

The `result` should be the input multiplied by 2 not by itself. However, as a user we would not know what the error is, only the developer would know.

### Verification Approaches Quiz

> 50% of my company employees are testers, and the rest spends 50% of their time testing.

_Who said that_?

Bill Gates when he was at Microsoft.

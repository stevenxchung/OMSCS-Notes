# Lesson 11

In this lesson we will revisit the UML diagram exercise we covered previously in the library exercise. We will focus on how we can leverage OCL to address additional aspects of the diagram.

## Limitations

For UML diagrams, either the specification as given by the diagram must be supplemented or an entirely new specification must be introduced.

## Side Effects

**Side effects** specify an even more complex situation - one where an operation actually results in a change of state.

## Observations

We should be open during the process of analysis to the possibility of new requirements arising. This could include further consultation with the customer. A simple set of requirements can have so many issues - this should illustrate the value of constructing an OCL specification.

## Section Quizzes

### Requirements Quiz

_Determine which of the requirements the diagram is able to adequately address with a `+` or cannot address with a `-`._

- Req 1: -
- Req 2: +
- Req 3: -
- Req 4: -
- Req 5: -
- Req 6: -
- Req 7: -
- Req 8: -
- Req 9: +
- Req 10: -
- Req 11: -

## Requirement 6 Quiz

_Which of the classes in the diagram is most appropriate to associate with Requirement #6 (checking out books)?_

`Book` is the most appropriate class.

## CheckedOut Quiz

_Does the constraint for the checkout period sound more like a class invariant or an operation?_

Sounds more like an invariant.

## Requirement 7 OCL Quiz

_Complete the OCL constraint for Requirement #7 (AV material checkout)._

- Attribute name: checkOutPeriod
- Operator: =
- Value: 2

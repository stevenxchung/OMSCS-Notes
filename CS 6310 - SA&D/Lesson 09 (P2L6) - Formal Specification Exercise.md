# Lesson 9

We need to know what a program is supposed to do before we begin to write it. In this lesson we will focus on **specifications**. Specifications are informal text in a structured document.

## FOL

There are two notations for specifications:

- Mathematical logic
- OCL

**FOL (First Order Logic)** enables you to precisely express propositions, combine them, and quantify them.

## OCL

The other language we will use is **OCL (Object Constraint Language)** which is a part of UML. OCL provides a syntax for FOL that can be used to annotate UML diagrams.

## Sorting

A simple example will be to sort vectors of integers in ascending order (see lecture for full example). How to express this using specification notation?

## Process

The process of expressing the problem is to break the specification into three pieces:

1. Signature: what does the program look like?
2. Pre-condition: what must be true about the input?
3. Post-condition: what must be true about the output?

## Signature

The signature gives the name of the program, the names and types of the input arguments and the name and type of the results.

For `SORT` the signature is: `Vector<int> Y = SORT(Vector<int> X)`, where `X` and `Y` have explicit names (can be used in pre and post conditions). Additionally, `int` could be any data type.

## Summary

To summarize:

- Sometimes you need a way to precisely express exactly what functionality is required by a system
- A variety of formal languages and tools exists for writing such specifications
- The effort can save a lot of rework resulting from misunderstood requirements

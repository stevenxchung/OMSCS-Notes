# Lesson 20

As software architecture evolves so do the tools required to describe architectures. In this lesson, we will examine **ADL** (Architecture Description Language).

## ACME

**ACME** is a simple extensible ADL developed by CMU and USC-ISI specifically designed to facilitate the interchange of architecture descriptions.

## ACME Features

Some of the features of ACME include:

- Vocabulary for talking about architectures
- Extension mechanism enabling tool-specific sub-languages to be embedded
- Generics, families, and types for defining architectural styles
- Descriptions can be converted into first order logic

## Decomposition

For software architectural descriptions, there are two kinds of decompositions: horizontal and vertical.

## Representations

ACME supports vertical composition by allowing any component or connect to be represented by one or more lower level views. Each view is called a **representation**. There is a mapping between the levels called a **rep-map**.

## Extending ACME

Software architectures of any degree of complexity can be represented either textually or graphically. Many tools require more detailed information. ACME includes an extension mechanism called the **property sub-language**.

## Properties

A **property** in ACME is an identifier that can be associated with a value. Such name-value pairs are parsed by not interpreted by ACME.

## Families

ACME supports the modeling of architectural styles using **families**. Element types make up the vocabulary of the family. Style rules are encoded as properties for using the family.

## Open Semantic Framework

**Open semantic framework** supports reasoning about software architectural descriptions.

## ACME Limitations

The main goal of ACME is to enable architectural descriptions to be expressed in a way that can be used by a variety of tools. However, it lacks features found in more elaborate ADLs.

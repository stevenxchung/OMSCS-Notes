# Lesson 5

In this lesson we will focus on requirements and prototyping including requirements engineering activities and object-oriented design.

## Interview With Jane Cleland-Huang

What are **software requirements**? Software requirements provide us a description of what a system has to do. They typically describe functionality of the features that system has to deliver in order to satisfy its stakeholders.

What is **RE (requirements engineering)**? RE covers a number of activities such as:

- Working with stakeholders to discover requirements
- Analyzing discovered requirements to weigh tradeoffs
- Specifications that describe software functionality
- Validation of deliverable
- Requirements management process (change management)

RE includes _engineering_ in the term because it requires a systematic process throughout the whole lifecycle of the deliverable.

## General RE Definition

RE establishes the services that the customer requires from the software system. RE also establishes the constraints under which the software system operates.

**SRS (software requirements specification)** which is established under RE should focus on the the _what_ (e.g., what should our software system do) rather than the _how_ (e.g., how should our software system accomplish tasks).

## Software Intensive Systems

What do we mean when we talk about software systems? A software system is really a software _intensive_ system that includes software, hardware, and context in which the system is used.

## Software Quality

Based on what we discussed about software intensive systems, software quality is not just a function of our software but also the user experience provided by our deliverable.

## Identifying Purpose

Identifying a purpose is to define requirements. This is a very difficult task due to factors such as:

- Sheer complexity of purpose/requirements
- People not knowing what they want
- Changing requirements
- Conflicting requirements

## Completeness And Pertinence

It is very difficult to have a complete picture of the software. Another issue occurs when software developers collect too many irrelevant requirements. Requirements must be accurate, complete and pertinent.

## RE Definition Breakdown

The RE definition can be broken down as follows:

1. RE is a set of activities
2. Communication is as important as analysis
3. Quality means fitness-for-purpose (must understand software purpose)
4. Designers need to know how and where the system will be used
5. RE is split between needs and what is possible
6. Successful RE depends on identifying all stakeholders

## Defining Requirements

Requirements can be application domain or machine domain:

**Application domain** is the world in which software will operate and are characterized by:

- Domain properties
- Requirements

**Machine domain** is the domain on which the software will run and are characterized by:

- Computers
- Programs

Lastly, **specifications** are formal descriptions of what the software system should do in order to fulfill requirements in both domains. Specifications must take into account:

1. _Events_ in the real world that the machine can _sense_
2. _Actions_ in the real world that the machine can _cause_

## Functional And Non-functional Requirements

There are two general types of requirements for system at a high-level:

1. **Functional**: what the system does or computation to solve the problem
2. **Non-functional**: refers to the system's qualities, e.g., security, usability, etc.
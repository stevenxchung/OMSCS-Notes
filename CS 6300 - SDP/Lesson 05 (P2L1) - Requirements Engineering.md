# Lesson 5

In this lesson we will focus on requirements and prototyping including requirements engineering activities and object-oriented design.

## Interview With Jane Cleland-Huang

Q: What are **software requirements**?

A: Software requirements provide us a description of what a system has to do. They typically describe functionality of the features that system has to deliver in order to satisfy its stakeholders.

Q: What is **RE (requirements engineering)**?

A: RE covers a number of activities such as:

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

## User And System Requirements

We also must take into account user and system requirements:

**User requirements**:

- Written for customers
- Often in natural language, no technical details

**System requirements**:

- Written for developers
- Detailed functional and non-functional requirements
- Clearly and more rigorously specified

## Requirements Origins

So where do these requirements come from? There are many possible sources, below are some of the main sources:

- Stakeholders
- Application domain
- Documentation

## Elicitation Problems

During software development, there exists several elicitation problems which make gathering requirements difficult:

1. Thin spread of domain knowledge
2. Knowledge is tacit
3. Limited observability
4. Bias

## Traditional Techniques

Thankfully, there are some techniques we can use to combat elicitation issues discussed earlier:

- **Background reading**: reading through existing documentation on the problem space to gather requirements but can be cumbersome and open-ended
- **Hard data and samples**: includes using already collected data and samples to establish requirements but can be difficult to determine what data is useful
- **Interviews**: can probe users in-depth to determine requirements but typically requires an expert who knows how to interview to optimize results
- **Surveys**: can quickly collect information from a large number of people but can constrain the information the users can provide
- **Meetings**: can collectively decide on useful or not useful information for requirements but needs to be properly organized to be optimal

## Other Techniques

There also exists other techniques for requirements gathering:

- **Collaborative techniques**: supports incremental development of complex systems with large diverse user populations
- **Social approaches**: techniques which exploit social sciences to better collect information from stakeholders and environment (e.g., ethnographic techniques which can help with observing users in their original environment)
- **Cognitive techniques**: leverages cognitive science to discover expert knowledge

## Modeling Requirements

Once requirements are established, it is important to decide what to model and how to model:

1. _What to model_ depends on which aspects of the requirements are most important
2. _How to model_ will offer different perspectives on the models selected for modeling

## Analyzing Requirements

There are three steps when analyzing requirements:

1. **Verification**: _developers_ check if the requirements accurately address customer needs as well as completeness, relevance, etc.
2. **Validation**: _stakeholders_ check if the collected requirements define the system that the stakeholders desire
3. **Risk analysis**: relates to analyzing any possible risks involved in development and mitigating those risks

## Requirements Prioritization

Requirements should be prioritized as there are limited resources and an inability to satisfy all requirements in the real world. Prioritization may be categorized as follows:

- Mandatory: i.e., a feature that is critical to address customer needs
- Nice to have: i.e., a feature that may compliment customer needs
- Superfluous: i.e., a feature that is not actually needed

## Requirements Engineering Process

In general, there are four main steps in the requirements engineering process:

1. **Elicitation**: abstracting requirements from various sources
2. **Modeling**: representing the requirements using formal notation
3. **Analysis**: identifying possible issues with the requirements
4. **Negotiation**: discussions between developers and stakeholders regarding requirements until a consensus is reached

Note that this process is a highly iterative process and make take many iterations before requirements are finalized.

## SRS

Why is the SRS important? The SRS offers a way to communicate requirements to others. Different projects require different SRS. The IEEE has defined a standard in which requirements may be specified:

1. Introduction
2. User requirements
3. System requirements (functional and non-functional)

It is important to note that requirements should have the following properties:

- Simple (specific not compound)
- Testable
- Organized
- Numbered (traceability purposes)

## Section Quizzes

### Pertinence Quiz

_Consider an information system for a gym. In the list below, mark all the requirements that you believe are pertinent_.

- Members of the gym shall be able to access their training programs
- The system shall be able to read member cards
- Personal trainers shall be able to add clients

### Completeness Quiz

> Consider an information system for a gym. In the list below (provided), mark all the requirements that you believe are pertinent.

1. _Is the above list complete_? No

### Irrelevant Requirements Quiz

_Why can irrelevant requirements be harmful_?

- They can introduce inconsistency
- They can waste project resources

### Defining Requirements Quiz

> Referring to the figure that we just discussed (provided), indicate, for each of the following items, whether they belong to the machine domain (1), application domain (2), or their intersection (3).

1. _An algorithm sorts a list of books in alphabetical order by the first author's name_. Machine domain
2. _A notification of the arrival of a message appears on a smart watch_. Their intersection
3. _An employee wants to organize a meeting with a set of colleagues_. Application domain
4. _A user clicks a link on a web page_. Their intersection

### Requirements Quiz

_Which of the following requirements are non-functional requirements_?

- The WordCount program should be able to process large files
- The Login program for a website should be secure

### Requirements Prioritization Quiz

> Imagine that you have collected the following set of five requirements for an ATM system but only have resources to satisfy two, possibly three of those
>
> Suitably prioritize the requirements by marking them as Mandatory, Nice to have, or Superfluous.

1. _The system shall check the PIN of the ATM card before allowing the customer to perform an operation_. Mandatory
2. _The system shall perform an additional biometric verification of the customer's identity before it allows the customer to perform an operation_. Superfluous
3. _The system shall allow customer to withdraw cash using an ATM card_. Mandatory
4. _The system shall allow customer to deposit money using an ATM card_. Nice to have
5. _The system shall allow customer to change the PIN of an ATM card_. Superfluous

# Module 3

This module covers lessons 12 through 18. Notes will be primarily from the main lecture content rather than external resources.

In the following lessons, we will go more in-depth on the different types of AI algorithms deployed in practice (e.g., facial recognition, NLP, and predictive algorithms). We continue to focus on instituting _fairness_ in these algorithms by examining scenarios, tools used in each scenario, ethical issues, and possible solutions.

## Lesson 12 Word Embeddings

### Fairness In AI/ML

The goal of this lesson is to understand and apply basic AI/ML techniques to data scenarios, with a focus on instituting _fair_ practices when designing decision-making systems based on big data.

### Word Embedding (NLP)

- Word embeddings are a _set of techniques_ in **NLP (natural language processing)** for identifying similarities between words in a corpus by using some type of model to _predict the co-occurrence_ of words within a small chunk of text
- Word embeddings _transform human language_ meaningfully into a _numerical form_. This allows computers to understand the nuances implicitly encoded into our languages

### Word Similarity And Relatedness

How do we determine similarities and relatedness for words?

- _Representing words_ has become a convenient way to compute _similarities_ (e.g., pizza to pasta)
- **Relatedness**: measures the semantic similarity between words (e.g., pizza to Italy)

Regarding vector space models:

- **Vectorization**: the process of converting text to numbers. This conversion helps us to measure the similarity between words
- **Vector space model**: an algebraic model for representing text as a vector of identifiers in which semantically similar words are mapped to proximate points in geometric space

Vectors space models can be represented as:

- **Document occurrence**: assign identifiers corresponding to the count of words in each document (from a cluster of documents) in which the word occurs
- **Word context**: quantify co-occurrence of terms in a corpus by constructing a co-occurrence matrix which captures the number of times a term appears in the context of another term

### Cosine Similarity And Word Analogy

We can use **cosine similarity** to compute the similarity between two word vectors. However, this notion of similarity depends on what vector representation is selected to represent the words found in your corpus. Given two vectors $a$ and $b$, the cosine similarity is defined as the _dot-product_ of the two vectors divided by their _length_.

Word analogy problems have become one of the _standard tools for evaluating context-based word vectors_.

### Word Embeddings (`word2vec`)

> Word2vec is a technique for natural language processing published in 2013. The word2vec algorithm uses a neural network model to learn word associations from a large corpus of text. Once trained, such a model can detect synonymous words or suggest additional words for a partial sentence. As the name implies, word2vec represents each distinct word with a particular list of numbers called a vector. The vectors are chosen carefully such that a simple mathematical function (the cosine similarity between the vectors) indicates the level of semantic similarity between the words represented by those vectors. -Wiki

## Lesson 13 Bias In Word Embeddings

### Bias In Word Embedding

The following biases occur in word embeddings:

- Cultural biases
- Biased framings of women
- Ethnic stereotypes
- African-american names are associated with unpleasant words
- Male names associated more with career words, female names with family words
- Competence adjectives are biased toward men

### Why Does This Happen (Word Embeddings)

In general, embeddings reflect ethnic stereotypes over time.

How do we go about fixing this issue? A couple of ways:

1. **Identify bias direction**: may involve calculating error differences and then averaging out the result (average difference)
2. **Neutralize**: for every word that is **not** definitional, _project_ to get rid of bias
3. **Equalize pairs**: for each pair of words, ensure that the vector length is equal

## Lesson 14 Facial Recognition

### Facial Recognition

Example of facial recognition:

- Exam identity verification
- Physical building access
- Computer/device access
- Passport verification
- Jail management systems and booking
- Law enforcement investigations
- Photo tagging in Facebook
- Smartphone and app access

### Facial Recognition Algorithms

In general, facial recognition algorithms involve:

- **Face detection**: to identify and locate human faces in an image regardless of their position, scale, in plane rotation, orientation, pose (out of plane rotation), and illumination
- **Two-class classification**: face vs. non-face

The objective of any face detection algorithm is to locate all faces, irrespective of:

- Positioning (e.g., frontal, side-view, upside down)
- Rotation and pose
- Occlusion
- Resolution or image quality
- In a _single_ image or a _sequence_ of images involving motion (such as in video)
- After detecting the face, image is typically _segmented_ based on this information, and normalizes for translation, scale, rotations

Types of facial recognition tasks:

- **Multi-class classification**: one person vs. all the others
- **Face identification**: given an image that belongs to a person in a database, tell which person it is
- **Face verification**: Given an image, verify whether it is from the same person it is claiming to be

**Face space** is a theory in psychology that defines a _multidimensional_ space in which recognizable faces are stored. The representation of faces within this space are according to _invariant features_ of the face itself.

Human biases during facial recognition include:

- **“Own-race” bias**: We are over twice as likely to identify own own-race than other-race. Less hits, more false alarms with other-race faces than with own-race faces
- **"Own-gender" bias**
- **"Own-age" bias**

Appearance-based methods (classifier) can be trained, typically using positive (and usually negative) examples of faces, for face recognition applications.

### Deep Neural Network Examples

**Deep neural networks** are now one of the most common methods for face recognition and in encoding attributes from the images. The general procedure includes:

1. _Extract_ facial features for an image
2. _Feed_ the features into a classifier such as a neural network
3. _Classify_ the image/features to one of the pre-selected emotion categories (6 universal emotions + neutral)

Cross-cultural research by Ekman shows (and has also been refuted by others) that some emotional expressions are universal:

- Happiness
- Sadness
- Anger
- Fear
- Disgust/surprise

Emotions are reflected in _voice_, _hand_ and _body gestures_, and mainly through _facial expressions_. By knowing a person’s emotion, an AI/ML system can adapt to the user. Responding appropriately to the user’s emotional state will be perceived as more natural, engaging, and trusting.

In addition to market research, emotion detection can be used to monitor driver attention, monitor movie audience reactions, and even help healthcare professionals assess the wellbeing of patients.

## Lesson 15 Bias In Facial Recognition

### Issues With Facial Recognition Algorithms

Identification becomes problematic due to:

- Resolution (not enough pixels)
- Facial pose (e.g., angled)
- Illumination
- Occluded facial areas

These result in distorted facial features, high errors in measurements, and limited data or feature points to analyze. No standards exist for _acceptable_ error rates meaning _success_ is subjective. It varies depending on the facial recognition system used and the application it’s used in. There are two kinds of errors:

1. **False-positives**: wrongly matching innocent people with photos in the database
2. **False-negatives**: not catching people even when their photo is in the database

### Bias In Facial Recognition

Some additional problems with facial recognition bias:

- **Priors**: demographics in law enforcement databases $\not =$ general population. More males, more minorities, younger age
- **Bias**: The most prominent study (Klare et al.) found that several leading algorithms performed worse on underrepresented minorities, women, and young adults than on Caucasians, men, and older people, respectively
- **Consequences**: If the suspect is an underrepresented minority, the system is more likely to erroneously fail to identify the right person, potentially causing innocent people to be bumped up the list—and possibly even investigated
- **Awareness**: e.g., police claim that their photo comparison algorithm is **not** biased towards minorities since it matches through distance and patterns only instead of through skin, age, or sex but in practice this may not be the case
- **No tests for bias**: There is no _independent_ testing regime for biased error rates, e.g., two major face recognition companies admitted that they did not run these tests

### Why Does this Happen (Facial Recognition)

Why do biases occur in facial recognition systems?

- Training sets are _hard_ to get
- If you are testing your accuracy on equally non-diverse image set, you will **not** get real-world accuracy measurements
  - To address – some companies make an effort to pay for extra images
  - Others, scrape the web to get the images that they need, which sometimes causes push-back

What are some ways bias is being addressed in industry:

- **InclusiveFaceNet**: improving face attribute detection with race and gender diversity
- Google researchers discuss a system for detecting _face attributes_ by learning the different attributes associated with different race and gender identities
- Example _face attributes_ for _race representation_ include: bangs, big lips, blurry, chubby, double chin, narrow eyes, pale skin, pointy nose, wearing necklace, and young

## Lesson 16 Predictive Algorithms Part 1

### What Are Predictive Algorithms

**Predictive algorithms** define and learn models to estimate likely outcomes based on historical data. Why predictive algorithms?

- Some outcomes may be _difficult_ to model except with examples (e.g., recognition of faces)
- The amount of knowledge needed to find correlations may be _too large_ for encoding by humans or by hand (e.g., in medical diagnostics)
- Some problems may adapt quickly over time and continuous redesign of the system by hand may be difficult (e.g., search engines)

Typical prediction tasks include:

- **Classification**: classify an instance into a category
- **Regression**: predict a numerical label for an unlabeled observation
- **Clustering**: discovering groups of similar instances

Prediction models continuous-valued functions, i.e., predicts unknown or missing
values. Prediction is _similar_ to classification: construct a model and use model to predict unknown value. Prediction is _different_ from classification, prediction models continuous-valued functions versus predicting categorical class labels.

Another issue that occurs in predictive algorithms is _generalization_:

- How do we ensure good generalization, i.e., avoid “over-fitting” on our particular data samples?
- We are ultimately interested in good performance on new (unseen) test data (i.e., the population).

### Predictive Algorithm Examples

This section includes real-world predictive algorithm examples (see lecture for more details).

### Learning Methods

As mentioned previously, predictive algorithms include:

- **Supervised learning**: labels are provided and there is a strong learning signal present between inputs and outputs (e.g., classification, regression)
- **Unsupervised learning**: there is no direct learning signal or obvious correlations between inputs and outputs. We’re simply trying to find some structure in the data (e.g., clustering, dimensionality reduction)

### Clustering

Clustering methods include the following tasks:

- Finding a picture in the database which is closest to the query image
- Checking feature labels
- Declaring the class of query image to be the same as that of the closest picture

In general, clustering can be accomplished by:

1. Finding a group structure in the data
2. Establishing the existence of classes given features
3. Mapping each data point to a discrete cluster index

### Regression

Some observations when doing regression:

- **Ockham’s razor**: prefer the simplest hypothesis consistent with data
- **Similarity/continuity bias**: similar inputs should have similar outputs

Two types of generalization errors:

1. **Overfitting**: models with too _many_ parameters may fit the training data well (_low bias_), but are sensitive to choice of training set (_high variance_)
2. **Underfitting**: models with too _few_ parameters may not fit the data well (_high bias_) but are consistent across different training sets (_low variance_)

### Decision Tree

**Decision trees** are simple, practical, and easy to interpret. Given a set of instances (with a set of features), a tree is constructed with internal nodes as the features and the leaves as the classes:

- Phase one: _tree construction_
  - At start, all the training examples are at the root
  - Examples are partitioned recursively based on selected attributes
- Phase two: _tree pruning_ is where branches are removed that are identified as noise or outliers
- _Testing_: the attribute values of a new data example are tested against the
  decision tree

## Python Predictive Algorithms (Supplemental Material)

This section includes supplemental material on Python predictive algorithms (see lecture for more details).

## Lesson 17 Predictive Algorithms Part 2

### Crime-based Predictive Algorithms In Use​

Crime-based predictive algorithms have many applications. One type of application is identifying potential crime hot spots based on where crime is _previously reported_, **not** where it is known to have _occurred_.

### COMPAS

**COMPAS (Correctional Offender Management Profiling for Alternative Sanctions)** is a 137-question questionnaire and predictive model for _risk of recidivism_. The model is a proprietary secret of Northpointe, Inc.

Supreme Court of Wisconsin ruled that judges are allowed to use COMPAS scores, but they:

- Must receive them accompanied by disclaimers and criticisms
- Can use them as a factor to give non-prison alternatives to prison
- Can use them as a factor to impose terms and conditions in parole

_Tradeoffs_ must be built into the prediction algorithm and are _policy decisions_.

### Judges’ Release Decisions Vs. Machine Predictions And Crime Risk​

Decisions to jail vs. releasing defendants:

- Kleinberg et al. (2017) compares the accuracy of human decisions and machine predictions in the criminal justice system
- Data: 750,000 individuals arrested in New York City between 2008-2013

Are predictive algorithms at least better than people?

Discrimination/suboptimal choice is **not** driven entirely by deep-rooted beliefs. Decisions can also vary greatly based on factors _unrelated_ to substantive features of the issue at hand.

Use of big data for predictive analytics raises serious ethical concerns, particularly in the context of _criminal justice_. How large should the gains be from machine prediction before its adopted? Tension between two views:

1. Should a person be treated _differently_ simply because they share attributes with others who have higher risks of crime?
2. Should police/judges/decision makers _discard_ information that could help make society fairer and potentially more just than it is now _on average_?

## Lesson 18 Predictive Algorithms Part 3

### Bias In Predictive Algorithms

Below are some scenarios and problems regarding bias in predictive algorithms:

- Imagine that you are an emergency room in a hospital that collects data on newly admitted patients (e.g., blood pressure, age, gender, etc.)
  - _Problem_: how to predict high-risk patients and discriminate them from low-risk patients
- Credit card company that collects thousands of applications every day for applicants applying for new credit cards
  - _Problem_: how to predict whether a credit application should be approved or not approved and the amount of credit to provide

In summary, predictive algorithms use _labeled data_ to make predictions, such data is rampant with _human biases_. Examples of human bias in labeled data include:

- Reporting bias
- Selection bias
- Stereotypical bias
- Historical biases

Additionally, there are also biases present in the _collection of data_.

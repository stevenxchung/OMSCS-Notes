# Module 3

This module covers lessons 19 through 22. Notes will be primarily from the main lecture content rather than external resources.

In the following lessons, we will learn how to examine an AI system design using various fairness parameters and AI toolboxes (E.g., Fairness 360 and What-If). Additionally, we will assess bias while taking into consideration the ethical and legal issues associated with bias. The goal is to be able to use these tools to transform a biased dataset into a more objective dataset.

## Lesson 19 Fairness And Bias

### Fairness And Bias

**Algorithmic fairness**: is a growing field of research that aims to mitigate the effects of unwarranted bias/discrimination on people propagated by AI/ML algorithms. The primary focus is on mathematical formalisms and algorithm approaches of fairness to help develop solutions.

Feedback loop of algorithmic bias includes:

- **Representational harm**: when an AI/ML system amplifies or reflects negative stereotypes about particular groups
- **Opportunity denial**: when an AI/ML system negative impacts individuals’ access to opportunities, resources, and overall quality of life
- **Disproportionate failure**: when the experience of interacting with an AI/ML system is disproportionately failing for particular groups

### Addressing Source Of Bias

In the past, there were very few views and mitigation strategies to address bias. Today, one view is that algorithmic biases are a result of _human biases_ (which may be caused by misinformation or bad data). As the saying goes: _garbage in, garbage out_. See the lecture slides for specific examples of bias problems in practice and how to go about addressing _sources of bias_.

### Addressing Fairness Measures

Much like addressing sources of bias, there were no previous strategies to do so. Currently, we examine _blindness and disparate impact_ as a metric to gauge fairness. See the lecture slides for specific examples of bias problems in practice and how to go about addressing _fairness measures_.

Some principles for quantifying fairness include:

- _Predictive algorithms_:
  - Predictions for people with similar non-protected attributes should be similar
  - Differences should be mostly explainable by non-protected attributes
- _Frameworks_
  - Fairness at the individual level: _consistency or individual fairness_
  - Fairness at the group level: _statistical parity_

Algorithms for bias mitigation include:

- **Pre-processing algorithms**:
  - Reweighing
  - Optimized pre-processing
  - Learning fair representations
  - Disparate impact remover
- **In-processing algorithms**:
  - Adversarial de-biasing
  - Prejudice remover
- **Post-processing algorithms**:
  - Equalized odds post-processing
  - Calibrated equalized odds post-processing
  - Reject option classification

For more information on each of these algorithms see [Machine Learning Models: Bias Mitigation Strategies](https://dzone.com/articles/machine-learning-models-bias-mitigation-strategies)

## Lesson 20 Fairness And Bias Assessment Tools

### AI Fairness 360

**AI Fairness 360** is an extensible toolkit for detecting, understanding, and mitigating unwanted algorithmic bias. It comprises of leading fairness metrics and algorithms from industry and academia. The 360 tool is designed to translate new research from the lab to industry practitioners (via _Scikit-learn's fit/predict paradigm_)

### What-If Tool

**What-If Tool** was created to address the following gap:

> What if you could inspect machine learning models, with minimal coding required?

It also tries to show how a model performs before and after bias is mitigated. See the class notes or lecture for more details on how this bias mitigation tool works.

## Lesson 21 AI/ML Techniques For Bias Mitigation

### Solutions To Mitigate Bias

In the past, very few if any solutions existed to address bias. Today, we can utilize _fair classifiers_ to mitigate biases in our AI and ML models. Note that it still is not 100% possible to mitigate bias and create fair algorithms.

Questions to keep in mind when evaluating fairness-aware algorithms:

- _Which algorithm is the best_?
  - On which dataset?
  - How was it pre-processed?
  - Under which measure?
  - With which training/test split?
  - What if there are multiple sensitive attributes?

One of the challenges of bias mitigation is that we **cannot** simply drop protected attributes since other features are correlated with them. Performance can depend on which _attribute_ you focus on and what _algorithm_ you choose.

### Fairness-aware Algorithms Trade-offs

Some trade-offs to consider when mitigating biases:

- Is the model doing _good_ things or _bad_ things to people?
  - If your model is sending people to jail, may be better to have more false positives than false negatives
  - If your model is handing out loans, may be better to have more False Negatives than False Positives
- Determining thresholds for accuracy vs. fairness must take into considerations _legal, ethical and trust_ guidelines (see lecture for more details and examples)

## Lesson 22 AI, Society, And Ethics Wrap-up

### It's Not Easy

Discovering, addressing, and mitigating bias is not easy. There are many ongoing events in society and in industry that prove that this is the case in practice (see lecture).

### Last Thoughts

Some takeaways include:

- Intended use of AI/ML can provide great value:
  - Increased productivity
  - Overcome human biases
- The stakes are high, with potential _long-term negative social impact_
  - Injustice
  - Significant public embarrassments
- AI/ML models may boost bias even further
  - Pros and cons of benchmark datasets
  - Facebook feed: elections/polarizations
  - Twitter bots: Brexit
- We do not know the ground truth that ML relies on:
  - What does _fairness_ or _unbiased_ really mean?
  - How to translate the definition of fairness to math and supervise our models?

Why should we care about AI, ethics, and society?

- Ethical responsibility
- Selfish reasons (since we are humans and we want AI algorithms to work for us)

At the end of the day, both are valid reasons for studying AI, ethics, and society.

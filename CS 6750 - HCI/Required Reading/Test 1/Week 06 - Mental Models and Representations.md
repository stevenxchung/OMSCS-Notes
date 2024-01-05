# Week 6

> Ten questions on each test will be based on these readings. From the perspective of the test, your emphasis in reading these papers should be in getting a sufficient understanding of the material to answer high-level questions about the paper, as well as to be able to find answers quickly for more specific questions.

## Section 3.4: Mental Models And Metaphor

> MacKenzie, I.S. (2013). Section 3.4: Mental Models & Metaphor. Human-Computer Interaction: An Empirical Research Perspective. (pp. 88-92). Waltham, MA: Elsevier.

Topic: mental models and metaphors.

One of the most common ways to learn and adapt is through _physical analogy_ or _metaphor_. Physical analogies and metaphors are examples of the more general concept of _mental models_, also known as _conceptual models_.

- **Implementation models** - are systems that impose on the user a set of interactions that follow the inner workings of an application; they are to be avoided. The user is prompted for information when it is convenient for the program to receive it, not when it makes sense to the user.

## Section 3.8: Interaction Errors

> MacKenzie, I.S. (2013). Section 3.8: Interaction errors. Human-Computer Interaction: An Empirical Research Perspective. (pp. 111-116). Waltham, MA: Elsevier.

Topic: the big errors are the easy ones—they get fixed. It is the small errors that are interesting.

At the end of the day, however, human performance is what counts. Physical properties, although instructive and essential, are secondary. Put another way, human performance is like food, while physical properties are like plates and bowls. It is good and nutritious food that we strive for.

Another reason little errors tend to linger is that they are often deemed _user errors_, not design, programming, or system errors. 

These errors, like most, are more correctly called _design-induced errors_.

Examples:
- Discard Changes.
- CAPS_LOCK.
- Scrolling Frenzy.
- Focus Uncertainity.

## Chapter 5: Human Error? No, Bad Design

> Norman, D. (2013). Chapter 5: Human Error? No, Bad Design. In The Design of Everyday Things: Revised and Expanded Edition. (pp. 162-216). Arizona: Basic Books.

The tendency to stop seeking reasons as soon as a human error has been found is widespread.

Topic: we should treat all failures in the same way: find the fundamental causes and redesign the system so that these can no longer lead to problems.

- **Delibrate Violations** - Errors are not the only type of human failures. Sometimes people knowingly take risks. When the outcome is positive, they are often rewarded. When the result is negative, they might be punished.
- **Root cause analysis** - investigate the accident until the single, underlying cause is found. 'Five Why' method. 
- **Slip** - occurs when a person intends to do one action and ends up doing something else; there are two types: _action-based_ nad _memory-lapse_, _description-similarity_, _mode_error_, _capture_slip_
- **Mistake** - occurs when the wrong goal is established or the wrong plan is formed; there are three types: _rule-based_, _knowledge-based_, and _memory-lapse_

Slips occur when the goal is correct, but the required actions are not done properly: the exe-
cution is flawed. Mistakes occur when the goal or plan is wrong.

- **Example of an action-based slip:** I poured some milk into my coffee and then put the coffee cup into the refrigerator. This is the correct action applied to the wrong object.
- **Example of a memory-lapse slip:** I forget to turn off the gas burner on my stove after cooking dinner.

Memory lapses can lead to either slips or mistakes, depending upon whether the memory failure was at the highest level of cognition (mistakes) or at lower (subconscious) levels (slips).

- **Example of knowledge-based mistake:** Weight of fuel was computed in pounds instead of kilograms.
- **Example of memory-lapse mistake:** A mechanic failed to complete troubleshooting because of distraction.

Key design principles for errors:

- Design for both expert and novice users
- Use the power of constraints, forcing functions, and natural mappings
- Bridge the two gulfs (execution and evaluation) by making options available and status readable and accurate

## A “Pile” Metaphor For Supporting Casual Organization Of Information

> Mander, R., Salomon, G., & Wong, Y. Y. (1992, June). A “pile” metaphor for supporting casual organization of information. In Proceedings of the SIGCHI Conference on Human Factors in Computing Systems (pp. 627-634). ACM.

Topic: investigation on how people deal with flow of information in their workspaces reveals that users organize their documents in piles thus leading into the desktop interface element - the pile (as seen on a Mac OS).

- **User-created piles** - allow users to create piles of mixed content and multiple data types
- **System-created piles** - system can create piles for a user \
- **Document-centered model** - piles represented as a collection of individual items
- **Pile-centered model** - pile acts more like a folder with a single entity containing a collection of documents

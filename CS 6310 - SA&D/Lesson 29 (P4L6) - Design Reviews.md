# Lesson 29

High quality designs become more important as the size of applications being design grows. Additionally, the likelihood of a design flaw increases with the size of the application. Therefore, it is important to examine design validations and **design reviews**.

## Exercise Intro

In this lesson we will be primarily focusing on a design exercise by using a code example (Java) instead of a design example. The code exercise will be as follows:

- Computes the _sin_ function for argument _x_ to accuracy _e_ using a Maclaurin series expansion
- The line numbers appearing in parenthesis at the beginning of each line are not part of the program

## Observations

There are several observations from the exercise:

- Groups do better than individuals (many eyes phenomenon); however this comes at a cost
- Defects come in all forms, team review efforts can be a cost-effective way to find defects, reviews must be done in a systematic fashion

## Reviews

**Reviews** are also known as inspections or walkthroughs, are systematic readings of a software development artifact. Reviews complement other verification techniques such as testing and proofs.

The purpose of a review is to detect defects (bugs or faults) as well as check adherence to corporate or governmental standards. Reviews should not be used to educate staff members, report status or fix detected problems.

# Recommended Review Steps

There are several of steps we could take to conduct an effective review:

1. **Planning**
   - Participants are selected, meetings are scheduled, roles are assigned, the specific artifact or part of it is specified, and materials are distributed
   - These activities should be done at least five days in advanced
2. **Preparation**
   - Participants should individually study the materials noting potential defects
   - Expected rate of individual review should be about 10 pages of text or 100 LOC (lines of code) per hour
3. **Review**
   - Should last no more than two hours
   - Rate of review should be the same as that used for individual preparation
   - Individually noticed defects should be collected (should not be discussed further in the meeting)
4. **Rework**
   - Artifact's author should investigate the issues raised
   - Defects should be corrected
5. **Follow-up**
   - Author should report results to the moderator, then the moderator should confirm that the fixes have been properly implemented
   - Additionally, moderator should collect data on the review itself; this data should be recorded and saved
   - Moderator should suggest improvements to the review process itself

## Roles

There are also several of roles during a review process:

1. **Moderator**
   - Should determine whether the participants have done the necessary preparatory work
   - Should evaluate whether the work to be reviewed is actually ready for review
   - Should run the meeting and be technically competent
2. **Recorder**
   - Responsible for making a record of the issues raised during a review
   - May not be possible to determine in the review meeting itself whether an issue represents a defect
   - Should proactively clarify the issues raised (several issues may be intertwined) and should ask for clarification
3. **Reader**
   - Responsible for enforcing thoroughness by leading participants through the artifact (the artifact's author is oftentimes the reader)
   - Should use impersonal pronouns
   - Personalizing a review can raise the defensiveness level of participants
4. **Reviewers**
   - Include other participants in the meeting (typically three to six) who are responsible for raising the issues by asking questions
   - Should not explicitly suggest improvements
   - Productively raise issues without getting diverted by emotionally driven debates
5. **Review**

## Recording Form

A **recording form** includes:

- Each issue's location within the artifact, its description, its type, and its severity
- Issue types are artifact dependent
- Severity levels are also typically predefined (each organization should determine its own severity classification)

## Review Meeting

The review meeting should include the following:

1. Introduction of participants
2. Statement of objectives
3. Evaluation of preparedness
4. Systematic review
5. Recording of results
6. Review and summarization
7. Determination of who is responsible

## Thoroughness

**Thoroughness** is the key determinant of successful reviews is how thoroughly they examine the artifact. This includes line-by-line coverage, coverages of all use cases, checklist of common defect types, and coverage of verification conditions.

## Metrics

**Metrics** are used to observe review effectiveness. Metrics may include:

- Review rate in lines of artifact reviewed per staff-hour spent reviewing
- Defect rate in defects detected per staff-hour spent reviewing
- Defect density in defects per line of artifact
- Process yield computed by comparing the review-detected defects to the total defects

## Process Data

Reviews are an early step in an organizations efforts to improve the quality of the products it produces. A more sophisticated step is to review the review process itself. This is done by collecting data on the effectiveness of the reviews and to use it to improve the reviewing process.

## Effectiveness

Code reviews are an effective technique for detecting defects in artifacts. Between 70-90% of defects are found from code reviews. Code reviews amount to about 10-20% of the total cost of development. However, defect detection rates vary dramatically.

## Other Costs And Benefits

Benefits include:

- Individual skills can be enhanced by looking at other people's artifacts
- Some evidence to suggest that lightweight reviews are more effective

Costs include:

- Ego effect (danger of damaged egos)
- Big brother effect

## Summary

The later that a problem is detected, the more expensive it is to fix. Consequently, reviews are a cost effective way to find problems. However, reviews run the risk of revealing shallow problems. To reveal the real problems requires exposure of the design to experienced designers. Generally, short-term costs will be offset by the eventual saving.

## Section Quizzes

### Defects Quiz 1

_Write down defects you see with the line number and the defect detected._

- Line 6: `term = x` is a `float` assigned to a `double` variable
- Line 9: `term < e` is trying to evaluate different types

### Defects Quiz 2

_Indicate the type of error found on each line. Mark bug (B), documentation issue (D) , violation of coding standard (V), or inefficiency (I). For lines with multiple errors, enter as a list. Please enter the line number and the error(s) found._

- Line [1, 5, 6, 9, 10]: B
- Line 2: D
- Line 6: V
- Line [6, 8, 10]: I

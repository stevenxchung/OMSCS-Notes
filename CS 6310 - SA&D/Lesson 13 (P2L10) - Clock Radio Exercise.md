# Lesson 13

State charts are a precise way of modeling the behavior of complex, reactive systems. Errors can lead to safety, security and usability problems. In this lesson, we will examine how to model the behavior of a common clock radio.

## Description

_See lecture video for description of the clock radio problem_

## Exercise Introduction

The clock radio has several use cases:

- Setting the time
- Changing frequency
- Pressing "snooze"

## External Controls And Stimuli

Listed below are possible external controls on the system:

- Switch mode button (slide left or right)
- Turn frequency dial
- Switch AM/FM
- Press snooze (while beeping/not beeping)
- Press wake (pres hour/minute)
- Press sleep (press hour/minute)
- Press hour/minute

## From Action To Events

The next step is to turn the user actions into events. An event is an instantaneous occurrence to which the device should respond.

## Guarded Transitions

**Guarded transitions** are situations where the response to an event is conditions on a sub-machine being in a state.

## Cascaded Events

**Cascaded events** are responses to events in the form of broadcasting another internal event. This mechanism can be used to communicate between concurrently executing sub-machines.

## State Chart Modeling Method

Below are the steps to modeling a system with a state chart:

1. Prepare usage scenarios
2. Determine external percepts
3. Model percepts and states
4. Determine external controls and stimuli
5. Model with additional states and transitions/events
6. List stimulus/response(s) pairs
7. Add necessary internal states (e.g., timers)
8. Provide coordination mechanisms
9. Add actions/activities
10. Validate resulting machine vs scenarios

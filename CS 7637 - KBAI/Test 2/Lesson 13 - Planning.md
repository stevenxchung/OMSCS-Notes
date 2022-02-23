# Lesson 13

An intelligent agent maps perceptual histories into actions. Consequently, _planning_ is a powerful tool for action selection. In this lesson we will cover:

1. States, goals, and operators
2. Conflicts in planning
3. Partial-order planning
4. Hierarchical task networks

## Planning And State Spaces

Referring back to state spaces, a search method is inefficient because it uses no knowledge. Since we have knowledge of the goal and asset knowledge (i.e., how to select an operator), we could better select actions which allow us to obtain our goal as we saw with means-ends analysis.

Planning provides more systematic processes for selecting different operators. How to we do operator selection? We can do this the same way as mapping perceptual histories into actions. Operators represent mental representations of actions available in the world.

# Lesson 23

This lesson is primarily interviewing a chief architect from a company called LogicBlox. LogicBlox focuses on:

> Solving business problems with applications that evolve with business needs, in a unified environment with Big Data scale, spreadsheet flexibility, and advanced analytics.

The business model behind LogicBlox is SaaS (software as a service).

## LayerBlox

One of the novel ways LogicBlox has handled redundancy and enabled reusability in their software architecture is to have _LayerBloxs_ which takes care of commonly used services for various client applications. LayerBloxs accomplishes this by generating different variants of components using assembly specs and a reusable feature library. This is possible as LayerBloxs is based on feature-based design principles.

## References

Below are references used in building out LayerBlox:

- Don Batory: [Feature-Oriented Programming and the AHEAD Tool Suite.](https://gatech.instructure.com/courses/116212/files/13031401/download)
  Proceedings of the 26th International Conference on on Software Engineering, ICSE 2004, pp. 702-703.
- Don Batory and Sean O'Malley: [The Design and Implementation of Hierarchical Software Systems with Reusable Components.](https://gatech.instructure.com/courses/116212/files/13031583/download)
  ACM Transactions on Software Engineering and Methodology (TOSEM), 1(4):355-398, October, 1992.
- David L. Parnas: [Designing Software for Ease of Extension and Contraction.](https://gatech.instructure.com/courses/116212/files/13031585/download)
  IEEE Transactions on Software Engineering, SE-5(2):128-138, March, 1979.
- David L. Parnas: [On the Design and Development of Program Families.](https://gatech.instructure.com/courses/116212/files/13031397/download)
  IEEE Transactions on Software Engineering, SE-2(1):1-9, 1976.
- Yannis Smaragdakis and Don Batory: [Implementing Layered Designs with Mixin Layers.](https://gatech.instructure.com/courses/116212/files/13031399/download)
  Object-Oriented Programming, pp. 550-570.

## Implications And Advice

Advice from Kurt:

- Get good at data modeling the structure of data in a system on a conceptual level can pay dividends in the long run
- Using an algebraic approach to think about software composition (e.g., what are their properties, when are they useful, and how to use them to inspire designs)
- Knowing a body of related work when you start a new problem as in trying to relate your problem to a problem that has already been seen that you can heavily borrow from

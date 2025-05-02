---
title: "Lesson 5: Unit Testing Code"
teaching: 15
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

Testing is a critical part of writing reliable, maintainable code — especially in collaborative or research environments where reproducibility and correctness are key. In this session, we will explore why testing matters, and introduce different levels of testing — from small, focused unit tests, to broader integration and system tests that check how components work together. We will also look at testing approaches such as regression testing (to ensure changes do not break existing behavior) and property-based testing (to test a wide range of inputs automatically). Finally, we will cover mocking, a technique used to isolate code during tests by simulating the behavior of external dependencies.


## Introduction to testing

Code testing is the process of verifying that your code behaves as expected and continues to do so as it evolves. It helps catch bugs early, ensures changes do not unintentionally break existing functionality, and supports the development of more robust and maintainable software. Whether you’re working on a small script or a large application, incorporating testing into your workflow builds confidence in your code and makes collaboration and future updates much easier.

### Why test your code?

Being able to demonstrate that a process generates the right results is important in any field of research, whether it is software generating those results or not. So when writing software we need to ask ourselves some key questions:

- Does the code we develop work the way it should do?
- Can we (and others) verify these assertions for themselves?
- Perhaps most importantly, to what extent are we confident of the accuracy of results that software produces?

If we are unable to demonstrate that our software fulfills these criteria, why would anyone use it? Having well-defined tests for our software helps ensure your software works correctly, reliably, and consistently over time. By identifying bugs early and confirming that new changes do not break existing functionality, testing improves code quality, reduces the risk of errors in production, and makes future development faster and safer.

### Types of Testing - Levels

Testing can be carried out at different code levels to ensure software behaves correctly at various stages of execution. 

*Unit testing* focuses on the smallest testable parts of an application, such as individual functions or methods, to verify they work in isolation. 

*Integration testing* takes it a step further by checking that different modules or components of the code interact and function together as expected. 

At the highest level, *system testing* evaluates the complete application, testing it as a whole to ensure that all parts interact well together to deliver the desired outcomes under real-world conditions.


### Types of testing - approaches (regression testing, property-based testing)
### Mocking

## Practical Work

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

- Does the code we develop works as expected?
- To what extent are we confident of the accuracy of results that software produces?
- Can we (and others) verify these assertions for themselves?

If we are unable to demonstrate that our software fulfills these criteria, why would anyone use it? 

As a codebase gets larger, debugging can become increasingly difficult and new code may introduce bugs or unexpected behaviour in other parts if your code it does not even touch. Tests can help you pick up problems before they become a runtime bug
and a failing test will also help pinpoint where the problem lies. Tests also provide invocation examples for other develoeprs and users of our code, makit easier to reuse. 

Having well-defined tests for our software helps ensure your software works correctly, reliably, and consistently over time. By identifying bugs early and confirming that new changes do not break existing functionality, testing improves code quality, reduces the risk of errors in production, and makes future development and long-term maintenance faster and safer. 


### Types of Testing - Levels

Testing can be performed at different code levels, each serving a distinct purpose to ensure software behaves correctly at various stages of execution. Together, these testing levels provide a structured approach to improving software quality and reliability.

*Unit testing* is the most granular level, where individual components—like functions or classes—are tested in isolation to confirm they behave correctly under a variety of inputs. This makes it easier to identify and fix bugs early in the development process.

*Integration testing* builds on unit testing by checking how multiple components or modules work together. This level of testing helps catch issues that arise when components interact — such as unexpected data formats, interface mismatches, or dependency problems.

At the highest level, system testing evaluates the software as a complete, integrated system. This type of testing focuses on validating the entire application's functionality from end to end, typically from the user’s perspective, including inputs, outputs, and how the system behaves under various conditions. 

### Types of Testing - Approaches 

Different approaches to code testing help ensure that software behaves as expected under a range of conditions. When the expected output of a function or program is known, tests can directly check that the results match fixed values or fall within a defined confidence interval. 

However, for cases where exact outputs are not predictable — such as simulations with random elements — *property-based testing* is useful. This method tests a wide range of inputs to ensure that certain properties or patterns hold true across them. 

Another important approach is *regression testing*, which helps detect when previously working functionality breaks due to recent changes in the code. By rerunning earlier tests, developers can catch and address these regressions early, maintaining software stability over time.

### Mocking

When running tests, you often want to focus on testing a specific piece of functionality, but dependencies on external objects or functions can complicate this, as you cannot always be sure they work as expected. Mocking addresses this by allowing you to replace those dependencies with "mocked" objects or functions that behave according to your instructions. So, *mocking* is a testing technique used to isolate the unit of code being tested by replacing its dependencies with simplified, controllable versions — known as *mocks*. 

These mocks mimic the behavior of real components (such as databases, APIs, or external services) without requiring their full functionality or availability. This allows developers to test specific code paths, simulate error conditions, or verify how a unit interacts with other parts of the system. Mocking is especially useful in unit and integration testing to ensure tests remain focused, fast and reliable.

For example, if a function modifies data and writes it to a file, you can mock the file-writing object, so instead of creating an actual file, the mocked object stores the "written" data. This enables you to verify that the data written is as expected, without actually creating a file, making tests more controlled and efficient.

### Related Practices

[Code style and linting](./20-introduction.md) are essential practices in code testing, as they help ensure that code is readable and maintainable by following established conventions, such as PEP8 in Python. Linting tools automatically check that code adheres to these style guidelines, reducing errors and improving consistency. 

[Continuous Integration (CI)](././60-introduction.md) further enhances testing practices by automating key processes, such as running tests and linting tools, every time code changes are committed. This helps catch issues early, maintain code quality, and streamline the development workflow. Together, these practices improve code reliability and make collaboration smoother.


## Practical Work

In the rest of this session, we will walk you through writing tests for your code.

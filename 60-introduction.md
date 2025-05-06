---
title: "Lesson 6: Continuous Integration"
teaching: 15
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

Doing tasks manually can be time-consuming, error-prone, and hard to reproduce, especially as complexity grows. Using automation allows computers to handle repetitive, structured tasks reliably, quickly, and consistently, freeing up your time for more valuable and creative work.

## Introduction to Automation

Automation is the process of using scripts or tools to perform tasks without manual intervention. In software development, automation helps streamline repetitive or complex tasks, such as running tests, building software, or processing data. 

By automating these actions, you save time, reduce the chance of human error, and ensure that processes are reproducible and consistent. Automation also provides a clear, documented way to understand how things are run, making it easier for others to replicate or build upon your work.

## Intro to Continuous Integration

Building on the concept of automation, Continuous Integration (CI) is the practice of regularly integrating code changes into a shared repository and automatically running tasks and key checks, such as comiling code sand running tests across multiple platforms to catch issues early, verifing code style with linters, building documentation pages from docstrings (structured documentation embedded in the code), etc. 
This helps maintain code quality and ensures new contributions do not break existing functionality. 

A variety of CI tools and services, like GitHub Actions, GitLab CI, or Jenkins, make it easy to set up automated workflows triggered by code changes. 

CI can also be extended into Continuous Delivery (CD), which automates the release or deployment of code to production or staging environments.

### Principles of CI

Software development typically progresses in incremental steps and requires a significant time investment. It is not realistic to expect a complete, feature-rich application to emerge from a blank page in a single step. The process often involves collaboration among multiple developers, especially in larger projects where various components and features are developed concurrently.

Continuous Integration (CI) is based on the principle that software development is an incremental process involving ongoing contributions from one or more developers. Integrating large changes is often more complex and error-prone than incorporating smaller, incremental updates.
So, rather than waiting to integrate large, complex changes all at once, CI encourages integrating small updates frequently to check for conflicts and inconsistencies and ensure all parts of the codebase work well together at all times. 
This becomes even more critical for larger projects, where multiple features may be developed in parallel - CI helps manage the complexity of merging such contributions by making integrations a regular, manageable part of the workflow.

### Common CI Tasks

When code is integrated, a range of tasks can be carried out automatically to ensure quality and consistency, including:

- compiling the code
- running a test suite and checking test coverage
- verifying that the code adheres to project, team, or language style guidelines
- building or generating documentation
- other custom tasks may also be included, depending on project needs.

These steps are typically executed as part of a structured sequence known as the “CI pipeline”.

### Why use CI?

CI offers several advantages that can significantly improve the software development process. 

It saves time and effort for you and your team by automating routine checks and tasks, allowing you to focus on development rather than manual verification. 

CI also promotes good development practices by enforcing standards. For instance, many projects are configured to reject changes unless all CI checks pass. 

Modern CI services make it easy to run its tasks and checks across multiple platforms, operating systems, and software versions, providing capabilities far beyond what could typically be achieved with local infrastructure and manual testing. 

While there can be a learning curve when first setting up CI, a wide variety of tools are available, and the core principles are transferable between them, making these valuable and broadly applicable skills.

### CI Tools & Services

There are a wide range of CI-focused workflow services and different tools available to support various aspects of a CI pipeline. Many of these services have Web-based interfaces and run on cloud infrastructure, providing easy access to scalable, platform-independent pipelines. However, local and self-hosted options are also available for projects that require more control or need to operate in secure environments. Most CI tools are generally language- and tool-agnostic; if you can run a task locally, you can likely incorporate it into a CI pipeline. 

Popular cloud-based services include [GitHub Actions](https://github.com/features/actions), [Travis CI](https://www.travis-ci.com/), [CircleCI](https://circleci.com/), and [TeamCity](https://www.jetbrains.com/teamcity/), while self-hosted or hybrid solutions such as [GitLab CI](https://docs.gitlab.com/ee/ci/), [Jenkins](https://www.jenkins.io/), and [Buildbot](https://buildbot.net/) also available.

### Beyond CI - Continuous Deployment/Delivery

You may frequently come across the term CI/CD, which refers to the combination of Continuous Integration (CI) and Continuous Deployment or Delivery (CD). While CI focuses on integrating and testing code changes, CD extends the process by automating the delivery and deployment of software. This can include building installation packages for various environments and automatically deploying updates to test or production systems. For example, a web application could be redeployed every time a new change passes the CI pipeline. CD helps streamline the release process for packages or applications, for example by doing nightly builds and deploying them to a public server for download, making it easier and faster to get working updates into the hands of users with minimal manual intervention.

## Practical Work

In the rest of this session, we will walk you through setting up a basic CI pipeline using GitHub Actions to help you integrate, test, and potentially deploy your code with confidence.

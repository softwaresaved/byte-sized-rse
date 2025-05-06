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

## Introduction to Automation

Automation is the process of using scripts or tools to perform tasks without manual intervention. In software development, automation helps streamline repetitive or complex tasks, such as running tests, building software, or processing data. 

By automating these actions, you save time, reduce the chance of human error, and ensure that processes are reproducible and consistent. Automation also provides a clear, documented way to understand how things are run, making it easier for others to replicate or build upon your work.

## Intro to Continuous Integration

Building on the concept of automation, Continuous Integration (CI) is the practice of regularly integrating code changes into a shared repository and automatically running tasks and key checks, such as comiling code sand running tests across multiple platforms to catch issues early, verifing code style with linters, building documentation pages from docstrings (structured documentation embedded in the code), etc. 
This helps maintain code quality and ensures new contributions do not break existing functionality. 

A variety of CI tools and services, like GitHub Actions, GitLab CI, or Jenkins, make it easy to set up automated workflows triggered by code changes. 

CI can also be extended into Continuous Delivery (CD), which automates the release or deployment of code to production or staging environments.


## Extending/beyond CI - continuous deployment/delivery

- what is continous deployment/delivery?
- some example maybe?

## Practical Work

In the rest of this session, we will walk you through setting up a basic CI pipeline using GitHub Actions to help you integrate, test, and potentially deploy your code with confidence.

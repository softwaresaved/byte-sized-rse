---
title: "Lesson 1: Integrated Development Environments"
teaching: 15
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- What is an Integrated Development Environment (IDE)?
- Why use an IDE?
- What are common IDE features that code developers find extremely useful?
- What are some commonly used IDEs among the RSE community?


::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Explain what an Integrated Development Environment (IDE) is and list a number of IDEs used by RSEs
- List common IDE features and explain how they contribute to easier and quicker code development

::::::::::::::::::::::::::::::::::::::::::::::::

## What is an Integrated Development Environment (IDE)?

An Integrated Development Environment (IDE) is a software application that provides a comprehensive workspace for writing, editing, testing, and debugging code—all in one place. It combines several tools that developers need into a single interface to streamline the code development process. IDEs are extremely useful and modern software development would be very hard without them. 

### Why use an IDE?

An IDE brings everything you need to write, test, and debug code into one place — saving time by helping you write better code faster.
IDEs help by:

- reducing setup and development time - everything you need for editing, running, and debugging code is in one place and the need to switch between different tools/applications/windows is significantly reduced
- offering helpful tools like syntax checking, code suggestions and autocomplete, and error checking leading to fewer errors thanks to real-time feedback and intelligent suggestions
- making it easier to debug and test code leading to easier issue detection and fixing
- providing a consistent environment across projects

For beginners, IDEs lower the barrier to entry by making it easier to spot mistakes and understand code structure. 
For experienced developers, IDEs boost productivity and streamline complex workflows.

### Common IDE Features

The following is a list of the most commonly seen IDE features:

- **code editting** - providing a place to write and edit code
- **syntax highlighting** - to show programming language constructs, keywords and the syntax errors with visually distinct colours and font effects for better readability
- **code completion** - to speed up programming by suggesting a set of possible (syntactically correct) code options
- **code search** - to find package, class, function and variable declarations, their usages and referencing
- **version control support** - to interact with source code repositories
- **debugging support** - for setting breakpoints in the code editor, step-by-step execution of code and inspection of variables to help find and fix bugs in code
- **integrated terminal** - to run commands without leaving the IDE
- **project/file explorer** - to navigate the code project structure easily

### Popular IDEs

Here are a few widely used IDEs across different languages and fields:

- [Visual Studio Code (VS Code)][vs-code] – lightweight and highly customisable; supports many languages
- [PyCharm][pycharm] – great for Python development
- [RStudio][r-studio] – designed specifically for R programming
- [Eclipse][eclipse] – often used for Java and other compiled languages
- [JupyterLab][jupyter-lab] – interactive environment for Python and data science
- [Spyder][spyder] – popular among scientists using Python

## What is Code Debugging?

Code debugging is the process of identifying, isolating, and fixing errors or bugs in your software or script. Bugs can manifest as unexpected behavior, crashes, or incorrect outputs. Debugging is an essential step in software development, ensuring that your code runs as intended and meets quality standards.

### Why Debugging Matters?

Even small mistakes in code can cause unexpected behavior or crashes. Debugging helps with:

- **code correctness** - debugging ensures your program works as expected and meets requirements
- **error resolution** - debugging helps you understand why your code isn't performing correctly, allowing you to find and fix issues that make your program behave incorrectly rather than just guessing.
- **improving code quality** - regular debugging leads to cleaner, more reliable and performant code and reduces the risk of problems in production.
- **efficient code development** - familiarity with debugging tools and techniques can significantly reduce the time spent on troubleshooting and enhance overall productivity.

### Common Debugging Techniques

- Adding print statements at certain points in the code to print and trace variable values and check code flow is one of the simplest debugging methods
- Using a debugger integrated in your IDE allows you to set breakpoints, step through your code line by line, and inspect variables at runtime
- Incorporating logging into your application can provide insights into its behavior over time and help diagnose issues that occur in specific runtime conditions
- Writing tests that automatically check your code's functionality can help catch bugs early in the development process

### How do we use a Debugger?

We will focus on familiarising ourselves with a debugger built in into VS Code.

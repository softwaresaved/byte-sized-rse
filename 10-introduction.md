---
title: "Lesson 1: Code Development & Debugging with IDEs"
teaching: 15
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- What is an Integrated Development Environment (IDE) and what role does it play in software development?
- What are the common features of IDEs?
- Why is debugging important, and what are the main techniques developers use to debug their code?
- How can you use a debugger in an IDE like Visual Studio Code to find and fix errors in your code?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Define what an Integrated Development Environment (IDE) is and describe its role in the software development process
- Identify common features of IDEs and explain how they support efficient code writing, debugging, and software project management
- Explain the importance of debugging and list common debugging techniques
- Demonstrate how to use a debugger within an IDE like Visual Studio Code
- Recognise the benefits of using an IDE for improving code quality, reducing errors, and accelerating software development

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

Let’s look at what most IDEs offer - these features all work together to make your life easier when coding:

- **Code editing** functionality with **syntax highlighting**
- **Code completion** to speed up your typing by suggesting a set of possible (syntactically correct) code options
- **Code search** to find functions, classes, or variables quickly
- **Version control integration** to interact with source code repositories and tools (e.g., Git)
- **Built-in debugging tools** like setting breakpoints, step-by-step execution of code and inspection of variables to help find and fix bugs in code
- **Integrated terminal** for running commands without leaving the IDE
- **Project explorer** to easily navigate your files

### Popular IDEs
  
Here are a few widely used IDEs across different languages and fields:

- [Visual Studio Code (VS Code)][vs-code] – lightweight and highly customisable; supports many languages
- [PyCharm][pycharm] – great for Python development
- [RStudio][r-studio] – tailored for R programming but allows users to mix (R Markdown) text with code in R, Python, Julia, shell scripts, SQL, Stan, JavaScript, C, C++, Fortran, and others, similar to Jupyter Notebooks.
- [Eclipse][eclipse] – often used for Java and other compiled languages
- [JupyterLab][jupyter-lab] – interactive environment for Python and data science
- [Spyder][spyder] – popular among scientists using Python

## What is Code Debugging?

Now, what happens when your code does not work as expected? That is where code debugging comes in.
Debugging means finding, understanding, and fixing errors in your code — which can manifest as unexpected behavior, crashes, or incorrect outputs. 
Debugging is an essential step in software development, ensuring that your code runs as intended and meets its requirements (and quality standards).

### Why Debugging Matters?

Debuggin ensures your code behaves as it should and helps you find the root cause of problems — not just guess - when it does not.
Even small mistakes in code can cause unexpected behavior or crashes. Debugging helps with:

- **code correctness** - to ensure your program works as expected and meets requirements
- **error resolution** - to help you understand why your code is not performing correctly, allowing you to find and fix issues that make your program behave incorrectly
- **improving code quality** - regular debugging leads to cleaner, more reliable and performant code and reduces the risk of problems in production
- **efficient code development** - familiarity with debugging tools and techniques can significantly reduce the time spent on troubleshooting and enhance overall productivity.

Debugging is a normal part of the code development process - it is not just about fixing mistakes — it is about understanding your code better. 

### Common Debugging Techniques

Let's be real — everyone’s code breaks sometimes. Debugging is just part of the game. For starters, you can try **rubber duck debugging** - a technique where you explain your code, line by line, out loud —  to a colleague or to an inanimate object like a rubber duck. The idea is that by forcing yourself to verbalise what your code is supposed to do, you slow down and think more clearly about each part, which often helps you spot mistakes or logical errors you might have missed when just reading the code silently.

One of the simplest tricks is **adding print statements to your code**: just printing out variable values or messages at key points can quickly show you where things start to go wrong. 

**Logging** is another smart move, especially for bigger projects, because it helps you track what your program is doing over time and help diagnose issues that occur in specific runtime conditions. A variant of logging is to use **assert statements** in your code - 

But if you want to level up, using a **built-in debugger** (like the one in VS Code) is a game-changer — you can set breakpoints, step through your code line by line, and actually see what is happening in real time. 

And if you really want to catch problems early, **writing tests** to check that your code behaves properly can save you from bigger headaches later. 

### How do we use a Debugger?

In the rest of this session, we will walk you through how to use a debugger in VS Code, focusing on practical steps and tips to help you find and fix errors more efficiently in your code.
It is easier than you think and can really save you time.

::: keypoints

- Integrated Development Environments (IDEs) are all-in-one tools for writing, editing, testing, and debugging code, improving developer efficiency by reducing the need to switch between different applications.
- Common IDE features include code editing, syntax highlighting, code completion, version control integration, debugging tools, project navigation, and built-in terminals.
- Debugging is the process of finding and fixing bugs in code to ensure it behaves as intended, improving code quality and reliability.
- Common debugging techniques include adding print statements, using built-in debuggers to set breakpoints and inspect variables, writing tests, and using logging.
- Using an IDE for debugging allows developers to step through their code interactively, making error detection and resolution much faster and more effective.

:::

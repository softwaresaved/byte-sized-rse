---
title: "Lesson 2: Code Style, Quality & Linting"
teaching: 15
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- Why does consistent code style matter in software development?
- What are some common code styling practices and conventions?
- How can poor coding style lead to bugs and maintenance issues?
- What is a linter, and how does it help improve code quality?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Understand why consistent code style is important for collaboration and long-term maintainability.
- Identify key code style practices and how they vary between programming languages.
- Recognise how maintaining good code style can reduce bugs and improve code quality.
- Explain what a linter is and describe its role in detecting errors and enforcing style.

::::::::::::::::::::::::::::::::::::::::::::::::

## Introduction to Code Style

### Why Does Code Style Matter?

Software development is inherently a collaborative activity. Even if you do not currently intend for anyone else to read your code, chances are someone will need to in the future — and that person might even be you, months or years later. By following and consistently applying code styling guidelines, you can significantly improve the readability and maintainability of your code. Consistency plays a vital role in this process. Adopting a clear set of style guidelines not only helps you write uniform code but also makes it easier to switch between projects. This is especially important when working as part of a team, where shared understanding and clarity are essential.

### Key Code Style Practices & Conventions

Styling practices and conventions play a key role in writing readable and maintainable code, but they can vary significantly between programming languages. These conventions generally cover aspects such as line length, line splitting, the use of white space, naming conventions for variables, functions, and classes, as well as indentation and commenting styles (where not enforced by the language itself).

It is important to note that programmers often have strong and differing opinions about what constitutes good style. For example, many style guides recommend a maximum line length of 80 characters, a convention that dates back to older hardware and terminal limitations. While some developers continue to find this helpful for readability and side-by-side editing, others argue that it feels unnecessarily restrictive on modern screens. Despite these differences, adopting and adhering to a consistent style within a project helps ensure clarity and makes collaboration smoother.

There are many established code style guides tailored to specific programming languages, such as:

- [PEP8](https://peps.python.org/pep-0008/) and [Google Style Guide](https://google.github.io/styleguide/pyguide.html) for Python
- [Google C++ Style Guide](https://google.github.io/styleguide/cppguide.html) and [C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines) for C++
- [Airbnb JavaScript Style Guide](https://airbnb.io/javascript/) and [Google JavaScript Style Guide](https://google.github.io/styleguide/jsguide.html) and [JavaScript Standard Style](https://standardjs.com/) for JavaScript
- [Go Style Guide](https://google.github.io/styleguide/go/) and [Go Styleguide](https://github.com/bahlo/go-styleguide) for Go.

### Maintaining Code Quality to Reduce Bugs

Poor coding style can lead to bugs and maintenance issues because it makes code harder to read, understand, and debug. Inconsistent naming, unclear structure, and sloppy formatting can cause confusion about what the code is doing, making it easier to introduce mistakes. 
Many things that seem harmless and do not cause immediate syntax errors while writing code can produce logic errors, wrong results and lead to issues later on - making them especially tricky to detect and fix.
Small issues like unused variables, accidental redefinitions, or incorrect scoping can go unnoticed and later cause unexpected behavior or subtle logic errors. Over time, this makes the codebase more fragile, harder to maintain, and much more difficult for others — or even your future self — to fix or extend.

Some examples of small oversights that stack up over time include: 

- defining variables or importing modules or headers that that are never used can clutter the code
- using vague variable names like `data` everywhere can make it unclear which `data` you are actually handling, causing mistakes
- bad indentation can cause logic errors — like running a block of code when you did not intend to
- variable scoping problems (e.g. reusing the same variable name in different scopes can lead to *shadowing*, where a local variable hides a global or outer-scope variable, resulting in unexpected values being used.

## Introduction to Linters

### What is a Linter and Why Use One?

A linter is a tool that performs static analysis on your code — meaning it examines the source code without running it — to detect potential errors, stylistic issues, and code patterns that might cause bugs in the future. The term originates from a 1970s tool for the C programming language called "lint".

Linters help catch errors early and enforce consistent code style, making your code more reliable, readable, and easier to maintain. They are especially useful for improving code quality and streamlining collaboration in teams.

### Example Linting Tools 

There are various linting and style-checking tools available for popular programming languages. 

For example, in Python:

- [`flake8`](https://flake8.pycqa.org/en/latest/) checks code for compliance with PEP8
- [`pylint`](https://pypi.org/project/pylint/) performs style checking along with additional linting functionalities
- [`bandit`](https://bandit.readthedocs.io/en/latest/) focuses on static analysis to detect potential security vulnerabilities.

### Linting Automation Using Continuous Integration

The use of linting tools is often automated through integration with continuous integration (CI) pipelines or pre-commit hooks available in version controlled code repositories, helping to streamline the development process and ensure code quality consistently on each commit. This is covered in a separate session.

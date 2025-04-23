---
title: "Lesson 2: Code Style & Linting"
teaching: 15
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- Why does code style matter?
- What is a linter and why use one?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Understand key code styling practices, conventions and specifications
- Use code style practices and linting tools to maintain code quality and reduce bugs and errors
- Automate code linting using continuous integration 

::::::::::::::::::::::::::::::::::::::::::::::::

## Intro to code style

### Why does code style matter?

Software development is inherently a collaborative activity. Even if you do not currently intend for anyone else to read your code, chances are someone will need to in the future — and that person might even be you, months or years later. By following and consistently applying code styling guidelines, you can significantly improve the readability and maintainability of your code. Consistency plays a vital role in this process. Adopting a clear set of style guidelines not only helps you write uniform code but also makes it easier to switch between projects. This is especially important when working as part of a team, where shared understanding and clarity are essential.

Using a consistent code style helps maintain code quality by making it easier to read, understand, and debug, ultimately reducing the likelihood of errors and bugs.

### Key code style practices, conventions and specifications

Styling practices and conventions play a key role in writing readable and maintainable code, but they can vary significantly between programming languages. These conventions generally cover aspects such as line length, line splitting, the use of white space, naming conventions for variables, functions, and classes, as well as indentation and commenting styles (where not enforced by the language itself).

It is important to note that programmers often have strong and differing opinions about what constitutes good style. For example, many style guides recommend a maximum line length of 80 characters, a convention that dates back to older hardware and terminal limitations. While some developers continue to find this helpful for readability and side-by-side editing, others argue that it feels unnecessarily restrictive on modern screens. Despite these differences, adopting and adhering to a consistent style within a project helps ensure clarity and makes collaboration smoother.

There are many established code style guides tailored to specific programming languages, such as:

- [PEP8](https://peps.python.org/pep-0008/) and [Google Style Guide](https://google.github.io/styleguide/pyguide.html) for Python
- [Google C++ Style Guide](https://google.github.io/styleguide/cppguide.html) and [C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines) for C++
- [Airbnb JavaScript Style Guide](https://airbnb.io/javascript/) and [Google JavaScript Style Guide](https://google.github.io/styleguide/jsguide.html) and [JavaScript Standard Style](https://standardjs.com/) for JavaScript
- [Go Style Guide](https://google.github.io/styleguide/go/) and [Go Styleguide](https://github.com/bahlo/go-styleguide) for Go.

## Intro to linters

- What is a linter and why use one?
- Example linting tools (e.g. in Python)
- Taking linting automation further using continuous integration

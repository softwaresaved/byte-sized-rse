---
title: "Lesson 4: Code Review"
teaching: 15
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- What are the benefits of collaborative code development?
- How can collaborating improve the quality and effectiveness of your code?
- What practices and tools support effective collaboration?
- Why should collaborative tools and workflows be adopted early in a project?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Identify benefits of coding with others, including improved code quality and shared ownership.
- Recognise common collaborative practices such as code review, pair programming, and version control.
- Understand how early adoption of collaborative tools helps prepare for scaling up development.
- Apply the practical collaborative strategy *code review* in a software project.

::::::::::::::::::::::::::::::::::::::::::::::::


This session introduces key practices for effective coding and collaboration within research software projects. You will learn how to work together on code through structured approaches such as code review, understand common workflows and tools that support collaborative development, and explore the processes that help maintain code quality and team productivity. We will then take a practical look at how to carry out code reviews using GitHub, one of the most widely used platforms for collaborative software development.

## Introduction to Coding Within a Collaboration

Software development thrives on collaboration, even when much of the coding is done individually. Getting input from others can have a big impact on the quality, maintainability, and effectiveness of your work, often requiring only a small investment of time. Since there is rarely a single “perfect” way to solve a problem, working with others allows you to share knowledge, skills, and perspectives, leading to better solutions and new insights. Through collaboration, you can learn new techniques, discover tools and infrastructure that streamline development, and help build a shared understanding that benefits the wider team or community.

### What are the Benefits of Coding With Others?

There are many benefits to coding with others. Collaborative coding practices — such as pair programming, code reviews, and shared repositories — can help catch bugs earlier, improve code readability, and increase overall code quality. It also fosters shared ownership of the codebase, making it easier for teams to maintain and extend code over time.

Importantly, it is best to adopt collaborative tools and practices before they become urgent. Setting up processes, code sharing and collaboration platforms (like GitHub or GitLab), and development workflows early on means you will be ready to handle code review, version control, and team communication smoothly when collaboration intensifies. Early investment in collaboration infrastructure pays off by preventing confusion and bottlenecks later in a project.

## Introduction to Code Review

### What is Code Review?

Code review is the process of examining and discussing someone else's code with the goal of checking its correctness and improving its quality and readability at the point when the code changes.
It is a key collaborative and software quality assurance practice in software development that can help identify bugs early, ensure consistency with coding standards, and support knowledge sharing across a team. 

Code review is universally applicable throughout the software development cycle - from design to development to maintenance. According to Michael Fagan, the author of the *code inspection* technique, [rigorous inspections can remove 60-90% of errors from the code even before the first tests are run](https://ieeexplore.ieee.org/document/5388086). Furthermore, according to Fagan, the cost to remedy a defect in the early (design) stage is 10 to 100 times less compared to fixing the same defect in the development and maintenance stages, respectively. Since the cost of bug fixes grows in orders of magnitude throughout the software lifecycle, it is far more efficient to find and fix defects as close as possible to the point where they are introduced.

### Why do Code Reviews?

Code review is very useful for all parties involved - someone checks your design or code for errors and gets to learn from your solution; having to explain code to someone else clarifies your rationale and design decisions in your mind too.

The specific aims of a code review can vary depending on the context — for example, production-ready code might undergo rigorous scrutiny, while early-stage prototypes may be reviewed more informally for general structure and approach. Code reviews can follow a formal process (e.g. structured pull requests with approval workflows) or take a more informal shape (e.g. ad hoc peer review or pair programming), depending on the needs of the project and the team.

### Code Review Types
  
There are several types of code review, each suited to different contexts and goals. 

An *informal review* involves casually asking a colleague for input or advice. This type of review is often used to improve understanding, share skills, or get help with problem-solving, rather than enforce specific standards. 

Some examples include *over-the-shoulder code review* (when one developer talks the other developer through the code changes while sitting at the same machine) and *pair programming* (when two developers work on the code at the same time with one of them actively coding and the other providing real-time feedback). The main focus here generally is on improving skills, understanding code and problem solving.

A *modification/contrubution-based review* occurs when changes or additions to a codebase are reviewed as they happen — commonly used in version-controlled software development workflows like GitHub pull requests. This approach is still considered informal (although tool-assisted) and focuses on ensuring understanding, clarity, maintainability, and code quality. 

A more rigorous and formal method is the *structured codebase review*, such as a *Fagan inspection*, where a team examines a codebase systematically, following strict criteria to identify defects or ensure conformance to standards. While this method can be highly effective, it is resource-intensive and less common in the research software community (but it does occur).The main focus is generally on conformance to processes & practices and identifying defects.

### Core Review Practices & Processes


## Practical Work

In the rest of this session, we will walk you through how a code review process works using GitHub.

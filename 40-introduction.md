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

Code review is valuable at all stages of the software development lifecycle — from initial design through development to ongoing maintenance — but it is best to incorporate it right from the start. According to Michael Fagan, the author of the *code inspection* technique, [rigorous inspections can remove 60-90% of errors from the code even before the first tests are run](https://ieeexplore.ieee.org/document/5388086). Furthermore, according to Fagan, the cost to remedy a defect in the early (design) stage is 10 to 100 times less compared to fixing the same defect in the development and maintenance stages, respectively. Since the cost of bug fixes grows in orders of magnitude throughout the software lifecycle, it is far more efficient to find and fix defects as close as possible to the point where they are introduced.

### Why do Code Reviews?

Code review is very useful for all the parties involved - code author as well as reviewers - someone checks your design or code for errors and gets to learn from your solution; having to explain code to someone else clarifies your rationale and design decisions in your mind too. In general, code reviews help improve code quality, catch bugs early, and promote shared understanding among team members. They also support skill development and encourage consistent coding practices across a project.

The specific aims of a code review can vary depending on the context — for example, production-ready code might undergo rigorous scrutiny, while early-stage prototypes may be reviewed more informally for general structure and approach. Code reviews can follow a more formal process (e.g. structured pull requests with approval workflows) or take an informal shape (e.g. ad hoc peer review or pair programming), depending on the needs of the project and the team.

### Code Review Types
  
There are several types of code review, each suited to different contexts and goals. 

An *informal review* involves casually asking a colleague for input or advice. This type of review is often used to improve understanding, share skills, or get help with problem-solving, rather than enforce specific standards. 
Some examples include *over-the-shoulder code review* (when one developer talks the other developer through the code changes while sitting at the same machine) and *pair programming* (when two developers work on the code at the same time with one of them actively coding and the other providing real-time feedback). 

A *code modification & contrubution-based review* occurs when changes or additions to a codebase are reviewed as they happen — commonly used in version-controlled software development workflows like GitHub's pull requests. This approach is a bit more formal (e.g. structured pull requests with approval workflows) and tool-assisted, and focuses on ensuring understanding, clarity, maintainability, and code quality. 

A more rigorous and formal method is the *structured codebase review*, such as a *Fagan inspection*, where a team examines a codebase systematically, following strict criteria to identify defects or ensure conformance to standards. While this method can be highly effective, it is resource-intensive and less common in the research software community (but it does occur). It focuses generally on conformance to processes and practices and identifying defects.

### Code Review Practices & Processes

In this session, we will focus on code review practices centered around code modifications and contributions. The aim is to integrate code review into the research software development process in a way that is lightweight, low-stakes, and easy to adopt. Even a short initial code review can have a significant impact. As highlighted in ["Best Kept Secrets of Peer Code Review" by Jason Cohen](https://www.amazon.co.uk/Best-Kept-Secrets-Peer-Review/dp/1599160676), the first hour of review is the most critical and productive, with diminishing returns thereafter.

The goal is to strike a practical balance: invest enough time to offer useful, actionable feedback without turning reviews into a bottleneck.
When reviewing code, focus on:

- Code quality - is the code clear and readable? Do functions serve a single purpose? Is it well-structured and consistent with the rest of the project?
- Best practices and conventions - is the project’s coding style followed? Are tests and documentation included and up to date?
- Efficiency and minimalism - does the change duplicate existing functionality (found elsewhere in the code or in a third-party library)? Is it limited to what’s required by the issue or ticket?
- Knowledge sharing: ask clarifying questions (do not assume you understand everything or know best) and offer respectful, specific feedback. This helps everyone learn and builds team trust.

Given the value of that first hour, keep your efforts targeted. Do not spend time on:

- Linting or style issues - automated tools or CI pipelines should catch these
- Hunting for bugs, unless something clearly looks wrong — instead, check that tests exist for various cases that should catch bugs
- Fixing unrelated legacy issues that pre-date the change — log those separately to avoid scope creep
- Architectural overhauls — save big-picture changes for design discussions or dedicated meetings to decide whether the code needs to be restructured
- Refactoring everything — provide only a few critical suggestions and aim for incremental improvement, not perfection.

In practice, code review often involves following a *project-specific checklist* to ensure consistency and alignment with coding standards. The process is typically *iterative*, with reviewers and contributors engaging in a cycle of discussion, updates, and re-review to address questions and refine changes before integration. If a conversation is taking place in a code review that has not been resolved by one or two back-and-forth exchange, then consider scheduling a conversation 
or a pair programming session to discuss things further (and record the outcome of the discussion - e.g. in the pull requests’s comments). This way - you can enhance code quality and collaborative learning. 

### Code Review Tools & Platforms

Modern source code management (SCM) tools such as Git, Mercurial, and Subversion are well suited for conducting code reviews focused on changes or contributions. These tools track modifications and provide clear “diffs” (differences) that make it easier to inspect code updates line-by-line. 

On top of these, various higher-level software development support platforms — such as GitHub, Review Board, JetBrains Space, and Atlassian Crucible — offer additional features and tools to streamline the review process, including inline comments to facilitate discussions, approval workflows, and integration with issue trackers. Many projects also adopt custom workflows tailored to their specific needs, balancing formality and flexibility to best support their development practices.

## Practical Work

In the rest of this session, we will walk you through how a code review process works using GitHub.

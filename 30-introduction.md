---
title: "Lesson 3: Intermediate Git"
teaching: 15
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::


Basic Git training usually covers the essential concepts, such as adding files, committing changes, viewing commit history, and checking out or reverting to earlier versions. 
But for RSEs working in collaborative, code-intensive projects, that is just the tip of the iceberg. 
More detailed topics like branching and merging strategies, and understanding merge conflicts are critical for managing code across teams and maintaining clean, reproducible development workflows.

In this session, we will explore branching and feature branch workflow, a popular method for collaborative development, along with some intermediate and advanced Git features (merging, rebasing, cherry-picking) 
and handling merge conflicts that can help streamline your development workflow and avoid common pitfalls.

## Introduction to Feature Branch Workflow

### Git Branches

You might be used to committing code directly, but not sure what branches really are or why they matter? 
When you start a new Git repository and begin committing, all changes go into a branch — by default, this is usually called `main` (or `master` in older repositories).
The name `main` is just a convention — a Git repository’s default branch can technically be named anything.

Why not just always use `main` branch? While it is possible to always commit to `main`, it is not ideal when you're collaborating with others, you are working on new features or want 
to experiment with your code, and you want to keep main clean and stable for your users and collaborators.

Creating a separate branch (often called a "feature" branch) allows you to add or test code without affecting the main line of development, work in parallel with collagues without worrying that
your code may break something for the rest of the team and review and merge changes safely after testing using pull/merge requests.

## Introduction to Merging Strategies

- Options for merging (fast forward, merge commit, rebase and merge)
- Other useful git features (cherry picking via git cherry-pick, stashing changes via git stash, resetting local state via git reset)

::::::::::::::::::::::::::::::::::::: keypoints

- Branches help you manage change, collaborate better, and avoid messy mistakes on main.

:::::::::::::::::::::::::::::::::::::

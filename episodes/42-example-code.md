---
title: "4.2 Some Example Code"
teaching: 10
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- What does a bad code repository look like?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Obtain example code used for this lesson
- Describe the purpose of the example code repository

::::::::::::::::::::::::::::::::::::::::::::::::

## Creating a Copy of the Example Code Repository

For this lesson we'll need to create a new GitHub repository based on the contents of another repository.

1. Once logged into GitHub in a web browser,
go to https://github.com/UNIVERSE-HPC/review-example.
1. Select 'Use this template', and then select 'Create a new repository' from the dropdown menu.
1. On the next screen, ensure your personal GitHub account is selected in the `Owner` field, and fill in `Repository name` with `review-example`.
1. Ensure the repository is set to `Public`.
1. Select `Create repository`.

You should be presented with the new repository's main page.
Next, we need to clone this repository onto our own machines,
using the Bash shell.
So firstly open a Bash shell (via Git Bash in Windows or Terminal on a Mac).
Then, on the command line,
navigate to where you'd like the example code to reside,
and use Git to clone it.
For example, to clone the repository in our home directory (replacing `github-account-name` with our own account),
and change directory to the repository contents:

```bash
cd
git clone https://github.com/github-account-name/review-example
cd review-example
```

## Examining the Code

This repository contains code written in Python to analyse a dataset from the UK ResearchFish publication database.
For the purposes of this training, we'll be using this repository to make some high-level commits and create a pull request for review. It's not necessary for us to delve deeper into how it works, but note that the repository contents have been modified to deliberately include many problem and errors!

::::::::::::::::::::::::::::::::::::: keypoints 

- Encountering a "bad" code repository is an opportunity to learn what not to do!

::::::::::::::::::::::::::::::::::::::::::::::::

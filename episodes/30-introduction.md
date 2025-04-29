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

In this session, we will explore branching and feature branch workflow, a popular method for collaborative development, along with some intermediate Git features (merging, rebasing, cherry-picking) 
and handling merge conflicts that can help streamline your development workflow and avoid common pitfalls.

## Introduction to Feature Branch Workflow

### Git Branches

You might be used to committing code directly, but not sure what branches really are or why they matter? 
When you start a new Git repository and begin committing, all changes go into a branch — by default, this is usually called `main` (or `master` in older repositories).
The name `main` is just a convention — a Git repository’s default branch can technically be named anything.

Why not just always use `main` branch? While it is possible to always commit to `main`, it is not ideal when you're collaborating with others, you are working on new features or want 
to experiment with your code, and you want to keep main clean and stable for your users and collaborators.

### Feature Branch

Creating a separate branch (often called a "feature" branch) allows you to add or test code (containing a new "feature") without affecting the main line of development, work in parallel with collagues without worrying that
your code may break something for the rest of the team and review and merge changes safely after testing using pull/merge requests.

How do you decide when to use a new branch? You should consider starting a new branch whenever you are working on a distinct feature or fixing a specific bug. 
This allows you to collect a related set of commits in one place, without interfering with other parts of the project.

Branching helps separate concerns in your codebase, making development, testing, and code review much easier. It also reduces the chance of conflicts during collaborative work, especially when multiple people are contributing to the same repository.

This approach is known as the **feature branch workflow**. In this model, each new feature or fix lives in its own branch. Once the work is complete and has been tested, the branch is reviewed 
by project collaborators (other than the code author), any merge conflicts addressed and the new work merged back into the main branch.
Using feature branches is an efficient way to manage changes, collaborate effectively, and keep the main branch stable and production-ready.

## Introduction to Merging Strategies

- Options for merging (fast forward, merge commit, rebase and merge)
- Other useful git features (cherry picking via git cherry-pick, stashing changes via git stash, resetting local state via git reset)

### Merging

When you are ready to bring the changes from your feature branch back into the main branch, Git offers you to do a merge - a process that unifies work done in 2 separate branches. 
Git will take two (or more - you can merge more branches at the same time) commit pointers and attempt to find a common base commit between them. 
Git has several different methods to find a base commit - these methods are called "merge strategies". Once Git finds a common base commit it will create a new "merge commit" that combines the changes of the specified merge commits. Technically, a merge commit is a regular commit which just happens to have two parent commits.

Each merge strategy is suited for a different scenario. The choice of strategy depends on the complexity of changes and the desired outcome. Let's have a look at the most commonly used merge strategies.

### Fast Forward Merge

A fast-forward merge occurs when the main branch has not diverged from the feature branch - meaning there are no new commits on the main branch since the feature branch was created. 

```text
A - B - C [main]
         \
          D - E [feature]
```

In this case, Git simply moves the main branch pointer to the latest commit in the feature branch. This strategy is simple and keeps the commit history linear - i.e. the history is one straight line.

After a fast forward merge:

```text
A - B - C - D - E [main][feature]
```

### 3-Way Merge with Merge Commit

A fast-forward merge is not possible if the main and the feature branches have diverged. 

```text
A - B - C - F [main]
         \
          D - E [feature]
```

If you try to merge your feature branch changes into the main branch and other changes have been made to main - regardless of whether these changes create a conflict or not - Git will try to do a 3-way merge and generate a merge commit. 

A merge commit is a dedicated special commit that records the combined changes from both branches and has two parent commits, preserving the history of both lines of development. The name "3-way merge" comes from the fact that Git uses three commits to generate the merge commit - the two branch tips and their common ancestor to reconstruct the changes that are to be merged.

```text
A - B - C - F - "MergeCommitG" [main]
         \     /
          D - E [feature]
```

In addition, if the two branches you are trying to merge both changed the same part of the same file, Git will not be able to figure out which version to use and merge automatically.
When such a situation occurs, it stops right before the merge commit so that you can resolve the conflicts manually before continuing.

Here is a little comparison of the two merge strategies we covered so far.

| Fast Forward      | 3-Way Merge |
| ----------------------- | ----------------------|
| No new commits on main  |  New commits on main  |
| Linear History          | Commit with 2 parents   |
| No merge commits        | Merge commit is created |

 	
### Rebase and Merge

In Git, there is another way to integrate changes from one branch into another: the rebase.

Let's go back to an earlier example from the 3-way merge, where main and feature branches have diverged with subsequent commits made on each (so fast-forward merging strategy is not an option).

```text
A - B - C - F [main]
         \
          D - E [feature]
```

When you rebase the feature branch with the main branch, Git replays each commit from the feature branch on top of all the commits from the main branch in order. This results in a cleaner, linear history that looks as if the feature branch was started from the latest commit on main. 

So, all the changes introduced on feature branch (commits D and E) are reapplied on top of commit F - becoming D' and E'. Note that D' and E' are rebased commits, which are actually new commits with different SHAs but the same modifications as commits D and E.


```text
A - B - C - F [main]
             \
              D' - E' [feature]
```

At this point, you can go back to the main branch and do a fast-forward merge with feature branch.

Fast forward merge strategy is best used when you have a short-lived feature branch that needs to be merged back into the main branch, and no other changes have been made to the main branch in the meantime.

Rebase is ideal for feature branches that have fallen behind the main development line and need updating. It is particularly useful before merging long-running feature branches to ensure they apply cleanly on top of the main branch.
Rebasing maintains a linear history and avoids merge commits, making it look as if changes were made sequentially and as if you created your feature branch from a different point in the repository's history. 
A disadvantage is that it rewrites commit history, which can be problematic for shared branches as it requires force pushing.

### Squash and Merge


::::::::::::::::::::::::::::::::::::: keypoints

- Branches help you manage change, collaborate better, and avoid messy mistakes on main.

:::::::::::::::::::::::::::::::::::::

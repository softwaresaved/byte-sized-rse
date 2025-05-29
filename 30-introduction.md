---
title: "Lesson 3: Intermediate Git"
teaching: 15
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- What is a Git branch and why is it useful in collaborative development?
- When should I create a new branch in my project?
- What are the differences between fast-forward merge, 3-way merge, rebase, and squash and merge?
- How does Git handle merging when branches have diverged?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Understand the purpose and benefits of using Git branches, especially the feature branch workflow in collaborative projects.
- Compare Git merging strategies (fast-forward, 3-way merge, rebase, squash and merge) and understand when to use each.
- Gain familiarity with intermediate Git features, including cherry-picking, stashing, and resetting.

::::::::::::::::::::::::::::::::::::::::::::::::


Basic Git training usually covers the essential concepts, such as adding files, committing changes, viewing commit history, and checking out or reverting to earlier versions. 
But for RSEs working in collaborative, code-intensive projects, that is just the tip of the iceberg. 
More detailed topics like branching and merging strategies, and understanding merge conflicts are critical for managing code across teams and maintaining clean, reproducible development workflows.

In this session we will explore branching and feature branch workflow, a popular method for collaborative development using Git, along with some intermediate Git features (merging, rebasing, cherry-picking) 
and handling merge conflicts that can help streamline your development workflow and avoid common pitfalls in collaborative software development.

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
	
### Rebase & Merge

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
Rebasing maintains a linear history and avoids merge commits (like fast forwarding), making it look as if changes were made sequentially and as if you created your feature branch from a different point in the repository's history. 
A disadvantage is that it rewrites commit history, which can be problematic for shared branches as it requires force pushing.

Here is a little comparison of the three merge strategies we have covered so far.

| Fast Forward      | Rebasing | 3-Way Merge |
| ----------------------- | ----------------------|----------------------|
| Maintains linear history  |  Maintains linear history | Non-linear history (commit with 2 parents) |
| No new commits on main | New commits on main | New commits on main |
| Avoids merge commits         | Avoids merge commits | Uses merge commits |
| Only works if there are no new commits on the main branch        | Works for diverging branches | Works for diverging branches |
| Does not rewrite commit history | Rewrites commit history | Does not rewrite commit history |

### Squash & Merge

Squash and merge squashes all the commits from a feature branch into a single commit before merging into the main branch. This strategy simplifies the commit history, making it easier to follow.
This strategy is ideal for merging feature branches with numerous small commits, resulting in a cleaner main branch history. 

## Handy Git Features for Managing Local Changes

As your projects grow, you will occasionally need to manage your local code history more precisely. Git offers a few useful features to help you do just that — especially when you are not quite ready to commit or want to isolate specific changes.

### Git Stash: Setting Changes Aside for Later

Imagine you are halfway through some code changes and suddenly need to switch tasks or pull updates from the remote branch. Committing is not ideal yet — so what do you do?
Use `git stash` to safely store your uncommitted changes in a local "stash". This lets you clean your working directory and avoid conflicts, without losing any work. When you are ready, you can bring those changes back using `git stash pop`.

### Git Cherry-Pick: Pulling in a Specific Commit

Sometimes, you want to take just one specific commit (say, from another branch) and apply it to your current branch — without merging the whole branch. That is where `git cherry-pick` command comes in. It applies the changes from the chosen commit directly on top of your current branch, as if you’d made them there all along.

### Git Reset: Rewinding Your Commit History

Made a commit too soon? `git reset` allows you to undo commits locally. It moves your branch pointer back to an earlier commit, turning those "undone" changes into uncommitted edits in your working directory. It is handy for rewriting local history before sharing code — but be careful using it on shared branches, as it alters commit history.

## Practical Work

In the rest of this session, we will walk you through the feature branch workflow, different merging strategies and handling conflicts before merging.

::::::::::::::::::::::::::::::::::::: keypoints

- A Git branch is an independent line of development; the default is conventionally called `main` (but all branches are equal and the main branch can be renamed).
- Branches help you manage change, collaborate better, and avoid messy mistakes on main.
- Feature branches let you develop and test code without affecting the main branch and support collaborative and parallel development.
- Fast-forward merges are used when the main branch has not changed since the feature branch was created, resulting in a linear history.
- 3-way merges occur when both branches have diverged; Git creates a merge commit to preserve both histories.
- Rebasing replays feature branch commits on top of the main branch for a cleaner, linear history—but it rewrites history and should be used with care.
- Squash and merge compresses all changes from a feature branch into a single commit, simplifying history.
- Understanding different merge strategies and when to use them is crucial for maintaining clean and manageable project histories.

:::::::::::::::::::::::::::::::::::::

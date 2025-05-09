---
title: "3.6 Merge Conflicts"
teaching: 10
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

## Work on Another Issue

Now we still have two remaining  issues we can look at.
Interestingly, both of them require changes that can cause a conflict when merging,
so let's look at those now.

First, let's go to the `main` branch and pull the repository changes on this branch to our local repository.
Generally, it's good practice to use `git pull` to synchronise your local repo with the GitHub one before doing any further work.

```bash
git checkout main
git pull
git log
```

So now, again, we have those two commits on main as we would expect.
Let's create a feature branch to fix our snake-case issue.

```bash
git branch issue-1-use-snake-case
git checkout issue-1-use-snake-case
```

So now, edit the `climate_analysis.py` file,
and change functions to use a snake case style,
e.g. change `FahrToCelsius` to `fahr_to_celsius`.
Remember to also change the one in the `fahr_to_kelvin` function as well.

Note we've changed the call to `fahrtocelsius` near the bottom.
let's commit this to our new feature branch:

```bash
git add climate_analysis.py
git commit -m "#1 use snake case naming"
```

Now we can commit as before

```bash
git push --set-upstream origin issue-1-use-snake-case
```

## Introducing a Conflict

At this point, we could follow this advice and merge this branch's work into the `main` branch,
which would be very neat and tidy.
But life is rarely like that: what happens when someone else commits their changes in some way to the main branch?
Where does that leave us when we come to merge?

You may recall we created an issue for fixing the function call to the `FahrToCelsius` function, where the call referenced the function incorrectly.
Let's assume that a colleague has made these changes,
and updated the `main` branch.
Let's pretend we're our colleague,
and we're making this fix to the main branch.
First, let's switch to the main branch:

```bash
git checkout main
git status
git log
```

Now as we can see, this main branch is completely unaware of the commits in our new feature branch,
and is at the initial state of the repository.
Let's make the fix.
Now we could (and should) create a feature branch here,
make and commit the change,
then merge with the main branch.
But for expediency, we'll commit directly to the main branch,
and assume they did it the right way.
Edit the `climate_analysis.py` file, 
and update the `FahrToCels` function call to `FahrToCelsius`,
and save the changes.

```bash
git status
git add climate_analysis.py
git commit -m "#3 Fix incorrect function call"
git log
git push
```

Now - we have this extra commit on main,
which we can see if we do:

```bash
git log
```

## Resolving a Merge Conflict

Now let's see what happens when we create a pull request on our feature branch, as before, and try to merge.
Again, let's go to GitHub and then:

1. Go to `Pull requests`, and select `New pull request`.
1. Select the new feature branch `issue-1-use-snake-case`.
1. Select this new branch in `compare:`,
and ensure that `base:` says `main`.

Note that now it says we can't automatically perform this merge.
Essentially, it's compared the source and destination branches,
and determined that there is a conflict,
since there are different edits on the same line for commits in the `main` and feature branch.
But we'll go ahead and create the PR anyway:

1. Select `Create pull request`.
1. For the title, add "Fixes #1 - use snake case naming".
1. Assign yourself to the issue.
1. Select `Create pull request`.

We should now see that "This branch has conflicts that must be resolved".
And in this case, there is only one conflicting file - `climate_analysis..py`,
but there could be more than one.
Now we can attempt to resolve the conflict by selecting `Resolve conflicts`.

The GitHub interface  is really useful here.
It tells you which files have the conflicts on the left (only `climate_analysis.py` in this case),
and where in each file the conflicts are.
So let's fix the conflict.
Near the bottom, we can see that our snake case naming of that function call conflicts with the fix to it,
and this has caused a conflict.

Now importantly we have to decide how to resolve the conflict.
Fortunately, our fix for the snake_case issue resolves this issue as well,
since we're calling the function correctly,
which makes the other fix redundant.
So let's remove the other fix,
by editing out the chevron and equals parts, and the fix we don't want.
We then select `Mark as resolved`, then `Commit merge`.
Now unfortunately, due to the conflict commit,
we can no longer rebase and merge.
So select the option to create a `Merge commit`,
then select `Merge pull request`,
and `Confirm merge`.
And as before, delete the feature branch which is no longer needed.

## Commits Highlighted in Issues

If we go to the repository's list of commits now in the `main` branch,
we see that we have a "merge branch main into issue-1-use-snake-case" commit which resolves the conflict (which occurred on the feature branch)
and also a merge pull request commit,
for when we merged the feature branch with main.

::::::::::::::::::::::::::::::::::::: keypoints 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

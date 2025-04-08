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

Now we have two other issues we can look at
And these are interesting - both of them require changes that can cause a conflict when merging
Let's look at those now
First, let's go to main and pull the repository changes on the main branch to our local repository
Always a good idea to do this! use git pull to synchronise your local repo with the GitHub one
git checkout main
git pull
git log
So now, again, we have those two commits on main as we would expect
Let's create a feature branch to fix our snake-case issue
git branch issue-1-use-snake-case
git checkout issue-1-use-snake-case
So now, edit the climate_analysis.py file, and change functions to use a snake case style
e.g. FahrToCelsius to fahr_to_celsius
Remember to change the one in the fahr_to_kelvin function!
Note we've changed the call to fahrtocelsius near the bottom
let's commit this to our new feature branch
git add climate_analysis.py
git commit -m "#1 use snake case naming"
Now we can commit as before
git push --set-upstream origin issue-1-use-snake-case

## Introducing a Conflict

At this point, we could follow this advice and merge this branch's work into the main branch
This would be very neat and tidy!
But life is rarely like that - and what happens when someone else commits their changes in some way to the main branch?
Where does that leave us when we come to merge?
Let's find out!
You may recall we created an issue for fixing the function call to the FahrToCelsius function - the call referenced the function incorrectly.
The function name was wrong
Let's assume that a colleague has made these changes, and updated the main branch
Hopefully they've done this on a feature branch and merged it, but maybe not!
Let's pretend we're our colleague, and we're making this fix to the main branch
First, let's switch to the main branch
git checkout main
git status
git log
Now as we can see, this main branch is completely unaware of the commits in our new feature branch
And is at the initial state of the repository
Let's make the fix
Now we could (and should) create a feature branch here, make and commit the change, then merge with the main branch
But for the sake of time, let's just commit directly to the main branch, and assume they did it the right way
Edit the climate_analysis.py file
And update the "FahrToCels" function call to "FahrToCelsius", and save the changes
git status
git add climate_analysis.py
git commit -m "#3 Fix incorrect function call"
git log
git push
Now - we have this extra commit on main
Which we can see if we do
git log

## Resolving a Merge Conflicts

Now let's see what happens when we create a pull request on our feature branch, as before, and try to merge
Again, let's go to GitHub and this time, go to "Pull requests", select "New pull request"
And select the new feature branch issue-1-use-snake-case
Then select it in "compare", and ensure that "base" says "main"
now - note that is says we can't automatically merge!
It's handy that it does this - it's compared the source and destination branches, and determined that there is a conflict
Since there are different edits on the same line for commits in the main and feature branch
But we'll go ahead and create the PR anyway - select "Create pull request"
title: Fixes #1 - use snake case naming
assign yourself
create pull request
We create the PR, and we see "This branch has conflicts that must be resolved"
And in this case, there is only one conflicting file - climate_analysis.py - but there could be more than one
Now we can attempt to resolve the conflict by selecting "resolve conflicts"
QUESTION: who's resolved conflicts during a merge on the command line? Yes/No
It can be a bit tricky, yes?
The GitHub interface for doing this is quite a bit nicer!
It tells you which files have the conflicts on the left (only climate_analysis.py in this case)
And where in each file the conflicts are
So let's fix the conflict
Near the bottom, we can see that our snake case naming of that function call conflicts with the fix to it
And this has caused a conflict
Now importantly we have to decide how to resolve the conflict
If we're lucky, common sense can help us!
Now our snake_case fix resolves this issue anyway, since we're calling the function correctly, which makes the other fix redundant
So let's remove the other fix
We do this by editing out the chevron and equals parts, and the fix we don't want
We then select "Mark as resolved", then "commit merge"
Now unfortunately, due to the conflict commit, we can no longer rebase and merge
So select the option to create a merge commit
Then select merge pull request, and confirm merge
And as before, delete the feature branch

## Commits Highlighted in Issues

if we go to the repository's list of commits now (in the main branch) we see that
we have a "merge branch main into issue-1-use-snake-case" commit which resolves the conflict (which occurred on the feature branch)
and also a merge pull request commit, for when we merged the feature branch with main

::::::::::::::::::::::::::::::::::::: keypoints 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

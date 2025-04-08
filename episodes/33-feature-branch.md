---
title: "3.3 Feature Branch Workflow"
teaching: 10
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

## Create new feature branch to work on first issue

We'll start by working on the missing docstring issue
For the sake of this activity, let's assume that the bug which causes the script to fail is being tackled by someone else

So let's now create a feature branch (also known in some places as “topic” branches), and work on adding that docstring, using that branch
Now on the command line, we've checked out our new repository, and can see what branches it currently has by doing
git branch (with no arguments)
And we can see we have only our main branch
With an asterisk to indicate it's the current branch we're on
[[[
git branch -a
Where “-a” means show us all branches
But also two “remotes/origin” branches - which are references to the remote repository we have on GitHub
In this case, a reference to the equivalent “main” branch in the remote repository
HEAD here - as you may know - refers to the latest commit, so this refers to the latest commit on the main branch (which is where we are now)
You can think of ”origin” as a stand-in for the full repository URL
Indeed, if we do “git remote -v”, we can see the full URL for “origin”
The first - remotes/origin/HEAD - refers to the latest commit on the active branch on the remote repo
The second - refers to the branch itself
]]]
If we do “git log”, we can see only one commit so far
So, in order to get started on our docstring work, let's tell git to create a new branch by using “git branch” to create a branch this time
When we name the branch, it's considered good practice to include the issue number, and perhaps something useful about the issue, in the name of the feature branch
Makes it easier to see what this branch was about
git branch issue-2-missing-docstrings
Now if we use “git branch, we can see that our new branch has been created! Great!
But - if we type “git status”, we see that we're still on our main branch, and any commits at this point will still go  on this main branch and not our new one
QUESTION: who's created their new feature branch? Yes/No
So what we need to do is to switch to this new branch, which we can do via
git checkout issue-2-missing-docstrings
Now if we do “bit branch” again, we can see we're on the new branch
And if we do “git status”, we also see that we're on this new branch
A very good habit to get into - use “git status” before you do anything
It helps to clarify on which branch you're working, and also any outstanding changes you may have forgotten about!
Now, one thing that's important to realise, is that the contents of the new branch are at the state at which we created the branch
something…
If we do “git log”, to show us the commits, we can see they are the same as when we first cloned the repository
i.e. from the first commit
So any commits we do now, will be on our new feature branch and will depart from this commit on the main branch
and be separate from any other commits that occur on the main branch

## Work on first issue in feature branch

Now we're on our feature branch, we can make some changes to fix this issue
So open up the climate_analysis.py file in an editor of your choice
For simplicity, I'm just going to use a command line editor called nano
I'm going to add the following to the FahrToKelvin function

    """Converts fahrenehit to kelvin

    Args:
        fahr (float): temperature in fahrenheit

    Returns:
        float: temperature in kelvin
    """
QUESTION: Who has added this to the file, and saved it? Yes/No

Now we've done this, let's commit this change to the repository on our new branch
git add climate_analysis.py
git commit -m “#2 Add missing function docstring”
Notice we've added in the issue number and a short description to the commit message here
If you've never seen this before, this is considered good practice
We've created an issue describing the problem, and in the commit, we reference that issue number explicitly
Later, we'll see GitHub will pick up on this, and in this issue, we'll be able to see the commits associated with this issue
Now we've also got a module docstring to add as well, so let's add that
Open up our editor on this file again

""" Performs conversions between different temperature scales.”””

git add climate_analysis.py
git commit -m “#2 Add missing module docstring”
So again, we're committing this change against issue 2
Now let's look at our new branch
git log
So, as we can see, we now have our initial commit (inherited from the main branch) and our two new commits on this branch for our missing docstring)

QUESTION: who's edited the file and made the changes, and committed them - who's done that twice? Yes/No

## Push new feature branch and commits to GitHub

Now let's push these changes to GitHub
Since this is a new branch, we need to tell GitHub where to push the new branch commits, by naming the branch on the repository
If we just type “git push”
We get a suggestion telling us so, which is quite helpful!
git push --set-upstream origin issue-2-missing-docstrings
So here, we're telling git to push the changes on the new branch to a branch with the same name on the remote repository
‘origin' here is a shorthand that refers to the originating repository (the one we cloned originally)
You'll notice a message suggesting we could do a pull request to merge the changes with the main branch
QUESTION: who's committed that change and pushed the new branch with its commits to GItHub? Yes/no
Let's do this now!

::::::::::::::::::::::::::::::::::::: keypoints 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

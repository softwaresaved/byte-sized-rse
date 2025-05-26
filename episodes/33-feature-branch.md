---
title: "3.3 Feature Branch Workflow"
teaching: 10
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- How do I use Git to create and work on a feature branch?
- How do I push my local branch changes to GitHub?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Create and use new a feature branch in our repository to work on an issue
- Fix issue and commit changes to the feature branch
- Push the new branch and its commits to GitHub

::::::::::::::::::::::::::::::::::::::::::::::::

## Create new feature branch to work on first issue

We'll start by working on the missing docstring issue.
For the purpose of this activity,
let's assume that the bug which causes the script to fail is being tackled by someone else.

So let's create a feature branch,
and work on adding that docstring, using that branch.
But before we do, let's take a look and see what's already there.

### Examining Existing Repository Branches

We've already checked out our new repository,
and can see what branches it currently has by doing:

```bash
git branch
```

```output
* main
```

And we can see we have only our main branch,
with an asterisk to indicate it's the current branch we're on.

We can also use `-a` to show us all branches:

```bash
git branch -a
```

```output
* main
  remotes/origin/HEAD -> origin/main
  remotes/origin/main
```

Note the other two `remotes/origin` branches,
which are references to the remote repository we have on GitHub.
In this case, a reference to the equivalent `main` branch in the remote repository.
`HEAD` here, as you may know, refers to the latest commit,
so this refers to the latest commit on the main branch (which is where we are now).
You can think of `origin` as a stand-in for the full repository URL.
Indeed, if we do the following,
we can see the full URL for `origin`:

```bash
git remote -v
```

```output
origin	git@github.com:steve-crouch/git-example2.git (fetch)
origin	git@github.com:steve-crouch/git-example2.git (push)
```

If we do `git log`, we can see only one commit so far:

```bash
git log
```

```output
commit be6376bb349df0905693fdaad3a016273de2bdeb (HEAD -> main, origin/main, origin/HEAD)
Author: Steve Crouch <s.crouch@software.ac.uk>
Date:   Tue Apr 8 14:47:05 2025 +0100

    Initial commit
```

### Creating a new Branch

So, in order to get started on our docstring work,
let's tell git to create a new branch.

When we name the branch, it's considered good practice to include the issue number (if there is one),
and perhaps something useful about the issue,
in the name of the feature branch.
This makes it easier to see what this branch was about:

```bash
git branch issue-2-missing-docstrings
```

Now if we use the following,
we can see that our new branch has been created:

```bash
git branch
```

```output
  issue-2-missing-docstrings
* main
```

However, note that the asterisk indicates that we are still on our main branch,
and any commits at this point will still go on this main branch and not our new one.
We can verify this by doing `git status`:

```output
On branch main
Your branch is up-to-date with 'origin/main'.

nothing to commit, working tree clean
```

:::::::::::::::::: instructor

### Creating Feature Branch - Checkin

Who's created their new feature branch?

::::::::::::::::::

### Switching to the New Branch

So what we need to do now is to switch to this new branch,
which we can do via:

```bash
git switch issue-2-missing-docstrings
```

```output
Switched to branch 'issue-2-missing-docstrings'
```

Now if we do `git branch` again,
we can see we're on the new branch.
And if we do `git status` again,
this verifies we're on this new branch.

Using `git status` before you do anything is a good habit.
It helps to clarify on which branch you're working,
and also any outstanding changes you may have forgotten about.

Now, one thing that's important to realise,
is that the contents of the new branch are at the state at which we created the branch.
If we do `git log`, to show us the commits,
we can see they are the same as when we first cloned the repository (i.e. from the first commit).
So any commits we do now,
will be on our new feature branch and will depart from this commit on the main branch,
and be separate from any other commits that occur on the main branch.

## Work on First Issue in New Feature Branch

Now we're on our feature branch, we can make some changes to fix this issue.
So open up the `climate_analysis.py` file in an editor of your choice.

Then add the following to the `FahrToKelvin` function (just below the function declaration):

```python
    """Converts fahrenheit to kelvin

    Args:
        fahr (float): temperature in fahrenheit

    Returns:
        float: temperature in kelvin
    """
```

Then save the file.

:::::::::::::::::: instructor

### Changing the File - Checkin

Who has added this to the file, and saved it?

::::::::::::::::::

Now we've done this, let's commit this change to the repository on our new branch.

```bash
git add climate_analysis.py
git commit -m "#2 Add missing function docstring"
```

Notice we've added in the issue number and a short description to the commit message here.
If you've never seen this before, this is considered good practice.
We've created an issue describing the problem,
and in the commit, we reference that issue number explicitly.
Later, we'll see GitHub will pick up on this,
and in this issue, we'll be able to see the commits associated with this issue.

Now we've also got a module docstring to add as well, so let's add that.
Open up our editor on this file again,
and add the following to the top of the file:

```python
""" Performs conversions between different temperature scales."""
```

Then, add and commit this change:

```bash
git add climate_analysis.py
git commit -m "#2 Add missing module docstring"
```

So again, we're committing this change against issue number 2.
Now let's look at our new branch:

```bash
git log
```

```output
commit 6bfc96e2961277b441e5f5d6d924c4c4d4ec6a68 (HEAD -> issue-2-missing-docstrings)
Author: Steve Crouch <s.crouch@software.ac.uk>
Date:   Tue Apr 8 15:40:47 2025 +0100

    #2 Add missing module docstring

commit 20ea697db6b122aae759634892f9dd17e6497345
Author: Steve Crouch <s.crouch@software.ac.uk>
Date:   Tue Apr 8 15:29:37 2025 +0100

    #2 Add missing function docstring

commit be6376bb349df0905693fdaad3a016273de2bdeb (origin/main, origin/HEAD, main)
Author: Steve Crouch <s.crouch@software.ac.uk>
Date:   Tue Apr 8 14:47:05 2025 +0100

    Initial commit
```

So, as we can see, on our new feature branch we now have our initial commit inherited from the main branch,
and also our two new commits.

:::::::::::::::::: instructor

### Comming on the Branch - Checkin

Who's edited the file and made the changes, and committed them - who's done that twice?

::::::::::::::::::

## Push New Feature Branch and Commits to GitHub

Let's push these changes to GitHub.
Since this is a new branch, we need to tell GitHub where to push the new branch commits,
by naming the branch on the remote repository.

If we just type `git push`:

```bash
git push
```

```output
fatal: The current branch issue-2-missing-docstrings has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin issue-2-missing-docstrings
```

We get a suggestion telling us we need to do this,
which is quite helpful!

```bash
git push --set-upstream origin issue-2-missing-docstrings
```

```output
Enumerating objects: 8, done.
Counting objects: 100% (8/8), done.
Delta compression using up to 20 threads
Compressing objects: 100% (6/6), done.
Writing objects: 100% (6/6), 805 bytes | 805.00 KiB/s, done.
Total 6 (delta 2), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (2/2), completed with 1 local object.
remote: 
remote: Create a pull request for 'issue-2-missing-docstrings' on GitHub by visiting:
remote:      https://github.com/steve-crouch/git-example2/pull/new/issue-2-missing-docstrings
remote: 
To github.com:steve-crouch/git-example2.git
 * [new branch]      issue-2-missing-docstrings -> issue-2-missing-docstrings
Branch 'issue-2-missing-docstrings' set up to track remote branch 'issue-2-missing-docstrings' from 'origin'.
```

So here, we're telling git to push the changes on the new branch to a branch with the same name on the remote repository.
`origin` here is a shorthand that refers to the originating repository (the one we cloned originally).
You'll notice a message suggesting we could create a pull request to merge the changes with the main branch.

:::::::::::::::::: instructor

### Pushing the Feature Branch to GitHub - Checkin

Who's committed that change and pushed the new branch with its commits to GitHub?

::::::::::::::::::

Let's pushing the feature branch to GitHub now!

::::::::::::::::::::::::::::::::::::: keypoints 

- A branch is one version of your project that can contain its own set of commits
- Feature branches enable us to develop / explore / test new code features without affecting the stable main code
- Use `git branch` to create a new branch in Git
- Use `git switch` to change to and use another branch
- Add an issue number, e.g. `#1` to a Git commit message so GitHub registers those commits under that issue
- Use `git push --set-upstream origin branch-name` to push the commits on a new branch to a GitHub repository

::::::::::::::::::::::::::::::::::::::::::::::::

---
title: "3.5 Merging a Pull Request"
teaching: 10
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

## How to Merge the Pull Request?

You'll notice there's a subtle dropdown on the “Merge pull request” button
And one other option we have is how to perform the merge
You may remember from the introduction about doing a “rebase and merge” as opposed to just doing a merge commit
Since it leads to a cleaner repository history
For example, if we did a normal merge here, we'd end up with our two new commits and a merge commit
But if we do a rebase and then merge, our two commits are essentially just added to the top of main
Let's do that - select the third option in the dropdown: “Rebase and merge”
Note that if there had been a conflict with any commits on the main branch, we very likely wouldn't have been able to merge using this method
Which in itself is a good question - even if we'd done a straight commit, what would happen if there was a conflict?
If we have time, we'll look at this later
A question came up earlier about disadvantages of using rebasing
You can also do rebasing with branches on the command line
But a word of warning - when doing this, be really sure you know what you're doing
Since rebasing in this way rewrites the repository's history
And therefore, with rebasing, there is a GOLDEN RULE
Which states that you should only rebase with a local branch, never a public (shared) branch you suspect is being used by others
When rebasing, you're re-writing the history of commits
If someone else has the repository on their own machine and has worked on a particular branch, say
If you rebase on that branch, the history will have changed, and they will run into difficulties due to the rewritten history
It can get quite messy!
If in doubt, do a standard merge

## Merge the Pull Request

So now let's go ahead and “Rebase pull request”
We can add more information here if needed - but let's “Confirm rebase and merge”
Note that it says  that the merge was done successfully, and suggests we can delete the branch
QUESTION:  who has merged the pull request? Yes/No
We said earlier that branches in Git should be short lived where possible, and keeping branches hanging around may cause confusion
So let's delete it now
Now if we go the main branch on the main repository page in GitHub, we can see that the changes have been merged
And if we look at “commits”, we can see the commits we made on our feature branch have been added to the main branch

## See Commits on Issues

Now, remember those commit messages with the issue numbers in them?
If we go to our issues, we can see them with the commits associated with those issues
They're listed in chronological order
Which is really handy when checking on issue progress
Plus, it means the reason behind each commit is now traceable back to the originating issue
So why are there two sets of commits, when we only made one?
That's because we first made two commits to the branch
And then, using a rebase method, we applied our commits to the main branch

## Summary

So what are the benefits so far?
By using different feature branches, as opposed to just committing directly to the main branch, we've isolated the “churn” of developing a feature from the main branch
So this really is a key benefit - it allows us to maintain a working main branch
It also gives us the opportunity to abandon a branch entirely, with no need to manually change things back
In such a case, all we need to do is delete the branch
Another benefit is in the other direction
We are also effectively isolated from the changes being made on other feature branches
So when a number of changes are being made, we still (hopefully!) only have to worry about our own changes
And it also gives us a process that helps us maintain a working version on main for our users (which may very well include ourselves!)
And it also gives us a mechanism - via pull requests - to have others review our code before changes are introduced into the codebase

So what we've shown is one way to use feature branch workflow
Using feature branches directly off the main branch, and merging to main
We've chosen this way for the training, since it's more straightforward to teach in a practical activity
But there are others
Another way is to use a long-lived branch off of main, called usually something like “dev” or “develop”
And this dev branch would represent a general branch of development
And using this approach, feature branches are created off of the dev branch instead, and then merged back to the dev branch
And later, when a release of the software is due, or at an appropriate point, the dev branch is merged with the main branch
This gives development greater distance from the main branch, which could be a good thing
And it means you can merge and test all changes together on that branch before you merge with the main branch, to ensure it all works together
But also means when it comes to merge, it can be more difficult since the dev branch could have built up a considerable number of changes that need to be merged
In either case, the key is to make sure that code is tested and checked with the right people in your team before you merge to main

::::::::::::::::::::::::::::::::::::: keypoints 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

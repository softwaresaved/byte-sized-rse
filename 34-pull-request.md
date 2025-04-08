---
title: "3.4 Creating a Pull Request"
teaching: 10
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

## How to Merge our Changes with `main`?

We've essentially fixed this issue now, so next we need to somehow merge these changes on our feature branch with the main branch
And we'll do that now by using a pull request
Now before this, particularly if it was code I was changing, I would normally have tested the changes and ensured the code is working properly
To save time, we haven't done that here, but that's definitely something worth noting!
Before pushing any changes, test your code first
If you have any unit tests, run those too to check that your changes haven't broken anything
And also, particularly if this was a change implementing a new feature, I'd consider writing a new unit test to test that feature
You may have been present at our previous Research Software Camp session on code review, where we used pull requests as a mechanism to review code changes across a team
We'll be using a pull request here too
But if you weren't, a pull request is a way to propose changes on a particular Git branch, and request they be merged with another branch
They're really useful as a tool in teams, since they provide a way to check the changes before doing a merge
They allow you to see the changes to files across all the commits in the branch, and look at how these commits will change the codebase
And you can assign a number of reviewers to review the pull request, and submit a review with their thoughts on whether to accept the pull request, or make changes, and so on. Really useful!
So we could create the pull request on the command line, but we'll use the GitHub interface to do it
Which frankly, is much clearer and gives you a far better view of what's going on!
So let's go back to our repository on GitHub
You may see a message about protecting the main branch
We may come back to this later, so no need to worry about this for now!
If we select the dropdown where it says “main”, it gives us a list of branches
We can see all branches by selecting that option at the bottom
And now, we can see we have our new branch that has appeared
Which is separate from our main branch
If we select that, we can see the state of the repository within this branch
Including the new latest commits here - on climate-analysis.py

## Create a Pull Request

Let's create the pull request now, by selecting “Compare & pull request”
We could also do this from “Pull requests” if we wanted, but let's take the offered option
Now it shows us an interface for creating the PR
Importantly, at the top, it shows us which branch will be merged with which branch
With the source branch on the right, and the destination branch on the left
This should be our new branch for compare, and main for base
Also, it tells us we are “able to merge” - and in this case, there are no conflicts to worry about, which is really handy
You may rightly ask “what do I do if there are conflicts?” - a good question, and we'll look at this later!
Below this, it also shows us the commits associated with this branch
as well as the sum of changes to the files by these commits
We'll rename the PR to reference issue 2 directly
Changing it to “Fixes #2 - missing docstrings”
We could add more contextual information if needed
And also assign reviewers, as we did in the previous session on code review
But for simplicity, we'll leave those for now
But we will assign the PR to ourselves, since it's a good idea to assign responsibility where we can
…and let's create the pull request
QUESTION: who's created the pull request? Yes/No

Now we get another screen describing the new PR itself
If we'd assigned any reviewers, we now wait for their reviews of this pull request - and we could assume we've just done that, and the PR is good
Again, this is a major strength of using PRs, and I thoroughly recommend it
By PRs, and having reviews of PRs, it's not just a number of people making changes in isolation
In collaborations around software, it's so important to increase the flow of information between people making changes, in case there are any new potential issues that are introduced
And PRs give us that discipline - an opportunity really - to make sure that the changes we are making are well considered
And this becomes part of the overall cycle of development
We write code, we have it reviewed, it gets merged
But also, we help with reviewing other code too
Again, it tells us we can merge this branch automatically, and also the list of commits involved
Interestingly, even though we have created this PR to do a merge, we could continue developing our code on this new branch indefinitely if we wanted
We could make and push new commits to this branch, which would show up here
And we could merge at a future date
This may be particularly useful if we need to have a longer discussion about the PR as it is developing
And the discussion could be captured in the comments for the PR
And when ready, we could then merge the PR
Which raises the question, of how long should PRs be open, or branches for that matter
To some degree, this depends on the nature of the changes being made
But branches in Git are designed, and should be wherever possible, short-lived
The longer a branch is open, the more potential changes could be made to the main branch
Then when it comes time to merge the branch, we may get a lot of conflicts we need to manage
So generally, it's a good idea to keep your branches open for a day or two, a few days maximum, before creating a PR and doing a merge if you can
Note that we can also see this PR, as well as any others, by selecting the “Pull request” tab


::::::::::::::::::::::::::::::::::::: keypoints 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

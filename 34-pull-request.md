---
title: "3.4 Creating a Pull Request"
teaching: 10
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- How can I organise a set of changes together so they can be merged later?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Describe what is meant by a pull request
- Describe the benefits of using pull requests
- Create a pull request using GitHub to group together and propose a set of changes to be merged to another branch

::::::::::::::::::::::::::::::::::::::::::::::::

## How to Merge our Changes with `main`?

We've essentially fixed the docstring issue now,
so next we need to somehow merge these changes on our feature branch with the main branch.

:::::::::::::::::::::::::::::::::::::::::  callout

## Test Code Before you Push it!

Now before we this, ordinarily we should test the changes and ensure the code is working properly.
To save time, we haven't done that here, but that's definitely something worth noting:

- Before pushing any changes, always manually test your code first.
- If you have any unit tests, run those too to check that your changes haven't broken anything.
- Particularly if this was a change implementing a new feature, consider writing a new unit test to test that feature.

::::::::::::::::::::::::::::::::::::::::::::::::::

And we'll do that now by using what's known as a *pull request*.
A pull request is a way to propose changes on a particular Git branch, and request they be merged with another branch.
They're really useful as a tool in teams,
since they provide a way to check the changes before doing a merge.
They allow you to see the changes to files across all the commits in the branch,
and look at how these commits will change the codebase.
And you can assign a number of reviewers to review the pull request,
and submit a review with their thoughts on whether to accept the pull request,
or make changes, and so on. Really useful!
So we could create the pull request on the command line,
but we'll use the GitHub interface to do it.
Which frankly, is much clearer and gives you a far better view of what's going on.

So let's go back to our repository on GitHub.
You may see a message displayed at the top about protecting the main branch.
We may come back to this later, so no need to worry about this for now.

If we select the dropdown where it says "main", it gives us a list of branches.
We can see all branches by selecting that option at the bottom.
Now, we can see we have our new branch that has appeared,
which is separate from our main branch.
If we select that, we can see the state of the repository within this branch,
including the new latest commits here - on our `climate-analysis.py` file.

## Create a Pull Request

Let's create the pull request now,
by selecting `Compare & pull request`.
We could also do this from the `Pull requests` tab from the top menu as well,
then selecting `New pull request`.

Now it shows us an interface for creating the pull request:
- Importantly, at the top, it shows us which branch will be merged with which branch,
with the source (or comparison) branch on the right,
and the destination branch on the left.
This should be our new branch for `compare:`, and `main` for `base:`.
- It tells us we are "able to merge" - and in this case, there are no conflicts to worry about, which is really useful to know.
So what if there are conflicts? This is something we'll look at later.
- Below this, it also shows us the commits associated with this branch
as well as the sum of changes to the files by these commits.

In the title, we'll rename the PR to reference issue 2 directly,
changing it to `Fixes #2 - missing docstrings`.
We could add more contextual information in the description if needed.
We could also assign others as reviewers,
as we did in the previous session on code review.
But for simplicity, we'll leave those for now.
But we will assign the pull request (or PR for short) to ourselves,
since it's a good idea to assign responsibility where we can.
So let's create the pull request by selecting the button.

QUESTION: who's created the pull request? Yes/No

Now we get another screen describing the new PR itself.
If we'd assigned any reviewers, we now wait for their reviews of this pull request.
At this point, we could assume we've just done that, and the PR has been approved and is ready to merge.

By contributing work in PRs, and having reviews of PRs,
it's not just a number of people making changes in isolation.
In collaborations around software,
it's very important to increase the flow of information between people making changes
in case there are any new potential issues that are introduced.
And PRs give us that discipline - an opportunity really - to make sure that the changes we are making are well considered.
This then becomes part of the overall cycle of development:
we write code, we have it reviewed, it gets merged.
But also, we help with reviewing other code too.

Coming back to the interface,
it now tells us we can merge this branch automatically,
and also the list of commits involved.
Interestingly, even though we have created this PR to do a merge, we could continue developing our code on this new branch indefinitely if we wanted.
We could make and push new commits to this branch, which would show up here,
and we then merge at a future date.
This may be particularly useful if we need to have a longer discussion about the PR as it is developing.
The discussion would be captured in the comments for the PR,
and when ready, we then merge the PR.

:::::::::::::::::::::::::::::::::::::::::  callout

## How Long should PRs be Open?

Which raises the question, of how long should PRs be open, or branches for that matter?
To some degree, this depends on the nature of the changes being made
But branches in Git are designed, and should be wherever possible, short-lived and deleted when no longer required.
The longer a branch is open, the more potential changes could be made to the main branch.
Then when it comes time to merge the branch, we may get a lot of conflicts we need to manage.
So generally, it's a good idea to keep your branches open for a day or two, a few days maximum, before creating a PR and doing a merge if you can.
Note that we can also see this PR,
as well as any others, by selecting the `Pull request` tab.

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: keypoints 

- Always test code before you push changes to a remote repository
- Pull requests give us the opportunity to properly consider and review logical sets of changes to our codebase before they are merged
- GitHub gives us powerful tools to create and manage pull requests
- Where possible, keep Git branches short lived and merge them as soon as is convenient, to avoid increasing disparities between the feature branch and main branch

::::::::::::::::::::::::::::::::::::::::::::::::

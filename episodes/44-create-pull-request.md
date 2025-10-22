---
title: "4.4 Submiting a Pull Request"
teaching: 10
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- How do you create a pull request using GitHub?
- How long should we keep a pull request open?
- How do we request a review of a pull request?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Create a pull request based on the changes we submitted to a new branch
- Describe the reasons to keep a pull request short-lived
- Request a review of your pull request from another participant

::::::::::::::::::::::::::::::::::::::::::::::::

## Creating a Pull Request

Let's create a pull request now from this new branch.

1. First, go the `Pull requests` tab at the top of the group repository main page, and select `New pull request`
1. In the `Compare changes` page that comes up:
   - Select `compare:` and select your new branch, e.g. `readme-broken-link-fix`. You should now see a summary of the changes between the new branch and the main branch, i.e. a single commit and the fix you made earlier
   - Select `Create pull request`
1. In the `Open a pull request` page that appears:
   - Add details for pull request before creating it, including a reviewer, label, title, and description
   - Enter a fitting title, brief description, and label
   - Select `Create pull request`

You’ll then see a summary of the pull request, including a summary of any conflicts with the base (`main`) branch, of which there should be none.
There’s also an option to merge the pull request - but don’t do this yet, since you’ll need to wait for your pull request to be reviewed!

QUESTION: who's been able to create a new pull request? Yes/No

Interestingly, even though we have created this PR to do a merge, we could continue developing our code on this new branch indefinitely if we wanted.
We could make and push new commits to this branch, which would show up here, and we then merge at a future date.
This may be particularly useful if we need to have a longer discussion about the PR as it is developing.
The discussion would be captured in the comments for the PR, and when ready, we then merge the PR.

:::::::::::::::::::::::::::::::::::::::::  callout

## How Long should PRs be Open?

Which raises the question, of how long should PRs be open, or branches for that matter?
To some degree, this depends on the nature of the changes being made.
But branches in Git are designed, and should be wherever possible, short-lived and deleted when no longer required.
The longer a branch is open, the more potential changes could be made to the main branch.
Then when it comes time to merge the branch, we may get a lot of conflicts we need to manage.
So generally, it's a good idea to keep your branches open for a day or two, a few days maximum, before creating a PR and doing a merge if you can.
Note that we can also see this PR,
as well as any others, by selecting the `Pull request` tab.

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: challenge

## Obtain a GitHub Account ID from another Participant

For the next stage, you'll be reviewing a pull request. Either:

- If you are attending a workshop with other learners,
the instructor will enable you to obtain a GitHub account ID from another learner so you can request a review of your pull request from them, and you'll also be requested as a reviewer on someone else's pull request.
- If you are going through this material on your own,
you can review the pull request you made on your own repository instead.

:::::::::::::::::::::::::::::::::::::

To assign your reviewer to your PR:

1. Go back to your repository's main page
1. Select `Pull requests`, and then the PR you created
1. Select `Reviewers` and add the GitHub account for the reviewer

You should see an orange filled circle next to their name, indicating that you have requested their review and they have yet to submit it.
We could add as many reviewers as we want, particularly if this is a complex change that affects many aspects of the codebase.

QUESTION: who has managed to add the other account and request a review from them? Yes/No

::::::::::::::::::::::::::::::::::::: keypoints 

- Try to keep pull requests short-lived to avoid them becoming outdated with other branches such as `main`
- We can request reviewers for a pull request by adding their GitHub account to a list of `Reviewers`

::::::::::::::::::::::::::::::::::::::::::::::::

---
title: "4.5 Reviewing a Pull Request"
teaching: 10
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- How do I submit a review of a pull request?
- On what information about a pull request do I base my review?
- What are the levels of approval for a pull request review?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Describe how GitHub presents the information related to a pull request
- Add review comments to a pull request
- Submit a review of a pull request

::::::::::::::::::::::::::::::::::::::::::::::::

Let's now adopt a new role - that of the reviewer of someone else's pull request (or PR for short).

## Write a Review of the PR

To see a list of PR review requests for you, go to https://github.com/pulls/review-requested.
You should see a review request from another participant, so select this from the list.

This will present an overview of the pull request (PR), including on separate tabs:

- `Conversation` - an overview of the PR, including comments and other activities associated with the PR,
as well as a summary at the end, indicating the overall status in terms of reviews requested, and whether there are any merge conflicts with the base branch (`main` in this case)
- `Commits` - a list of all commits on the feature branch that have yet to be merged into the base branch
- `Checks` - whether there are any automated checks implemented in GitHub Actions and their status
- `Files changed` - the list of files and their line-by-line changes for this PR

If you select the `Files changed` tab,
or if you select `Add your review` from the `Conversation` page which takes you to the same tab,
you can then begin your review.

By default, the presented view indicates a "unified" view.
This shows deletions highlighted in red,
and additions highlighted in green.

Another view is the "split" view of these changes,
which is selectable by clicking on the cog-like icon and selecting `Split`.
This provides a side-by-side alternative,
with the older version on the left, and the newer version on the right.
In this case, you should see a number of green highlighted lines on the right side of this view,
indicating the added lines.

When providing a review, we have the option of adding comments or suggestions inline to the proposed changes.
By hovering over a line and selecting the `+` symbol at the start of the line,
we're able to add a comment on that line,
for example if we spotted a spelling or grammatical mistake,
or in the case of code, a programmatic problem or other issue.

We have the option of adding comments or suggestions inline to the proposed changes, if we want.
For example, perhaps we know there is a Zenodo record for the code that this article points to, which we think should be added.

1. Hovering over the line containing the fix and select the `+` symbol at the start of the line
1. Add a comment, something like `We should also link to the Zenodo record for the code, at https://zenodo.org/record/250494#.Y2UUN-zP1R4`
1. Then select `Start a review`

Can add as many comments as we want at this review stage, to any line.
If this were a larger pull request, we would review all the other changes, and add comments as needed.

Finally, as a reviewer of this pull request, we can complete our review:

1. Select `Finish our review`
1. Add a brief comment, e.g. `Overall, the changes look good, although we should consider adding the Zenodo repository link`

And then we can select one of the following options:

- `Comment` - where you're just leaving a comment and aren't requesting any changes
- `Approve` - no comments are changes are necessary
- `Request changes` - feedback must be addressed before it can be merged

For simplicity, let's just go with the first option for this exercise.

Finally, select `Submit review`, and our role as reviewer on the pull request is complete!
The originator of the PR can then take our review into account, and make changes in response to the review.

QUESTION: Who's submitted a very brief code review? Yes/No

::::::::::::::::::::::::::::::::::::: callout

## The `Approve` and `Request changes` options are unavailable!

If you're following through the material on your own,
and have reviewed your own pull request,
you'll notice that the `Approve` and `Request changes` options are not available.
This is because GitHub does not allow users to approve their own pull requests.
The reason for this is that it goes against the reason behind pull requests - to have others review your changes, and in a usual team environment, you'd ask a colleague (or colleagues) to do a review.

GitHub still allows you to submit a review to your PRs with comments however,
so for the purposes of this training feel free to select the `Comment` option instead.

:::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: keypoints 

- The key reason to use pull requests is to ensure that code changes are reviewed by other team members before they are merged
- We can elect to approve changes, request changes prior to merging a pull request, or block a merge until requested changes are satisfied
- GitHub doesn't allow the creator of a pull request to approve it

::::::::::::::::::::::::::::::::::::::::::::::::

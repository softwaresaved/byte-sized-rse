---
title: "4.5 Reviewing a Pull Request"
teaching: 10
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

Let's now adopt a new role - that of the reviewer of a pull request (or PR for short).
Let's assume that a colleague has created a pull request of his own, for the purposes of this exercise, it's on their own repository
But it could be a shared repository we are both working on
In a collaborative environment, this is mostly likely going to be the case
So let's take a look at it and review it

## Write a Review of the PR

So we open the repo URL link in a browser, and go to “Pull requests" on the repo main page
Then select the pull request
To review the request's changes, we can go to 'Files changed' - one of the tabs
Which perhaps unsurprisingly, shows us the changes in each file, in this case just one file, and one change
The view on the left (in red) is the old version, and the view on the right (in green), is the revised version of the line change

We have the option of adding comments or suggestions inline to the proposed changes, if we want
For example, perhaps we know there is a Zenodo record for the code that this article points to, which we think should be added
By hovering over a line and selecting the '+' symbol at the start of the line
And adding a comment
So select the changed line, and add something like
We should also link to the Zenodo record for the code that this article links to, at https://zenodo.org/record/250494#.Y2UUN-zP1R4
Then selecting 'Start a review'
Can add as many comments as we want
If this were a larger pull request, we would review the other changes, and add comments as needed

So let's assume we've done that

Finally, as a reviewer of this pull request, we “Finish our review"
We can add a comment, maybe with some high-level observations or suggestions
Overall, the changes look good, although we should consider adding the Zenodo repository link.

And then we can select whether (three options here)
Comment - we can just leave a comment to consider
Approve - the pull request is approved as is
Request changes - there are some aspects that must be addressed before it can be merged
For simplicity, let's just go with the first option for this exercise

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

So then submit the review, and our role as reviewer on the pull request is complete
The other participant can then take our review into account, when deciding whether to merge that pull request

QUESTION: Who's submitted a very brief code review? Yes/No

::::::::::::::::::::::::::::::::::::: keypoints 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

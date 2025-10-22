---
title: "4.3 Fixing a Repository Issue"
teaching: 10
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- How do we approach grouping commits together for a pull request?
- Can we use GitHub to directly make changes to files?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Create an issue on GitHub that describes a problem with the example codebase
- Use the GitHub file editor to make a direct change to a file in our example repository
- Submit the fix for the issue on a new repository branch

::::::::::::::::::::::::::::::::::::::::::::::::

## Adding an Issue to the Repository

Let's first add an issue to the repository, which will represent something we need to work on.
For the sake of this exercise, it doesn't really matter what the issue is, but perhaps we've spotted a problem with our codebase during development and we need to note this problem needs to be fixed.

If we look at the README for the repo we can see there's a broken link near the top, so let's register that as an issue.

1. Go to your repository's main page in GitHub in a browser, and select `Issues` at the top.
You'll notice a new page with no issues listed at present.
1. Select `New issue`.
1. On the issue creation page, add something like the following:
   - In the title add: Broken link to article
   - In the description add: The README link to the SSI website article is broken, resulting in a page not found error
1. Assign ourselves to the issue by selecting `Assign yourself`.
1. Assign the `Documentation` label to the issue.
1. Select `Create` to create the issue.

QUESTION: who's been able to create a new issue on the repository? Yes/No

## Fixing the Issue

Now let's assume at some future date we decide to fix the issue.
Now in most cases, we'd probably do this by having the repository cloned on our machine, and then we'd make the change, and submit it that way.
But in the interests of time and simplicity, we'll just use GitHub's direct file editing feature.

1. Go to the repository's main page
1. Navigate to the `README` file in the file navigator
1. Select the edit icon shaped like a pen/pencil on the top right
1. In the file editor, fix the broken link by removing the bit that says "typo/"

So we now need to commit the change.
It's good practice when committing a change is to refer to the issue number in the commit message,
which will give us traceability for changes back to the originating issue when looking at the commits in a repository.

1. Select `Commit changes...` in the top right.
1. This is the first issue on the repository, so let's refer to that with `#1 - Fix broken article link` as the commit message
1. We could optionally put more info about the fix in the description if we wanted

Now importantly, we want to submit this change as a pull request on a new branch,
since this will allow others to review that pull request.

1. Select the second option `Create a new branch for this commit and start a pull request`
1. Enter a meaningful name for this new branch, e.g. `readme-broken-link-fix`
1. Select `Propose changes`

This change is now submitted to this new branch.
If you go to the main repository page and select `branches`, you'll see our new branch in the list.

QUESTION: who's managed to commit their fix to a new branch? Yes/No

::::::::::::::::::::::::::::::::::::: keypoints 

- We use branches to contain the change commits we want to submit within a pull request

::::::::::::::::::::::::::::::::::::::::::::::::

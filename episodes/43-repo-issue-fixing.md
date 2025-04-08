---
title: "4.3 Fixing a Repository Issue"
teaching: 10
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

## Adding an Issue to the Repository

Next thing to do is to add an issue to the repository
Which will represent something we need to work on
For the sake of this exercise, it doesn't really matter what the issue is
But perhaps we've spotted a problem with our codebase during development, and we need to note this problem needs to be fixed

For example, if we look at the README for the repo, we can see there's a broken link
Clearly a problem, so let's register that as an issue
Select “Issues”, then “New issue”
Title: Broken link to article
Description: The README link to the SSI website article is broken, resulting in a page not found error
Select “Submit new issue”
Have opportunity to assign someone to the issue - let's say me
And also assign what type of issue it is
It's a problem with the README, so that's probably documentation, so let's set it as that

QUESTION: who's been able to create a new issue on the repository? Yes/No

## Fixing the Issue

Now the next thing, is perhaps a bit later on, we decide to fix the issue
So we navigate to the README (go to repository main page)
And here, for the sake of the exercise, we'll just use GitHub's edit mechanism to edit the file directly
Alternatively, and in most cases, we'd probably do this by having the repository cloned on our machine, and then we'd make the change, and submit it that way
But in the interests of time and simplicity, we'll just use GitHub's edit function
So select the edit icon
And edit the README to fix the link (remove the bit that says “typo/“)

So we now need to commit the change, so we now select “Commit changes” in the top right
Good practice when committing a change is to refer to the issue number in the commit message
This gives us traceability for changes back to the originating issue
We had our issue number 1, so let's refer to that
#1 - Fix broken article link
We could optionally put more info about the fix in the description if we wanted

Now importantly, we want to submit this change as a pull request on a new branch
This will allow others to review that pull request
Selecting the second option here allows us to create a new branch for these changes
And we can give this new branch an identifiable name
readme-broken-link-fix

Once we select propose changes, this change is submitted and our new branch, with that fix, is created
And scrolling down, we can see our change highlighted

QUESTION: who's managed to commit their fix to a new branch? Yes/No

::::::::::::::::::::::::::::::::::::: keypoints 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

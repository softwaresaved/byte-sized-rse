---
title: "3.2 Some Example Code"
teaching: 10
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

## Creating a Copy of the Example Code Repository

FIXME: copy git-example repo into softwaresaved

So the first thing we need to do is create a new GitHub repository from a template repository
So first go to https://github.com/UNIVERSE-HPC/git-example [copy and paste]
Select ‘Use this template’ -> Create a new repository
Set owner and repo name (e.g. git-example), ensure it’s set to public, Create


## Examining the Code

Let’s first take a look at the example code on GitHub
You’ll find the code in the root of the repository you’ve just cloned
cd git_example
Look at climate_analysis.py
It’s designed to perform some temperature conversions from fahrenheit to either celsius or kelvin
The code is for illustrative purposes
If we actually wanted to do temperature conversions, there are at least three existing Python packages we would ideally use instead
And with this code, there are a number of rather large issues (which is deliberate!)
The code is a little untidy - inconsistent spacing and commenting, hardcoded file paths, not  using a library to handle the CSV data files, and others, such as…
function names are capitalised - perhaps we need to change these to be lower case, and use underscores between words - a naming style also known as snake case
also, we’re missing some comments (known as docstrings) describing the function and the script (or module) itself
for those that haven’t encountered docstrings yet, they are special comments described in a particular format that describe what the function or module is supposed to do
you can see an example here - e.g. what it does, input arguments, what it returns
there’s also an incorrect function name FahrToCels - which should be FahrToCelsius - this will cause it to fail if I run it
one thing to note on this repository is that we have a single main branch
used to be called a master branch, which you may see in older repositories
you’ll notice some commits on the main branch already - one way to look at this is as a single “stream” of development
we’ve made changes to this codebase one after the other on this main branch
however, it might be that we may want to add a new software feature, or fix a bug in our code
and this may take, maybe, more than a few commits to complete and make it work, perhaps over a matter of hours or days
of course, as we make changes to make this feature work, the commits along the way may well break the “working” nature of our repository
and after that, users getting hold of our software by cloning the repo, also get a version of the software that then isn’t working
this is also true for developers as well - it’s hard to develop, say, a new feature for a piece of software, if you don’t start with software that is working
the problem would also become compounded if other developers came on board, perhaps as part of a new project that will develop the software
what would be nice, would be to have our cake and eat it, so to speak
where we can change our code using version control to track our changes,
but not interfere with our working code on the main branch
Fortunately, repository branches can give us just that

## Create Example Issues

Before we do that, let’s create a few new issues on our repository, to represent some work we’re going to do in this session
One thing that might be good to do is to tidy up our code
So let’s add issues to fix that script function naming bug, changing our function names to use snake case, and add the missing docstrings
So go to your new repository in GitHub in a browser, and select “Issues”
Then select “New issue”, and add something like the following
In the title add: Functions should use snake case naming style
In summary I’ll add the following, but don’t feel you need to!
Naming of functions currently is using capitalisation, and needs to follow snake case naming instead
For the purposes of this activity, let’s also assign ourselves, then select “Submit the issue”
Repeat for another two issues - although to save time, let’s only focus on adding the issue title this time
The googledoc has the list of titles to use for each issue
“Add missing docstrings to function and module”
“Script fails with undefined function name error”
We’ll refer back to these later!
QUESTION: who’s created the three issues? Yes/No


::::::::::::::::::::::::::::::::::::: keypoints 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

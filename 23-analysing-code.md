---
title: "2.3 Analysing Code using a Linter"
teaching: 10
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

## Installing a Code Linter

The first thing we need to do is Install pylint
Now fortunately, pylint can be installed as a Python package
QUESTION: who has installed a Python package before, using the program pip? Yes/No
QUESTION: who has created and used a Python virtual environment before? Yes/No
Ok, so we’re going to create what’s known as a virtual environment
This is a genuinely very useful technique - I cannot recommend this strongly enough!
There isn’t a developer I know that doesn’t use virtual environments to install their packages whenever they can
And to be honest, this could be a topic all on its own
The idea is that
Instead of installing Python packages at the level of our machine’s Python installation, which we could do
We’re going to install them within their own container, which is separate to the machine’s Python installation
And then we’ll run our Python code only using packages within that virtual environment
The benefit of this is that it creates a clear separation between the packages we use for this project, and the packages we use for another
The other benefit is that we don’t end up with a machine’s Python installation with a clutter of a thousand different packages
Can become very difficult to tell which packages are used for which project
If someone else needs to run your code for example, by using a virtual environment, you can be sure what your code actually needs as dependencies

## Setting up a Development Environment

So let’s create a Python virtual environment now, and activate it
So, make sure you’re in the root directory of the repository, then type
python -m venv venv
Here, we’re using the built-on Python venv module - short for virtual environment - to create a virtual environment directory called venv
We could have called the directory anything, but naming it venv is a common convention
We create the venv within the repository root directory, which is also an established convention
This makes sure the venv is closely associated with this project, and not easily confused with another
Once created, we can activate the venv so it’s the one in use
We do that by:
(if on Linux or Mac) source venv/bin/activate
(if on Windows) source venv/Scripts/activate
QUESTION: who has successfully created and activated their virtual environment? Yes/No?
Ok, so what’s in this virtual environment?
we can do: pip list
We can see this is essentially empty, aside from some default packages that are always installed
So, the next thing we can do is install any packages needed for this codebase
It turns out, there isn’t any needed for the code itself
But - we wish to use pylint, and that’s a python package
So we can install pylint into our virtual environment using
pip install pylint
You’ll notice the prompt changes to reflect that the virtual environment is active - a handy reminder
And with that, we’re ready to go
Important thing with virtual environments
Don’t add the venv directory to a GitHub repository

## Analysing our Code using a Linter

Now the magic can happen - let’s run pylint
If you run it without any arguments, we can see it’s got a daunting array of options
But fortunately the basic use is very simple
Let’s point it at our code and see what it thinks
pylint climate_analysis.py
We run this, and it gives us a report
essentially, a list of issues, and a score
for each issue, it tells us the filename, the line number and text column the problem occurred, an issue identifier (what type of issue it is), and some text describing this type of error (as well as a shortened form of the error type)
You’ll notice there’s also a score at the bottom, out of 10
Essentially, for every infraction, it deducts from the ideal score of 10 
It is perfectly possible to get a negative score! It just keeps deducting from 10!
But we can see here that our score appears very low - 0.59/10
If we were to resolve each of these issues in turn, we should get a perfect score
We can also ask for more information on an error type
for example, we can see at line 9, near column 35, there is a trailing whitespace
pylint —help-msg C0303
Which is helpful if we need clarification
if we edit the file, e.g. nano climate-analysis.py
and go to line 9, column 35,
(we can use nano’s cursor locator function to help us find column 35),
we can see that there is an unnecessary space
I’ve made this visible in nano so you can see it (although usually you wouldn’t)
QUESTION: who’s managed to run pylint on the example code? Yes/No
Let’s fix this issue now. Let’s remove the space and re-run pylint on it
Delete space, save
pylint climate_analysis.py
And we see that the error has disappeared and our score has gone up!
Note that it also gives us a comparison against our last score
Warning - it can get quite addictive to keep increasing your score
which might well be the point!
So looking at the issue types, what do the C, W, R symbols mean?
Show pylint —long-help
At the end, we can see a breakdown of what they mean
I is for informational messages
C for a programming standards violation - it’s not conforming to the normally accepted conventions of writing good code, things like variable or function naming
R for a need to refactor, due to a “bad code smell”
W for warning - something that
E for error - so pylint think’s it’s spotted a bug (useful, but I wouldn’t depend on this!)
and F for a fatal pylint error
So if we run it again on our code
pylint climate_analysis.py
We can see that most of our issues are do to with conventions


::::::::::::::::::::::::::::::::::::: keypoints 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

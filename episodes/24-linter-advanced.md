---
title: "2.4 Advanced Linting Features"
teaching: 10
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

## More Verbose Reporting

We can also obtain a more verbose report, which gives us a lot more detail
pylint —reports y file
QUESTION: for those doing activity, who’s managed to run this command? YES/NO
It gives  you some overall statistics, plus comparisons with the last time you ran it
such as how many modules, classes, methods and functions were looked at
some raw metrics - we’ll come back to that
the extent of code duplication (none, which is good)
the number of messages by category (again, we can see that it’s mainly convention issues)
and a sorted count of the messages we received
now coming back to the raw metrics
We can see that  is breaks down our program into how many lines are
code lines, 
python docstrings
standalone comments
and empty lines
this is very useful, since it gives us an idea of how well commented our code is
in this case - not very well commented at all!
what’s a good % of comments to aim for? well it depends
for normal comments, the usually accepted wisdom is to add them to explain why you are doing something, or perhaps to explain how necessarily complex code works

## Increasing our Pylint Score - Adding a Docstring

QUESTION: Who’s familiar with Python docstrings? Yes/No
for those that don’t know, docstrings are a special kind of comment for a function, that explain what the function does, the parameters it expects, and what is returned
you can also write docstrings for classes, methods, and modules
but you should usually aim to add docstring comments to your code wherever you can, particularly for critical or complex functions
let’s add one to our code now, to the fahr_to_celsius function

    """Convert fahrenheit to Celsius.

    :param fahr: temperature in Fahrenheit
    :returns: temperature in Celsius
    """

Re-run pylint - can see we have one less docstring error, and a slightly higher score
If you’d like to know more about docstrings and commenting, we’ve included a link to a RealPython tutorial on comments and docstrings, and the different ways you can format them. that’s really good

## Configuring Pylint Rules

Specifying a pylint rcfile - e.g. to ignore/specify rules
Write a module docstring that exceeds 100 characters
Show pylint complaining about long line length
pylint --generate-rcfile
Specify long line length
Edit .pylintrc file, add C0301 to disable=
Re-run pylint
When to use? Agree as a team

## Summary

What doesn’t pylint - and other code analysis tools - give us?
What are their limitations?
They don’t tell us that the code works - this first and foremost
And they don’t tell us if the results our code produces are actually correct
So we still need to test our code
They don’t give us any Idea of whether it’s a good implementation
And that the technical choices are good ones
For example, this code does its own temperature conversions
It turns out there’s a number of well-maintained Python packages that do this, e.g. pytemperature
so we should be using a tried and tested package instead of reinventing the wheel
They also don’t tell us if the implementation is actually fit for purpose
Ok, so the code is a good implementation, and it works as expected
But is it actually solving the intended problem?
They also don’t tell us anything about the data the program may use
Which may have its own problems
So we have to be a bit careful
These are all valid, high-level questions to ask while you’re writing code
I’ve added them to the google doc
As a team, and also individually
In the fog of development, it can be surprisingly easy to lose track of what’s actually being implemented

A good idea is to revisit these questions regularly, to be sure you can answer them!
A high score or zero warnings may give us false confidence
Just because we have reached a 10.00 score, doesn’t mean the code is actually GOOD
Just that it’s likely well formatted and hopefully easier to read and understand
But nevertheless, it’s a low effort way to check our code
And such tools are still very useful, as far as they go

::::::::::::::::::::::::::::::::::::: keypoints 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

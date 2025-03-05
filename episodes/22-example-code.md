---
title: "2.2 Some Example Code"
teaching: 10
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

## Obtaining Some Example Code

FIXME: copy code-style-example into softwaresaved org

Open a shell
On own machine: open terminal with a bash shell
Using the shell, we’re going to use Git to clone our example GitHub code repository
The URL is bit long - see the session notes for a copy and pastable link - it’s the second link at the top
git clone https://github.com/UNIVERSE-HPC/code-style-example


## Examining the Code

Next, let’s take a look at the code, which is in the root directory of the repository
So the example code here is designed to process temperature data from a separate data file (which is also in the repository in the data directory)
The idea is that is reads in fahrenheit data from a data file, and prints out fahrenheit temperatures in both celsius and kelvin
The data file is a CSV file (see sc_climate_data_10.csv) which is held in the data directory
It contains a number of lines, each containing a number of values, each separated by a comma
There’s also a comment line at the top, to tell us what each column represents
Now let’s take a look at the Python code
Use any editor you like to open the file, I’ll use a command line one called nano
If you’re on a Mac or Linux, you should be able to use this too
cd code-style-example
nano climate-analysis.py
The code opens the data file, defines some functions to do some conversions 
I should point out that the code is deliberately written to be bad
In so many ways we’ll look into
Developers sometimes talk about “code smells”
Code smells are cursory indications from looking at the source code that a piece of code may have some deeper issues
And looking at this code, it smells pretty terrible
We can see that there is inconsistent spacing, bunching in some places, very spread out in others, for example
This doesn’t engender a great deal of confidence that the code will work as we expect
It raises the question that if the style of the code appears rushed, what else has been rushed?
It’s design? Testing?
Something to bear in mind when writing code!

QUESTION: who has seen or used code that looks like this? Yes/No?
QUESTION: who has written code like this? Yes/No

No one writes great code that’s readable, well formatted, and well designed all the time
Sometimes you often need to explore ideas with code to understand how the code should be designed
May involve trying things out first
But … the key is that once you understand how to do something,
it’s a good idea to make sure it’s readable and understandable by others
And this includes a future version of yourself, 6 months down the line
So it’s really helpful to have good clean code so your colleagues or development team can understand it
So it can be extended and otherwise modified in the future
But it’s also a really good idea if you write readable code for just yourself.
You never know. The code may be useful elsewhere!
An all too familiar example is
You stop developing a piece of code, and put it to one side. Maybe it’s not needed any more, perhaps a project has finished. You forget about it
BUT… suddenly, there’s a need to use the code again
Maybe all of it in another project, or maybe to just part of it
You come back to your code, and it’s a mess you can’t understand
By spending a little time now to write good code while you understand it,
you can save yourself (and possibly others) a lot of time later

## Running the Example Code

Now despite the issues with the code, does it work? Let’s find out 
So in the shell
In the root directory of the repository, we can type
python climate_analysis.py
And we can see that the code does indeed appear to work, with celsius and kelvin values being printed to the terminal
But how can we improve its code formatting?
Let’s use Pylint, a static Python code analysis tool to help us

::::::::::::::::::::::::::::::::::::: keypoints 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

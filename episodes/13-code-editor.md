---
title: "1.3 Using the Code Editor"
teaching: 10
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

Now we've acquainted ourselves with running VSCode, let's take a look at our example code.
Select the `climate_analysis.py` file in the explorer window, which will bring up the contents of the file in the code editor.

::::::::::::::::::::::::::::::::::::::::: callout

## The File Explorer has Disappeared!

You may find, perhaps on reopening VSCode, that the explorer is no longer visible.
In this case, you can select `Explorer` from the sidebar to bring it back up again,
and if you don't currently have a workspace loaded,
you can select `Open Folder` to select the code folder.

:::::::::::::::::::::::::::::::::::::::::

Note that as an example, it's deliberately written to have flaws.
Things like the line spacing is inconsistent, there are no code comments, there's a variable that's not used, and you may spot other issues too.
But in essence, the code is designed to do the following:

1. Open a file in the CSV (comma separated value) format
1. Go through the file line by line, and:
   - If the line begins with a `#` symbol, ignore it.
   - Otherwise, extract the fourth column (which is in Fahrenheit), convert it to Celsius and Kelvin, and output those readings.

Let's take a look at some of what the code editor gives us.

## Syntax Highlighting

You'll notice that the Python syntax is being highlighted for us, which helps readability.

FIXME: add screenshot of code editor with syntax highlighting of code example

Here, it uses colour to distinguish the various parts of our program.
Functions are yellow, Python statements are purple, variables are light blue, and strings are this reddy-orange, and so on.
Which, perhaps unsurprisingly, is a feature known as Syntax Highlighting, and it's possible to edit the colour scheme to your liking for a particular language if you like, although we won't go into that now.

This is really handy to give you immediate feedback on what you are typing, and can help you to identify common syntax mistakes.
For example, deleting the closing parenthesis on `open` - the opening one goes red, with a squiggly line underneath, indicating an issue.

So this is great, and helps us understand what we are writing, and highlights some mistakes.

## Code Completion

Something that's also useful is VSCode's ability (via the Python and Pylance extensions) to help you write and format your code whilst you're typing.

For example, on a blank line somewhere, enter `for x in something:`.

On the next line, we can see that it's automatically indented it for us, knowing that we're inside a loop.

Another really helpful feature is something known as code completion (in VSCode, this is referred to as IntelliSense).
This is a great time saver, and a really useful feature of IDEs.
Essentially, as you type, it works out the context of what you are doing, and gives you hints.
For example, if we start typing a variable we've already defined, for example `climate_data`,
we can see that it's zeroing in as we type on the options for what we might be trying to type.
When we see `climate_data`, we can press `Tab` to complete it for us.
As another example, if we wanted to open another file, we might type `new_file = open(`.
In this case, it provides information on the file `open` function and its arguments, along with a description of what it does.
This is really handy to we don't have to take the time to look up all this information up on the web, for example.

## Code Linting

FIXME: intro to code linter (add to intro section)

In the introduction we covered code linting tools,
which go even further that syntax highlighting to analyse and identify deeper issues with our code.
The good news is that we can install a Python linter in VSCode to give us this code analysis functionality, by installing a linter extension.
As before, select the `Extensions` icon and this time search for `Pylint`, the one by Microsoft, and click `Install`.

::::::::::::::::::::::::::::::::::::::::: callout

## What is Pylint?

Pylint is a tool that can be run from the command line or via IDEs like VSCode,
which can help our code in many ways:

- Ensure consistent code style : whilst in-IDE context-sensitive highlighting such as that provided by VSCode, it helps us stay consistent with established code style standards such as ([PEP 8](https://peps.python.org/pep-0008/)) as we write code by highlighting infractions.
- Perform basic error detection: Pylint can look for certain Python type errors.
- Check variable naming conventions: Pylint often goes beyond PEP 8 to include other common conventions, such as naming variables outside of functions in upper case.
- Customisation: you can specify which errors and conventions you wish to check for, and those you wish to ignore.

:::::::::::::::::::::::::::::::::::::::::

Going back to our code you should now find lots of squiggly underlines of various colours.

::::::::::::::::::::::::::::::::::::::::: callout

## I don't see any Squiggly Underlines!!

If you happen to not see any squiggly underlines in the editor,
it could be the linter extension hasn't looked at your code yet.
In order to trigger the linter to show us further issues, try saving the file to trigger the linter to do this.
So go to `File` then `Save` on the menu bar, and you should now see a lot of squiggly underlines in the code.

:::::::::::::::::::::::::::::::::::::::::

These squiggly lines indicate an issue, and by hovering over them, we can see details of the issue.
For example, by hovering over the variables `shift` or `comment` - we can see that the variable names don't conform to what's known as an `UPPER_CASE` naming convention.
Simply, the linter has identified these variables as constants, and typically, these are in upper case. We should rename them, e.g. `SHIFT` and `COMMENT`.
But following this, we also need to update the reference to `comment` in the code so it's also upper case.
Now if we save the file selecting `File` then `Save`, we should see the linter rerun, and those highlighted issues disappear.

We can also see a comprehensive list of all the issues found, by opening a code `Problems` window.
In the menu, go to `View` then `Problems`, and then you'll see a complete list of issues which we can work on displayed in the pane at the bottom of the code editor.
We don't have to address them, of course, but by following them we bring our code style closer to a commonly accepted and consistent form of Python.

The linter also picks up things like functions that don't have docstrings which we'll take a look at.
For now, we can close the `Problems` pane.

## Need a Thing? Install an Extension!

As we just saw, included in the list of issues with our code was the lack of docstrings.
If we want to write good code, we should be adding code comments, including docstrings for our functions, methods, and modules.

Let's try and find an extension that might help us with writing docstrings.
Select the `Extensions` icon, and type `docstring` - you should see an `autoDocstring` extension by Nils Werner at the top.
Select that, and you'll see a page outlining what it is
Also note via the number of downloads that it's very widely used.

What's really handy is the little video that shows us what it does
This looks exactly like what we're after!
Select `Install`.

Now, when we go to a function for example `FahrToCelsius`, go to the next line, and add `"""`, we'll see a small pop-up to add a docstring. Press `Tab` to do so.

FIXME: add screenshot snippet showing docstring boilerplate being added

It does all the hard work of adding in the structure of a docstring for us, so we just need to fill in the blanks.
This is another good example of us realising it would be nice to have something to help us, searching for an extension, and trying it out.


::::::::::::::::::::::::::::::::::::::::: callout

## Using a Git Code Repository?

For those of you familiar with version control and who retrieved the example code via cloning its repository instead of downloading it, there are some other editor features that help with using version control.
One of these is that the filename changes colours in the file explorer depending on its status within version control:

- White - an existing file is unchanged from the copy in the local repository).
- Orange - the content of an existing file has changed, and the change(s) have not been tracked by version control yet.
- Green - a new file has been added and is unknown to version control.

So at a glance, you can get an idea of what's changed since your last commit.

:::::::::::::::::::::::::::::::::::::::::

## Summary

So in summary, many of these editing features are typical of IDEs in general,
and the great thing is that they are really helpful at saving us time.
Things like syntax highlighting, code completion, automatic code formatting and inserting docstrings, may not seem like much, but it all adds up!

::::::::::::::::::::::::::::::::::::: keypoints 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

---
title: "1.3 Using the Code Editor"
teaching: 10
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- How do I open a source code file in VSCode?
- What editing features will help me when writing code?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Use syntax highlighting to identify code styling issues and common coding mistakes
- Use code completion to automate finishing an incomplete code statement
- Use an extension to help with writing Python docstrings
- Describe how VSCode highlights the status of files managed under version control

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

Note that as an example, the code is deliberately written to have flaws.
Things like the line spacing is inconsistent, there are no code comments, there's a variable that's not used, and you may spot other issues too.
But in essence, the code is designed to do the following:

1. Open a file in the CSV (comma separated value) format
1. Go through the file line by line, and:
   - If the line begins with a `#` symbol, ignore it.
   - Otherwise, extract the fourth column (which contains temperature in Fahrenheit), convert it to Celsius and Kelvin, and output those readings.

Let's take a look at some of what the code editor gives us.

## Syntax Highlighting

You'll notice that the Python syntax is being highlighted for us, which helps readability.

Here, it uses colour to distinguish the various parts of our program.
Functions are yellow, Python statements are purple, variables are light blue, and strings are this reddy-orange, and so on.
Which, perhaps unsurprisingly, is a feature known as Syntax Highlighting, and it's possible to edit the colour scheme to your liking for a particular language if you like, although we won't go into that now.

This is really handy to give you immediate feedback on what you are typing, and can help you to identify common syntax mistakes.
For example, deleting the closing parenthesis on `open` - the opening one goes red, with a squiggly line underneath, indicating an issue.

So this is great, and helps us understand what we are writing, and highlights some mistakes.

## Code Completion

Something that's also useful is VSCode's ability (via the Python and Pylance extensions) to help you write and format your code whilst you're typing.

For example, on a blank line somewhere, enter `for x in something:`, and press the enter (or return) key.

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

## Need a Thing? Install an Extension!

A great feature of VSCode is the ease with which we can add new extensions when we need them.
For example, if we want to write good Python code, we should be adding code comments, including docstrings for our functions, methods, and modules.

Let's try and find an extension that might help us with writing docstrings.
Select the `Extensions` icon, and type `docstring` - you should see an `autoDocstring` extension by Nils Werner at the top.
Select that, and you'll see a page outlining what it is
Also note via the number of downloads that it's very widely used.

What's really handy is the little video that shows us what it does
This looks exactly like what we're after!
Select `Install`.

Now, when we go to a function for example `FahrToCelsius`, go to the next line, and add `"""`, we'll see a small pop-up to add a docstring. Press `Tab` to do so.

It does all the hard work of adding in the structure of a docstring for us, so we just need to fill in the blanks.
This is another good example of us realising it would be nice to have something to help us, searching for an extension, and trying it out.
For example, filling in the blanks for our generated docstring:

```python
    """Convert Fahrenheit to Celsius.

    Args:
        fahr (int): temperature in Fahrenheit

    Returns:
        int: temperature in Celsius
    """
```

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

- IDEs typically have a host of features that help save time when writing code
- Syntax highlighting gives you immediate feedback of potential issues as you write code
- Code completion helps to automatically finish incomplete code statements and names

::::::::::::::::::::::::::::::::::::::::::::::::

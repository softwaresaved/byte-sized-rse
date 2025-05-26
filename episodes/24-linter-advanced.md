---
title: "2.4 Advanced Linting Features"
teaching: 10
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- What can I do to increase the detail of Pylint reports?
- How can I reduce unwanted messages from Pylint?
- How can I use static code analysis tools within VSCode?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Use Pylint to produce a verbose report showing number of occurrences of encountered message types
- Fix an issue within our code to increase our Pylint score
- Specify message types to Pylint that we don't want reported
- Install a Pylint extension into VSCode

::::::::::::::::::::::::::::::::::::::::::::::::

## More Verbose Reporting

We can also obtain a more verbose report by adding `--reports y` to the command, which gives us a lot more detail:

```bash
pylint --reports y file
```

Here's a part of that output:

```output
...
Messages
--------

+---------------------------+------------+
|message id                 |occurrences |
+===========================+============+
|redefined-outer-name       |4           |
+---------------------------+------------+
|invalid-name               |4           |
+---------------------------+------------+
|missing-function-docstring |2           |
+---------------------------+------------+
|unused-import              |1           |
+---------------------------+------------+
|unspecified-encoding       |1           |
+---------------------------+------------+
|superfluous-parens         |1           |
+---------------------------+------------+
|missing-module-docstring   |1           |
+---------------------------+------------+
|consider-using-with        |1           |
+---------------------------+------------+
...
```

:::::::::::::::::: discussion

### Pylint Verbose Reporting - Checkin

For those doing activity, who's managed to run this command?

::::::::::::::::::

It gives you some overall statistics,
plus comparisons with the last time you ran it,
on aspects such as:

- How many modules, classes, methods and functions were looked at
- Raw metrics (which we'll look at in a minute)
- Extent of code duplication (none, which is good)
- Number of messages by category (again, we can see that it's mainly convention issues)
- A sorted count of the messages we received

Looking at raw metrics,
we can see that it breaks down our program into how many lines are
code lines, Python docstrings, standalone comments, and empty lines.
This is very useful, since it gives us an idea of how well commented our code is.
In this case - not very well commented at all!
For normal comments, the usually accepted wisdom is to add them to explain *why* you are doing something, or perhaps to explain how necessarily complex code works,
but not to explain the obvious,
since clearly written code should do that itself.

## Increasing our Pylint Score - Adding a Docstring

:::::::::::::::::: discussion

### Docstrings - Checkin

Who's familiar with Python docstrings?

::::::::::::::::::

Docstrings are a special kind of comment for a function,
that explain what the function does,
the parameters it expects, and what is returned.
You can also write docstrings for classes, methods, and modules,
but you should usually aim to add docstring comments to your code wherever you can, particularly for critical or complex functions.

Let's add one to our code now, within the `fahr_to_celsius` function.

```python
    """Convert fahrenheit to Celsius.

    :param fahr: temperature in Fahrenheit
    :returns: temperature in Celsius
    """
```

Re-run `pylint` command - can see we have one less docstring error, and a slightly higher score.

If you'd like to know more about docstrings and commenting,
there's an in-depth [RealPython tutorial](https://realpython.com/documenting-python-code/) on these and the different ways you can format them.

## Ignoring Issues

We can instruct pylint to ignore any particular types of issues,
which is useful if they are not seen as important or pedantic,
or we need to see other types more clearly.
For example, to ignore any unused imports:

```bash
pylint --disable=W0611 climate_analysis.py
```

Or, to disable all issues of type "warning":

```bash
pylint --disable=W climate_analysis.py
```

This can be particularly useful if we wish to ignore particularly pedantic rules,
such as long line lengths over 100 characters.

::: challenge

Edit the `climate_analysis.py` file and add in a comment line that exceeds 100 characters.
Then re-run pylint and determine the issue identifier for this message,
and re-run pylint again disabling this specific issue.

:::: solution

```bash
pylint climate_analysis.py
```

```output
************* Module climate_analysis
climate_analysis.py:3:0: C0301: Line too long (111/100) (line-too-long)
climate_analysis.py:17:0: C0325: Unnecessary parens after '=' keyword (superfluous-parens)
climate_analysis.py:1:0: C0114: Missing module docstring (missing-module-docstring)
...
```

We can see that the identifier is `C0301`, so:

```bash
pylint --disable=C0301 climate_analysis.py
```

::::

:::

However, if we wanted to ignore this issue for the foreseeable future,
typing this in every time would be tiresome.
Fortunately we can specify a configuration file to pylint which specifies how we want to interpret issues.

We do this by first using pylint to generate a default `.pylintrc` file.
It directs this as output to the shell,
so we need to redirect it to a file to capture it.
Ensure you are in the repository root directory, then:

```bash
pylint --generate-rcfile > .pylintrc
```

If you edit this generated file you'll notice there are many things we can specify to pylint.
For now, look for `disable=` and add `C0301` to the list of ignored issues already present that are separated by commas, e.g.:

```text
# no Warning level messages displayed, use "--disable=all --enable=classes
# --disable=W".
disable=C0301,
        raw-checker-failed,
        bad-inline-option,
        locally-disabled,
        file-ignored,
        suppressed-message,
        useless-suppression,
        deprecated-pragma,
        use-implicit-booleaness-not-comparison-to-string,
        use-implicit-booleaness-not-comparison-to-zero,
        use-symbolic-message-instead
```

Every time you re-run it now, the `C0301` issue will not be present.

## Using Pylint within VSCode

The good news is that if you're using the VSCode IDE,
we can also (or alternatively) install a Python linter in VSCode to give us this code analysis functionality, by installing the Pylint extension.
Select the `Extensions` icon and this time search for `Pylint`, the one by Microsoft, and click `Install`.

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

## Summary

Code linters like pylint help us to identify problems in our code,
such as code styling issues and potential errors,
and importantly, if we work in a team of developers such tools help us keep our code style *consistent*.
Attempting to understand a code base which employs a variety of coding styles (perhaps even in the same source file) can be remarkably difficult.

But there are some aspects we should be careful of when using linters and interpreting their results:

- **They don't tell us that the code actually works** and they don't tell us if the results our code produces are actually correct, so we still need to test our code.
- **They don't give us any Idea of whether it's a good implementation**, 
and that the technical choices are good ones.
For example, this code contains functions to conduct temperature conversions, but it turns out there's a number of well-maintained Python packages that do this (e.g. [pytemperature](https://pypi.org/project/pytemperature/))so we should be using a tried and tested package instead of reinventing the wheel.
- **They also don't tell us if the implementation is actually fit for purpose**. Even if the code is a good implementation, and it works as expected, is it actually solving the *intended* problem?
- **They also don't tell us anything about the data the program uses**
which may have its own problems.
- **A high score or zero warnings may give us false confidence**.
Just because we have reached a 10.00 score, doesn't mean the code is actually *good* code, just that it's likely well formatted and hopefully easier to read and understand.

So we have to be a bit careful.
These are all valid, high-level questions to ask while you're writing code, both as a team, and also individually.
In the fog of development, it can be surprisingly easy to lose track of what's actually being implemented and how it's being implemented.
A good idea is to revisit these questions regularly, to be sure you can answer them!

However, whilst taking these shortcomings into account, linters are a very low effort way to help us improve our code and keep it consistent.

::::::::::::::::::::::::::::::::::::: keypoints 

- Use the `--reports y` argument on the command line to Pylint to provide verbose reports
- Instruct Pylint to ignore messages on the command line using the `--disable=` argument followed by comman-separated list of message identifiers
- Use `pylint --generate-rcfile > .pylintrc` to generate a pre-populated configuration file for Pylint to edit to customise Pylint's behaviour when run within a particular directory
- Pylint can be run on the command line or used within VSCode
- Using Pylint helps us keep our code consistent, particularly across teams
- Don't use Pylint feedback and scores as the only means to judge code quality

::::::::::::::::::::::::::::::::::::::::::::::::

---
title: "2.3 Analysing Code using a Linter"
teaching: 10
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- What tools can help with maintaining a consistent code style?
- How can I keep dependencies between different code projects separate?
- How can we automate code style checking?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Use pylint to verify a program’s adherence to an established Python coding style convention
- Describe the benefits of a virtual environment
- Create and use a virtual environment to manage Python dependencies separately for our example code
- Install the Pylint static code analysis tool as a VSCode extension
- Use the Pylint extension to identify deeper potential issues and errors
- List the various types of issue messages that are output from Pylint
- Fix an issue identified by Pylint and re-run Pylint to ensure it is resolved

::::::::::::::::::::::::::::::::::::::::::::::::

## Installing a Code Linter

The first thing we need to do is install pylint,
a very well established tool for statically analysing Python code.

Now fortunately, pylint can be installed as a Python package,
and we're going to create what's known as a virtual environment to hold this installation of pylint.

QUESTION: who has installed a Python package before, using the program pip? Yes/No
QUESTION: who has created and used a Python virtual environment before? Yes/No

### Benefits of Virtual Environments

Virtual environments are an indispensible tool for managing package dependencies across multiple projects,
and could be a whole topic itself.
In the case of Python, the idea is that instead of installing Python packages at the level of our machine's Python installation,
which we could do,
we're going to install them within their own "container",
which is separate to the machine's Python installation.
Then we'll run our Python code only using packages within that virtual environment.

There are a number of key benefits to using virtual environments:

- It creates a clear separation between the packages we use for this project,
and the packages we use other projects.
- We don't end up with a machine's Python installation containing a clutter of a thousand different packages,
where determining which packages are used for which project often becomes very time consuming and prone to error.
- Since we are sure what our code actually needs as dependencies,
it becomes much easier for someone else (which could be a future version of ourselves) to know what these dependencies are and install them to use our code.
- Virtual environments are not limited to Python; for example there are similar tools for available for Ruby, Java and JavaScript.

### Setting up a Virtual Environment

Let's now create a Python virtual environment and make use of it.
Make sure you're in the root directory of the repository, then type

```bash
python -m venv venv
```

Here, we're using the built-on Python venv module - short for virtual environment - to create a virtual environment directory called `venv`.
We could have called the directory anything, but naming it `venv` (or `.venv`) is a common convention,
as is creating it within the repository root directory.
This makes sure the virtual environment is closely associated with this project, and not easily confused with another.

Once created, we can *activate* it so it's the one in use:

```bash
[Linux] source venv/bin/activate
[Mac] source venv/bin/activate
[Windows] source venv/Scripts/activate
```

You should notice the prompt changes to reflect that the virtual environment is active, which is a handy reminder. For example:

```output
(venv) $
```

QUESTION: who has successfully created and activated their virtual environment? Yes/No?

Now it's created, let's take a look at what's in this virtual environment at this point.

```bash
pip list
```

```output
Package    Version
---------- -------
pip        22.0.2
setuptools 59.6.0
```

We can see this is essentially empty,
aside from some default packages that are always installed.
Note that whilst within this virtual environment,
we no longer have access to any globally installed Python packages.

### Installing Pylint into our Virtual Environment

The next thing we can do is install any packages needed for this codebase.
As it turns out, there isn't any needed for the code itself,
but we wish to use pylint, and that's a python package.

::::::::::::::::::::::::::::::::::::::::: callout

## What is Pylint?

Pylint is a tool that can be run from the command line or via IDEs like VSCode,
which can help our code in many ways:

- Ensure consistent code style : whilst in-IDE context-sensitive highlighting such as that provided by VSCode, it helps us stay consistent with established code style standards such as ([PEP 8](https://peps.python.org/pep-0008/)) as we write code by highlighting infractions.
- Perform basic error detection: Pylint can look for certain Python type errors.
- Check variable naming conventions: Pylint often goes beyond PEP 8 to include other common conventions, such as naming variables outside of functions in upper case.
- Customisation: you can specify which errors and conventions you wish to check for, and those you wish to ignore.

:::::::::::::::::::::::::::::::::::::::::

So we can install pylint into our virtual environment:

```bash
pip install pylint
```

Now if we check the packages, we see:

```bash
pip list
```

```output
Package           Version
----------------- -------
astroid           3.3.9
dill              0.3.9
isort             6.0.1
mccabe            0.7.0
pip               22.0.2
platformdirs      4.3.7
pylint            3.3.6
setuptools        59.6.0
tomli             2.2.1
tomlkit           0.13.2
typing_extensions 4.13.1
```

So in addition to pylint,
we see a number of other dependent packages installed that are required by it.

We can also *deactivate* our virtual environment:

```bash
deactivate
```

You should see the `(venv)` prefix disappear,
indicating we have returned to our global Python environment.
Let's reactivate it since we'll need it to use pylint.

```bash
[Linux] source venv/bin/activate
[Mac] source venv/bin/activate
[Windows] source venv/Scripts/activate
```

## Analysing our Code using a Linter

Let's point pylint at our code and see what it reports:

```bash
pylint climate_analysis.py
```

We run this, and it gives us a report containing issues it has found with the code,
and also an overall score.

```output
************* Module climate_analysis
climate_analysis.py:9:35: C0303: Trailing whitespace (trailing-whitespace)
climate_analysis.py:9:0: C0325: Unnecessary parens after '=' keyword (superfluous-parens)
climate_analysis.py:1:0: C0114: Missing module docstring (missing-module-docstring)
climate_analysis.py:4:0: C0103: Constant name "shift" doesn't conform to UPPER_CASE naming style (invalid-name)
climate_analysis.py:5:0: C0103: Constant name "comment" doesn't conform to UPPER_CASE naming style (invalid-name)
climate_analysis.py:6:15: W1514: Using open without explicitly specifying an encoding (unspecified-encoding)
climate_analysis.py:8:0: C0116: Missing function or method docstring (missing-function-docstring)
climate_analysis.py:8:0: C0103: Function name "FahrToCelsius" doesn't conform to snake_case naming style (invalid-name)
climate_analysis.py:8:18: W0621: Redefining name 'fahr' from outer scope (line 20) (redefined-outer-name)
climate_analysis.py:9:4: W0621: Redefining name 'celsius' from outer scope (line 21) (redefined-outer-name)
climate_analysis.py:11:0: C0116: Missing function or method docstring (missing-function-docstring)
climate_analysis.py:11:0: C0103: Function name "FahrToKelvin" doesn't conform to snake_case naming style (invalid-name)
climate_analysis.py:11:17: W0621: Redefining name 'fahr' from outer scope (line 20) (redefined-outer-name)
climate_analysis.py:12:4: W0621: Redefining name 'kelvin' from outer scope (line 22) (redefined-outer-name)
climate_analysis.py:6:15: R1732: Consider using 'with' for resource-allocating operations (consider-using-with)
climate_analysis.py:1:0: W0611: Unused import string (unused-import)

------------------------------------------------------------------
Your code has been rated at 0.59/10 (previous run: 0.59/10, +0.00)
```

For each issue, it tells us:

- The filename
- The line number and text column the problem occurred
- An issue identifier (what type of issue it is)
- Some text describing this type of error (as well as a shortened form of the error type)

You'll notice there's also a score at the bottom, out of 10.
Essentially, for every infraction, it deducts from an ideal score of 10.
Note that it is perfectly possible to get a negative score,
since it just keeps deducting from 10!
But we can see here that our score appears very low - 0.59/10,
and if we were to now resolve each of these issues in turn, we should get a perfect score.

## Identifying and Fixing an Issue

We can also ask for more information on an issue identifier.
For example, we can see at line 9, near column 35, there is a trailing whitespace

```bash
pylint --help-msg C0303
```

```output
:trailing-whitespace (C0303): *Trailing whitespace*
  Used when there is whitespace between the end of a line and the newline. This
  message belongs to the format checker.
```

Which is helpful if we need clarification on a particular message.

If we now edit the file, and go to line 9, column 35,
we can see that there is an unnecessary space.

QUESTION: who's managed to run pylint on the example code? Yes/No

Let's fix this issue now by removing the space,
save the changed file,
and then re-run pylint on it.

```bash
pylint climate_analysis.py
```

```output
------------------------------------------------------------------
Your code has been rated at 1.18/10 (previous run: 0.59/10, +0.59)
```

And we see that the `C0303` issue has disappeared and our score has gone up!
Note that it also gives us a comparison against our last score.

As a gentle warning: it can get quite addictive to keep increasing your score,
which might well be the point!

So looking at the issue identifiers, e.g. `C0303`, what do the `C`, `W`, `R` prefix symbols mean?

```bash
pylint --long-help
```

At the end, we can see a breakdown of what they mean:

- `I` is for informational messages
- `C` is for a programming standards violation. Part of the code is not conforming to the normally accepted conventions of writing good code (e.g. things like variable or function naming)
- `R` for a need to refactor, due to a "bad code smell”
- `W` for warning - something that isn't critical should be resolved
- `E` for error - so pylint think's it's spotted a bug (useful, but don't depend on this to find errors!)
- `F` for a fatal pylint error

So if we run it again on our code:

```bash
pylint climate_analysis.py
```

```output
************* Module climate_analysis
climate_analysis.py:9:0: C0325: Unnecessary parens after '=' keyword (superfluous-parens)
climate_analysis.py:1:0: C0114: Missing module docstring (missing-module-docstring)
climate_analysis.py:4:0: C0103: Constant name "shift" doesn't conform to UPPER_CASE naming style (invalid-name)
climate_analysis.py:5:0: C0103: Constant name "comment" doesn't conform to UPPER_CASE naming style (invalid-name)
climate_analysis.py:6:15: W1514: Using open without explicitly specifying an encoding (unspecified-encoding)
climate_analysis.py:8:0: C0116: Missing function or method docstring (missing-function-docstring)
climate_analysis.py:8:0: C0103: Function name "FahrToCelsius" doesn't conform to snake_case naming style (invalid-name)
climate_analysis.py:8:18: W0621: Redefining name 'fahr' from outer scope (line 20) (redefined-outer-name)
climate_analysis.py:9:4: W0621: Redefining name 'celsius' from outer scope (line 21) (redefined-outer-name)
climate_analysis.py:11:0: C0116: Missing function or method docstring (missing-function-docstring)
climate_analysis.py:11:0: C0103: Function name "FahrToKelvin" doesn't conform to snake_case naming style (invalid-name)
climate_analysis.py:11:17: W0621: Redefining name 'fahr' from outer scope (line 20) (redefined-outer-name)
climate_analysis.py:12:4: W0621: Redefining name 'kelvin' from outer scope (line 22) (redefined-outer-name)
climate_analysis.py:6:15: R1732: Consider using 'with' for resource-allocating operations (consider-using-with)
climate_analysis.py:1:0: W0611: Unused import string (unused-import)

------------------------------------------------------------------
Your code has been rated at 1.18/10 (previous run: 1.18/10, +0.00)
```

We can see that most of our issues are do to with coding conventions.

::::::::::::::::::::::::::::::::::::: keypoints 

- Virtual environments help us maintain dependencies between different code projects separately, avoiding confusion between which dependencies are strictly required for a given project
- One method to create a Python virtual environment is to use `python -m venv venv` to generate a virtual environment in the current directory called `venv`
- Code linters such as Pylint help to analyse and identify deeper issues with our code, including potential run-time errors
- Pylint outputs issues of different types, including informational messages, programming standards violations, warnings, and errors
- Pylint outputs an overall score for our code based on deductions from a perfect score of 10

::::::::::::::::::::::::::::::::::::::::::::::::

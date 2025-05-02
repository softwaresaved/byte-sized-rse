---
title: "6.2 Some Example Code"
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

FIXME: copy factorial-example repo into softwaresaved

For this lesson we'll need to create a new GitHub repository based on the contents of another repository.

1. Once logged into GitHub in a web browser,
go to https://github.com/UNIVERSE-HPC/ci-example.
1. Select 'Use this template', and then select 'Create a new repository' from the dropdown menu.
1. On the next screen, ensure your personal GitHub account is selected in the `Owner` field, and fill in `Repository name` with `ci-example`.
1. Ensure the repository is set to `Public`.
1. Select `Create repository`.

You should be presented with the new repository's main page.
Next, we need to clone this repository onto our own machines,
using the Bash shell.
So firstly open a Bash shell (via Git Bash in Windows or Terminal on a Mac).
Then, on the command line,
navigate to where you'd like the example code to reside,
and use Git to clone it.
For example, to clone the repository in our home directory (replacing `github-account-name` with our own account),
and change directory to the repository contents:

```bash
cd
git clone https://github.com/github-account-name/ci-example
cd ci-example
```

## Examining the Code

Next, let's take a look at the code, which is in the `factorial-example/mymath directory`, called `factorial.py`,
so open this file in an editor.
You may recall we used this example in the last session on unit testing.

As a reminder, the example code is a basic Python implementation of Factorial.
Essentially, it multiplies all the whole numbers from a given number down to 1
e.g. given 3, that's 3 x 2 x 1 = 6 - so the factorial of 3 is 6.

We can also run this code from within Python to show it working.
In the shell,
ensure you are in the root directory of the repository,
then type:

```bash
python
```

```python
Python 3.10.12 (main, Feb  4 2025, 14:57:36) [GCC 11.4.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 
```

Then at the prompt, import the `factorial` function from the `mymath` library and run it:

```python
>>> from mymath.factorial import factorial
>>> factorial(3)
```

Which gives us 6 - which gives us some evidence that this function is working.
But this isn't really enough evidence to give us confidence in its overall correctness.

## Running the Tests

For this reason, this code repository already has a series of unit tests,
that allows us to automate this results checking,
written using a Python unit testing framework called `pytest`.
Note that this is a different unit testing framework that we looked at in the last session!

Navigate to the repository's `tests` directory, and open a file called `test_factorial.py`:

```python
import pytest
from mymath.factorial import factorial


def test_3():
    assert factorial(3) == 6

def test_5():
    assert factorial(5) == 120

def test_negative():
    with pytest.raises(ValueError):
      factorial(-1)
```

The key difference when writing tests for `pytest` as opposed to `unittest`,
is that we don't need to worry about wrapping the tests in a class:
we only need to write functions for each test,
which is a bit simpler.
But they otherwise essentially work very similarly in both frameworks.

So essentially, this series of tests will check whether calling our `factorial` function gives us the correct result,
given a variety of inputs:

- `factorial(3)` should give us 6
- `factorial(5)` should give us 120
- `factorial(-1)` should raise a Python `ValueError` which we need to check for

## Setting up a Virtual Environment for `pytest`

So how do we run these tests?
Well, we need to create a virtual environment,
since we're using a unit test framework that's supplied by another Python library which we need to have access to.

You may remember we used virtual environments previously.
So in summary, we need to:

- Create a new virtual environment to hold packages
- Activate that new virtual environment
- Install `pytest` into our new virtual environment

So:

```bash
python -m venv venv
```

Then to activate it:

```bash
[Linux] source venv/bin/activate
[Mac] source venv/bin/activate
[Windows] source venv/Scripts/activate
```

To install `pytest`:

```bash
pip install pytest
```

Then, in the shell, we can run these tests by ensuring we're in the repository's root directory,
and running the following (very similar to how we ran our previous `unittest` tests):

```bash
python -m pytest tests/test_factorial.py 
```

You'll note the output is slightly different:

```output
============================= test session starts ==============================
platform linux -- Python 3.10.12, pytest-8.3.5, pluggy-1.5.0
rootdir: /home/steve/test/ci-example2
collected 3 items                                                              

tests/test_factorial.py ...                                              [100%]

============================== 3 passed in 0.00s ===============================
```

But essentially, we receive the same information: a `.` if the test is successful,
and a `F` if there is a failure.

We can also ask for verbose output,
which shows us the results for each test separately,
in the same way as we did with `unittest`,
using the `-v` flag:

```bash
python -m pytest -v tests/test_factorial.py 
```

```output
============================= test session starts ==============================
platform linux -- Python 3.10.12, pytest-8.3.5, pluggy-1.5.0 -- /home/steve/test/ci-example2/venv/bin/python
cachedir: .pytest_cache
rootdir: /home/steve/test/ci-example2
collected 3 items                                                              

tests/test_factorial.py::test_3 PASSED                                   [ 33%]
tests/test_factorial.py::test_5 PASSED                                   [ 66%]
tests/test_factorial.py::test_negative PASSED                            [100%]

============================== 3 passed in 0.00s ===============================
```

[CHECKPOINT - who's run the tests and got this output? Yes/No]

::::::::::::::::::::::::::::::::::::: keypoints 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

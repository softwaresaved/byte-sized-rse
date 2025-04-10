---
title: "5.2 Some Example Code"
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

For this lesson we'll be using some example code available on GitHub,
which we'll clone onto our machines using the Bash shell.
So firstly open a Bash shell (via Git Bash in Windows or Terminal on a Mac). Then, on the command line, navigate to where you'd like the example code to reside,
and use Git to clone it.
For example, to clone the repository in our home directory,
and change our directory to the repository contents:

```bash
cd
git clone https://github.com/UNIVERSE-HPC/factorial-example
cd factorial-example
```


## Examining the Code

Next, let's take a look at the code, which is in the `factorial-example/mymath directory`, called `factorial.py`,
so open this file in an editor.

The example code is a basic Python implementation of Factorial.
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
Of course, in practice, our functions may well be more complicated than this,
and of course, they may call other separate functions.
Now we could just come up with a list of known input numbers and expected outputs and run each of these manually to test the code,
but this would take some time.
Computers are really good at one thing - automation - so let's use that and automate our tests,
to make it easy for ourselves.

## Running the Tests

As it turns out, this code repository already has a test.
Navigate to the repository's `tests` directory, and open a file called `test_factorial.py`:

```python
import unittest
from mymath.factorial import factorial


class TestFactorialFunctions(unittest.TestCase):

    def test_3(self):
        self.assertEqual(factorial(3), 6)
```

Now, we using a Python unit test framework called `unittest`.
There are other such frameworks for Python, including `nose` and `pytest` which is very popular,
but the advantage of using `unittest` is that it's already built-in to Python so it's easier for us to use it.

Before we look into this example unit test, questions
*Who here is familiar with object oriented programming?*  Yes/No
*Who's written an object oriented program?* Yes/No 

:::::::::::::::::::::::::::::::::::::::::  callout

## What is Object Oriented Programming?

For those that aren't familiar with object oriented programming,
it's a way of structuring your programs around the *data* of your problem.
It's based around the concept of objects, which are structures that contain both data and functions that operate on that data.
In object oriented programming, objects are used to model real-world entities, such as people, bank accounts, libraries, books, even molecules, and so on.
With each object having its own:

- data - known as attributes
- functions - known as methods

These are encapsulated within a defined structure known as a class.
An introduction to object oriented programming is beyond the scope of this session,
but if you'd like to know more there's a great [introductory tutorial](https://realpython.com/python3-object-oriented-programming/) on the [RealPython](https://realpython.com/) site.
This site is a great practical resource for learning about how to do many things in Python!

::::::::::::::::::::::::::::::::::::::::::::::::::

For the purposes of this activity, we use object oriented classes to encapsulate our unit tests since that's how they're defined in the `unittest` framework.
You can consider them as a kind of syntactic sugar to group our tests together,
2ith a single unit test being represented as a single function - or method - within a class.

In this example, we have a class called `TestFactorialFunctions` with a single unit test, which we've called `test_3`.
Within that test method, we are essentially doing what we did when we ran it manually earlier:
we're running factorial with the argument 3, and checking it equals 6.
We use an inbuilt function, or method, in this class called `assertEqual`, that checks the two are the same,
and if not, the test will fail.

So how do we run this test?
In the shell, we can run this test by ensuring we're in the repository's root directory, and running:

```bash
python -m unittest tests/test_factorial.py 
```

```output
.
----------------------------------------------------------------------
Ran 1 test in 0.000s

OK
```

[CHECKPOINT - who's run the tests and got this output? Yes/No]

So what happens?
We see a single `.`,  we see a message that says it ran very quickly, and `OK`.
The single dot means the single test we have was successfully run,
so our test passes!

But how does unittest know what to run exactly?
Unit test frameworks like `unitttest` follow a common pattern of finding tests and running them.
When we give a single file argument to `unittest`,
it searches the Python file for `unittest.TestCase` classes,
and within those classes, looks for methods starting with `test_`, and runs them.
So we  could add more tests in this class in the same way,
and it would run each in turn.
We could even add multiple `unittest.TestCase` classes here if we wanted, 
each testing different aspects of our code for example,
and `unittest` would search all of these classes and run each `test_` function in turn.

## Testing for Failure

We've seen what happens if a test succeeds,
but what happens if a test fails?
Let's deliberately change our test to be wrong and find out,
by editing the `tests/test_factorial.py` file,
changing the expected result of `factorial(3)` to be `10`, and saving the file.

We'll rerun our tests slightly differently than last time:

```bash
python -m unittest -v tests/test_factorial.py
```

In this case, we add `-v` for more verbose output,
giving us detailed results test-by-test.

```output
test_3 (tests.test_factorial.TestFactorialFunctions) ... FAIL

======================================================================
FAIL: test_3 (tests.test_factorial.TestFactorialFunctions)
----------------------------------------------------------------------
Traceback (most recent call last):
  File "/home/steve/factorial-example/tests/test_factorial.py", line 8, in test_3
    self.assertEqual(factorial(3), 10)
AssertionError: 6 != 10

----------------------------------------------------------------------
Ran 1 test in 0.000s

FAILED (failures=1)
```

In this instance we get a `FAIL` instead of an `OK` for our test,
and we see an `AssertionError` that `6` is not equal to `10`,
which is clearly true.

Let's now change our faulty test back by editing the file again,
changing the `10` back to `6`,
and re-run our tests:

```bash
python -m unittest -v tests/test_factorial.py
```

```output
test_3 (tests.test_factorial.TestFactorialFunctions) ... ok

----------------------------------------------------------------------
Ran 1 test in 0.000s

OK
```

This illustrates an important point with our tests:
it's important to make sure your tests are correct too.
So make sure you work with known 'good' test data which has been verified to be correct!

::::::::::::::::::::::::::::::::::::: keypoints 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

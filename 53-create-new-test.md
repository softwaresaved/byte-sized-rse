---
title: "5.3 Creating a New Test"
teaching: 10
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- How do I write a unit test?
- How do I write a unit test that tests for an error?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Implement and run unit tests to verify the correct behaviour of program functions
- Describe how and when testing fits into code development
- Write a unit test that tests for an expected error

::::::::::::::::::::::::::::::::::::::::::::::::

## Add a New Test

As we've mentioned,
adding a new unit test is a matter of adding a new test method.
Let's add one to test the number `5`.
Edit the `tests/test_factorial.py` file again:

```python
  def test_5(self):
    self.assertEqual(factorial(5), 120)
```

[CHECKPOINT - who's finished editing the file Yes/No]

And then we can run it exactly as before, in the shell

```bash
python -m unittest -v tests/test_factorial.py 
```

```output
test_3 (tests.test_factorial.TestFactorialFunctions) ... ok
test_5 (tests.test_factorial.TestFactorialFunctions) ... ok

----------------------------------------------------------------------
Ran 2 tests in 0.000s

OK
```

We can see the tests pass.
So the really useful thing here,
is we can rapidly add tests and rerun all of them.
Particularly with more complex codes that are harder to reason about,
we can develop a set of tests into a suite of tests to verify the codes' correctness.
Then, whenever we make changes to our code,
we can rerun our tests to make sure we haven't broken anything.
An additional benefit is that successfully running our unit tests can also give others confidence that our code works as expected.

[CHECKPOINT - who managed to run this with their new unit test Yes/No]

## Change our Implementation, and Re-test

Let's illustrate another key advantage of having unit tests.
Let's assume during development we find an error in our code.
For example, if we run our code with `factorial(10000)` our Python program from within the Python interpreter, it crashes with an exception:

```python
>>> from mymath.factorial import factorial
>>> factorial(10000)
```

```output
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/home/steve/factorial-example/mymath/factorial.py", line 11, in factorial
    return  n * factorial(n-1)
  File "/home/steve/factorial-example/mymath/factorial.py", line 11, in factorial
    return  n * factorial(n-1)
  File "/home/steve/factorial-example/mymath/factorial.py", line 11, in factorial
    return  n * factorial(n-1)
  [Previous line repeated 995 more times]
  File "/home/steve/factorial-example/mymath/factorial.py", line 8, in factorial
    if n == 0 or n == 1:
RecursionError: maximum recursion depth exceeded in comparison
```

It turns out that our factorial function is *recursive*,
which means it calls itself.
In order to compute the factorial of 10000, it does that a lot.
Python has a default limit for recursion of 1000,
hence the exception,
which is a bit of a limitation in our implementation.
However, we can correct our implementation by changing it to use a different method of calculating factorials that isn't recursive.
Edit the `mymath/factorial.py` file and replace the function with this one:

```python
def factorial(n):
    """
    Calculate the factorial of a given number.

    :param int n: The factorial to calculate
    :return: The resultant factorial
    """
    factorial = 1
    for i in range(1, n + 1):
        factorial = factorial * i
    return factorial
```

Make sure you replace the code in the `factorial.py` file,
and not the `test_factorial.py` file.

This is an *iterative* approach to solving factorial that isn't recursive,
and won't suffer from the previous issue.
It simply goes through the intended range of numbers and multiples it by a previous running total each time,
but doesn't do it recursively by calling itself.
Notice that we're not changing how the function is called,
or its intended behaviour.
So we don't need to change the Python docstring here,
since it still applies.

We now have our updated implementation, but we need to make sure it works as intended.
Fortunately, we have our set of tests, so let's run them again:

```bash
python -m unittest -v tests/test_factorial.py
```

```output
test_3 (tests.test_factorial.TestFactorialFunctions) ... ok
test_5 (tests.test_factorial.TestFactorialFunctions) ... ok

----------------------------------------------------------------------
Ran 2 tests in 0.000s

OK
```

And they work, which gives us some confidence - very rapidly - that our new implementation is behaving exactly the same as before.
So again, each time we change our code,
whether it's making small or large changes,
we retest and check they all pass

[CHECKPOINT - who managed to write unit test and run it? Yes/No]

::::::::::::::::::::::::::::::::::::: callout

## What makes a Good Test?

Of course, we only have 2 tests so far, and it would be good to have more
But what kind of tests are good to write?
With more tests that sufficiently test our code,
the more confidence we have that our code is correct.
We could keep writing tests for e.g., 10, 15, 20, and so on.
But these become increasingly less useful,
since they're in much the same "space".
We can't test all positive numbers,
and it's fair to say at a certain point,
these types of low integers are sufficiently tested.
So what test cases should we choose?

We should select test cases that test two things:

- The paths through our code, so we can check they work as we expect.
For example, if we had a number of paths through the code dictated with if statements,
we write tests to ensure those are followed.
- We also need to test the boundaries of the input data we expect to use, known as *edge cases*.
For example, if we go back to our code.
we can see that there are some interesting edge cases to test for:

- Zero?
- Very large numbers (as we've already seen)?
- Negative numbers?

All good candidates for further tests,
since they test the code in different ways,
and test different paths through the code.

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

:::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: keypoints 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

---
title: "5.4 Handling Errors"
teaching: 10
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

## How do we Handle Testing for Errors?

But what do we do if our code is expected to throw an error?
How would we test for that?

Let's try our code with a negative number,
which we've already identified as a good test case,
from within the python interpreter:

```python
>>> from mymath.factorial import factorial
>>> factorial(-1)
```

We can see that we get the result of 1,
which is incorrect,
since the factorial function is undefined for negative numbers.

Perhaps what we want in this case is to test for negative numbers as an invalid input,
and display an exception if that is the case.
How would we implement that,
and how would we test for the presence of an exception?

In our implementation let's add a check at the start of our function,
which is known as a *precondition*.
The precondition will check the validity of our input data before we do any processing on it,
and this approach to checking function input data is considered good practice.

Edit the `mymath/factorial.py` file again,
and add at the start, below the docstring:

```python
if n < 0:
    raise ValueError('Only use non-negative integers.')
```

If we run it now, we should see our error:

```python
>>> from mymath.factorial import factorial
>>> factorial(-1)
```

```output
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/home/steve/factorial-example/mymath/factorial.py", line 9, in factorial
    raise ValueError('Only use non-negative integers.')
ValueError: Only use non-negative integers.
```

Sure enough, we get our exception as desired.
But how do we test for this in a unit test,
since this is an exception, not a value?
Fortunately, unit test frameworks have ways to check for this.

Let's add a new test to `tests/test_factorial.py`:

```python
    def test_negative(self):
        with self.assertRaises(ValueError):
          factorial(-1)
```

So here, we use `unittest`'s built-in `assertRaises()` (instead of `assertEquals()`) to test for a `ValueError` exception occurring when we run `factorial(-1)`.
We also use Python's `with` here to test for this within the call to `factorial()`.
So if we re-run our tests again, we should see them all succeed:

```bash
python -m unittest -v tests/test_factorial.py
```

You should see:

```output
test_3 (tests.test_factorial.TestFactorialFunctions) ... ok
test_5 (tests.test_factorial.TestFactorialFunctions) ... ok
test_negative (tests.test_factorial.TestFactorialFunctions) ... ok

----------------------------------------------------------------------
Ran 3 tests in 0.000s

OK
```

## Brief Summary

So we now have the beginnings of a test suite!
And every time we change our code, we can rerun our tests.
So the overall process of development becomes:

- Add new functionality (or modify new functionality) to our code
- Potentially add new tests to test any new functionality
- Re-run all our tests

::::::::::::::::::::::::::::::::::::: keypoints 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

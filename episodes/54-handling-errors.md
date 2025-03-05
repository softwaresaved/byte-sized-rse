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

But what do we do if our code is expected to throw an error?
How would we test for that?

Well, let’s try our code with a negative number
Which we’ve identified as a good test case
(Don’t need to run this bit) Run the python interpreter
from mymath.factorial import factorial
factorial(-1)
We can see that we get 1
This is incorrect, since the factorial function is undefined for negative numbers
Perhaps what we want in this case is to test for negative numbers as an input, and display an exception if that is the case
How would we implement that, and how would we test for the presence of an exceptoin?
So in our implementation, let’s add a check at the start of our function
This is known as a precondition
Where we check the validity of our input data before we do any processing on it
And is considered good practice
So add at the start, below the docstring
if n < 0:
    raise ValueError('Only use non-negative integers.')
If we run it now, we should see our error
from mymath.factorial import factorial
factorial(-1)
Sure enough, we get our exception as desired
But how do we test for this in a unit test?
This is an exception, not a value
Fortunately, unit test frameworks have ways to check for this
Let’s add a new test
  def test_negative(self):
    with self.assertRaises(ValueError):
      factorial(-1)
So here, we use unittests built-in assertRaises (instead of assertEquals) to test for a ValueError exception occurring when we run factorial(-1)
We use Python’s ‘with’ here to test for this within the call to factorial
So if we re-run our tests again, we should see them all succeed
And we do!

## Brief Summary

So we now have the beginnings of a test suite!
And every time we change our code, we can rerun our tests
So the overall process of development becomes
Add new functionality to our code
And then add new tests to test that new functionality


::::::::::::::::::::::::::::::::::::: keypoints 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

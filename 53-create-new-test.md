---
title: "5.3 Creating a New Test"
teaching: 10
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

## Add a New Test

So how do we add a new unit test?
We add a new test method...
Let's add one to test the number 5 - feel free to code along with me!
  def test_5(self):
    self.assertEqual(factorial(5), 120)

[CHECKPOINT - who's finished editing the file Yes/No]

And then we can run it exactly as before, in the shell
python -m unittest -v tests/test_factorial.py 
And they pass!
So the really useful thing here, is we can rapidly add tests and rerun them
And with more complex codes that are harder to reason about, we can develop a set of tests into a suite of tests to verify the codes' correctness
Whenever we make changes to our code, we can rerun our tests to make sure we haven't broken anything
An additional benefit is that successfully running our unit tests can also give others confidence that our code works as expected

[CHECKPOINT - who managed to run this with their new unit test Yes/No]


## Change our Implementation, and Re-test

So let's illustrate another key advantage of having unit tests
(Don't need to do this bit) Now, let's assume during development we find an error in our code
for example, if we run our code with factorial(10000) our Python program crashes with an exception…
It turns out that our program is recursive - it calls itself
And in order to compute the factorial of 10000, it does that a lot
Now Python has a default limit for recursion of 1000, hence the exception
Bit of a limitation in our implementation
But, we can correct our implementation by changing it to use a different method of calculating factorials that isn't recursive
Let's do that - you can copy and paste the replacement code in the Google Doc  session notes into the factorial.py file
Make sure you replace the code in the factorial.py file, not the test_factorial.py file!
So, we open the factorial.py file in mymath directory…
factorial = 1
for i in range(1, n + 1):
    factorial = factorial * i
return factorial
This is an iterative approach to solving factorial that isn't recursive
And shouldn't suffer from the previous issue
It simply goes through the intended range of numbers and multiples it by a previous running total each time, but doesn't do it recursively
Now, we're not changing how the function is called, or its intended behaviour
So we don't need to change the Python docstring here
So, we have our new implementation, but we need to make sure it works as intended
Fortunately, we have our set of tests, so let's run them again!
python -m unittest -v tests/test_factorial.py
And they work - this gives us some confidence - very quickly - that our new implementation is behaving as we would want
So again, each time we change our code - small or large changes - we retest
And check they all pass

[CHECKPOINT - who managed to write unit test and run it? Yes/No]

::::::::::::::::::::::::::::::::::::: callout

## What makes a Good Test?

Of course, we only have 2 tests so far, and it would be good to have more
But what kind of tests are good to write?
With more tests that sufficiently test our code, the more confidence we have that our code is correct
We could keep writing tests for e.g., 10, 15, 20
But these become increasingly less useful - they're in much the same space
We can't test all positive numbers, and it's fair to say at a certain point, these types of low integers are sufficiently tested
So what test cases should we choose?
We should select test cases that test two things
The paths through our code - so we can check they work
So if we had critical paths dictated with if statements, we write tests to ensure those are followed
But also we need to test the boundaries of the input data we expect to use - known as edge cases
For example, if we go back to our code
We can see that there are some interesting edge cases to test for
What about zero?
What about very large numbers - as we've already seen?
Or negative numbers?
All good candidates for further tests!

:::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: keypoints 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

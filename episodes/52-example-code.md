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

Using the shell, we're going to use Git to clone our example GitHub code repository
So start a terminal and do the following:

git clone https://github.com/UNIVERSE-HPC/factorial-example


## Examining the Code

Next, let's take a look at the code, which is in the factorial-example/mymath directory, called factorial.py
If you're on your own machine, you can use an editor to open the file
Or navigate to it using the shell, and use the ‘cat' command on the file
If on replit, you can navigate to it from the file navigator on the left and select the file
So the example code is a basic Python implementation of Factorial
Essentially, it multiplies all the whole numbers from a given number down to 1
e.g. given 3, that's 3 x 2 x 1 = 6 - so factorial of 3 is 6

We can also run this code to show it working, and also that it appears to work
So in the shell
In the root directory of the repository, we can type
python
from mymath.factorial import factorial [to import the factorial function into Python]
And then run the function, for example
factorial(3)
Which gives us 6 - which looks good

Some evidence this function is working!
Which is good
Of course, in practice, our functions may well be more complicated than this! And of course, may call other separate functions
Now we could just come up with a list of known input numbers and expected outputs and run each of these manually
But this would take some time!
And computers are really good at one thing - automation - so let's use that and automate our tests
Let's make it easy for ourselves

## Running the Tests

Now, as it turns out, this code repository already has a test - let's take a look
Navigate to the repository's ‘tests' directory, and open a file called test_factorial.py
Now, we using a Python unit test framework called unittest
Advantage of using unittest is that it's already built-in to Python - much easier for training!
But a more popular one is Pytest that you may wish to look into
Before we look into this example unit test, questions
*Who here is familiar with object oriented programming?*  Yes/No
*Who's written an object oriented program?* Yes/No 
For those that aren't familiar with object oriented programming…
It's a way of structuring your programs around the data of your problem space
It's based around the concept of objects, which are structures that contain both data and functions that operate on that data
In OOP, objects are used to model real-world entities, such as people, bank accounts, libraries, books, even molecules, and so on
With each object having its own
data - known as attributes
and functions - known as methods
These are encapsulated within a defined structure known as a class
Now, an introduction to OOP is beyond the scope of this session
If you'd like to know more about object oriented programming, there's a great introductory tutorial on the realpython site
https://realpython.com/python3-object-oriented-programming/
Plus, the realpython site is a great resource for learning about Python!
But for the purposes of this activity, we use oo classes to encapsulate our unit tests since that's how they're defined in the unittest framework
And you can consider them as a kind of syntactic sugar to group our tests together
With a single unit test being represented as a single function - or method - within a class
So in this example, we have a class called TestFactorialFunctions with a single unit test, which we've called test_3
And within that test method, we are essentially doing what we did when we ran it manually earlier
We're running factorial with the argument 3, and checking it equals 6
We use an inbuilt function, or method, in this class called ‘assertEqual', that checks the two are the same
If not, the test fails

So how do we run this test?
In the shell, we can run this test by ensuring we're in the repository's root directory, and running
python -m unittest tests/test_factorial.py 
[CHECKPOINT - who's run the tests and got this output? Yes/No]
So what happens?
We see a single ‘.',  we see a message that says it ran very quickly, and ‘OK'.
So what does this single dot mean? It means the single test we have was successfully run
Ok that's great - out test passes!
But how does unittest know what to run exactly?
Well, unit test frameworks like unitttest follow a pattern of finding tests and running them
When we give a single file argument to unittest, it searches the python file for unittest classes
And within those classes, looks for methods starting with ‘test_', and runs them
That's it!
So we  could add more tests in this class and it would run each in turn
We could even add multiple unittest classes here if we wanted, each testing different aspects of our code for example, and unittest would search all of these classes and run each test_ function in turn

## Testing for Failure

We've seen what happens if a test succeeds
But what happens if a test fails?
Let's deliberately change our test to be wrong and find out
e.g. change the expected result of factorial(3) to be 10
We rerun our tests - slightly differently than last time
python -m unittest -v tests/test_factorial.py
In this case, we add ‘-v' for more verbose output, giving us results test-by-test
And we get a ‘FAIL' in place of an ok for our test
In this case, we see an AssertionError that 6 is not equal to 10!
Let's change our faulty test back, re-run our tests
This illustrates an important point with our tests
It's important to make sure your tests are correct too
So make sure you work with known ‘good' test data which has been verified to be correct!

::::::::::::::::::::::::::::::::::::: keypoints 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

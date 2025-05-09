---
title: "1.4 Running and Debugging Code"
teaching: 10
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- How do I run code in VSCode?
- How do I use a debugger to locate the source of a problem in my code?
- How does debugging fit within the broader process of development?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Use VSCode to run a Python script and have any text output displayed within a terminal
- Add a debugging breakpoint to a Python script
- Run a debugger so it pauses program execution at a breakpoint
- Use the debugger to step through our code statement by statement
- Use debugging information to identify the cause of a problem in our code

::::::::::::::::::::::::::::::::::::::::::::::::


## Running Python in VSCode

Now let's try running a Python file.
First, make sure your Python doesn't have any errors!
Then, select the "Play"-looking icon at the top right of the code editor.

FIXME: screenshot snippet of the play icon?

You should see the program run, and output displayed in a pop-up terminal window at the bottom:

```output
steve@laptop:~/code-style-example$ /bin/python3 /home/steve/code-style-example/climate_analysis.py
Max temperature in Celsius 14.73888888888889 Kelvin 287.88888888888886
Max temperature in Celsius 14.777777777777779 Kelvin 287.92777777777775
Max temperature in Celsius 14.61111111111111 Kelvin 287.76111111111106
Max temperature in Celsius 13.838888888888887 Kelvin 286.9888888888889
Max temperature in Celsius 15.477777777777778 Kelvin 288.62777777777774
Max temperature in Celsius 14.972222222222225 Kelvin 288.1222222222222
Max temperature in Celsius 14.85 Kelvin 288.0
Max temperature in Celsius 16.33888888888889 Kelvin 289.4888888888889
Max temperature in Celsius 16.261111111111113 Kelvin 289.4111111111111
Max temperature in Celsius 16.33888888888889 Kelvin 289.4888888888889
steve@laptop:~/code-style-example$ 
```

::::::::::::::::::::::::::::::::::::::::: callout

## Error: `the term conda is not recognised`

If you're running an Anaconda distribution of Python on Windows,
if you see this error it means that VSCode is not looking in the right place for Anaconda's installation.
In this case, you may need to configure VSCode accordingly.

VSCode has a sophisticated method to access it's inner functionality known as the Command Palette, which we'll use to address this.
Activate the Command Paletter by pressing `Ctrl` + `Shift` + `P` simultaneously,
then type `Terminal: Select Default Profile`.
From the options, select `Command Prompt C:\WINDOWS\...`,
and hopefully that should resolve the issue.

:::::::::::::::::::::::::::::::::::::::::

The pop-up window is known as the "Console",
and essentially is a terminal, or command prompt, where the program is run.
You'll notice we can also type in commands here too.
For example in Windows, you could type `dir`, on Mac or Linux you could type `ls` - to get a listing of files, for example.

We can also close this terminal/console at any time,
and start a new one by selecting `Terminal` from the menu and selecting `New Terminal`. So when we write and run our code, we have the option of never having to leave VSCode at all for most things.

## Debugging Code

Now finally, let's look at a feature with IDEs which is often overlooked, that of the debugger.

A debugger is a bit like performing exploratory surgery on a patient.
You know there's something wrong, but you don't know exactly where the problem resides.
What's useful with debuggers is that you go looking within the codebase as it's actually running to find the source of the problem.

In order to run a debugging session we first need to tell the IDE where we'd like to examine the code.
Then you run the code in a special way, using a debugger,
and it pauses the execution of the code at that point.
You then have the freedom to take a look around and examine the state of variables, which functions have been called up until this point, and so on,
and hopefully identify the cause of the issue.

Now, many people when starting out with coding disregard debuggers as complicated and tough to understand.
And 30 or 40 years ago, debuggers were indeed quite complicated to set up and use.
But these days, debuggers are perhaps a little more straightforward,
with IDEs doing a lot of complex stuff for us.

### Introducing a Problem

Let's assume we have a problem with our code - by introducing one.
In our `climate_analysis.py` code, where it says `if data[0][0] != COMMENT`, replace `COMMENT` with `'!'`.
We perhaps might assume one of our colleagues erroneously made this change, but we haven't spotted it yet.
We try to run the code as before, and now it doesn't work.
We get a `ValueError`, which informs us it couldn't perform a conversion of a value extracted from the data file to a float as part of its temperature conversion.

### Adding a Debugging Breakpoint

Now we know where the error is occurring but we don't know the source of the problem, which may not be in the same place.
So let's add in what is known as a **breakpoint** to our code.
This is where the debugger will stop running the code and pause for us
Let's add it at the start of the `for line in climate_data:` line.
We do that by clicking in the left margin for that line.
By hovering in the margin, you'll see a faded red dot appear.
Select it on that line and this sets the breakpoint.

### Using the Debugger

Let's run the code using the debugger.
Select the `Run and Debug` icon on the left, and select `Run and Debug`.
Then it will likely ask two questions in pop-up pane near the top:

1. It asks you to `Select debugger`, so select the suggested `Python Debugger`.
1. Then it asks you to `Select a debug configuration`, so select `Python File` to debug the current file.

Now the Python script is running in debug mode.
You'll see the execution has paused on the line we entered the breakpoint, which is now highlighted.,
Some new information is now displayed in various panes on the left of the code editor.
In particular:

FIXME: show screenshot of debugging panes (esp. variables and call stack)

- `VARIABLES` - on the left, we can see a list of variables, and their current state, at this point in the script's execution, such as `COMMENT` and `SHIFT`, and `climate_data` (which is a reference to our open data file).
We don't have many at the moment.
It also distinguishes between local variables and global variables - this is to do with the "scope" of the variables, as to how they are accessible from this point in the running of the code.
Global variables can be seen from anywhere in the script.
And local variables are those that are visible from this point of the program.
If we were within a function here, we would see variables that are defined and only used within that function as local variables only.
For example, if we set a breakpoint within the `FahrToKelvin` function,
we would see `kelvin` as a local variable, but it wouldn't be listed as a global variable.
- `CALL STACK` - this is a record of the journey the script has taken, in terms of functions called, to get to this position in its execution.
It shows us that we are at the top level of our script,
which makes sense, since our breakpoint is at the top level of script,
and not within any function.
If it were within the `FahrToKelvin` function, for example, we'd see that added to the call stack.
It also shows us the line number where execution has paused at this level of the call stack.

Now, we can also see some new icons at the top to do with debugging:

FIXME: show screenshot snippet of debugging icons

- The first one is continue, which allows the script to keep running until the next breakpoint.
- The next one allows us to step over - or through - the script one statement at a time.
- The next two allow us to choose to step into or out of a function call, which is interesting.
If we want to examine the inner workings of a function during this debug session, we can do that.
- The green cycle one is to restart the debug process.
- The red cross stops debugging completely.

So let's step through our code by selecting the second icon and see what happens.
As we do so, we can see the variable state changing.
By looking in the variables section, we can see that the `line` variable contains the first line read from the data file.
On the next step, we've reached the `if` statement.
If we step again, and then again, our program halts because it's run into the problem we saw before.

This tells us something useful - that the problem occurs in the first iteration of the loop.
So, this implies, the problem might be with the first line of data being processed,
since the Python is going through the data file line by line.
If we re-run the debugger, we can go through this process again.
And we can see something interesting when we get to the `if` statement.
From the code, we know that the if statement is looking for an exclamation mark at the beginning of the line to indicate a comment.
However, the data variable contains a ‘#' as the first character instead.
Therefore, in this case, the code will assume it's a data line and attempt to process it as such.
And then it will fail with the exception we saw before.

### Fixing the Issue

So now we've identified the problem, we can fix it.

Firstly, stop the debug process by selecting the red square.
Then edit the `if` line to search for `COMMENT` instead, reverting the code to what it was before.
We can then rerun the debugger if we wish, to check our understanding.
And as we step through the code, we can see if correctly identifies the first line as a comment, and ignores it, continuing to the iteration of the for loop, and the next line of data.
Now we have our solution fixed, we can stop the debugger again.

We've now solved our problem, so we should remove the breakpoint.
Running our code again as normal, we can see it now works as expected.

## Debugging in Context

Typically, we'd use debugging when we've discovered a problem.
Other techniques, such as testing, are great at identifying that there **are** problems,
but not always the root cause and location of the actual problem.
Debugging is the next step of that process.
Sometimes, we discover a problem - perhaps our code testing show us there's an issue,
or maybe we find out some other way.
If we're lucky, we can identify and fix the problem quickly.
Where we can't, debugging is there to help us.
With particularly complex programs, it can be very difficult to reason about how they work, and where the problem are,
and debugging allows us to pick apart that process, and step by step, help us find the source of those issues.

::::::::::::::::::::::::::::::::::::: keypoints 

- Run a script by selecting the "Play" icon in VSCode
- Debugging allows us to pause and inspect the internal state of a program while it is running
- Specify the points a debugger should pause by adding breakpoints to specific lines of code
- When a breakpoint is reached, a debugger typically shows you the current variables and their values and the stack of functions called to reach the current state
- Debuggers typically allow us to: step through the code a statement at a time, step into or out of a function call if we need further debugging information regarding that function, and continue execution until another breakpoint is reached or the end of the program
- Testing is used to identify the existence of a problem, whilst we use debugging to locate the source of a problem

::::::::::::::::::::::::::::::::::::::::::::::::

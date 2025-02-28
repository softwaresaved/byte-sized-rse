---
title: "1.4 Running and Debugging Code"
teaching: 10
exercises: 2
---

:::::::::::::::::::::::::::::::::::::: questions 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

Now let’s try running a Python file
First, make sure your Python doesn’t have any errors!
Then, select the “Play”-looking icon at the top
You should see the program run, and output displayed in a pop-up window at the bottom
QUESTION: did you see the program output in the window at the bottom? yes/no
IF NO: if you’re on Windows, and installed anaconda, did you get an error message saying “the term conda is not recognised”? yes/no
[problem: is that VSCode is not looking in the right place for anaconda’s installation. Fix: Command Palette (Ctrl/Shift P) -> Terminal: Select Default Profile, select Command Prompt C:\WINDOWS\…]
QUESTION: if you encountered this error, does this fix it? yes/no
This pop-window/terminal is known as the “Console”, and essentially is a terminal, or command prompt, where the program is run
You’ll notice we can also type in commands here too. e.g. in Windows, you could type “dir”, on mac or Linux you could type “ls” - to get a listing of files, for example
This is all great so far
The really nice thing, is that for many things, when we write and run our code, we never have to leave VSCode at all, which I find really efficient
Now finally, let’s look at a feature with IDEs which is often overlooked, that of the debugger
A debugger is a bit like performing exploratory surgery on a patient
You know there’s something wrong, but you don’t know exactly where
So you go looking within the codebase as it’s running to find the source of the problem, then fix it
So how it works, is that you essentially tell the IDE where you’d like to examine the code
Then you run the code in a special way, using a debugger
And it pauses the running at that point
You then you can take a look around and examine the state of variables, which functions have been called up until this point, and so on
And hopefully, you’ll spot the cause
Now, many people when starting out with coding, me included, disregarded debuggers as complicated and tough to understand
And 30 or 40 years ago, debuggers were indeed quite complicated to set up and use
But these days, debuggers are at least a little more straightforward, with IDEs doing a lot of complex stuff for us, which is great
So let’s try out debugging on this code
Let’s assume we have a problem with our code - by introducing a problem!
Where it says “if data[0][0] != COMMENT”, replace COMMENT with ‘!’
We perhaps might assume one of our colleagues erroneously made this change, but we haven’t spotted it
We try to run the code, and lo and behold, it doesn’t work
We get a ValueError - where it couldn’t perform a conversion of a value extracted from the data file to a float (as part of its temperature conversion)
So ok, now we know where the error is occurring, but we don’t know the source of the problem, which not be in the same place - but somewhere before
So let’s add in what is known as a “breakpoint” to our code
This is where the debugger will stop running the code and pause for us
Let’s add it at the start of the “for line in climate_data:” line
We do that by clicking in the left margin for that line
By hovering in the margin, you’ll see a faded red dot appear, select it on that line
This sets the breakpoint
Now, let’s run the code using the debugger
Select the ‘Run and debug’ icon on the left, and select ‘Run and debug’
You’ll likely see a pop-up appear asking about “Debug Configuration”
Select the one “Python File”, perhaps near the top
Now the Python script is running in debug mode
You’ll see the execution has paused on this line (which is now highlighted), and some new information is displayed
On the left, we can see a list of variables, and their current state, at this point in the script’s execution
Such as comment and shift, and climate_data (which is a reference to our open data file). We don’t have many at the moment
It also distinguishes between local variables and global variables - this is to do with the “scope” of the variables, as to how they are accessible from this point in the running of the code
Global variables can be seen from anywhere in the script
And local variables are those that are visible from this point of the program
If we were within a function here, we would see variables that are defined and only used within that function as local variables only
for example, if we set a breakpoint within the FahrToKelvin function,
we would see “kelvin” as a local variable, but it wouldn’t be listed as a global variable 
We can also see a call stack, which is a record of the journey the script has taken, in terms of functions called, to get to this position
It shows us that we are at the top level of our script
Which makes sense, since our breakpoint is at the top level of script
And not within any function. If it were within the FahrToKelvin function, for example, we’d see that added to the call stack
Now, we can also see some new icons at the top to do with debugging
The first one, is continue - it allows the script to keep running until the next breakpoint
The next one allows us to step over - or through - the script one statement at a time
The next two allow us to choose to step into or out of a function call, which is interesting. If we want to examine the inner workings of a function during this debug session, we can do that
The green cycle one is to restart the debug process
And the red cross stops debugging completely
So let’s step through our code, and see what happens
As we do so, we can see the variable state changing
We can now see that the line variable contains the first line read from the data file
By looking in the variables section
On the next step, we’ve reached the if statement
If we step again, and then again, our program halts because it’s run into the problem we saw before
Now this tells us something
It tells us that the problem occurs in the first iteration of the loop
So, this implies, the problem might be with the first line of data being processed
If we re-run the debugger, by selecting the green cycle, we can do it again
And we can see something interesting when we get to the if statement
We know that the if statement is looking for an exclamation mark at the beginning of the line to indicate a comment
However, the data variable contains a ‘#’ as the first character instead
So in this case, the code will assume it’s a data line and attempt to process it as such
And then it will fail with the exception we saw before
So - we’ve identified the problem! Now let’s fix it
Firstly, stop the debug process by selecting the red square
Then edit the if line to search for ‘COMMENT’ instead
We can then rerun the debugger if we wish, to check our understanding
And as we step through the code, we can see if correctly identifies the first line as a comment, and ignores it, continuing to the iteration of the for loop, and the next line of data
[Stop the debugger]
We’ve now solved our problem, so we should remove the breakpoint
Running our code again as normal, we can see it seems to work. Problem fixed!
So debugging code is a useful feature
And let’s set it in context with other practices of software development
Typically, we’d use debugging when we’ve discovered a problem
Those of you who attended the Byte-sized RSE session on testing, may remember we looked at using unit testing to check our programs behaved as we intended
i’ve put a link to a guide that introduces unit testing into the googledoc if you’re interested
and looks at the kinds of things we looked at in that session
By writing test cases as bits of code to check functions produced results with certain inputs
This was great at helping us discover the presence of problems with our code
But only told us there was a problem - it doesn’t tell us where
Well, debugging is the next step of that process
Sometimes, we discover a problem - perhaps our unit tests show us there’s an issue
Or maybe we find out some other way
If we’re lucky, we can identify and fix the problem quickly
Where we can’t, debugging is there to help us
With particularly complex programs, it can be very difficult to reason about how they work, and where the problem are
Debugging allows us to pick apart that process, and step by step, help us find the source of those issues

::::::::::::::::::::::::::::::::::::: keypoints 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

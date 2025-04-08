---
title: "2.2 Some Example Code"
teaching: 10
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

## Obtaining Some Example Code

FIXME: copy code-style-example into softwaresaved org

For this lesson we'll be using some example code available on GitHub,
which we'll clone onto our machines using the Bash shell.
So firstly open a Bash shell (via Git Bash in Windows or Terminal on a Mac). Then, on the command line, navigate to where you'd like the example code to reside,
and use Git to clone it.
For example, to clone the repository in our home directory:

```bash
cd
git clone https://github.com/UNIVERSE-HPC/code-style-example
```


## Examining the Code

Next, let's take a look at the code, which is in the root directory of the repository in a file called `climate_analysis.py`.

```python
import string


shift = 3
comment = '#'
climate_data = open('data/sc_climate_data_10.csv', 'r')

def FahrToCelsius(fahr):
    celsius = ((fahr - 32) * (5/9)) 
    return celsius
def FahrToKelvin(fahr):
    kelvin = FahrToCelsius(fahr) + 273.15
    return kelvin



for line in climate_data:
    data = line.split(',')
    if data[0][0] != comment:
        fahr = float(data[3])
        celsius = FahrToCelsius(fahr)
        kelvin = FahrToKelvin(fahr)
        print('Max temperature in Celsius', celsius, 'Kelvin', kelvin)
```

The code is designed to process temperature data from a separate data file.
The code reads in data line by line from the data file, and prints out fahrenheit temperatures in both celsius and kelvin.

The code expects to find the data file `sc_climate_data_10.csv` (formatted in the Comma Separated Value CSV format) in the `data` directory,
and looks like this:

```text
# POINT_X,POINT_Y,Min_temp_Jul_F,Max_temp_jul_F,Rainfall_jul_inch
461196.8188,1198890.052,47.77,58.53,0.76
436196.8188,1191890.052,47.93,58.60,0.83
445196.8188,1168890.052,47.93,58.30,0.74
450196.8188,1144890.052,48.97,56.91,0.66
329196.8188,1034890.052,49.26,59.86,0.78
359196.8188,1017890.052,49.39,58.95,0.70
338196.8188,1011890.052,49.28,58.73,0.74
321196.8188,981890.0521,48.20,61.41,0.72
296196.8188,974890.0521,48.07,61.27,0.78
299196.8188,972890.0521,48.07,61.41,0.78
```

It contains a number of lines, each containing a number of values, each separated by a comma.
There's also a comment line at the top, to tell us what each column represents.

Now let's take a look at the Python code,
using any text or code editor you like to open the file.
You can also use `nano` if you'd prefer to use the command line, e.g.

```bash
cd code-style-example
nano climate-analysis.py
```

The code opens the data file, and also defines some functions to do two temperature conversions from Fahrenheit to Celsius and Fahrenheit to Kelvin.
Note that for the purposes of this lesson,
the code is deliberately written to contain some issues!

## Why Write Readable Code?

QUESTION: who has seen or used code that looks like this? Yes/No?
QUESTION: who has written code like this? Yes/No

No one writes great code that's readable, well formatted, and well designed all the time.
Sometimes you often need to explore ideas with code to understand how the code should be designed,
and this typically involves trying things out first.
But... the key is that once you understand how to do something,
it's a good idea to make sure it's readable and understandable by other people,
which may includes a future version of yourself,
6 months into the future.
So it's really helpful to end up with good clean code so yit's easier to understand.

Another key benefit to writing "cleaner" code is that its generally easier to extend and otherwise modify in the future.
When code is initially written it's often impossible to tell if it will be reused in some way elsewhere.
A familiar scenario is that you stop developing a piece of code for a while,
and put it to one side.
Maybe it's not needed any more,
or perhaps a project has finished.
You forget about it, until suddenly, there's a need to use the code again.
Maybe all of it needs to be reused in another project,
or maybe just a part of it.
However, you come back to your code, and it's a mess you can't understand.
But by spending a little time now to write good code *while you understand it*,
you can save yourself (and possibly others) a lot of time later!

:::::::::::::::::::::::::::::::::::::::::  callout

## Does my Code Smell?

Developers sometimes talk about “code smells”.
Code smells are cursory indications from looking at the source code that a piece of code may have some deeper issues.
And looking at this code, it smells pretty terrible.
For example, we can see that there is inconsistent spacing, with lines bunched together in some places, and very spread out in others.
This doesn't engender a great deal of confidence that the code will work as we expect,
and it raises the question that if the style of the code appears rushed, what else has been rushed?
How about the design of the code?
Something to bear in mind when writing code!

::::::::::::::::::::::::::::::::::::::::::::::::::

## Running the Example Code

Now despite the issues with the code, does it work?
Let's find out.
So in the shell, in the root directory of the repository:

```bash
python climate_analysis.py
```

```output
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
```

And we can see that the code does indeed appear to work,
with celsius and kelvin values being printed to the terminal.
But how can we improve its readability?
We'll use a special tool, called a code linter,
to help us identify these sorts of issues with the code.

::::::::::::::::::::::::::::::::::::: keypoints 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

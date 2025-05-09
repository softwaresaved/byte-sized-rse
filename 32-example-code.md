---
title: "3.2 Some Example Code"
teaching: 10
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- What are Git "branches"?
- Why should I separate different strands of code work into "feature branches"?
- How should I capture problems with my code that I want to fix?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Obtain example code used for this lesson
- List the issues with the example code
- Describe the limitations of using a single branch on a repository
- Create issues on GitHub that describe problems that will be fixed throughout the lesson

::::::::::::::::::::::::::::::::::::::::::::::::

## Creating a Copy of the Example Code Repository

FIXME: copy git-example repo into softwaresaved

For this lesson we'll need to create a new GitHub repository based on the contents of another repository.

1. Once logged into GitHub in a web browser,
go to https://github.com/UNIVERSE-HPC/git-example.
1. Select 'Use this template', and then select 'Create a new repository' from the dropdown menu.
1. On the next screen, ensure your personal GitHub account is selected in the `Owner` field, and fill in `Repository name` with `git-example`.
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
git clone https://github.com/github-account-name/git-example
cd git-example
```

## Examining the Code

Let's first take a look at the example code on GitHub,
in the file `climate_analysis.py`.

```python
SHIFT = 3
COMMENT = '#'
climate_data = open('data/sc_climate_data_10.csv', 'r')


def FahrToCelsius(fahr):
    """COnverts fahrenehit to celsius

    Args:
        fahr (float): temperature in fahrenheit

    Returns:
        float: temperature in Celsius
    """
    celsius = ((fahr - 32) * (5/9)) 
    return celsius
def FahrToKelvin(fahr):
    kelvin = FahrToCelsius(fahr) + 273.15
    return kelvin



for line in climate_data:
    data = line.split(',')
    if data[0][0] != COMMENT:
        fahr = float(data[3])
        celsius = FahrToCels(fahr)
        kelvin = FahrToKelvin(fahr)
        print('Max temperature in Celsius', celsius, 'Kelvin', kelvin)
```

If you have been through previous Byte-sized RSE episodes,
you may have already encountered a version of this code before!

It's designed to perform some temperature conversions from fahrenheit to either celsius or kelvin,
and the code here is for illustrative purposes.
If we actually wanted to do temperature conversions,
there are at least three existing Python packages we would ideally use instead that would do this for us (and much better).
Similarly, this code should also use a library to handle the CSV data files,
as opposed to handling them line by line itself.

There are also a number of other rather large issues (which should be emphasised is deliberate!):

- The code is quite untidy, with inconsistent spacing and commenting which makes it harder to understand.
- It contains a hardcoded file path,
as opposed to having them within a separate configuration file or passed in as an argument.
- Function names are capitalised - perhaps we need to change these to be lower case, and use underscores between words - a naming style also known as snake case.
- The code is also some comments (known as docstrings) describing the function and the script (or module) itself.
For those that haven't encountered docstrings yet,
they are special comments described in a particular format that describe what the function or module is supposed to do.
You can see an example here in the `FahrToCelsius` function,
where the docstring explains what the function does,
its input arguments, and what it returns.
- An incorrect function name `FahrToCels`, which should be `FahrToCelsius`. This will cause it to fail if we try to run it.

Another thing to note on this repository is that we have a single main branch (also used to be called a master branch which you may see in older repositories).
You'll also notice some commits on the main branch already.
One way to look at this is as a single "stream" of development.
We've made changes to this codebase one after the other on this main branch,
however, it might be that we may want to add a new software feature, or fix a bug in our code later on.
This may take, maybe, more than a few commits to complete and make it work, perhaps over a matter of hours or days.
Of course, as we make changes to make this feature work, the commits along the way may well break the "working" nature of our repository
and after that,
users getting hold of our software by cloning the repo,
also get a version of the software that then isn't working.
This is also true for developers as well:
for example, it's very hard to develop a new feature for a piece of software if you don't start with software that is already working.
The problem would also become compounded if other developers become involved,
perhaps as part of a new project that will develop the software.
What would be really helpful would be to be able to do all these things whilst always maintaining working code in our repository.
Fortunately, version control allows us to create and use *separate branches* in addition to the main branch, 
which will not interfere with our working code on the main branch.
Branches created for working on a particular feature are typically called *feature branches*.

## Create Example Issues

Before we look into branches,
let's create a few new issues on our repository,
to represent some work we're going to do in this session.

One thing that might be good to do is to tidy up our code.
So let's add issues to fix that script function naming bug,
changing our function names to use snake case,
and add the missing docstrings.

Let's create our first issue about using snake case:

1. Go to your new repository in GitHub in a browser, and select `Issues` at the top.
You'll notice a new page with no issues listed at present.
1. Select `New issue`.
1. On the issue creation page, add something like the following:
   - In the title add: Functions should use snake case naming style
   - In the description add: Naming of functions currently is using capitalisation, and needs to follow snake case naming instead.
1. We can also assign people to this issue (in the top right),
and for the purposes of this activity,
let's assign ourselves,
so select `Assign yourself`.
1. Select `Create` to create the issue.

:::: challenge

## Adding Work for Ourselves

Repeat this process for the other two issues in the following order:
- "Add missing docstrings to function and module"
- "Script fails with undefined function name error"
We'll refer back to these issues later!

::::

QUESTION: who's created the three issues? Yes/No


::::::::::::::::::::::::::::::::::::: keypoints 

- Using Git branches helps us keep different strands of development separated, so development in one strand doesn't impact and confuse development in the others
- Branches created to work specifically on a particular code feature are called *feature branches*
- GitHub allows us to capture, describe and organise issues with our code to work on later

::::::::::::::::::::::::::::::::::::::::::::::::

---
title: "1.3 Using the Code Editor"
teaching: 10
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

Now we've acquainted ourselves with running VSCode, let’s take a look at our example code.
Note that as an example, it’s deliberately written to have flaws.
Things like the line spacing is inconsistent, there are no code comments, there’s a variable that’s not used, and you may spot other issues too.
But in essence, the code is designed to do the following:

1. Open a file in the CSV (comma separated value) format
1. Go through the file line by line, and:
   - If the line begins with a `#` symbol, ignore it.
   - Otherwise, extract the fourth column (which is in Fahrenheit), convert it to Celsius and Kelvin, and output those readings.

Let’s take a look at some of what the code editor gives us.
You’ll notice that the Python syntax is being highlighted for us, which helps readability
Here, it uses colour to distinguish the various parts of our program
functions are yellow, Python statements are purple, variables are light blue, and strings are this reddy-orange, and so on
Which, perhaps unsurprisingly, is a feature known as Syntax Highlighting, and it’s possible to edit the colour scheme to your liking for a particular language if you like, although we won’t go into that now
This is really handy to give you immediate feedback on what you are typing, and can help you to identify common syntax mistakes
for example, deleting the closing parenthesis on ‘open’ - the opening one goes red, with a squiggly line underneath, indicating an issue
So this is great, and helps us understand what we are writing, and highlights some mistakes. But we can take it further
If you were here for the last Byte-sized RSE session, you may remember we looked at using what’s known as a code linter tool to check our code for deeper issues, and suggest common conventions to make our code more readable
The good news is that we can install a Python linter in VSCode to give us similar functionality,  by installing a linter extension
So let’s go to extensions, and search for “pylint”, the one by microsoft, and click install


Now, let’s go back to our code
You may find lots of squiggly underlines
But if you don’t, in order to trigger the linter to show us further issues, I usually find saving a file triggers the linter to examine our code
So go to File -> Save on the menu bar, and you should see a lot of squiggly underlines in our code
These squiggly lines indicate an issue - by hovering over them, we can see details of the issue
For example, by hovering over
“shift” or “comment” - we can see that the variable names don’t conform to what’s known as an UPPER_CASE naming convention
Simply, the linter has identified these variables as constants, and typically, these are in upper case. We should rename them like this [demo]
But we also need to update the reference to lower case comment in the code [demo]
Now if we save the file (File -> Save), we should see the linter rerun, and those issues disappear
We can also see a comprehensive list of all the issues found, by opening a Problems window
In the menu, go to View -> Problems, then you’ll see a complete list of issues which we can work on
We don’t have to, of course, but by following them we bring our code style closer to a commonly accepted form of Python
It also picks up things like functions missing docstrings - we’ll look at this later
For now, we can close the Problems window
Something that’s also useful is VSCode’s ability to help you format your code whilst you’re typing
For example, “for x in something:” [show indentation]
On the next line, we can see that it’s automatically indented it for us, knowing that we’re inside a loop
[Delete for added loop]
Another really helpful feature is something known as code completion (in VSCode, this is referred to as IntelliSense)
This is a great time saver, and a really useful feature of IDEs
Essentially, as you type, it works out the context of what you are doing, and gives you hints
For example, if we start typing a variable we’ve already defined, for example “climate_data”, we can see that it’s zeroing in as we type on the options for what we might be after. When we see “climate_data”, we can press “Tab” to complete it for us
As another example, if I wanted to open another file: “new_file = open(“ - it provides information on the “open” command and its arguments, along with a description of what it does [scroll down]
So, we don’t have to take the time to look all this information up on the web, for example
Autodocstring
Something we noted earlier, in the list of issues with our code, was the lack of docstrings
If we want to write good code, we should be adding code comments, including docstrings for our functions, methods, and modules 
Well, it sure would be nice if there was something to add in docstrings for us. Let’s try and find an extension that might help us
Select the extensions icon, and type “docstring” - you should see “autodocstring” at the top
Select that, and you’ll see a page outlining what it is
Also note it’s very widely used - 4.6M downloads
What’s really handy is the little video that shows us what it does
This looks exactly like what we’re after!
Select install
Now, when we go to a function for example, go to the next line, and add “””, we’ll see a small pop-up to add a docstring - press Tab to do so
It does all the hard work of adding in the structure of a docstring for us, so we just need to fill in the blanks
This is another good example of us realising it would be nice to have something to help us, searching for an extension, and trying it out
If we bring up the explorer sidebar, we can see an Outline of our code, which helps us to navigate around larger code files quickly, by double clicking on the items
And for those of you familiar with version control, there are some other editor features that help with this
One of these is that the filename changes colours in the file explorer
white (means the file is unchanged from the copy in the local repository), orange (means its changed), or if it’s red, it indicates that there’s a code problem somewhere
There’s also the timeline, which shows you a history of what’s happened to this workspace
In terms of commits to it within the repository, in this case, only an initial commit of our files, and also some local changes as we’ve saved the file

So in summary, many of these editing features are typical of IDEs in general
The great thing is that they are helpful at saving us time
Things like syntax highlighting, code completion, automatic code formatting and inserting docstrings, may not seem like much, but it all adds up
As you get more familiar with these features, writing code just becomes quicker and more pleasant

::::::::::::::::::::::::::::::::::::: keypoints 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

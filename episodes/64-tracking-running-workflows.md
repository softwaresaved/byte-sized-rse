---
title: "6.4 Tracking a Running Workflow"
teaching: 10
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

## Checking a Running Workflow

We've committed our workflow,
so how do we know its actually running?
Since the workflow is triggered on each `git push`,
if we go back to our main repository page,
we should see an orange circle next to the most recent commit displayed just above the directory contents.

FIXME: add screenshot of main page with orange CI running marker

When this workflow is complete, it will display either a green tick for success,
or a red cross if the workflow encountered an error.
You can also see a history of the past workflow runs' failures or successes for each workflow run triggered on the commits page,
by selecting `Commits` on the right of this most recent commit display.

FIXME: add screenshot of commits page with a single workflow result entry

For more detail we can check the progress of a running workflow by selecting `Actions` in the top navigation bar (e.g. https://github.com/steve-crouch/ci-example/actions).
We can see here that a new run has started,
titled with our commit message.
This page also shows a historical log of any other previous workflow runs too.

We can also view a complete log of the output from workflow runs,
by selecting the first (and only) entry at the top of the list.
This will then display a list of our `job`s (in this case only `build-and-test`).
If we select `build-and-test` we'll see an in-progress log of our workflow run,
separated into separate collapsed steps that we may expand to view further detail.
Each of the steps is named from the `name` labels we gave each step.
Note that the workflow may still be running at this point,
so not all steps may be complete yet.

FIXME: show workflow log of completed run

If we drill down by selecting the `Test with pytest` entry,
we'll get a breakdown of the thing we're really interested in:

```output
Run python -m pytest -v tests/test_factorial.py
============================= test session starts ==============================
platform linux -- Python 3.11.12, pytest-7.2.0, pluggy-1.0.0 -- /opt/hostedtoolcache/Python/3.11.12/x64/bin/python
cachedir: .pytest_cache
rootdir: /home/runner/work/ci-example2/ci-example2
collecting ... collected 3 items

tests/test_factorial.py::test_3 PASSED                                   [ 33%]
tests/test_factorial.py::test_5 PASSED                                   [ 66%]
tests/test_factorial.py::test_negative PASSED                            [100%]

============================== 3 passed in 0.01s ===============================
```

Which shows us that our tests were successful!

## Triggering our Workflow with Code Changes

Now if we make a change to our code, our workflow will be triggered and these tests will run,
so let’s make a change.

In GitHub (or on the command line if you prefer),
edit the source code file `mymath/factorial.py`,
add an additional line before `return factorial`.
Then save the file (if editing locally), and commit the change.

If we return to the GitHub Actions workflow list and select the most recent workflow run,
we should see the workflow execute successfully as before - so we know our change hasn't broken anything.

## Summary

Our workflow will now be triggered every time a change to our code is pushed to our GitHub repository,
which means that our code is now always being checked against our tests.
Although we must remember to check the workflow log for this to have value. 
We also need to be sure that our tests sufficiently verify the behaviour of our code as it evolves,
so we should ensure we update our tests as necessary,
and adding new tests as required to verify new functionality.

::::::::::::::::::::::::::::::::::::: keypoints 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

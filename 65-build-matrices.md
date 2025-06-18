---
title: "6.5 Build Matrices"
teaching: 10
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

## Running Workflows over Multiple Platforms

So far, every time our workflow is triggered, it runs over a single operating system, Ubuntu.
From an automation perspective this is incredibly helpful,
since although running our unit tests is a quick process,
by automating it this cumulative savings in time becomes considerable.
However, what if we wanted to test our code across different versions of Python installed on different platforms,
such as Windows and Mac OS?
Let's look at a feature called build matrices which allows us to do this,
and really show the value of using CI to test code at scale.

Suppose the intended users of our software use either Ubuntu, Mac OS, or Windows,
and have Python versions 3.10 through 3.12 installed,
and we want to support all of these.
Assuming we have a suitable test suite,
it would take a considerable amount of time to set up testing platforms to run our tests across all these platform combinations.
Fortunately, CI can do the hard work for us very easily.

First, let's update our workflow to specify which platforms and Python versions we wish to run,
by adding/changing the following where `runs-on` is defined:

```yaml
    strategy:
      matrix:
        os: ["ubuntu-latest", "macos-latest", "windows-latest"]
        python-version: ["3.10", "3.11", "3.12"]

    runs-on: ${{ matrix.os }}
```

Here we define a build matrix that specifies each of the `os` and `python-version` we want to test,
such that new jobs will be created that run our tests for every permutation of these two variables.
So, we should expect 9 jobs to run in total.

We also change `runs-on` to refer to the `os` component of our `matrix`,
using `{{ }}` as a means to reference these values.

Similarly, we need to update our Python setup section to make use of the `python-version` component of our build matrix:

```yaml
    - name: Set up Python ${{ matrix.python-version }}
      uses: actions/setup-python@v5
      with:
        python-version: ${{ matrix.python-version }}
```

Once we've saved our workflow, commit the changes to the repository as before.

If we view the most recent GitHub Actions workflow run,
we should see that a new job has been created for each of the 9 permutations.

FIXME: add GA screenshot showing all 9 permutations running

Note all jobs are running in parallel (up to the limit allowed by our account) which potentially saves us a lot of time waiting for testing results.
Therefore overall, this approach allows us to massively scale our automated testing across platforms we wish to test.

## Failed CI Builds

A CI build can fail when, e.g. a used Python package no longer supports a particular version of
Python indicated in a GitHub Actions CI build matrix.
In this case, the solution is either to upgrade the Python version in the build matrix (when possible),
or to downgrade the package version (and not use the latest one like we have been doing in this course).

Also note that, if one job fails in the build for any reason,
all subsequent jobs will get cancelled because of the default behavior of
GitHub Actions.
From [GitHub's documentation](https://docs.github.com/en/actions/using-jobs/using-a-matrix-for-your-jobs#handling-failures):

*GitHub will cancel all in-progress and queued jobs in the matrix if any job in the matrix fails.*
This behaviour can be controlled by changing the value of the `fail-fast` property in the `strategy` section:

```yaml
...
   strategy:
     fail-fast: false
     matrix:
...
```

This would ensure that all matrix jobs will be run to completion regardless of any failures,
which is useful so that we are able to identify and fix all failures at once,
as opposed to having to fix each in turn.

::::::::::::::::::::::::::::::::::::: keypoints 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

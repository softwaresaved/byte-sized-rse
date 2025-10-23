---
title: "6.3 Defining a Workflow"
teaching: 10
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

## How to Describe a Workflow?

Now before we move on to defining our workflow in GitHub Actions,
we'll take a very brief look at a language used to describe its workflows,
called YAML.

Originally, the acronym stood for *Yet Another Markup Language*,
but since it's not actually used for document markup,
it's acronym meaning was changed to *YAML Aint Markup Language*.

Essentially, YAML is based around key value pairs, for example:

```yaml
name: Kilimanjaro
height_metres: 5892
first_scaled_by: Hans Meyer
```

Now we can also define more complex data structures too.
Using YAML arrays, for example,
we could define more than one entry for `first_scaled_by`,
by replacing it with:

```yaml
first_scaled_by:
  - Hans Meyer
  - Ludwig Purtscheller
```

Note that similarly to languages like Python,
YAML uses spaces for indentation (2 spaces is recommended).
Also, in YAML, arrays are sequences,
where the order is preserved.

There's also a short form for arrays:

```yaml
first_scaled_by: [Hans Meyer, Ludwig Purtscheller]
```

We can also define nested, hierarchical structures too, using YAML *maps*.
For example:

```yaml
name: Kilimanjaro
height:
  value: 5892
  unit: metres
  measured:
    year: 2008
    by: Kilimanjaro 2008 Precise Height Measurement Expedition
```

We are also able to combine maps and arrays,
for example:

```yaml
first_scaled_by:
  - name: Hans Meyer
    date_of_birth: 22-03-1858
    nationality: German
  - name: Ludwig Purtscheller
    date_of_birth: 22-03-1858
    nationality: Austrian
```

So that's a very brief tour of YAML,
which demonstrates what we need to know to write GitHub Actions workflows.

## Enabling Workflows for our Repository

So let's now create a new GitHub Actions CI workflow for our new repository that runs our unit tests whenever a change is made.

Firstly, we should ensure GitHub Actions is enabled for repository.
In a browser:

1. Go the main page for the `ci-example` repository you created in GitHub.
1. Go to repository `Settings`.
1. From the sidebar on the left select `General`, then `Actions` (and under that, `General`).
1. Under `Actions permissions`, ensure `Allow all actions and reusable workflows` is selected,
otherwise, our workflows won't run!

## Creating Our First Workflow

Next, we need to create a new file in our repository to contain our workflow,
and it needs to be located in a particular directory location.
We'll create this directly using the GitHub interface,
since we're already there:

1. Go back to the repository main page in GitHub.
1. Select `Add file` (you may need to expand your browser Window to see `Add file`) then `Create new file`.
1. We need to add the workflow file within two nested subdirectories,
since that's where GitHub will look for it.
In filename text box, add `.github` then add `/`.
This will allow us to continue adding directories or a filename as needed.
1. Add `workflows`, and `/` again.
1. Add `main.yml`.
1. Should end up with `ci-example / .github / workflow / main.yml in main` in the file field.
1. Select anywhere in the `Edit new file` window to start creating the file.

Note that GitHub Actions expects workflows to be contained within the `.github/workflows` directory.

Let's build up this workflow now.

### Specify Workflow Name and When it Runs

So first let's specify a name for our workflow that will appear under GitHub Actions build reports,
and add the conditions that will trigger the workflow to run:

```yaml
name: run-unit-tests

on: push
```

So here our workflow will run when changes are pushed to the repository.
There are [other events](https://docs.github.com/en/actions/writing-workflows/choosing-when-your-workflow-runs/events-that-trigger-workflows) we might specify instead (or as well) if we wanted,
but this one is the most common.

### Specify Structure to Contain Steps to Run on which Platform

GitHub Actions are described as a sequence of jobs (such as building our code, or running some tests),
and each job contains a sequence of steps
which each represent a specific "action" (such as running a command, or obtaining code from a repository).

Let's define the start of a workflow job we'll name `build-and-test`:

```yaml
jobs:

  build-and-test:

    runs-on: ubuntu-latest
```

We only have one job in this workflow,
but we may have many.
We also specify the operating systems on which we want this job to run.
In this case, only the latest version of Linux Ubuntu,
but we could supply others too (such as Windows, or Mac OS) which we'll see later.

When the workflow is triggered,
our job will run within a `runner`,
which you can think of as a freshly installed instance of a machine running the operating system we indicate (in this case Ubuntu).

## Specify the Steps to Run

Let's now supply the concrete things we want to do in our workflow.
We can think of this as the things we need to set up and run on a fresh machine.
So within our workflow, we'll need to:

- Check out our code repository
- Install Python
- Install our Python dependencies (which is just `pytest` in this case)
- Run `pytest` over our set of tests

We can define these as follows:

```yaml
    steps:

    - name: Checkout repository
      uses: actions/checkout@v4

    - name: Set up Python 3.11
      uses: actions/setup-python@v5
      with:
        python-version: "3.11"
```

We first use GitHub Actions (indicated by `uses: actions/`),
which are small tools we use to perform something specific.
In this case, we use:

- `checkout` - to checkout the repository into our runner
- `setup-python` - to set up a specific version of Python

Note that the `name` entries are descriptive text and can be anything,
but it's good to make them meaningful since they are what will appear in our build reports as we'll see later.

```yaml
    - name: Install Python dependencies
      run: |
        python3 -m pip install --upgrade pip
        pip3 install -r requirements.txt

    - name: Test with pytest
      run: |
        python -m pytest -v tests/test_factorial.py
```

Here we use two `run` steps to run some specific commands,
to install our python dependencies and run `pytest` over our tests,
using `-v` to request verbose reporting.

:::::::::::::::::::::::::::::::::::::::::  callout

## What about other Actions?

Our workflow here uses standard GitHub Actions (indicated by `actions/*`).
Beyond the standard set of actions,
others are available via the
[GitHub Marketplace](https://docs.github.com/en/developers/github-marketplace/github-marketplace-overview).
It contains many third-party actions (as well as apps)
that you can use with GitHub for many tasks across many programming languages,
particularly for setting up environments for running tests,
code analysis and other tools,
setting up and using infrastructure (for things like Docker or Amazon's AWS cloud),
or even managing repository issues.
You can even contribute your own.

::::::::::::::::::::::::::::::::::::::::::::::::::

## Adding our Workflow to our Repository

So once we've finished adding in our workflow to the file,
we commit this into our repository:

1. In the top right of the editing screen select `Commit changes...`.
1. Add in a commit message, e.g. “Initial workflow to run tests on push”.
1. Select `Commit changes`.

This commit action will now trigger the running of this new workflow,
since that's what the workflow is designed to do.

::::::::::::::::::::::::::::::::::::: keypoints 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

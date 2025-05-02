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
we’ll take a very brief look at a language used to describe its workflows,
called YAML.

Originally, the acronym stood for *Yet Another Markup Language*,
but since it’s not actually used for document markup,
it’s acronym meaning was changed to *YAML Aint Markup Language*.

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

So that’s a very brief tour of YAML,
which demonstrates what we need to know to write GitHub Actions workflows.

## Enabling and Creating Our First Workflow

So let’s now create a new GitHub Actions CI workflow for our new repository that runs our unit tests whenever a change is made.

Firstly, we should ensure GitHub Actions is enabled for repository.
In a browser:

1. Go the main page for the `ci-example` repository you created in GitHub.
1. Go to repository `Settings`.
1. From the sidebar on the left select `General`, then `Actions` (and under that, `General`).
1. Under `Actions permissions`, ensure `Allow all actions and reusable workflows` is selected,
otherwise, our workflows won’t run!

Next, we need to create a new file in our repository to contain our workflow,
and it needs to be located in a particular directory location.
We'll create this directly using the GitHub interface,
since we're already there:

1. Go back to the repository main page in GitHub.
1. Select `Add file` then `Create new file`.
1. We need to add the workflow file within two nested subdirectories,
since that’s where GitHub will look for it.
In filename text box, add `.github` then add `/`.
This will allow us to continue adding directories or a filename as needed.
1. Add `workflows`, and `/` again.
1. Add `main.yml`.
1. Should end up with `ci-example / .github / workflow / main.yml in main`
1. Select in the `Edit new file` window to start creating the file.

Let's build up this workflow now.

FIXME: turn the below into a step-by-step learning narrative, explaining each bit

```yaml
name: run-unit-tests

# We can specify which Github events will trigger a CI build
on: push

# now define a single job called 'build' (but could define more)
jobs:

  build:

    # we can also specify the OS to run tests on
    runs-on: ubuntu-latest

    # a job is a seq of steps
    steps:

    # Next we need to checkout our repository, and set up Python
    # A 'name' is just an optional label shown in the log - helpful to clarify progress - and can be anything
    - name: Checkout repository
      uses: actions/checkout@v3

    - name: Set up Python 3.10
      uses: actions/setup-python@v4
      with:
        python-version: “3.10”

    - name: Install Python dependencies
      run: |
        python3 -m pip install --upgrade pip
        pip3 install -r requirements.txt

    - name: Test with pytest
      run: |
        python -m pytest tests/test_factorial.py
```

So once we’ve done that, we commit this new workflow file into our repository.
At the bottom of the editing screen:

1. Add in a commit message, e.g. “Initial workflow to run tests on push”.
1. Select `Commit new file’.

This commit action will now trigger the running of this new workflow,
since that’s what the workflow is designed to do.

::::::::::::::::::::::::::::::::::::: keypoints 

- FIXME

::::::::::::::::::::::::::::::::::::::::::::::::

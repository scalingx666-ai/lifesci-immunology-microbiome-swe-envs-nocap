# Issue

**Title:** Separate support files copying from HTML formatting and doc improvements

## Description

Separate the operation that copies the support files from the operation
that formats the HTML file to display the plot. The reason why this is
useful is for example to test (see the changes in build.py), you no longer
need to regenerate the `new-emperor.html` file every time you make a change
in the JavaScript source, instead it can simply link to the original
support files.

I also changed the proportions displayed to be percentages instead.

Additionally I made some changes to the documentation to make use of
backticks.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `77c86c6da2b3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
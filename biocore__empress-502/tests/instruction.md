# Issue

**Title:** BLD: Small tweaks to GH Actions workflows

## Description

Nothing big, just some small fixes that should make development easier.

- Remove Node.js matrix for main CI, since the version number is hard-coded currently; this should remove the need to click through multiple pages when accessing the main CI (edit: actually maybe you still need to click through things twice, hm. at least it should simplify the code.)
  - In the future we could add back this matrix and use it to try multiple Node.js versions -- however I don't think it's an urgent priority, since Node.js is only used on the development side (so being exhaustive about versions working probably isn't too important, at least compared to Python versions in the standalone CI)
  - Another concern here is that trying multiple Node.js versions should probably be a separate process from installing/testing the Python code; I think the most efficient way to set this up this would be something like adding a different workflow for JS testing, then adding _another_ workflow for uploading to McHelper that is dependent on both the "JS testing" and "Python testing" workflows passing [but IDK how to do that right now]

- Make some documentation consistent btwn YAML files (e.g. Empress -> EMPress)

- Remove the "Empress" from the workflow names, renaming them to just "Main CI" and "Standalone CI" -- I think this makes the README badges/etc. easier to interpret

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `33ade9ca4778`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
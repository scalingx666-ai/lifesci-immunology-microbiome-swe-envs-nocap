# Issue

**Title:** try and use importlib where possible

## Description

Hey Scott,

I was just installing your new version in my new environment in Python 3.12.
I noticed that pkg_resources was missing from the installation causing a ModuleNotFoundError.
This could be fixed by running `pip install setuptools` but still gives a deprecation warning.
I tried to changing to importlib as the docs suggest, but the files API is missing from older versions of Python (3.8 for sure haven't checked the others).
This could be a workaround for all currently tested version and at some point you can drop the try/except clause.
I also tried what the comment suggested with the special characters, and it didn't raise any errors for me so I went ahead and removed that section.
Let me know what you think :)

Best,
Tristan

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c5e79dcf3319`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
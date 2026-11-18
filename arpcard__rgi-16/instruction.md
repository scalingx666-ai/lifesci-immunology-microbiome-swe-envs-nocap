# Issue

**Title:** Flexible python3 shebang for cli entrypoint

## Description

To accommodate use of virtual environments and different python install paths.

Upon install into virtual environment I wasn't able to immediately use the rgi command.  Changing the shebang allowed for more flexible use.

See "Impact on Script Launching": https://www.python.org/dev/peps/pep-0486/

Optional: use agnostic python instead of python3; except that python 3.6 is specified as a requirement.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `133e719db631`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
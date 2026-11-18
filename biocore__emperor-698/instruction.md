# Issue

**Title:** BUG: Fix a bug with the red-yellow-blue colormap

## Description

There was a typo in the name of the colormap that prevented the data
from being colored correctly.

## Before (notice the color selection menu)

<img width="1125" alt="screen shot 2018-10-03 at 5 24 20 pm" src="https://user-images.githubusercontent.com/375307/46446546-bc395900-c731-11e8-9d15-a6cc7e6e3f16.png">


## After

<img width="1114" alt="screen shot 2018-10-03 at 5 25 52 pm" src="https://user-images.githubusercontent.com/375307/46446550-c0657680-c731-11e8-87dc-e5090a98c252.png">

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `afcc45007716`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
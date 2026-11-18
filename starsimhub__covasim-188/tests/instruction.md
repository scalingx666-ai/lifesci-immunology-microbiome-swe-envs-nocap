# Issue

**Title:** Fix Edge error

## Description

Adds code that hopefully issues an appropriate warning for people using Edge. NOTE: I do not have Edge so I have not tested it, it's taken from:
https://vuejsdevelopers.com/2017/09/24/vue-js-single-file-javascript-components/

I think this is fine seeing as IE/Edge are ~2% of the global browser market share:
https://gs.statcounter.com/browser-market-share

Closes

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4c254e7e275c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
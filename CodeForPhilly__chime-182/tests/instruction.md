# Issue

**Title:** 112 model

## Description

sorry, this is all over the place 
- Jason and I decided  wasn't really on the mark by recommending objects rather than functions
- even then, i largely didn't touch the chain of function calls that is the model because i thought they were suffficient  
- snuck in some housekeeping -
- - `# type: ignore` annotation to imports
- - took charting functions out of `presentation.py` into `charts.py` 
- - more things i've forgotten about sorry
- - moved `build_*_df` funcs from `utils.py` into `models.py` because they have mathematical content. 
- *mainly what i did:* changed signatures from `*args` to `p: Parameters` wherever possible.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d6217750786d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
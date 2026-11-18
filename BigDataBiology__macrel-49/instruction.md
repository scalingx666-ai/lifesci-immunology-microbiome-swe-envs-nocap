# Issue

**Title:** Eliminate R dependencies and implement OOP in macrel features computation

## Description

The new version of macrel does change some probabilities (14/899) in the testing due to the rounding problem when transferring from R to python. However, no classification changed and the behavior is stable. Now it uses one additional module (database) to perform the calculation of the same features done before and I rewrote this new module to implement more object-oriented programing.

The simple use of the modlamp was not possible because it uses different scales and to make it ordered I rewrote some functions and others were just adapted.

The elimination of R dependency was cleaned in the testing and installing routines which reduced the time of CI testing to 5 min.

After the CLI testing, I checked that with the dependencies, Macrel package now is 200MB less heavy than before.

The changes made actually slow down the program, but not so drastically.

I tested with 1 million simulated peptides, to conclude the computation of the
features in the modified version and the original version the difference was barely 15 min:

| **method / time** | **modified version** | **original** |
| :---: | :---: | :---: |
| real | 78m 16.521s | 63m 37.135s | 
| user | 40m 30.502s | 40m 35.820s | 
| sys | 0m 8.305s | 0m 15.105s | 
    
Questions: 

**To be rebased (maybe some manual edits will be necessary)**

1. No problems, I am going to rebase it.

**The GPL issue needs to be clarified**

2. I modified the README and LICENSE files to incorporate this info

**I still prefer the older fasta.py to introducing the biopython dependency and see no argument for that change (and if there is an argument for that change, maybe do it as a separate PR so these things can be discussed separately)**

3. Reverted to fasta.py

**I am not a fan of the object-based interface (feels old-fashioned)...**

4. I just will keep the OOP architecture because I think it is encouraged in the new python version (3.10) and is easier to spot malfunctioning in the system. However, in the future, we always can revert it back.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `452e2edbbd90`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
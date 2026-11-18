# Issue

**Title:** Update lint-package.yml

## Description

`lintr` needs to be aware of all the functions from the package to avoid the `unknown global function` warning. 
This PR updates the `lintr` action 

It should fix [these warnings](https://github.com/EpiModel/EpiModel/runs/7416569905?check_suite_focus=true#step:5:15) in #751

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `44c270c41edf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
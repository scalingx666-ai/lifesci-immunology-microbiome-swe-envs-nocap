# Issue

**Title:** Use typer to manage CLI

## Description

This PR make use of Typer to have  fancy looking help section ! 

- Use this hack to allow multiple value on optional arguments : 
- It replaces also tqdm by rich progress bar. Add --no-progress option to disable progress bar
- Change verbose behavior. default logging level is set to INFO and  using `--verbose` sets it to DEBUG

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c481d7c1ead2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
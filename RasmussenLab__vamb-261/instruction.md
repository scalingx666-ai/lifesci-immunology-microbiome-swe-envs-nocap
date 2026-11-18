# Issue

**Title:** Use loguru as logging framework

## Description

Before, Vamb did not use a logging framework, but printed to a logfile, which was passed to every function that needed to log. This had several issues:
* Logging was only printed to the logfile, not stderr,
* Logging was hard to customize, since you needed to customize 100s of print statements instead of a central logger object
* Lots of functions needed to take a logger as an argument, when really a logger is global state and needs to be treated as such
* There were no timestamps in the logging

All of these points are now addressed.

## TODO
- [x] Format the logfile nicer

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `15638ffa8f30`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
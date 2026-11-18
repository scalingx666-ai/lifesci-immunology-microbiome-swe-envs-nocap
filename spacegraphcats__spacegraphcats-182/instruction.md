# Issue

**Title:** [MRG] add some workflow tests

## Description

This adds some actual tests of the new search workflow, and paves the way to adding some more. This is an imperfect start but at least makes sure that the most common scripts are executed :).

Specifically:
* The `dory` test is now run with code coverage.
* the `twofoo` test in the Makefile now does a full test of a real-ish workflow.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a99ed1b7b8f1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
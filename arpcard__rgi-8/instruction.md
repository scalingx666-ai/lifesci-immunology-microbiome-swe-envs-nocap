# Issue

**Title:** Argument parsing enhancements and data safety

## Description

Add a check that output and input don't have the same value when using
the clean option as this will result in clean deleting all the input
files

Move validation of options for aligner, data_type and input_type into
the argpaser itself using the choices kwarg.

Add type checking for certain options (e.g. check int input for threads
and making aligner, input_type options case insensitive)

Remove the now redundant help text specifying the options.

Remove redundant default values for required options

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `73c24b2db7ec`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
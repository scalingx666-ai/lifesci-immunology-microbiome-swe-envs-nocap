# Issue

**Title:** fix sub-directory path

## Description

This is a  

When I executed this code, I found that get_mount_point() returns complete paths, e.g. `/root/data/job` instead of "just" the sub-directory, i.e. `job`. Thus `get_support_file` returns the dst directory, instead of the src directory :-/

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0a29ac2ceba2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
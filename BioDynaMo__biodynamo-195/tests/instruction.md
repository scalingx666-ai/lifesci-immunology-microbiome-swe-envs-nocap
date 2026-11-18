# Issue

**Title:** Improve copy command for gtest files

## Description

On some systems copying $GTEST_SRC/include would not copy the
contents of the include directory, but rather the include
directory itself - resulting in: biodynamo/build/include/include

This would in return result in Cling not being able to find the
gtest headers and cause a segfault.

The improved copy command will always copy the contents correctly.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1b47940014db`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
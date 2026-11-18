# Issue

**Title:** Change prokka output

## Description

Changed what files from Prokka's output are retained. For all species reps, added ffn and gbk files to the output. For non-species reps in clusters, added ffn to the outputs.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a7b7320ba205`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Describe NCP in plain words and fix the docs footer

## Description

Retitles the NCP sections of the tools and plot API indices to "Patterns across patients, variables and time" with a one-sentence description, gives `tl.ncp` a matching plain-words summary line, and drops the doubled period in the docs footer.
Readers can now find `tl.ncp`, `pl.ncp` and `pl.ncp_cluster_trajectories` without knowing the name of the underlying decomposition.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6ef2ba54dbdc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** [MRG] add cdbg node annotations to multifasta query output

## Description

Addresses #420. I wanted a file that has the cdbg id mapped to the annotation that contains sequences in its nbhd.

Not sure if the naming scheme is sufficient, it was clear to me. 

I went for adding a separate file instead of combining all into one csv. Don't really care either way. 

@ctb ready for review and merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d0bc19138909`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
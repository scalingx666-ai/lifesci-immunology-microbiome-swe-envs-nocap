# Issue

**Title:** Add src/merge_aemb.py script to merge AEMB to abundance TSV

## Description

I'm generally wary of adding scripts, because they are hard to test. However, I'm making an exception here, because:
1. Creating the input abundance TSV file from --aemb inputs is the recommended way of creating abundances in Vamb, and it's important that it's easy
2. This script does not depend on Vamb and will not break when Vamb changes. In fact, it uses only numpy and stdlibs, and only reads and produces dirt simple, well-specified files making breakage unlikely.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3e135a3b10ac`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Parse Verkko-style TSV files of paths

## Description

and . This has the nice side effect of allowing multi-component paths (across all path filetypes, not just Verkko TSVs).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `88faf40bedf7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
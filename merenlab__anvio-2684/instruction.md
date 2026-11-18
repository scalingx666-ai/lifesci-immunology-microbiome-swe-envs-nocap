# Issue

**Title:** Allow user to set max reaction chain length for anvi-predict-metabolic-exchanges

## Description

This PR is related to  but is only a workaround for the memory issues described therein. It adds a new parameter to `anvi-predict-metabolic-exchanges` that exposes the `KGMLNetworkWalker`'s `max_reactions` parameter to the user.

When users set `--max-reactions-for-pathway-map-walk` (can use `--max-reactions` for short), the pathway map walk will artificially truncate after a given chain includes that many reactions. This means that the 'evidence' used to evaluate a given exchange is capped at a reaction chain length of this value.

It should be noted that the need to use this parameter indicates that something is likely going wrong with the Pathway Map walk, so it's best used with caution and as a workaround to things like memory issues from infinite cycles in the walk. I've included this warning explicitly in the help output.

I tested it on one of my problematic genomes that normally yields memory issues when walking pathway map 00061, and with `--max-reactions 20` it manages to finish without those problems:
```
anvi-predict-metabolic-exchanges -c1 GCA_002713325_1-contigs.db -c2 GCA_024276895_1-contigs.db -O test --max-reactions 20
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bab506a4faa6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** MRG: improve summary_csv for lingroups

## Description

- , needed for sankey plots from csv_summary w/ LINs and LINgroups #
- ref: 

- summary_csv: revert to lingroup LIN in lineage column (change in #3311 introduced this ~bug) 
- add lingroup column for lingroup name

NOTE: this PR adds the `lingroup` column to the `csv_summary` output for `tax metagenome` ONLY when we're using LINs and lingroups. I'm not sure this is the best approach, but I also don't want to add an empty useless column for everybody else? We could leave out the lingroup names, but then we're left with the LIN only, e.g. `0;1;1;8;1;0` rather than a nice, human-readable name (which is one of the key reasons to use `lingroup` file).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3898be6543a3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
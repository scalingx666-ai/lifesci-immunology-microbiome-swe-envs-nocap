# Issue

**Title:** adding group info for averaged data

## Description

Hi,

I was trying to use both `average_by` and `group_by` options in the `plot_composition()` function and noticed that my `group_by` info was ignored. It appears to me that after averaging, the current sample names `dfm$Sample` do not match with the original sample names `sample_names(x)` anymore. Therefore `match(as.character(dfm$Sample), sample_names(x))` returns a list of NAs. Therefore I'm proposing this quick fix. It works on my data/machine. Please consider.

Best,
Huan

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `786e09707f36`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
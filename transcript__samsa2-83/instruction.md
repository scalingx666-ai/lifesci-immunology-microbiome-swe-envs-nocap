# Issue

**Title:** Lisakmalins

## Description

@lisakmalins I tested this out, and overall it looks good!  

I did note an issue (on the sample_files_paired_end that's included with the SAMSA2 repo) that the `rbind` was failing on line 152 of the `run_DESeq_stats.R` script:

```
> complete_table <- rbind(complete_table, other_counts_table)
Error in match.names(clabs, names(xi)) : 
  names do not match previous names
```

My guess is that this is occurring because the file names aren't being filtered to take off the trailing file extension.  The `complete_table` has names that are just the sample numbers (1, 2, 3, 4), because it splits on underscores and then takes the second element (the one following "control_" or "experimental_"), in line 51, 55, 62, and 66.

To solve this, I made a couple updates to the way that these script parse the filenames so that it doesn't drop as much of the name as it did in the past, so the complete_table names align with the names in your `other_counts_table`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a6dad883c5f7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
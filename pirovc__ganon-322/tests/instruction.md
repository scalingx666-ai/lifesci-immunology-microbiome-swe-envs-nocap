# Issue

**Title:** Feature/write stats file

## Description

Add `--output-stats` to write an tabular file with statistics and totals from ganon-classify stderr log. The .sta contains the following fields:

```
prefix
hierarchy_label
seq_processed
seq_unclassified
seq_classified
seq_classified_perc
seq_unique_matches
seq_unique_matches_perc
seq_multiple_matches
seq_multiple_matches_perc
matches
avg_matches_ref_seq
dis_matches_rel_filter
dis_matches_fpr_query
kmers_proccessed
kmers_matched
kmers_from_classified_seqs
kmers_matched_perc
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b0dfb4f1d846`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
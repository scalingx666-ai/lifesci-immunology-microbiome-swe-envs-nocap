# Issue

**Title:** Fix missing score in input bins

## Description

This PR fixes the error reported in issue #34, which happened when writing input bin metrics to the output directory.

## What Went Wrong
The issue was caused when two input bins from different sets were sharing the same contig content. While the bins were dereplicated during scoring, binette was using the undereplicated bins when writing the metrics. This included unscored bins, which caused the error.

## How It’s Fixed
Now, only the dereplicated bins are used when writing metrics. The origin attribute tracks where each bin came from, so no information is lost in the process.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `92e78f099d7c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
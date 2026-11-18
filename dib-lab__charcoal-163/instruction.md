# Issue

**Title:** Add contig filter-by-query-bases-covered; refactor to stage1, stage2, etc.

## Description

This PR -

* adds `filter_by_query_coverage` to alignplot and the alignment reporting notebook;
* refactors things into stage1, stage2, etc rules and output directories;
* cleans up workflow, removes unnecessary files;
* other misc minor cleanup.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4df39c603fdf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Coverage Calculation

## Description

Added zebra filter's SortedRangeList for computing coverage.  
Implementations of mapper (plain and ordinal) now return dictionaries keyed by subject rather than sets of subject.  
Dictionary currently maps to list of (start,end) tuples defining read coverage (only implemented in plain mapper).  
Read coverage is demultiplexed, used to compute coverage (if a coverage_map object is sent), then stripped out.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8cc9516afeb6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
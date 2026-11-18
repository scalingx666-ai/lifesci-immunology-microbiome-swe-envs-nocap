# Issue

**Title:** Add new download genomes script that uses subdirs

## Description

This is a new version of the `download_genomes.py` script that puts them in two layers of nested subdirectories (just under the clade level) so as to keep the number of files per directory small.  I haven't yet evaluated the impact on downstream scripts, so maybe we just keep this pull request on the radar for a while before determining whether this really is the final form it should take.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c9e79b809243`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
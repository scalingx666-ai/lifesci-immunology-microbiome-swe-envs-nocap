# Issue

**Title:** Add fasta extension support

## Description

This PR adds the possibility to specify FASTA extensions to look for when using input bin directories. By default, the set of extensions includes '.fna', '.fasta', and '.fa', so Binette will only consider files with these extensions. The user can specify one or more extensions with the argument `--fasta_extensions`.  This addition should fix the problem found in #14.

It also adds bin directories with FASTA files to the test data set (see this repo to get the data: https://github.com/genotoul-bioinfo/Binette_TestData) and tests this kind of input in the CI commands.

Unit tests have been extended to cover more functions.

Additionally, it updates the version to 1.0.1 in preparation for a new release very soon.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8ea67975d1b0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Include an internal check for empty prokka fasta files

## Description

Hello @deyvidamgarten ,

I run into an issue where, for some of the contigs I was analyzing with `marvel`, `prokka` was producing empty protein fastas. These caused later `hmmer` searches to fail and the whole marvel workflow was failing.

This pull request addresses this issue.

* I included a small cleanup step of the intermediate prokka output so that the analysis keeps going. If everything is removed exit and warn the user.
* I included an `environment.yml` that freezes some dependencies to versions that worked for me. Since this was published, packages have been updated and the latest versions of `biopython` and `scikit-learn` throw errors. This is meant to be used with `conda`. 
* A brief description of how to use the `environment.yml` with conda is also included in the `README`.

I tested it with some of my broken files and it works as expected, at least the erroneous bins are skipped.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `623be82e9abc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
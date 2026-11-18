# Issue

**Title:** Program name fixies

## Description

This PR renames to programs: `anvi-script-gen-function-matrix-across-genomes` is now `anvi-gen-function-matrix`, and `anvi-script-gen-hmm-hits-matrix-across-genomes` is now `anvi-gen-hmm-hits-matrix`.

Following #2746, I realized that `anvi-script-gen-function-matrix-across-genomes` is no longer specific to 'genomes'. Which has never been the case actually, and I am not sure why the original script name had that level of specificity, but now it certainly not specific since PPCN normalization is only relevant for metagenomic assemblies.

While at it, I also fixed `anvi-script-gen-hmm-hits-matrix-across-genomes` since the same applies.

I think we should add the same flag to `anvi-gen-hmm-hits-matrix` (which will require PPCN reporting to be its own class elsewhere), but it can wait.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d29c26882c79`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
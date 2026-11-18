# Issue

**Title:** Fix pangenomics component test regressions

## Description

Fixes pangenomics component-test failures by avoiding lazy pan summary directory side effects, fixing pan
summary pandas row selection, and updating the pan representative test command to the current CLI.

Companion PR:

Together with the companion PR, this change allowed the local equivalents of the Component Tests and Migrations workflow
suites to complete:
- anvi-self-test --suite metagenomics-full --no-interactive
- anvi-self-test --suite pangenomics --no-interactive
- anvi-self-test --suite inversions --no-interactive

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fb36d9757c91`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
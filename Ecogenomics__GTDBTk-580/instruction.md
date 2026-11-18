# Issue

**Title:** fix(fixing of issue #573):

## Description

In some cases, when running the 3 classify steps independently, a genome may be filtered out in the alignment step. However, it's still present in the ani screening from the classify step and can have a ANI > 95% ( this can happen with partial genomes, where AF can still be high) Tk would try to report it twice in the summary file and would return an error. Instead we report it as classified with ani,
 but with a warning from the alignment step ( MSA < 10%).
 skani should reduce the number of such cases as it keep AF low for partial genomes.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ab573209fd2e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
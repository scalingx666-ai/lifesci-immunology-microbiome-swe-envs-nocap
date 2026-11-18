# Issue

**Title:** Fix strict syntax errors

## Description

Hi,

We are preparing the Nextflow 26.04 release, which will enable strict syntax by default.  Since viralrecon is one of the nf-core pipelines we like to use to battle-test Nextflow, I thought I might try to bring it into strict compliance

NOTE: I have zero domain knowledge of this pipeline! I simply refactored syntax as needed to satisfy the linter with minimal changes. Make sure to validate these changes for correctness.

Tagging @speizerj since I saw your implementation plan for strict syntax -- let me know if these changes make sense to you

Summary:
- Move top-level script statements into workflows (main script, VIRALRECON)
- Replace conditional include with conditional process call
- Replace for/while loops with equivalent methods
- Remove if statements from config -- this should work without creating loads of false warnings, because the strict syntax can validate selectors against conditional processes even if they aren't called in a run

Happy to answer any questions that you might have

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0278256d5957`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
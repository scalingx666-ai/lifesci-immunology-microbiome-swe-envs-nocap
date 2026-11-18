# Issue

**Title:** Bump nf-schema plugin to 2.7.2

## Description

## Description

Bumps the `nf-schema` Nextflow plugin from `2.5.1` to `2.7.2` (latest release) in `nextflow.config`.

This is a maintenance dependency bump only; there are no pipeline code or logic changes. The pipeline continues to use nf-schema for parameter validation and for building the input channel from the sample sheet. CI should confirm compatibility across the version range.

### Changes

- `nextflow.config`: `nf-schema@2.5.1` -> `nf-schema@2.7.2`
- `CHANGELOG.md`: added an entry under the unreleased section

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d4648a1a54f4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
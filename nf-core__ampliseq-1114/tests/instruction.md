# Issue

**Title:** Remove --input_folder, --input_folder_extensions and --multiple_sequencing_runs

## Description

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [x] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [x] Usage Documentation in `docs/usage.md` is updated.
- [x] `CHANGELOG.md` is updated.

## Description

.

`--input_folder`, `--input_folder_extensions` and `--multiple_sequencing_runs` are removed.
A sample sheet covers the same input, and its `run` column replaces `--multiple_sequencing_runs`.

- The `PARSE_INPUT` subworkflow, the three params, the direct FASTQ docs and the report's folder branch are removed.
- No tailored error: a removed param fails with Nextflow's "not declared" error, as for earlier removals.
- The schema now requires one of `--input` or `--input_fasta`; the runtime check stays for `--validate_params false`.

Verified: `prek run -a`, `nf-core pipelines lint` (0 failed), `nf-test tests/default.nf.test`, and a run with no input and with `--input_folder` to see both errors.
The CHANGELOG entry has the placeholder `#NNNN` until the PR number exists.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01PYuhWC4HE6BP63fnsVQZHN

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9ecbc2da1835`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
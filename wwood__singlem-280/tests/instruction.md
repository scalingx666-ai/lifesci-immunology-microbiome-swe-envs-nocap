# Issue

**Title:** Strengthen supplement matched protein sequence ID test

## Description

### Motivation
- Ensure matched protein sequence IDs produced by the supplement flow contain the originating SingleM/GraftM package basename for clearer provenance.
- Validate that the code which replaces raw HMM names in output IDs with package basenames is working as expected.

### Description
- Updated the supplement worker to map HMM `NAME` entries to `graftm_package_basename` and to use that package basename when constructing matched protein sequence IDs.
- Added validation when concatenating HMMs to fail on missing or duplicate HMM `NAME` entries and pass a `hmm_name_to_package` mapping into the per-genome worker.
- Strengthened `test_output_matched_protein_sequences` in `test/test_supplement.py` to acquire the metapackage, collect package basenames via `graftm_package_basename()`, and assert the matched protein record IDs include one of those basenames.

### Testing
- Ran the focused test file with `pixi run -e dev pytest test/test_supplement.py`.
- Test results: `7 passed, 2 skipped, 1 warning` and the test run completed successfully.

------
[Codex Task](https://chatgpt.com/codex/tasks/task_e_696420d8aa14832abe786744a103c2a1)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9dbf9dfb5698`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
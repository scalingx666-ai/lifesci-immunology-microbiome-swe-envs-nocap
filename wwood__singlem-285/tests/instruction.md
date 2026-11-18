# Issue

**Title:** Use polars for collapsing archive OTU tables

## Description

### Motivation

- The `write_collapsed_paired_with_unpaired_otu_table` implementation used `pandas` and produced failures in the collapse-to-sample tests; switching to `polars` enables safer, typed ingestion and deterministic grouping/aggregation for archive OTU tables.

### Description

- Replaced `pandas` usage in `write_collapsed_paired_with_unpaired_otu_table` with `polars` and removed the `pandas` import.
- Added `archive_schema` to map archive fields to typed Polars schema and read rows with `orient="row"` to avoid orientation warnings.
- Concatenated archives with `pl.concat`, removed sample suffixes using `pl` string ops, checked unique constraints via Polars, and sorted by `sequence`/`gene` to preserve deterministic order.
- Collapsed groups using `partition_by` and manual aggregation to preserve list-valued fields (`read_names`, `nucleotides_aligned`, `read_unaligned_sequences`, `equal_best_hit_taxonomies`) and produce `ar.data` as the expected list-of-lists structure.

### Testing

- Ran `pixi run -e dev pytest test/test_summariser.py` which passed: `28 passed, 1 skipped`.
- Ran the full test suite with `pixi run -e dev pytest test`, which completed but had one unrelated failure in `test/test_pipe.py::Tests::test_sample_name_strange_characters` caused by an external `diamond` process exit (`exit status -7`), not by the summariser changes.
- Iterative test-fix cycles were performed while developing the change until the summariser tests were green.

------
[Codex Task](https://chatgpt.com/codex/tasks/task_e_69797dee1630832ab2c34f65489b7f14)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b7ffba2258be`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Add --output-matched-protein-sequences option to supplement mode

## Description

### Motivation
- Provide an option to export protein sequences that matched HMM hits during `supplement` so users can inspect matched proteins alongside the matched transcripts.
- Keep the same read renaming convention using the `‡` delimiter so sequence identifiers remain compatible with downstream code.

### Description
- Added a new CLI argument `--output-matched-protein-sequences` in `singlem/main.py` and passed it into the supplement workflow as `output_matched_protein_sequences`.
- Propagated the argument through `Supplementor.supplement`, updated `generate_new_metapackage` and `gather_hmmsearch_results` signatures, and passed the value into worker calls.
- Implemented writing of matched protein sequences inside `run_hmmsearch_on_one_genome` by appending protein FASTA entries for transcripts in `matched_transcript_ids` and pre-creating/clearing the output file in `gather_hmmsearch_results` when requested.

### Testing
- Ran the full test suite with `pixi run -e dev pytest test` as required by project docs.
- Test run collected 244 items and completed with `2 failed, 222 passed, 20 skipped, 1 warning`.
- The two failing tests are `test/test_pipe.py::Tests::test_read_chunk_size_forward_gzip` and `test/test_pipe.py::Tests::test_read_chunk_size_paired`, which failed due to a `--read-chunk-size must be divisible by 4` validation error.
- All tests unrelated to `supplement` changes passed.

------
[Codex Task](https://chatgpt.com/codex/tasks/task_e_695ee2433084832a8cc37f58083b18f8)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1131a0f9b77c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
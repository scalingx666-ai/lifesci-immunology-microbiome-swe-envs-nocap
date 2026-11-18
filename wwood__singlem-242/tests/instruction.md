# Issue

**Title:** Fail when --krona used with taxonomic profile input

## Description

## Summary
- error if `singlem summarise` receives `--krona` with `--input-taxonomic-profile(s)`
- document that `--krona` only works with OTU tables and suggest `--output-taxonomic-profile-krona`
- test that the CLI rejects the invalid combination

## Testing
- `pytest test/test_summariser.py::Tests::test_krona test/test_summariser.py::Tests::test_krona_with_taxonomic_profile_input -q`

------
https://chatgpt.com/codex/tasks/task_e_68a036b5976c832a81c6fa061bb8169c

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b925fbb1d68e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
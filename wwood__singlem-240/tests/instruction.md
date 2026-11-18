# Issue

**Title:** Add flexible genome input options for pipe command

## Description

## Summary
- Allow providing genome input via files, directories, or lists for `pipe`
- Normalize genome FASTA paths with `parse_genome_fasta_files` shared by `singlem` and `lyrebird`
- Test directory and list genome inputs

## Testing
- `pytest test/test_pipe.py::Tests::test_genome test/test_pipe.py::Tests::test_genome_directory_input test/test_pipe.py::Tests::test_genome_fasta_list_input -q`

------
https://chatgpt.com/codex/tasks/task_e_689d5b4c8074832ab8b213ba7214ccfb

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7787583ce2e6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
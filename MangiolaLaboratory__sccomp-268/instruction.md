# Issue

**Title:** Add variability to composition mapping functionality

## Description

Introduce a new internal function `get_variability_to_composition_map` to match variability design columns to composition design columns based on their names. Implement error handling for missing terms in the mapping. Update the Stan model to incorporate the new mapping and adjust the model calculations accordingly. Add comprehensive tests to validate the mapping functionality and ensure robustness against missing terms.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b18f205a97b4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
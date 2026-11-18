# Issue

**Title:** Add merged GSA support

## Description

- Added support for merged gold standard assemblies based on `merged_gsa_combinations`. Example use case: samples of the same patient.

```
// Custom sample combinations for merged gold standard assemblies.
// Specify as a list of lists, e.g., [[0,1,2], [2,3,4], [5,6]]
// Each inner list represents a group of samples to merge.
// If empty ([]), no custom merged GSAs will be generated.
// Example for patient-specific merging: [[0,1,2], [3,4,5]] merges samples 0-2 and 3-5 separately.
merged_gsa_combinations = []
```

- Added anonymization for merged GSAs when anonymization is enabled.
- Added per-merged-GSA anonymization seed handling.
- Ensured merged GSA generation keeps sample combinations and reference FASTA inputs grouped correctly.
- Added a Python bamToGold.py implementation for BAM-to-GSA conversion.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2a77caf3abdc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
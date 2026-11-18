# Issue

**Title:** Try to parse abundance from headers

## Description

As requested by @akahles, this change _should_ allow to parse kmer counts from headers in [Logan format](https://github.com/IndexThePlanet/Logan/blob/main/Unitigs.md#data-format).

Some potential issues:

1. `[abundance]` in Logan headers is a floating-point number, but our counts are integer. Current implementation just converts them, so it truncates to 0. Any alternatives on how to assign them?
2. I just noticed that `parse_sequences` uses `uint32_t count`, while `annotate_data` uses `std::vector<uint64_t> kmer_counts`. We should probably unify them?
3. Should we _always_ try to read abundances from headers, or only if a flag is provided? How should we name the new flag if the latter?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `19cc9a8704be`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
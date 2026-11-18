# Issue

**Title:** Replace SequenceCount string alias with std::vector for proper numeric handling

## Description

This PR refactors the `SequenceCount` type from a `std::basic_string<SequenceCountUnitType>` to a `std::vector<SequenceCountUnitType>`, as the former was being used in ways not suitable for string operations (e.g. `+=`, `substr` on numeric data). This resolves build failures and makes the intent clearer.

Tested on FreeBSD 15 with Clang 19.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5f329c6d24a1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
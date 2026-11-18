# Issue

**Title:** v1.1.2 updates

## Description

Fixed:
- properly finding "unclassified" taxa in `tax_profile()`
- changing host removal module to use samflag "12" instead of "4" to remove a pair of read if either pair maps
- clearer logging statements regarding which filtering steps are actually run
- work around for failures to access Googlefonts in report generator

New Features:
- Adding `readstats.yaml` to record reads at initial and various filtering stages

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `eaf303ed195f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
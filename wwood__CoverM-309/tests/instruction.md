# Issue

**Title:** Keep a given --min-read-percent-identity in metabat mode

## Description

`contig --methods metabat` replaced any `--min-read-percent-identity` with 97% (#308). With this change, a given threshold is kept, and 97% applies only when none is given. The metabat entry in `contig --full-help` now says so. The secondary, supplementary and improper-pair settings are unchanged.

New test `test_metabat_given_percent_identity_is_kept`: `-m metabat --min-read-percent-identity 90` on `k141_2005182.head11.bam`.
- The expected row (6.04 / 1.12) was computed with CoverM 0.8.0 using `-m length mean variance --min-read-percent-identity 90 --min-covered-fraction 0 --contig-end-exclusion 75 --include-secondary`.
- At 97.001 the same command reproduces the existing `test_metabat_97_of_100_bases_should_fail` row exactly (1.9333 / 0.0631).
- Not built or run locally; please let CI confirm.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `679778d8275e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
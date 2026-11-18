# Issue

**Title:** Add exact pure-N codon origin posterior batch API (5.7.0)

## Description

A most-likely rearrangement cannot quantify whether a codon is entirely N-derived when compatible histories differ in their trimming/P contributions. Add `n_region_posterior_batch` using the existing exact sum-product recurrences, including single- and tandem-D histories. P-extended templates are excluded from pure N; unsupported queries retain null probabilities and requested row/position order.

The API uses the existing native batch runner and exports no generation-probability cache. Existing model parameters, generation probabilities and default scorers are unchanged. Bump the minor version to 5.7.0 and document the conditioning and non-N interpretation.

Validation: 1,874 release-tier tests passed, 7 skipped, 29 deselected; both C++ test executables pass; clean-wheel origin and tandem-Pgen golden checks pass (11 tests); strict Sphinx and focused Ruff checks pass. Exact toy cases cover fractional P/N and alternative D-placement histories, with current TRB/TRD/IGH thread equality and immutable anchors.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d7118357eaeb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
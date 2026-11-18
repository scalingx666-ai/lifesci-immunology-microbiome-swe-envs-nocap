# Issue

**Title:** Add exact pure-N intervals to masked generation probabilities

## Description

Masked generation probabilities can now require every nucleotide in a half-open codon interval to be an N addition. The existing scalar and batch degenerate-AA APIs reuse the same exact sum-product engine, including both tandem-D contractions, so residue alternatives and inserted intervals are summed without enumerating sequences. Default probabilities and bundled model assets remain unchanged.

The Python API exposes `n_region=(begin, end)` and per-motif `n_regions`; returned values are joint masses rather than origin posteriors. Invalid batch dimensions and interval coordinates raise explicitly. A correlated trimming/P example verifies why interval probabilities cannot be multiplied from separate site posteriors.

Validation: 1,876 non-slow/non-heavy tests pass; 31 native-origin/degenerate/golden checks pass from a clean built-wheel install; both C++ suites and strict Sphinx pass. The full local tier took 94.82 seconds, peaking at 10.70 GB summed process-tree RSS. Version 5.8.0 prepares the additive API release.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `634229c34518`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
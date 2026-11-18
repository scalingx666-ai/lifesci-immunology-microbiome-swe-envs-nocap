# Issue

**Title:** 5.0.0: remove unused comparison labels and reduce EM regression cost

## Description

Remove the unused `compare_models(labels=...)` keyword after its 4.9.0 deprecation. This is a 5.0.0 API change: table comparisons retain `by`, while graph labels remain on `compare_net_dot`. The CLI caller and migration docs are updated, and both default/custom removed keywords now raise TypeError.

Gene-prior tests previously performed five full TRB fits. The functional-support, normalization, deletion-support and generatability checks now share the existing 400-read, three-iteration positive-prior fit. Both 300-read, two-iteration fits for explicit-zero/default byte equality remain. Five exact-count tests exercise observed, unseen and nonfunctional V/J alleles at multiple priors, all-zero counts and the zero default on every CI matrix leg. Production inference and scientific thresholds are unchanged.

Clean sequential measurements on a 16-core Mac, same native Release build and thread budgets: original four tests 122.81 seconds; optimized suite plus five edge cases 89.21 seconds (27.4% less wall time). Native E-steps fall from 11 to 7. Each measurement used a fresh process; one run per shape. Final CI passed 1,251 tests. On separate Linux/Python 3.12 CI runners, gene-prior duration sums were 872.84 seconds before and 829.42 seconds after. The unchanged zero/default test took 327.15 versus 420.91 seconds, and the unchanged 400-read fit took 318.53 versus 408.51 seconds. Overall pytest time was 1,353.98 versus 1,443.05 seconds; this pair does not establish an overall CI speedup. The clean same-Mac pair and the reduction from 11 to 7 E-steps establish the measured test-work reduction.

Validation: 1,242 local tests passed (22 skipped, 19 slow cases deselected), including full-locus heavy cases; focused API/CLI/M-step checks passed. Zero-warning Sphinx build, wheel/sdist metadata and full-content privacy checks passed. Installed 5.0.0 wheel rejects both default/custom removed keywords and preserves real CLI table/graph output. Published mirpy 4.5.0 passes signature CLI serial/process equality against that wheel. Workshop calls bind to the new signatures. The stable distance-table schema is pinned by existing tests. Shared fitted state is read-only to its consumers.

. .

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3916bdf4fbdb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
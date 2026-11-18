# Issue

**Title:** Avoid coordinate materialization for header counts and signatures

## Description

Header-level label, count and signature queries were building full coordinate results and then discarding the positions. Aggregate decoded rows directly for all five non-coordinate query modes: labels, matches, counts-sum, per-k-mer counts and signatures. CLI and server requests share these methods.

Decode each distinct query k-mer once and preserve its query-position multiplicity. One private typed helper shares decoding and selection; scalar queries retain only counts, while positional queries scatter counts or presence bits back to query positions. Preserve thresholds, ordering, top-label selection before abundance weighting, and the full-presence signature shortcut. Public APIs and index formats are unchanged. Coordinate queries retain their requested output.

Validation on mex with GCC 13 Release/GNU ld, using the stacked #670 build:

- All 3,706 DNA unit tests passed, including new positional regressions across column, BRWT and both row-diff variants, plus independent expected counts for gaps and repeated k-mers.
- All six query modes matched master and the previous PR implementation on the production RefSeq mmap index: 252 complete ordered output comparisons, with checksums covering 12,600 timed queries per implementation.
- The selected-input timing ranges overlap and include noisy coordinate-control trials; this follow-up does not establish a general speedup for the new positional paths. It removes their coordinate-output allocation. These seven inputs are not a sample of production traffic.
- The full CLI/API integration suite completed: 3,358 passed, 16 expected failures and 276 unsupported coordinate/backend combinations skipped, with zero unexpected failures or errors. Fresh CI is running for this revision.

Earlier scalar-count validation included 473,742 independent literal-record comparisons. Existing mmap alignment diagnostics also reproduce with original code, so mmap is not claimed sanitizer-clean.

Also fixes macOS CI dependency selection: resolve OpenSSL before Simple-Web-Server overwrites the requested root, avoiding binaries linked to OpenSSL 4 on runners that install OpenSSL 3.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6a2f76c0f334`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
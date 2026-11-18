# Issue

**Title:** Bind searched reference indexes to source content

## Description

An installed ARDA inside another project’s virtual environment could adopt that project’s reference root. A newer stale MMseqs database could then search scaffold IDs against incompatible current markup, changing V calls and CDR boundaries despite identical package and FASTA hashes.

Require ARDA’s own source path for automatic checkout detection and validate content-bound immutable index generations, including split sequence/header payloads. Preserve legacy indexes and publish a complete generation atomically. The public `reference_index_identity()` API exposes the exact searched file hashes for downstream provenance.

Validation: 1,350 unit/synthetic/realworld tests passed (16 skips), 10 focused root/index/API checks passed, Ruff and warning-as-error Sphinx passed. The built 2.36.2 wheel was independently installed and all 63 package payloads verified. Supports antigenomics/tcren#30; publication remains at the PyPI approval gate.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `aa68f5e63ed8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
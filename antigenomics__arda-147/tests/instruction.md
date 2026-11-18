# Issue

**Title:** Release 2.36.1: preserve shared TRA/TRD alleles and resolve aliases before chain selection

## Description

Shared TRA/TRD V alleles were collapsed to one locus label, hiding 15 human and 42 mouse TRA memberships. Preserve all declared memberships in `Anchor.loci`, use them in candidate selection, and retain the existing singular label for compatibility.

Resolve accepted shared-gene aliases before choosing the chain in junction markup, scenario construction and D calling. A shared V with TRDJ now stays TRD, including aliases such as TRAV38-2 and DV8.

Prepare 2.36.1 with Nextflow pins, release notes, regression coverage across all five reference organisms, and explicit sdist exclusions for private instructions and local reports. Reference sequences and coordinates are unchanged.

Validation: focused regressions, source lint, zero-warning Sphinx build, isolated sdist/wheel build, fresh-wheel human/mouse checks, and sdist exclusion checks pass. Full release CI runs on this PR; the PyPI environment approval remains the author's gate.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `049553f35114`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
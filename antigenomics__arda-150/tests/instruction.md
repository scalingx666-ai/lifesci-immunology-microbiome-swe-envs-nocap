# Issue

**Title:** Release arda-mapper 2.36.2 reference-index repairs

## Description

Releases content-validated MMseqs index generations and source-root discovery fixes as arda-mapper 2.36.2. Raises the compatible seqtree minimum to 1.1.1 (<2), preserves integration version pins, and reconciles the productivity roadmap with the implemented FR4/frame/stop contract. TRDV–TRAJ reference completeness and recall remain tracked in #149; no pairing-policy change is included.

Validation: 1,358 local unit/synthetic/committed-realworld tests pass (nine optional OLGA skips); lint and strict Sphinx pass. The rebuilt native extension also passes focused integration checks against the actual seqtree 1.2.0 release wheel.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6ee957df0ce2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
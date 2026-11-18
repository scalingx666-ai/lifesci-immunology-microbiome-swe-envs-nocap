# Issue

**Title:** Batch correction searches within the allocated CPU budget

## Description

Correction previously called seqtree once per junction in abundance-parent selection, error-rate estimation, quality gating and pileup refinement. Submit one native query batch per phase and preserve the existing ordered parent decisions.

Expose `arda correct --threads` and `correct_airr(..., threads=...)`, validate the budget with the existing affinity/cgroup/SLURM resolver, and forward the pipeline budget to correction. Document per-sample external-worker allocation in the API, docs and skill.

Validation: focused correction and CLI tests, source lint and strict Sphinx pass. A Stratos diagnostic on 10,000 synthetic 45-nt junctions returned the same 5,000 parent assignments: per-query 0.257 s, batch/one-core 0.250 s, batch/16-core 0.0365 s (7.0x versus per-query). Full local unit/synthetic/real-world suite: 1,405 passed, nine OLGA-dependent tests skipped because that optional oracle is absent; CI remains required. No reference/model parameters changed; no version bump or release in this PR.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `92fc58df24d2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
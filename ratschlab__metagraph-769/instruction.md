# Issue

**Title:** State match-count cuts in search results

## Description

Capped JSON query results now include `cuts` with matched and returned counts, completeness and cutoff tie facts, preserving the existing selection and ordering. CLI JSON output includes the same cut facts.

List-server rows and cut records identify their configured pair with `graph` and an opaque `pair_id`, without raw index paths. The shared ID encoding also identifies traversal walks. Counts annotations report count ties without certifying median-abundance order; LABELS and COUNTS_SUM remain unstated.

The server reference documents the fields. Deploy compatible API identity handling before updating native servers. Added row metadata still requires traffic and cache qualification before a fleet rollout.

Developed with Codex.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `356fe1ee37a7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
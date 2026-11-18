# Issue

**Title:** State chosen record places and opaque pair IDs in traversal answers

## Description

Traversal consumers need the seed occurrence chosen for each record and the configured index pair that produced each walk. Header labels now include record-local `place` (`origin`, `dir`). List-server walks identify their pair with `graph` and an opaque `pair_id`.

The ID uses a versioned UUIDv5 encoding of the configured graph name and index paths. Raw paths are omitted from the response. This identifies a configured pair; content identity still comes from its deployment manifest. The traversal algorithm and chosen seed occurrence stay unchanged.

The response reference documents these fields. Deploy the compatible API adapter before updating native servers so manifest binding can resolve the new IDs.

Developed with Codex.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `503209e1c971`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
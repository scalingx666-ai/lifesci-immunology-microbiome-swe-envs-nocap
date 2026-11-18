# Issue

**Title:** Remove /resolve, seed selection and seed ids from labeled traversal

## Description

Labeled traversal keeps one route, `POST /traverse`. This PR removes `POST /resolve` and the flag `--resolve-max-query-bp`. `/traverse` no longer accepts `seeds[].seed_id` and no longer returns `seed_id`, `validated_seed_id` and `seed_id_mismatch`.

`/resolve` with `discover` called the same function as `/search` with `with_signature`. On the mini RefSeq index both return the same 25 records and k-mer counts, and the presence mask of `/search` is the runs of `/resolve` in run-length form. Seed selection read only that profile and never the index. The seed id was a hash of the seed and its label names. The web service has its own implementation of both.

A caller now finds the records that contain a query with `/search` and `with_signature`, and sends a part of the query with those records to `/traverse`. The manual page shows this. A profile of named labels without a walk is no longer available. `/traverse` still reports named labels that are not on every k-mer of the seed, with their runs, in `dropped_labels`.

The walker keeps the named-label check it runs on each seed. The mini-index tests take their labels from the signature function.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1bf1ea1d4852`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
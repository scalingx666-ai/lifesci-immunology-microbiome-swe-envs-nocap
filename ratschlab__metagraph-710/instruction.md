# Issue

**Title:** Traversal v1 (3/4): the /resolve and /traverse server routes

## Description

Third of four stacked PRs for labeled traversal, on #709 (merged).

`server_query` on a single index (`-i`, `-a`) now serves two more routes: `POST /resolve` and `POST /traverse`. A server started with a list of graphs does not have them. The schema is experimental and may still change. Requests are strict: an unknown field is a 400. The index of sequence header names is built on first use, no longer at startup.

`--traverse-max-seeds` and `--traverse-max-time-ms` bound a `/traverse` request, and a seed may be at most 10,000 bp long. `--resolve-max-query-bp` bounds the query of a `/resolve` request. A count must be a whole number, so `1e6` is refused.

`test_mini_refseq` runs in a new CI job on the published mini RefSeq index (42 records, pinned checksum, fetched by `scripts/traversal/fetch_mini_refseq.sh`). It checks header walks against the source records. Without the index the tests are skipped.

The integration tests start servers through one `start_server` helper in `integration_tests/base.py`, which `test_api` now uses too.

Compared with the prototype, there is no `metagraph traverse` command, no `/traverse/capabilities` route and no `schema_version` field, and `/resolve` has no `select.policy`, `candidates` or selection counts. The staging web service also uses graphlet output, cancellation and budgets, which these routes do not have yet.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7ab1dc0eb8f5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
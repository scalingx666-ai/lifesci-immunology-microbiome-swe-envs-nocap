# Issue

**Title:** Require edit permissions to modify an artifact

## Description

## What

`artifact_patch_request` and `artifact_status_put_req` gated changes to an
artifact on the *read* access check. `Study.has_access` returns True for every
user once the study is public, and `Study.status` is inferred as public when any
one of the study's artifacts is public, so that check is broader than what a
write path should accept.

Both now also require `Study.can_edit` — owner, shared users, superuser/admin —
or `Analysis.can_edit` for analysis artifacts, before the attribute is changed.
This covers both attributes `artifact_patch_request` handles, `/visibility/` and
`/name/`. Nothing changes for owners, shared users or admins.

## Why

The transition rules live in the button-rendering code
(`artifact_summary_get_request`), not in the endpoint those buttons call, so the
endpoint accepted transitions the UI never offers.

## Changes

* `qiita_pet/handlers/artifact_handlers/base_handlers.py`: edit check in
  `artifact_patch_request`.
* `qiita_pet/handlers/api_proxy/artifact.py`: same check in
  `artifact_status_put_req`, returning the module's error dict.
* `qiita_db/artifact.py`: corrected the `visibility` setter docstring, which
  still described the upstream propagation replaced in c309aa6b (#2098).
* Tests: a user with read-only access is refused both a visibility change and a
  rename on a public artifact, in `test_artifact_patch_request` and in
  `test_artifact_status_put_req_public_study_no_access`.
* `.github/workflows/qiita-ci.yml`: pinned `ruff` to 0.14.8. The lint job
  installed it unpinned and the repository carries no ruff configuration, so
  every release changes the effective rule set — the version current when this
  PR was opened reported 1695 errors across 155 files, nearly all in code this
  branch does not touch.

## CHANGELOG

There is no upcoming-release section yet — 2026.01 is at the top and is
deployed. Suggested entry for the new section:

* Changing an artifact's visibility or name now requires edit permissions on the
  study or analysis that owns it, rather than read access.

## Testing

`ruff check qiita_* setup.py scripts/qiita* notebooks/*/*.py` passes locally
with the pinned version. The test suite was not run locally — the local
`qiita_test` database is in use for unrelated schema work — so CI is the first
execution of the new tests.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01LcSuWDUMjSdtwbRLgMgYL1

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e0e7480a1b04`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
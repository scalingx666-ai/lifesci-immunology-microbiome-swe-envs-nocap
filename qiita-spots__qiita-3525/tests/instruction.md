# Issue

**Title:** Require real study access for non-public artifacts

## Description

## What

`Study.has_access(user)` returns `True` for any authenticated user when the study's status is `public`. That status is *inferred*: `infer_status` reports a study as public if **any one** of its artifacts is public. Two access checks were using that public-inclusive form for artifacts that are **not** public:

- `qiita_db/meta_util.py` `validate_filepath_access_by_user` — the only gate on `DownloadHandler` (`/download/<filepath_id>`), plus the prep information branch.
- `qiita_pet/handlers/artifact_handlers/base_handlers.py` `check_artifact_access` — the artifact page and PATCH paths, and `DownloadPrivateArtifactHandler`, which mints a 7-day signed JWT for the artifact.

So in a study holding a mix of public and non-public artifacts, the non-public ones were readable by anyone with an account.

Both call sites now pass `no_public=True` when the artifact itself is not public. In the prep information branch the descendants loop repeats the study check, so all three call sites there are changed — fixing only the first would have been bypassed by the loop.

## Scope of the change

For a **private** study nothing changes: `has_access` could never take the public shortcut there, so owner and shared access is untouched. The only behaviour that changes is the nominally-public-study case.

Not changed, deliberately: `check_access` in `qiita_pet/handlers/api_proxy/util.py` has 43 callers and tightening it would deny public-study reads across the API. The handlers that use it (`DownloadEBISampleAccessions`, `DownloadEBIPrepAccessions`, `DownloadSampleInfoPerPrep`) serve study metadata rather than artifact files, and `meta_util.py` already treats a public study's sample information as public by design.

The existing idiom elsewhere in the codebase already does this correctly and was used as the model: `DownloadRawData` calls `study.has_access(user, True)`, `DownloadStudyBIOMSHandler` computes `full_access` explicitly, and `DownloadPublicHandler` filters per artifact on `visibility != "public"`.

## Tests

Added two regression tests for the case the suite did not cover. `MetaUtilTests` only ever set **all** artifacts public or **all** private, so a study with mixed visibilities was never exercised:

- `test_validate_filepath_access_by_user_mixed_visibility`
- `test_check_artifact_access_mixed_visibility`

Both set a single artifact public via SQL, so the change is not propagated through the tree, then assert that a user without access to the study still cannot reach the artifacts that remain private.

**The test suite was not run locally.** The `qiita_test` database on the machine this was written on holds an unrelated schema, and `qiita_test_checker` rebuilds the `qiita` schema of whichever database the config names, so running it there would have destroyed that database. `ruff check` and `ruff format --diff` pass on the changed files. CI is the first run of these tests.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01LcSuWDUMjSdtwbRLgMgYL1

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9bcc1e975417`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
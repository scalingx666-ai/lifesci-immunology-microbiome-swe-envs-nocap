# Issue

**Title:** Fix PR size labeler failing on fork PRs

## Description

The `labeler` workflow fails on every PR opened from a fork with `curl: (22) The requested URL returned error: 403` when adding the `size/*` label. Under `pull_request`, GitHub hands fork PRs a read-only `GITHUB_TOKEN` regardless of the `permissions:` block. Only PRs from branches in nf-core/mag succeed.

The failure was silent before `codelytv/pr-size-labeler` v1.11.0 (the label just wasn't added); since then the action propagates API errors, so the check goes red.

## Changes

- Switch the trigger to `pull_request_target`, which gets a writable token for fork PRs. This is safe here because the job never checks out PR code: the action only counts changes through the API. This is the same fix upstream applied to its own labeler ().
- Pin the action to the `v1.12.0` commit SHA, since it now runs with a write token. `v1` currently points to the same commit, so behaviour is unchanged.

## Notes for maintainers

- `pull_request_target` runs the workflow from the base branch, so this PR's own labeler check will still fail; the fix takes effect after merge.
- GitHub will [block `pull_request_target` by default](https://github.blog/changelog/2026-09-17-workflow-execution-protections-in-github-actions-generally-available/) in affected public repositories from **November 2, 2026**, unless an Actions event policy explicitly allows it. An nf-core org/repo admin may need to allow it for this workflow.
- If `Label the PR size` is a required status check on `dev`, it should be removed: under `pull_request_target` it runs on the base-branch commit, not the PR commit.

## PR checklist

- [x] This comment contains a description of changes (with reason).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `264a7fe21697`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
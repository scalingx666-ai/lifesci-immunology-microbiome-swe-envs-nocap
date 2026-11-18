# Issue

**Title:** ci: bump docker actions to Node 24 majors

## Description

Fixes the GitHub Actions Node.js 20 deprecation warning from the docker publish workflows.

- `docker/setup-buildx-action` v3 → v4
- `docker/login-action` v3 → v4
- `docker/build-push-action` v6 → v7
- `docker/metadata-action` v5 → v6 (release workflow; also node20)

All new versions declare `using: node24`. Their breaking changes (removed deprecated inputs/envs) don't affect these workflows. All other workflows already run on Node 24.

The release workflow only runs on a published release, so it won't be tested until the next release.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Chores**
  * Updated the automation used to publish the latest and release Docker images. Image names, tags, credentials, and build settings remain unchanged.
  * These updates do not change the published images’ configuration or how they are tagged.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8ac46c09377c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
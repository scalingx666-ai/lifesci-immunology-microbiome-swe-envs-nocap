# Issue

**Title:** ci: use Python 3.12 for integration tests

## Description

Nightly builds on `develop` fail in every integration-test job since 2026-10-28.

GitHub moved `ubuntu-latest` (used by the shared `java-gradle.yaml@v4` workflow) from `ubuntu-24.04` to `ubuntu-26.04`. `actions/setup-python` has no Python 3.9 build for 26.04, so the setup step fails before Gradle runs:

```
The version '3.9' with architecture 'x64' was not found for Ubuntu 26.04.
```

This sets `test-integration-python-version` to `3.12`. The only integration test that uses Python is `itests/case016_ignored.sh`, which is disabled, so the version bump does not change test behaviour.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d91598aef6df`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
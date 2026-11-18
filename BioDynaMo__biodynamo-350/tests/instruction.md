# Issue

**Title:** Deprecate `macOS` < 12.0

## Description

Our support for macOS is founded in the `brew` package manager. `brew` no longer supports macOS 11 and, thus, our macOS 11 CI currently fails. This PR removes support for macOS < 12.0. 

See https://github.com/orgs/Homebrew/discussions/4827#discussioncomment-7189632

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `53b33d003dc4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
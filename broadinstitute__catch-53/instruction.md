# Issue

**Title:** Switch to GitHub Actions for build testing

## Description

This PR switches from Travis CI to GitHub Actions for build testing. It also:
- Adds linting before testing
- Expands testing to additional Python versions and macOS
- Changes the code coverage analysis from coveralls to codecov

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `204c36ee3c22`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
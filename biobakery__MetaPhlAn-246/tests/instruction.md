# Issue

**Title:** Make release deploy resilient to duplicate PyPI uploads

## Description

The `deploy` job in `Upload Python Package` failed during `twine upload` with `HTTP 400 Bad Request`, blocking release publishing. The failure stemmed from non-idempotent upload behavior when artifacts for the same release already exist on PyPI.

- **Deploy workflow hardening**
  - Updated `.github/workflows/python-publish.yml` to make the publish step tolerant of already-published artifacts.
  - Added verbose upload output to improve diagnosis for future PyPI/API failures.

- **Change details**
  - Replaced the upload command in the deploy job:

```yaml
- name: Build and publish
  run: |
    python setup.py sdist bdist_wheel
    twine upload --verbose --skip-existing dist/*
```

This keeps release runs from failing on duplicate artifact uploads while preserving normal publishing behavior for new artifacts.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2721089214ed`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
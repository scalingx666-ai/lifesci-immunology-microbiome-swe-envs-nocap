# Issue

**Title:** Fix PyPI deploy failure by normalizing package name in distribution metadata

## Description

The `deploy` GitHub Actions job failed during PyPI upload because release artifacts were generated with `MetaPhlAn` in the filename. PyPI now enforces normalized project naming in distribution filenames and rejected the upload.

- **Root cause**
  - `setup.py` used mixed-case `name='MetaPhlAn'`, producing artifacts like `MetaPhlAn-4.2.5-py3-none-any.whl`.
  - PyPI expected normalized project name `metaphlan` in the filename.

- **Change**
  - Updated package metadata in `setup.py` to use normalized lowercase project name.

- **Effect on deploy workflow**
  - Build artifacts are now emitted with normalized names (e.g., `metaphlan-4.2.5-...`) and align with PyPI upload requirements.

```python
# setup.py
setuptools.setup(
-    name='MetaPhlAn',
+    name='metaphlan',
    ...
)
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3ef0721e2902`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
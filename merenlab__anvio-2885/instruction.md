# Issue

**Title:** Remove `anvi-setup-modelseed-database --dir` default

## Description

This is a , which noticed that `anvi-setup-modelseed-database` had an absolute path in the anvi'o installation as the default of `--dir`. This default was found from `ModelSEEDDatabase.default_dir` when the module loaded, causing `anvi-script-gen-help-docs` to record the path from whichever machine ran it in `documentation.json`.

The default is now `None`, and `anvi-setup-modelseed-database` help text states that the program sets up the database in `anvio/data/misc/MODELSEED`, as before. No further changes were required, because `ModelSEEDDatabase.set_up` would already fall back to `ModelSEEDDatabase.default_dir` when `dir` is `None`. The one change in behavior is that a missing `anvio/data/misc` is now created rather than reported.

With `None`, the docs builder now leaves out the "Default:" field on the program's page.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3cecbb414168`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
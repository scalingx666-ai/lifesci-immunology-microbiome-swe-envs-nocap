# Issue

**Title:** Align conda and pip dependencies and fix `binette.yaml`

## Description

`binette.yaml` and `pyproject.toml` declared different versions for some dependencies. Also, `binette.yaml` no longer solved: because `bioconda` was listed before `conda-forge`, CheckM2's tensorflow dependency hit a conflict in the build libraries.

### Changes
- `binette.yaml`:
  - `conda-forge` is now listed before `bioconda`, as Bioconda recommends;
  - removed `requests` and `packaging`, which Binette doesn't use (CheckM2 still brings them in);
  - added `joblib`, which Binette imports but was missing;
  - pyfastx, typer and rich now have the same version bounds as `pyproject.toml`.
- `pyproject.toml`: rich is now allowed up to `<16`, so rich 14 and 15 can be installed. Removed the unused `setuptools-scm` from the build requirements.
- README and `docs/installation.md`: the Bioconda install command now uses `-c conda-forge -c bioconda`, without `defaults`.

This has been implemented with the help of Claude Code.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `10226fc534a1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
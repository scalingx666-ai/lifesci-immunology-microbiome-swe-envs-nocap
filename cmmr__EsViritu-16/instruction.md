# Issue

**Title:** remove deprecated distutils module for shutil.which

## Description

Hi,

Esviritu v1.0.3 installations through conda are not working properly because conda installs python 3.13 alongside, while Esviritu uses a module `distutils` which has been deprecated since v3.10 and removed since v3.12 (see [PEP-0632](https://peps.python.org/pep-0632/)). The `pyproject.toml` also only specifies that python 3.11 or greater can be used.

Instead of restricting python to v3.11, I replaced `distutils.spawn.find_executable` with `shutil.which`, which should retain the functionality but will work with newer versions of python. You will have to make a new release on bioconda for this to take effect however.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5ec3583afc66`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
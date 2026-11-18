# Issue

**Title:** Pep 625 fix

## Description

This email is notifying you of an upcoming deprecation that we have determined may affect you as a result of your recent upload to 'aviary-genome'.

In the future, PyPI will require all newly uploaded source distribution filenames to comply with [PEP 625](https://peps.python.org/pep-0625/). Any source distributions already uploaded will remain in place as-is and do not need to be updated.

Specifically, your recent upload of 'aviary-genome-0.11.0.tar.gz' is incompatible with PEP 625 because it does not contain the normalized project name 'aviary_genome'.

In most cases, this can be resolved by upgrading the version of your build tooling to a later version that supports PEP 625 and produces compliant filenames.

If you have questions, you can email [admin@pypi.org](mailto:admin@pypi.org) to communicate with the PyPI [admin@pypi.org](mailto:admin@pypi.org) to communicate with the PyPI administrators.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ba28c68b2657`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
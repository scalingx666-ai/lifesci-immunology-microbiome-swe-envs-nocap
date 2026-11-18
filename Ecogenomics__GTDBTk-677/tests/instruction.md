# Issue

**Title:** skani migration to 0.3.1

## Description

This pull request updates the SkANI integration in the codebase to support SkANI v0.3.1 and improve performance and usability for ANI calculations. Key changes include upgrading SkANI, adding persistent sketch directories, updating the CLI and APIs, and removing outdated references to Mash and older SkANI versions.

**SkANI Integration and Performance Improvements**

* Upgraded SkANI from v0.2.1 to v0.3.1 in the Dockerfile to use the latest features.
* Added support for a persistent sketch directory (skani_sketch_dir) to speed up repeated runs.
* Changed SkANI invocation from dist to search mode and updated progress bar handling and result parsing.

**Major Feature: Improved Species Assignment Accuracy**
* Removed an arbitrary limit on the number of genomes compared in dense genera.
This ensures that all representative genomes in a genus are compared, preventing incorrect species assignments when the closest genome by ANI is outside the previous 100-genome limit. This is especially important in dense genera like Collinsella and significantly improves classification accuracy, even if runtime increases slightly.

**Documentation and Reference Updates**

* Removed outdated references to Mash and older SkANI publications from README.md and docs/src/references.rst.

**Other Minor Improvements**

* Improved logging and progress reporting, including optional debug statements and better result capture in SkANI runs.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `be5b79984de8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
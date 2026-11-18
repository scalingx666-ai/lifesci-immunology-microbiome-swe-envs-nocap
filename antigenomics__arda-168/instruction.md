# Issue

**Title:** Make native developer setup self-contained and repeatable

## Description

A fresh developer setup can fail without CMake or AIRR build isolation, while repeat setup can reject an existing environment. An inherited `UV_PYTHON` can also redirect dependency installation away from the activated checkout environment.

Reuse the existing environment and interpreter, install CMake locally, and prepare AIRR with build isolation before the editable no-isolation step. Both dependency installs now explicitly target the checkout interpreter.

Validation: the offline real-uv regression fails against the previous setup script and passes with the repair for both new and existing environments (2 cases). It verifies actual installation into the checkout environment, absence from the external override environment, and preservation of the existing configuration and user marker. Shell syntax and diff checks pass; the change received independent review. The regression stops before dependency downloads/native compilation; current-head Linux CI (native build, lint and full tests), Windows annotation/cache checks and the docs build pass. Sequential setup only; concurrent installation is not claimed.

.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5ec45310e980`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
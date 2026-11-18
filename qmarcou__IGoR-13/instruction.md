# Issue

**Title:** Add -p to mkdir, allow for DESTDIR

## Description

Hello,
The mkdir fails when both igor and its subdirectoy models are to be created in /usr/share, hence the -p. When using igor from a chroot directory (or when preparing a package for Debian/Ubuntu) it is common to set the DESTDIR as a prefix to the installation directory.
Many thanks and regards,
Steffen

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4ce1b890f541`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** quote filenames before passing to shell

## Description

Without the single quotes around the filenames, filenames containing spaces will confuse shell.

This is a "minimally invasive" patch. Using shell is inherently insecure, there are still filenames that will break this (e.g. containing a single-quote character).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ca4711eff85d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
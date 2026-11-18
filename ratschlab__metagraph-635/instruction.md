# Issue

**Title:** README: modernize structure (logo, Quick start, MetaGraph Online)

## Description

Refresh the README with a native Conda installation, the current workflow wrapper and a complete build/query quick start. One shallow checkout supplies both the wrapper and example data. Retain direct CLI and Docker recipes, explain the index components, and link the hosted service with a measured MetaSUB example.

Use matching light/dark SVG logos in the README and documentation, update contributor credits, and clarify the BRWT clustering memory estimate.

The native quick start and count/coordinate workflows were exercised on Linux.

Prepared with Claude and Codex.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `83745dc22a61`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
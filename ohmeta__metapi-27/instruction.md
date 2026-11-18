# Issue

**Title:** Update checkm.smk

## Description

I found that problem happened in rule "checkm_lineage_wf": Command 'set -euo pipefail;  tar -czvf xxx/xxx/xx.data.tar xxx/xxx/xx/' returned non-zero exit. Suggest add "--warning=no-file-changed" to tar.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f55e79ecf99d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
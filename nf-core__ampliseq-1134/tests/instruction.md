# Issue

**Title:** Run the conda tests on runners with 32 GB of memory

## Description

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [x] `CHANGELOG.md` is updated.

## Description

The conda shard that runs `-profile test_savont` is cancelled with "The runner has received a shutdown signal" about 30 s after `DADA2_TAXONOMY` starts.
It was cancelled in every attempt on the 3.1.0 release PR (#1128) and in earlier runs.

DADA2 `assignTaxonomy` with GTDB R07-RS207 reaches about 11 GB resident, and the conda environment build for QIIME2 runs alongside at 2.4 to 5.4 GB.
Together this exceeds the 15.7 GB of the 4 CPU runner.
Conda has no memory cap, unlike the container engines.
The same shard passed only when runs-on happened to pick an `m7a` instance.

Conda jobs now use the `ram=32+64` runner (32 GB).
Other profiles keep `4cpu-linux-x64`.
Conda jobs run on PRs to `master` only.

The peak was measured on a separate machine, not on the CI runner.
This PR's own CI does not run the conda tests (it targets `dev`), so whether this fixes the shard will show on #1128 once this is merged.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01PYuhWC4HE6BP63fnsVQZHN

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0cd3c141623d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
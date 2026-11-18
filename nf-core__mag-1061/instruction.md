# Issue

**Title:** perf: speed up binning by not waiting for all mapping jobs

## Description

This is performance/QoL improvement.

Right now, binners have to wait for every `BOWTIE2_ASSEMBLY_ALIGN / MINIMAP2_ASSEMBLY_ALIGN` to finish, because `groupTuple(by:0)` doesn't know how many elements will be in the tuple.

In practice this means a couple of straggler alignment jobs stall the entire shortread (or longread) binning path, even for assemblies whose mappings already completed. This inflates runtimes and makes resource usage suboptimal.

Fix: the mappings per assembly are predictable from `binning_map_mode` (own -> 1, group -> samples in group, all -> total samples). We compute that count and wrap the key with `groupKey(key, count)`, so each group is released as soon as it's complete.

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/mag/tree/main/.github/CONTRIBUTING.md)
- [ ] If necessary, also make a PR on the nf-core/mag _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [ ] Make sure your code lints (`nf-core pipelines lint`).
- [x] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [ ] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `49e54010efc7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Implement proper Martingale strategy for memory

## Description

<!--
# jhuapl-bio/taxtriage pull request

Many thanks for contributing to jhuapl-bio/taxtriage!

Please fill in the appropriate checklist below (delete whatever is not relevant).
These are the most common things requested on pull requests (PRs).

Remember that PRs should be made against the dev branch, unless you're preparing a pipeline release.

Learn more about contributing: [CONTRIBUTING.md](https://github.com/jhuapl-bio/taxtriage/tree/master/.github/CONTRIBUTING.md)
-->

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
  - [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/jhuapl-bio/taxtriage/tree/master/.github/CONTRIBUTING.md)
  - [ ] If necessary, also make a PR on the jhuapl-bio/taxtriage _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [ ] Make sure your code lints (`nf-core lint`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [ ] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

___

I noticed that the memory requirements were being calculated in a manner that was _linear_, not _exponential_, for some processes.
This caused the first attempt of these processes to request twice as much memory as had been intended in the configuration.
In this PR, I implemented an exponential calculation for the memory requirements in question, similar to the [Martingale strategy](https://en.wikipedia.org/wiki/Martingale_\(betting_system\)).
These changes should be mostly transparent for cloud/cluster users.

I did have a question about the `KRAKEN2_KRAKEN2` process: This process's memory requirement is defined in two places (`conf/base.config` and `conf/modules.config`), but the requirements don't agree with each other.
Currently, the memory requirement in `conf/modules.config` overrides that in `conf/base.config`.
Should one of them be deleted, or should one of them be changed to match the other?
Until this question is answered, I will keep this PR in draft status.

Here are a few notes summarizing the existing and proposed calculations:

| `task.attempt` | Current calculation (code) | Proposed calculation (code)            | Proposed calculation (math, worked out)                                                                             |
|----------------|----------------------------|----------------------------------------|-------------------------------------------------------------------------------------------------------------|
| 1              | `72.GB * 1 * 2 = 144.GB`   | `72.GB * Math.pow(2, 1 - 1) =   72.GB` | $72 \mathrm{GB} \times 2^{(1-1)} = 72 \mathrm{GB} \times 2^0 = 72 \mathrm{GB} \times  1 =   72 \mathrm{GB}$ |
| 2              | `72.GB * 2 * 2 = 288.GB`   | `72.GB * Math.pow(2, 2 - 1) =  144.GB` | $72 \mathrm{GB} \times 2^{(2-1)} = 72 \mathrm{GB} \times 2^1 = 72 \mathrm{GB} \times  2 =  144 \mathrm{GB}$ |
| 3              | `72.GB * 3 * 2 = 432.GB`   | `72.GB * Math.pow(2, 3 - 1) =  288.GB` | $72 \mathrm{GB} \times 2^{(3-1)} = 72 \mathrm{GB} \times 2^2 = 72 \mathrm{GB} \times  4 =  288 \mathrm{GB}$ |
| 4              | `72.GB * 4 * 2 = 576.GB`   | `72.GB * Math.pow(2, 4 - 1) =  576.GB` | $72 \mathrm{GB} \times 2^{(4-1)} = 72 \mathrm{GB} \times 2^3 = 72 \mathrm{GB} \times  8 =  576 \mathrm{GB}$ |
| 5              | `72.GB * 5 * 2 = 720.GB`   | `72.GB * Math.pow(2, 5 - 1) = 1152.GB` | $72 \mathrm{GB} \times 2^{(5-1)} = 72 \mathrm{GB} \times 2^4 = 72 \mathrm{GB} \times 16 = 1152 \mathrm{GB}$ |

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `94830715e6d0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
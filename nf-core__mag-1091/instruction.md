# Issue

**Title:** chore: tweak process resources

## Description

Update process resources based on four benchmark runs of the pipeline, comparing measured usage from the Nextflow traces and execution reports against what each process reserves.

## Resource change reasoning

### Walltime increases to avoid known retries

`PYPOLCA_RUN`, `BUSCO_BUSCO` and `MULTIQC` each had tasks killed at exactly their time limit and then succeed on retry, so the first attempt was pure waste.

### CPU increases where the tool was saturating its allocation

`BOWTIE2_ASSEMBLY_ALIGN` and `BOWTIE2_PHIX_REMOVAL_ALIGN` both ran at essentially 100% CPU efficiency, meaning they were CPU-bound. Assembly align was also the largest wall-clock consumer among the aligners, so it benefits most.

### CPU reductions where the cores were never used

`GTDBTK_CLASSIFYWF`, `BUSCO_BUSCO`, `MINIMAP2_ASSEMBLY_ALIGN` and `CHOPPER` all reserved more cores than any task ever used. GTDB-Tk is the extreme case effectively single-threaded, consistent with `--gtdbtk_pplacer_cpus 1`, so its 10-core path is kept only for `single_job` mode, which the benchmark did not test.

### Memory reductions where the reservation was far above the peak

Several processes reserved one to two orders of magnitude more than they ever touched. Reductions keep clear headroom over the observed peak. Most of these tools are expected to have low memory footprint: `PROKKA`, `PRODIGAL`, etc.

### Memory increases where the peak met or exceeded the reservation

`BUSCO_BUSCO` and `MULTIQC` were both running at or above their limit; MULTIQC in particular spent four hours thrashing before being killed and then finished in minutes once the retry gave it more.

## Resource customization reordering

Named customisations are now sorted alphabetically with a comment recording the convention, and `docs/usage/resource_guidance.md` is regenerated to match.

## PR checklist

- [ ] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/mag/tree/main/.github/CONTRIBUTING.md)
- [ ] If necessary, also make a PR on the nf-core/mag _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [ ] Make sure your code lints (`nf-core pipelines lint`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [ ] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0cc93e198a7a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
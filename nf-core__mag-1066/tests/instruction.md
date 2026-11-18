# Issue

**Title:** perf: remove remaining lockings from mag

## Description

This is (hopefully) the last of my optimization-related PRs. It removes the remaining channel "locks" in the binning -> QC -> downstream path, points where a size-less `groupTuple()` forces every upstream task to finish before anything downstream can start.

1. **seqkit / bin length filtering**
	seqkit was still locking the pipeline via the `groupTuple()` that regrouped bins to decide which pass the length filter. On top of that, I'd forgotten to drop the `.transpose()` from the previous PR, so seqkit was running per bin instead of per binner batch. This refactors that section so each binner batch runs seqkit on its whole output at once and is filtered independently.

2. **QUAST**
	The input to QUAST_BINS was regrouped with a size-less `groupTuple()`, blocking it until all binning finished. Since each entry there already has a unique key, the `groupTuple()` was just reshaping single items, so I replaced it with a plain `.map`.

3. **Bin QC -> GTDB-Tk**
	Bin QC + GTDB-Tk was another locking point: GTDB-Tk needs the QC metrics to decide which bins are evaluated for taxonomy, and it consumed the concatenated QC summaries (all bins). To operate per binner batch, I changed BIN_QC to emit the per-group, per-tool QC summaries directly, and gave GTDB-Tk's `groupTuple` a size (the number of the qc tools enabled), so each GTDB-Tk job fires as soon as its QC finishes.

Snapshot effect: fewer seqkit processes (now per binner batch, not per bin), nothing more.

Here's a timeline of a test run. It shows no more locking points (all processes are well mixing and overlapping).
[execution_timeline_2026-07-03_09-02-54.html](https://github.com/user-attachments/files/29635600/execution_timeline_2026-07-03_09-02-54.html)

We also got nice CI time cutoffs from this: on average 23% less time compared to yesterday's runs like https://github.com/nf-core/mag/actions/runs/28590406418/


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
- [x] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `03de3381b1e8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
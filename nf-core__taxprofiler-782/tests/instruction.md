# Issue

**Title:** Save analysis-ready FASTQs for every host removal route

## Description

.

With host removal on, `--save_analysis_ready_fastqs` missed the host-removed reads:

- minimap2: SAMTOOLS_FASTQ writes `*_other.fastq.gz`, but the pattern was `*.fq.gz`
- deacon and hostile: no `analysis_ready_fastqs` entry at all

I've added the missing entries and fixed the pattern. DEACON_FILTER now also uses `${meta.id}_${meta.run_accession}` as its prefix, like the other host removal steps, because runs from the same sample were overwriting each other in `deacon/filter/`. That also changes melon's output names and sylph's report for single-run samples, so the `default` snapshot is updated too.

To test it, `save_analysis_ready_fastqs` is now on in `test_falcobbduk` (bowtie2 and minimap2), `test_alternativepreprocessing` (hostile) and `test_fastpnonpareilkrakenuniq` (deacon). I got the new file names for bowtie2/minimap2 and deacon from local runs. Hostile runs out of memory on my machine, so I worked out its names from how prinseq++ and hostile name their outputs, and CI will confirm those.

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] If you've fixed a bug or added code that should be tested, add tests!
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [x] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.

This was AI-assisted (Claude Code). I've gone through all the changes and test runs myself and understand them.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3b8595987ede`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
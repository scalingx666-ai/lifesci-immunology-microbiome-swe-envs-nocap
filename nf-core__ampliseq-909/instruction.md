# Issue

**Title:** Add truncq parameter for quality score-based read truncation

## Description

<!--
# nf-core/ampliseq pull request

Many thanks for contributing to nf-core/ampliseq!

Please fill in the appropriate checklist below (delete whatever is not relevant).
These are the most common things requested on pull requests (PRs).

Remember that PRs should be made against the dev branch, unless you're preparing a pipeline release.

Learn more about contributing: [CONTRIBUTING.md](https://github.com/nf-core/ampliseq/tree/master/.github/CONTRIBUTING.md)
-->

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [ ] ~~If you've fixed a bug or added code that should be tested, add tests!~~ I don't think this warrants an addition of an automated test.
- [ ] ~~If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/ampliseq/tree/master/.github/CONTRIBUTING.md)~~ Did not add a new tool
- [ ] ~~If necessary, also make a PR on the nf-core/ampliseq _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.~~ N/A
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [x] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [x] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [ ] ~~Usage Documentation in `docs/usage.md` is updated.~~ No relevant docs in `docs/usage.md`. Other relevant docs are updated.
- [ ] ~~Output Documentation in `docs/output.md` is updated.~~ No relevant docs in `docs/output.md`. Other relevant docs are updated.
- [x] `CHANGELOG.md` is updated.
- [ ] ~~`README.md` is updated (including new tool citations and authors/contributors).~~ N/A


Adds a parameter,`--truncq`, that allows read truncation by quality score, where each read is truncated at the first instance of a quality score less than or equal to `truncq`. The parameter is equivalent to `truncQ` in DADA2's [filterAndTrim](https://rdrr.io/bioc/dada2/man/filterAndTrim.html) method. `truncq` defaults to 2, which was already the default in the DADA2_FILTNTRIM module (https://github.com/nf-core/ampliseq/blob/2.14.0/conf/modules.config#L142).
In the DADA2 filtering and trimming steps, the truncQ parameter is applied before read length truncation for both [single](https://github.com/benjjneb/dada2/blob/ab844341c47d8fe922c2e9dea849bf2167bcd445/R/filter.R#L669-L684) and [paired](https://github.com/benjjneb/dada2/blob/ab844341c47d8fe922c2e9dea849bf2167bcd445/R/filter.R#L1031-L1068) reads.

The primary rationale for adding this parameter is to better handle ITS amplicons, but this parameter is applicable for any kind of amplicon e.g. 16S. Since ITS amplicons are variable-length by fungal species, it doesn't make sense to truncate all the reads to the same length using the `--trunclenf` and `--trunclenr` parameters. Truncation by quality score is an option to apply consistent truncation criteria while not having to do fixed-length truncation. In our lab's experiments so far using `truncq` and setting `trunclenf` and `trunclenr` to 0 (turning read length truncation off), we've found that a `truncq` value between 2 and 8 works best for Illumina paired-end reads (MiSeq v3 600 cycle kit). For more context, see the [thread on the nf-core #ampliseq channel](https://nfcore.slack.com/archives/CEA7TBJGJ/p1741801358033799).

Quality score truncation (using `--truncq`) and read length truncation (using `--trunclenf` and `--trunclenr`) all happen as part of the same DADA2 filterAndTrim method. If `--trunc_qmin` and `---trunc_rmin` are used to automatically calculate `trunclenf` and `trunclenr`, these values are determined using the read metrics calculated on the read input before DADA2 filterAndTrim is called, and so before `truncq` is applied. I added documentation accordingly, but if I need to make any further changes or rework how `truncq` interacts with the other read truncation parameters, please let me know.

Since I made some minor additions to `summary_report.html`, here is an example of the text in the relevant sections of the report, after running with the test profile with this command: `nextflow run ../../ampliseq/main.nf -profile test,singularity --truncq 7 --outdir .` New portions are _italicized_.

> Additional quality filtering can improve sequence recovery. Often it is advised trimming the last few nucleotides to avoid less well-controlled errors that can arise there. _Each read was truncated at the first instance of a quality score less than or equal to 7._ Reads were trimmed to a specific length and the length cutoff was automatically determined by the median quality of all input reads. Reads were trimmed before median quality drops below 25 and at least 75% of reads are retained, resulting in a trim of forward reads at 230 bp and reverse reads at 229 bp, reads shorter than this were discarded. Reads with more than 2 expected errors were discarded. Read counts passing the filter are shown in section ‘Read counts per sample’ column ‘filtered’.

> Data quality was evaluated with FastQC (Andrews, 2010) and summarized with MultiQC (Ewels et al., 2016). Cutadapt (Marcel et al., 2011) trimmed primers and all untrimmed sequences were discarded. Sequences that did not contain primer sequences were considered artifacts. Less than 27.5% of the sequences were discarded per sample and a mean of 86.3% of the sequences per sample passed the filtering. Adapter and primer-free sequences were processed sample-wise (independent) with DADA2 (Callahan et al., 2016) to eliminate PhiX contamination, _truncate reads at the first instance of a quality score less than or equal to 7_, trim reads (before median quality drops below 25 and at least 75% of reads are retained; forward reads at 230 bp and reverse reads at 229 bp, reads shorter than this were discarded), discard reads with > 2 expected errors, correct errors, merge read pairs, and remove polymerase chain reaction (PCR) chimeras; ultimately, 347 amplicon sequencing variants (ASVs) were obtained across all samples. Between 55.34% and 59.02% reads per sample (average 57%) were retained. The ASV count table contained in total 4921 counts, at least 1030 and at most 1387 per sample (average 1230).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0e7289dfc2f6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** KrakenUniq pathnames fix

## Description

Hi!! I can't say I completely understand how Nextflow works, but I was getting this fatal error, only running one sample in my samplesheet:

```
Apr-28 12:48:50.050 [Actor Thread 8] ERROR nextflow.processor.TaskProcessor - Error executing process > 'NFCORE_TAXPROFILER:TAXPROFILER:PROFILING:KRAKENUNIQ_PRELOADEDKRAKENUNIQ (microbialdb|1)'

Caused by:
  assert sequences.size() == prefixes.size()
         |         |         |        |
         |         7         |        1
         |                   ["RAMAN_R003_R003.se"]
         [sequences/scratch, sequences/s.2010961, sequences/taxprofiler, sequences/work, sequences/28, sequences/e0e6667e4f763ccf7733cd7cc7e474, sequences/RAMAN_R003_R003.unmapped_other.fastq.gz] -- Check script '/home/s.2010961/.nextflow/assets/nf-core/taxprofiler/./workflows/../subworkflows/local/../../modules/nf-core/krakenuniq/preloadedkrakenuniq/main.nf' at line: 47
```


With more than one sample, I was having a "file name collision" error, probably because it was splitting at every '/' and doing that to each sample in the samplesheet.

By placing [] around reads before it gets bundled with prefixes, sorted, placed into batches, etc, it solves the pathname from breaking apart. 

I'm not sure if anyone else has encountered this bug, but this has fixed the pipeline for me! I can now run KrakenUniq successfully, with either one or multiple samples. 

My samplesheet looks like this:
```
sample,run_accession,instrument_platform,fastq_1,fastq_2,fasta
RAMAN_R003,R003,OXFORD_NANOPORE,/scratch/scw1409/RAMAN/RAMAN_R003/RAMAN_R003.fastq.gz,,
```

databases.csv:
```
tool,db_name,db_params,db_type,db_path
krakenuniq,microbialdb,,long,/scratch/scw1409/dbs/KrakenUniq
```

I hope this is helpful. If it's a unique (hehe) error just for me (a.k.a., if I have been doing something wrong), please let me know!!

<!--
# nf-core/taxprofiler pull request

Many thanks for contributing to nf-core/taxprofiler!

Please fill in the appropriate checklist below (delete whatever is not relevant).
These are the most common things requested on pull requests (PRs).

Remember that PRs should be made against the dev branch, unless you're preparing a pipeline release.

Learn more about contributing: [CONTRIBUTING.md](https://github.com/nf-core/taxprofiler/tree/master/.github/CONTRIBUTING.md)
-->

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] Make sure your code lints (`nf-core pipelines lint`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [ ] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6dd7b434bac6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
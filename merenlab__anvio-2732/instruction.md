# Issue

**Title:** Snakemake Workflows: create subdirs for logs before we start running things

## Description

There was a recent change to the snakemake workflows: log files are now organized into subdirs within the overall log output directory, first by workflow name and then by rule. Creating directory structures like this:
```
00_LOGS/sra_download/check_md5sum  
00_LOGS/sra_download/fasterq_dump  
00_LOGS/sra_download/pigz  
00_LOGS/sra_download/prefetch
```

This works fine when the workflow is run locally, because snakemake handles the directory creation as needed. But we usually run these workflows on an HPC using [`clusterize` ](https://github.com/merenlab/clusterize) -- and `clusterize` will not let a job start if the log's directory doesn't exist when you submit it. This led to job submission errors like `00_LOGS/sra_download/prefetch isn't a directory so clusterize is unwilling to set 00_LOGS/sra_download/prefetch/SRRXXXXXX_prefetch.log as the output file`.

To fix it, this PR adds two lines of code so that snakemake will create the log file subdirectories before starting.

It makes one subdir for each rule in `self.rules`. The only problem is that this variable contains all possible rules for the workflow -- not just those that actually run. Which means the log directory gets populated with a bunch of subdirs that stay empty. To address this, I added a cleanup step that runs after the workflow finishes and `rmdir`s any empty log subdirectory.

I'm currently testing it using the SRA download workflow, but I think we also need to test it at least with metagenomics (particularly to ensure the cleanup step works, as that workflow has a LOT of rules that we hardly ever run).

If you can think of a better alternative fix than this, let me know.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f1637efc7712`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
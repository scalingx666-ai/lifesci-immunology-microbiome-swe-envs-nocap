# Issue

**Title:** Only annotate

## Description

I want to run the nextflow w/o the virus detection part. Let's say I have a FASTA with viruses sequences that I just want to annotate and not filter for putative virus signals. 

This is now implemented in the nextflow via the flag

```
--onlyannotate
```

If the flag is set, the detection sub-workflow will be skipped. Renaming and Length filtering will be still applied. 

I also added `--viphog_version` and `--meta_version` because Guillermo and I are currently testing the different model versions we have. With the flags, I can more easily switch between the different tables (this is more a development thing)

I thought you might be interested in the changes, so please have a look, and if you are fine please feel free to merge this into master.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `98aa9ad8ae69`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
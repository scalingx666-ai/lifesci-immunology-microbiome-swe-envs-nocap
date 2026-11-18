# Issue

**Title:** Prase.nf results are optional.

## Description

This is to prevent the pipeline from "failing" when there are no viral annotations.

With these changes, the pipeline now finishes in the parse.nf step and produces partial results:

```bash
$ ls -l results
total 2511
drwxrwsr-x 2 mbc metagen    4096 Apr 30 19:05 01-viruses
drwxrwsr-x 2 mbc metagen    4096 Apr 30 19:06 08-final
-rw-rw-r-- 1 mbc metagen 1285574 Apr 30 19:00 MGYG000437699_renamed.fasta
-rw-rw-r-- 1 mbc metagen 1285574 Apr 30 19:00 MGYG000437699_renamed_filt1500bp.fasta
-rw-rw-r-- 1 mbc metagen       0 Apr 30 19:06 virsorter_metadata.ts

$ cat results/08-final/MGYG000437699_virus_predictions.log 
Overall, no putative _viral contigs or prophages were detected in the analysed metagenomic assembly
PPR-Meta found 0 low confidence contigs.
Virus Finder found 0 high confidence contigs.
Virus Finder found 0 low confidence contigs.
Contig has an invalid category : 6
Virus Sorter found 0 high confidence contigs.
Virus Sorter found 0 low confidence contigs.
Virus Sorter found 0 putative prophages contigs.
```

The current behaviour is confusing, as nextflow will mark the pipeline as failed even though it's not a "runtime" error, it's just that there are no viral sequences found.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6483cbfea77b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
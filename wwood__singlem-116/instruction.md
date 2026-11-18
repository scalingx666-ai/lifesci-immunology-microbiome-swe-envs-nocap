# Issue

**Title:** Enable appraise to use default metapackage

## Description

Default metapackage seems to load ok, although get "Unknown search method naive" error. Presumably due to recent changes?

```
12/12/2022 01:42:35 PM INFO: Retrieval successful. Location of backpack is: /home/aroneys/s/aroneys/db/SingleM/S3.0.5.metapackage20220806.smpkg.zb
12/12/2022 01:42:35 PM INFO: Loaded 59 SingleM packages
12/12/2022 01:42:36 PM INFO: Read in 3377 markers from the different genomes
...
12/12/2022 01:42:37 PM INFO: Finished singlem DB creation
Traceback (most recent call last):
  File "/home/aroneys/m/users/aroneys/.conda/envs/singlem-dev/bin/singlem", line 7, in <module>
    exec(compile(f.read(), __file__, 'exec'))
  File "/mnt/hpccs01/scratch/microbiome/aroneys/src/singlem/bin/singlem", line 867, in <module>
    app = appraiser.appraise(genome_otu_table_collection=genomes,
  File "/mnt/hpccs01/scratch/microbiome/aroneys/src/singlem/bin/../singlem/appraiser.py", line 56, in appraise
    sample_to_binned = self._appraise_inexactly(
  File "/mnt/hpccs01/scratch/microbiome/aroneys/src/singlem/bin/../singlem/appraiser.py", line 140, in _appraise_inexactly
    queries = querier.query_with_queries(metagenome_collection, sdb_tmp, max_divergence, 'naive', SequenceDatabase.NUCLEOTIDE_TYPE, 1, None, True, None)
  File "/mnt/hpccs01/scratch/microbiome/aroneys/src/singlem/bin/../singlem/querier.py", line 167, in query_with_queries
    raise Exception("Unknown search method {}".format(search_method))
Exception: Unknown search method naive
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6e41d3273c7d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
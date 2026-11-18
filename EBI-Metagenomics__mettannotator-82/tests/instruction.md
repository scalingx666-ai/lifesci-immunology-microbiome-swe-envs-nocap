# Issue

**Title:** include logic to remove proteins annotated with ProtNLM from uniref dbs

## Description

Remove clusters of proteins annotated with ProtNLM, and also fix some bugs identified by LLMs:

#### Download breaks at every UniProt release

UniProt only serves the current release as FASTA, so we now host our own copy of each release: `tool-dbs/<db>_protnlm_filtered/<db>_protnlm_filtered_<release>.tar.gz`. Now the `reference-databases-preprocessing--pipeline` contains the logic to generate the database () and `DIAMOND_GETDB` downloads the release set in `diamond_unirefX_db_version`. 

#### Old db folders hard-fail with a bare missing-file

If `$params.dbs/uniref90` (or `uniref50`) exists without `db.filtered.dmnd`, the run stops with a message saying the folder predates the ProtNLM filtering and must be deleted.

Some points are also fixed on `reference-databases-preprocessing--pipeline`

#### An empty ID list silently produces a meaningless db
  
The filter uses `FILENAME==ARGV[1]` instead of `NR==FNR`, and `PROTNLM_GETIDS` fails if `protnlm_ids.txt` is empty. Covered by an nf-test.

#### The awk can over-match and double-count

Only the first top-level `RecName`/`SubName` of each entry is checked, since that is the name UniRef uses for the cluster. Each ID is printed once. Covered by an nf-test (ProtNLM name in second place, duplicate names, ProtNLM inside `Contains:`).

#### Runtime and retries in PROTNLM_GETIDS

TrEMBL processing moved out of mettannotator, so users never stream TrEMBL. In the preprocessing pipeline, inputs are downloaded once to the work dir, so retries and `-resume` don't download them again. The ProtNLM ID list is published as a record of what was removed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `82eb121b7cd5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
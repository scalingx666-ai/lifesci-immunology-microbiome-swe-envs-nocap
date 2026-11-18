# Issue

**Title:** Colabfold for anvi-gen-structure-database

## Description

anvi-gen-structure-database could previously predict protein structures only one way: template-based homology modelling with MODELLER (or importing pre-computed structures). This PR adds ColabFold (AlphaFold2) as a second prediction engine, selectable at run time with a new --engine {modeller,colabfold} flag (default modeller, so existing behavior is unchanged).

## What is new
```bash
# online MSA (public MMseqs2 server) good for a handful of sequences
anvi-gen-structure-database -c CONTIGS.db --engine colabfold \
                            --colabfold-conda-env colabfold \
                            --colabfold-msa-server \
                            --gene-caller-ids 1,2,3 -o STRUCTURE.db

# local MSA (recommended for many sequences)
anvi-gen-structure-database -c CONTIGS.db --engine colabfold \
                            --colabfold-conda-env colabfold \
                            --colabfold-db /path/to/colabfold_db \
                            --gene-caller-ids 1,2,3 -o STRUCTURE.db
```

New flags (in a COLABFOLD PARAMS group): --colabfold-conda-env, --colabfold-msa-server, --colabfold-db, --num-recycle, --amber, --colabfold-additional-parameters. --num-models and --skip-DSSP are shared across engines and were moved into a new SHARED PREDICTION PARAMS group.

## Some decisions were made:
- If --colabfold-conda-env is given, every ColabFold command is prefixed with conda run -n <NAME>, otherwise the programs are expected to be directly on the $PATH.
- MSA source is explicit. The user must choose the online server (--colabfold-msa-server) or a local database (--colabfold-db).
- All genes are predicted in a single batched ColabFold run rather than one-process-per-gene (as MODELLER uses). This is far more efficient on a GPU: ColabFold batches internally and reuses the compiled model across sequences.
--num-threads is the boss and overwrite all defaults from colabfold.
- The driver is split into run_search() / run_batch() methods so a future --only-msa / --only-predict checkpoint can be added.

## Update to the structure database (v2 to v3)

ColabFold reports different confidence metrics than MODELLER, so the schema was extended:

- models table: added mean_plddt and ptm (NULL for MODELLER/external rows; MODELLER's molpdf/GA341_score/DOPE_score stay NULL for ColabFold rows).
- residue_info table: added per-residue plddt (NULL for non-ColabFold structures).
- The DB now records which engine produced it.
- anvio/migrations/structure/v2_to_v3.py adds the columns (NULL for existing data) and tags existing databases as engine = "modeller" or "external" (guessable from the old db).

## Test
Added a small test in the component test for SCVs / SAAVs and structure database.

But in reality I only tested it on my laptop (no GPU) for now, with colabfold on the path. So still need to test:
- [x] conda env
- [x] using local colabfold database rather than the online MSA server
- [x] with actual GPU available

## Follow ups:
- anvi-update-structure-database does not support ColabFold DBs yet and raises a clear error directing users to create a new DB
- the --only-msa / --only-predict checkpoint split is coming later.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7000aa5b86a7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
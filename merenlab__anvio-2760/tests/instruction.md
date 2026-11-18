# Issue

**Title:** Checkpoint structure colabfold

## Description

Third PR regarding the integration of ColabFold (follows #2755 and #2759).
Colabfold has two distinct halves: the MSA generation (CPU heavy) and the structure prediction with AlphaFold2 (GPU heavy). And when you scale to many protein prediction, you may want to run these two step separately on different machinery with dedicated resources. 

So we add two flags to `anvi-gen-structure-database`: 
- `--only-msa` runs the MSA step and stops. The intermediary files and a manifest json are stored in the --dump-dir (required flag in this mode). No structure generated here. Only work with a local colabfold database as the public MSA server is fused with the prediction and cannot be split.
- `--only-predict` resumes from `--only-msa` checkpoint, predict structure and generate the structure database.

The checkpoint guard:
`--only-predict` takes the same contigs.db and gene of interest as the `--only-msa` counterpart. Before the prediction, it checks the fasta and contigs.db hash against the manifest and any mismatch, like a different contigs.db, different gene selection, or even edited genes is a hard error. WE DON'T WANT TO SILENTLY PRODUCE GARBAGE.

Testing needed:
- [x] run on server with local colabfold database (untestable locally)
  - [x] --only-msa
  - [x] --only-predict

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `66d21dff1a6f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
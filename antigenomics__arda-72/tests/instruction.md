# Issue

**Title:** Correct the memory guidance: peak RSS tracks repertoire richness, not read depth

## Description

The delivered docs claim arda is **"very low-memory (< 400 MB peak RSS, independent of read depth)"** in four places — README, `docs/pipeline_integration.rst`, and both the Nextflow module's README and its `process` comment.

That was measured before the Stage-3 assembler landed in 2.4.0. It is no longer true, and it is wrong in the direction that hurts: **Stage 3 holds the clone set in memory, so peak RSS follows repertoire richness.**

Measured at full depth, 32 cores, `arda rnaseq run --assemble`:

| reads | clonotypes | wall | peak RSS |
|---|---|---|---|
| 104.9 M (2×150) | 28,444 | 46 min | **2,707 MB** |
| 153.9 M (2×100) | 1,519 | 51 min | 511 MB |
| 138.5 M (2×100) | 30 | 45 min | **314 MB** |

The third sample has *more* reads than the first and uses 9× less RAM. Mapping alone is still flat (~300–400 MB at any depth) — it's the assembly + correction stage that scales.

Docs now say: budget **~4 GB** for a lymphocyte- or B-cell-rich sample, ~1 GB for a cold one, and `--no-assemble` restores the flat mapping-only profile under a hard memory cap.

Caught while collecting the 2.5.5 full-depth numbers. Someone sizing a SLURM or Nextflow memory directive off the old claim would have been OOM-killed on exactly the kind of sample arda exists for.

Docs build clean under `-W`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f677141dd705`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
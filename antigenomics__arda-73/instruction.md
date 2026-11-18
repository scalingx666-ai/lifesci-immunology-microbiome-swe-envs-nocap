# Issue

**Title:** 2.5.6: lock the reference fetch and swap `vdj/` in atomically

## Description

2.5.5 made the mmseqs **index** build safe under concurrency. The **reference fetch** that runs immediately before it had the same disease — and it is the worse of the two.

## Why it matters

`paths.database_dir` decides *"is the reference already here?"* by testing whether `<cache>/database/vdj/` is a directory. **Its mere existence is the gate.** So anything that lets `vdj/` become visible before it is complete doesn't produce a slow download or a crash — it makes every *other* arda process search an **incomplete reference** and report success over nothing. Same silent-success failure mode as the 0-byte index.

## Two things let it happen

**No lock.** arda is routinely run concurrently against the same cache — the Nextflow module launches one process per sample, a SLURM array one per task. On first use in a fresh environment all of them fetched into the same path at once.

**A cross-filesystem move.** The old code extracted into `/tmp` and called `shutil.move`. That is a rename only *within* one filesystem; across a boundary it silently degrades to a recursive **copy** — and `/tmp` and `~/.cache` normally are two different filesystems. So `vdj/` was populated **file by file**, in full view of everyone else. It also `rmtree`'d the existing tree before writing the new one, deleting files a concurrent reader could be mid-search on.

## The fix

Hold a build lock; extract into a staging dir **inside the destination** (so the swap is a rename, not a copy); publish with a single `os.replace`. `vdj/` is either absent or complete — never in between. Under `--force` the old tree is *renamed* aside rather than deleted, so a reader still holding its files keeps them.

The lock is now **one** implementation (`arda._locking.build_lock`) shared by the fetch and the index build, instead of two copies of the same loop.

## Tests

Two of the four **fail against the old code** (no lock; staging outside the destination).

The partial-visibility test is deliberately honest about its limit: it catches any file-by-file materialization (verified — swap the `os.replace` for a `copytree` and it reports `PARTIAL: 5 of 12`), but it *cannot* reproduce the cross-filesystem case on a same-filesystem test machine, because there `shutil.move` is already an atomic rename. That is exactly why the sibling-staging assertion exists, and the docstring says so rather than implying coverage it doesn't have.

Verified live: fetch into an empty cache pulls all 5 organisms, leaves no staging or lock dirs, and a second call is a no-op.

## Also

- `seqtree>=0.4` (was `>=0.2`). Clonotype output unchanged — `examples/rnaseq/clones.tsv` reproduces bit-for-bit.
- Version → 2.5.6, CHANGELOG.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f677141dd705`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
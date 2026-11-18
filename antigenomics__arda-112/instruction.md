# Issue

**Title:** A ledger for why a read did not map

## Description

`mapped_fraction` on its own made three different diagnoses into one number — the wrong organism,
a library with almost no receptor content, and a `--min-score` that is too strict — and those are
the three things it is usually asked to mean. This is the item roadmapped (not built) alongside
the QC work in #111, taken from MiXCR's align report.

## The ledger

`run/map` gains `unmapped.*`; the `sample` scope gains each bucket as a fraction of `total_reads`,
because a count of 788 says nothing beside another sample's 788.

| bucket | remedy it points at |
|---|---|
| `prefilter_rejected` | the k-mer screen is eating the library |
| `no_hit` | not a receptor read — or the wrong `--organism` across a whole batch |
| `hit_not_in_reference` | index/reference mismatch, not biology |
| `constant_only` | normal on a long insert; R2 sits in C and donates its isotype |
| `below_min_score` | the cutoff is doing the rejecting, not the library |
| `accounted` | `mapped_reads` + every bucket. **Should equal `total_reads`.** |

`no_hit` and `hit_not_in_reference` are separated because to the caller they are the same missing
row and completely different problems. The second is how 2.23.0's first-run defect presented —
every segment target resolving to `None` against a reference loaded before its markup was written
— and from outside it was a low mapped fraction and exit 0.

## Two things that would have made it silently wrong

**`accounted` is recomputed on a shard merge, not summed.** Summing is right only by coincidence,
and a shard whose own ledger was short would make the merged one look balanced — the one thing a
ledger must not do.

**`constant_only` counts reads, not fragments.** `_apply_constant_rule` also drops the
constant-only *mate* of a fragment it keeps — the read whose isotype it has just donated — and
that record is never in `n_drop`. Using the fragment count left **45 of 1,320** reads on
`tests/data/rnaseq_real` in no bucket at all, which the balance assertion caught.

## Verification

- `ruff check src/` clean, `make -C docs html` (`-W`) zero warnings
- **1,086 passed**, 9 skipped (was 1,073) — 13 new across `tests/unit/test_unmapped_ledger.py`
  and `tests/synthetic/test_unmapped_ledger_real.py`
- On `tests/data/rnaseq_real`: 453 mapped + 788 + 8 + 54 + 17 = **1,320** = `total_reads`,
  and a four-read-group run reports a ledger **identical** to the single-file run
- Hot-path cost: two integer increments on the already-dropped branch, two list lengths per batch

## Not done, deliberately

Splitting `no_hit` into no-V / no-J / V-and-J-on-different-mates, as MiXCR does. That needs the
rejection reason to survive out of `_best_hits`, inside the per-read path. Roadmapped behind a
measurement rather than guessed at.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `554e1bd42646`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
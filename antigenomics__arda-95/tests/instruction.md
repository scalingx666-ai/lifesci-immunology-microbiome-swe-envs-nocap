# Issue

**Title:** arda 2.11.0 — amplicon parity with MiXCR, two AIRR fields gated on evidence

## Description

Round 18 of the arda-benchmark comparison. Every number below was measured on the same input file
in the same job as its comparator; the cluster arm ran on aldan3 across 25 staged datasets and two
full-depth libraries.

## Speed — amplicon parity reached, then passed

| library | before | after | MiXCR 4.7.0 |
|---|---|---|---|
| TRA amplicon 100 k, 8 threads | 6.84 s / 20.4 s CPU | **5.55 s / 13.0 s CPU / 649 MB** | 5.90 s / 45.2 s CPU / 3,027 MB |
| bulk RNA-seq 100 k, 8 threads | 3.18 s / 11.1 s CPU | **2.60 s / 5.4 s CPU / 234 MB** | 4.54 s / 31.8 s CPU / 3,022 MB |
| IGH_repertoire 100 k, 32 threads | 173.27 s / 2,381 MB | **79.52 s / 1,706 MB** | — |
| IGH_naive 100 k, 32 threads | 166.79 s / 2,313 MB | **64.83 s / 1,585 MB** | — |

The recorded "MiXCR is 5.0× faster on amplicon" reproduces exactly (29.89 / 5.90 s) — for arda's
**default** config. Nobody re-measured after `--fast-segments` took the amplicon search from 202 s
of CPU to 20 s.

## What changed

**`--v-only-on-segment`** (off by default, needs `--two-pass`). A `v_only` read carries no J, so it
is aligned against its own `V|<allele>` segment instead of 15,414 V×J scaffolds — 77 % of the
amplicon rescue set at 338 µs/read against 31 µs. MMseqs2 still aligns and still returns a real bit
score over the same nucleotides, so `--min-score` keeps its meaning.

⛔ The gate is geometry, and it took two attempts. Routing on the shortlist reason alone cost 77 of
213 bulk junctions. Gating on where the *alignment* stopped passed every local test and then lost
**45 of 88,697 junctions on IGH_repertoire** at cluster scale — an ungapped extension breaks early
under mismatch load, so the alignment end understates how far the read reaches. The shipped gate
projects the read's remaining 3′ bases along the same diagonal: **0 junctions and 0 clonotypes lost
on all five SHM datasets and at full depth** (1.9 M and 66 M pairs).

**Two AIRR fields were being emitted without evidence.**
- `junction`: all 1,396 amplicon disagreements with IgBLAST were a pure 5′ boundary offset (3′ end
  correct in 100 %, zero wrong regions), 643 of them `TRAV25` reads whose V was trimmed past its own
  Cys104. Precision among emitted junctions **.96953 → .99919**, zero cost on bulk IG.
- `j_call`: copied from the scaffold unconditionally, so a V-only read inherited its scaffold's J —
  1,823 of 2,737 bulk mapped reads. Precision bulk **.1129 → .7842**, amplicon **.9685 → .9953**.

**`build-db --allow-chimeras`** (off by default) builds the `TRDV × TRAJ` scaffolds the default
refuses. IgBLAST calls that pairing on 530 of 48,030 amplicon reads and MiXCR agrees, while arda
calls the same J as both and emits no `v_call` — 83 % of its remaining `v_gene` gap. Which side is
right is a domain judgement, so it is a flag. It recovers 34 of the 530 and **all 34 junctions are
byte-exact vs IgBLAST**; the ceiling is region markup on those scaffolds, not the flag.

**Four optimizations, all byte-identical output** (5.96 → 5.55 s, 6.9 %):
- `format_rows` → C++ in the existing `_markup` extension (0.365 → 0.171 s in-run)
- `transfer_hit` walks the alignment once, not four times (`transfer_regions` calls 207,007 → 54,178)
- `_empty_record` copies a prototype dict instead of rebuilding it (8.8×)
- `_common_prefix`/`_common_suffix` → C++

⛔ Upgrading pybind11 (3.0.4 → 3.1.0) was measured and buys **nothing** — the vectorcall work
already shipped in 3.0.2, which arda has. nanobind's ceiling on arda's call shape is 0.58 %.

## Tests

624 pass, 9 skipped. New regression tests express the junction and `j_call` gates directly as
records — no reference DB, no MMseqs2, nothing to skip — plus C++/Python equivalence for the
formatter and the string helpers.

Full write-up: `results/round18/README.md` in arda-benchmark.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9958fd16cf89`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
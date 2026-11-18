# Issue

**Title:** docs: what productive / stop_codon / vj_in_frame actually mean

## Description

The three AIRR productivity columns are the most misread ones arda emits, and nothing stated their scoping in one place. This adds `docs/productivity.rst` (Analysis nav) and a README section, taught with real GenBank reads rather than prose.

## The rule, stated once

| column | scope |
|---|---|
| `vj_in_frame` | `(fwr4_start - v_coding_start) % 3 == 0` — where the frame **lands at FR4**, which is what decides whether the constant exon translates |
| `stop_codon` | FR1–FR3, CDR1–CDR2, the junction **and** FR4 |
| `productive` | the conjunction |
| all three | **empty**, not `F`, when the read reached neither the junction nor FR4 — ~72 % of mapped bulk reads |

Flags, never filters.

## Why it needed examples

`JX277388.1` (mouse TRB, `TRBJ2-5*01`) carries two nucleotides germline does not have, so the J's 5′ germline residues and its own FR4 **cannot both** sit in the germline frame. arda lands on the FR4 side — the side the constant exon splices to — and splicing `TRBC2*01` on gives **0 stop codons over 375 nt** of real TRBC2 protein. `JX277345.1` is the same shape with one nucleotide. `X60894.1` is the other case: a J truncated to a single FR4 residue, which no tool can call from that read.

## The trap the page exists for

Matching a junction's 3′ tail against the called J's germline residues is **not** a frame test. It fires on 51.8 % of IGL, 51.4 % of IGK and 39.8 % of IGH rows (mean `v_identity` .955–.968) against 3.4 % of TRB and 7.1 % of TRA (.992) — it detects hypermutation reaching the J.

That trap produced a wrong verdict on these exact rows. Re-tested by the sound method (splice C on, count stops), **arda is right on all 8 rows** where it and IgBLAST disagree, and no `partial_nt` change is wanted. `ROADMAP.md` is corrected and that open decision is closed.

## Verification

- `tests/realworld/test_productivity_examples.py` — 7 tests asserting every claim the page makes, so the examples cannot rot (doc invariant 9)
- 1,095 passed, 9 skipped (was 1,088)
- `ruff check src/` clean
- `sphinx-build -W` zero warnings

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `be8f9a7a5557`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
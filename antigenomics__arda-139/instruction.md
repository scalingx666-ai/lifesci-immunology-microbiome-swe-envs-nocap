# Issue

**Title:** Answer the germline boundary in nucleotides (vdjtools#182)

## Description

`Cdr3Markup` gains `v_end_nt` / `j_start_nt`. `v_end` / `j_start` keep their residue
semantics and their caller — `dpost` slices the non-templated middle with them.

An exonuclease does not stop on a codon boundary, so the last residue a germline touches is
usually part germline and part N region, and an alignment on the **protein** can only round that
to a whole residue. What the protein still fixes is which nucleotides are admissible: 17 of the 20
residues open every one of their codons with the same base, so against a germline `GGA` (Gly) an
observed Glu can only be `GAA` or `GAG` — both begin with the germline's `G`, so the germline
demonstrably reaches one nucleotide further. Where a residue's codons disagree they are weighed by
how far each lets the germline reach: a templated nucleotide is free, one that matches by chance
costs 1/4.

Measured on the **8,133** VDJdb human TRB junctions whose boundary every observation in
`isalgo/airr_control`'s `human.trb.ntvj` agrees on:

| quantity | 2.30.1 | this |
|---|---:|---:|
| `v.end`, VDJdb residues `(nt + 1) // 3`, exact | 5,839 (71.79 %) | **7,556 (92.91 %)** |
| `j.start`, VDJdb residues `ceil(nt / 3)`, exact | 7,968 (97.97 %) | 7,968 (97.97 %) |
| V boundary in nucleotides, exact | 2,355 (28.96 %) | **6,538 (80.39 %)** |
| J boundary in nucleotides, exact | 2,462 (30.27 %) | **6,057 (74.47 %)** |

VDJdb's legacy k-mer scanner measures 71.8 % on the same set — the same number as 2.30.1, because
both answer in whole residues. `j.start` cannot move and does not: VDJdb defines it as the first
**fully** J-templated residue, which is the same residue whether the germline reaches one or two
nucleotides into the one before it.

The two sides are bounded by different things. The V residue count is right on 83.99 % of records
and the extension on **95.71 %** of those, so V is limited by the protein alignment — the residual
is a synonymous codon inside the templated run, which breaks the nucleotide match while leaving the
amino-acid match intact. The J count is right on 97.97 % and the extension on **76.02 %**, because
the nucleotide a J boundary turns on is the codon's third, the one the genetic code leaves free.

Closes part of `antigenomics/vdjtools#182`; `vdjtools` consumes this next.

1,190 unit tests pass, `ruff` clean, `sphinx -W` green. 14 new tests in
`tests/unit/test_cdr3fix_boundary.py`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d82a3c4f043a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
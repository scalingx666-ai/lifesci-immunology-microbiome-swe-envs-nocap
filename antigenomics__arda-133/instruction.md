# Issue

**Title:** fix: the amino-acid V/J boundary stops where germline evidence stops

## Description

`_align` picks the best-scoring cell and, on a tie, preferred consuming more
query. A tie means the extra residues paid nothing, so crediting them to the
segment is attribution without evidence, and `v_end` / `j_start` landed about
two residues inside the N region.

Scoring is calibrated for nucleotides, where one substitution is a plausible
read error. In amino-acid space it is a much stronger claim, so one coincidental
match pays for a mismatch exactly. `CAGSGVSRDTQYF` against `TRBJ2-3*01`
(`STDTQYF`): `SRDTQYF` scores 6 matches minus 1 mismatch, tying `DTQYF`'s 5, and
nucleotide markup of that clonotype puts the boundary at `DTQYF`.

Two questions shared one answer, and they want different stringency. `_errors`
and `_repair` keep the full aligned extent, because a substitution one residue
short of the end is a typo to report. `v_end` / `j_start` now come from
`_supported`, which stops at the first position where the running score reaches
its maximum. A repair still earns the full extent: a repaired residue is one the
germline explains.

Measured against observed nucleotide markup of real repertoires, arda seeing
only the amino acids and the V/J calls. 25,000 human TRB clonotypes:
`v.end` exact 72.6% -> 73.3%, within one residue 98.7% -> 99.3%; `j.start`
exact 95.9% -> 97.7%, within one 97.7% -> 99.5%; boundaries out by two or more
on `j.start` 566 -> 10.

On 8,334 VDJdb records present in the same data, `j.start` exact goes 8,041 ->
8,164, past the k-mer scanner VDJdb ships today (7,987), while declining nothing
where that scanner declines two.

Costs nothing measurable: over 25,536 real clonotypes `vFixType`, `jFixType`,
`good` and the repaired CDR3 differ on zero records, and throughput is
unchanged. 1213 tests pass with no test modified, including
`test_deep_substitution_is_reported_but_not_repaired`, which is what separating
the two extents exists to preserve.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4f57bfde21b1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
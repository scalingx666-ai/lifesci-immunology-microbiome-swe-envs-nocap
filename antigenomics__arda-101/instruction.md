# Issue

**Title:** 2.19.0 — correct --flag-chimeras

## Description

A template-switch chimera is a query junction explained by two **more abundant** parents as prefix + suffix across one breakpoint. `chimera_parents` names them and the breakpoint. Off by default; **it never drops a row**.

## ⛔ The germline trap, measured — it is the whole filter

A junction is `V 3' tail` + `N/P/D` + `J 5' head`, and both tails are germline: every clonotype on a V starts with the same bases, every one on a J ends with them. On a TRA amplicon the median V-templated prefix is **10 nt** and the median J-templated suffix **25 nt**, against a median clone-specific core of **5 nt**.

So the same prefix/suffix test run on the raw junction rediscovers the germline and calls **52.20 % of clonotypes chimeric** (35.50 % of reads). With the templated tails excluded and 6 non-templated nt required each side: **0.02 %**.

## ⛔ Cell Ranger's rule does not port to bulk, and not because of the constant

Contigs sharing a V prefix ≥ 25 nt with differing CDR3s is a chimera signature *within a barcode*, where there is ~1 clone per chain. A polyclonal bulk repertoire has thousands of real clones per V gene — there, that rule describes almost every pair. What ports is UCHIME's shape, two more abundant parents, because the **abundance ordering** rather than the partition is what makes it a claim.

## Measured rate

| library | clonotypes | flagged | reads |
|---|---|---|---|
| Bulk RNA-seq (IG) | 1,741 | 7 (**0.40 %**) | 13 (0.18 %) |
| TRA amplicon | 19,844 | 1 (0.01 %) | 1 |

A 20× bulk-vs-amplicon enrichment, in the direction template-switch chemistry predicts — but far too small to justify deleting clonotypes, and the signature cannot separate a true chimera from two real clones that happen to share a prefix and a suffix. Hence a flag.

Requires the reference: with no anchors the germline cannot be excluded, so it emits **nothing** rather than a germline-driven guess.

## Tests

⚠ Every guard is mutation-tested, and **three of the first five tests passed with the bug in**:
- the germline test needed a query sharing *only* germline with each parent (the first version had no suffix parent, so nothing fired however wrong the code was);
- the abundance test needed the query to sort **last** — `setdefault` on a descending list otherwise makes it claim its own prefix and the check is never consulted;
- the SHM test needed both parents to genuinely match.

A fifth guard proved unreachable — an identical twin has Hamming 0, already caught by the ≤ 2 SHM check — and was deleted rather than left looking load-bearing.

858 pass across three tiers. Default output byte-identical; the column appears only with the flag.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `277d9851c1b8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
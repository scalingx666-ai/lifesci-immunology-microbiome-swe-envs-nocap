# Issue

**Title:** fix: a truncated anchor places the boundary it supports

## Description

.

## The defect

`cdr3fix` declined `v_end` on every allele whose anchor carries `status = truncated`, returning `FailedBadSegment` and `-1`. IMGT ships those allele records as partial sequences that stop inside the anchor region, so the templated run is short but *correct as far as it goes* — and refusing it threw away a boundary that was present.

Two alleles of one gene answered the same junction differently:

```
CASSLQGETQYF / TRBJ2-5*01
  TRBV11-2*01 -> NoFixNeeded       v_end 5
  TRBV11-2*02 -> FailedBadSegment  v_end -1     <- CASS, four residues of real germline
```

## The fix

An anchor of **3 or more** templated residues now places a boundary and reports it under a new fix type, **`TruncatedGermline`**.

- It counts as `good`, so these records do not drop out of a `good`-filtered pipeline.
- It ranks below every ordinary success, because `v_end` from one is a **lower bound**: residues past the record's end are unattributed, not known non-templated.
- The relabel is said *last* in each branch, so the repair still runs under its own fix type and `FixTrim`/`FixAdd`/`FixReplace` behaviour is untouched.
- The J side gets the same treatment on the same terms (mouse has 2 truncated J anchors; human has none).

Below the threshold nothing changes — `FailedBadSegment` keeps its meaning of "not in the reference, or too short to place anything".

### Why 3

That is where the prefix starts to carry information. Of the **1,101** human V anchors with two residues or more, **`CA` alone is 657 (59.7 %)** — a two-residue match places a boundary by coincidence. At three residues there are **62 distinct prefixes**, the most common being `CAR` at 283 of 989.

The rule admits **38 of the 63 truncated human V anchors and 43 of 53 mouse**, which is exactly the split the issue predicted.

## Verification

Against `isalgo/airr_control`'s nucleotide truth, on the seven junctions the issue lists with an unambiguous external boundary:

| junction | V | truth `v_end` | before | after |
|---|---|---:|---:|---:|
| `CASSLAGGSYEQYF` | `TRBV11-2*02` | 4 | −1 | **4** |
| `CASSLAGTGELFF` | `TRBV11-2*02` | 5 | −1 | **4** |
| `CASSLASGQETQYF` | `TRBV5-1*02` | 5 | −1 | **3** |
| `CASSLGTSSYEQYF` | `TRBV11-2*02` | 5 | −1 | **4** |
| `CASSLMRSSYNEQFF` | `TRBV11-2*02` | 5 | −1 | **4** |
| `CASSLPPDTQYF` | `TRBV11-2*02` | 4 | −1 | **4** |
| `CASSLQGETQYF` | `TRBV11-2*02` | 5 | −1 | **4** |

Never over-claims, exact on 2 of 7, within two residues on 7 of 7 — the behaviour a lower bound should have.

## Tests

Four faces, in `tests/unit/test_cdr3fix.py`:

1. The two sibling-allele pairs from the issue — `*02` now answers, `*01` is unchanged, and the J side does not move.
2. The seven nucleotide-truth rows, asserted as a **lower bound that never over-claims** rather than as golden values.
3. `C` and `CA` anchors still declining as `FailedBadSegment`.
4. The threshold **as a rule over the whole anchor table**, not as a handful of outcomes, so a reference rebuild cannot quietly move the line.

## Blast radius

No allele with `status = ok` or `no_anchor` moves — the new predicate is the old one for both. The committed `examples/` markup artifacts reproduce byte-for-byte (`examples/junctions.tsv`'s `bad-segment-refused` row uses `TRAV1-2*02`, which is `no_anchor`).

`1,176` unit + `100` synthetic/realworld pass (9 skipped, optional `olga` extra); `ruff` clean.

## Note on scope

The issue's table also lists 1,702 family-name declines. Those are a separate population — the issue itself says declining is correct for a bare family name — and commit `9f197f7` already resolved the one-functional-gene case. This PR is the 851 `*02`/`*03`/`*04`/`*07` keys, 802 of them `TRBV11-2*02`.

The sibling-allele fallback the issue mentions as the other option is **not** done here: it would re-attribute the coordinate to a different allele, which is ROADMAP item 12's question.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8a5e362f2806`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
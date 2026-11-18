# Issue

**Title:** 2.36.0 — a junction naming neither V nor J gets a locus proposed too

## Description

2.34.0 proposed a missing V or J from the junction, but only within the locus the *other* side named. A record naming **neither** came back refused — no locus, no boundary, nothing for a nucleotide stage to work on.

There is no new rule here. Every locus the organism ships now competes, scored by the same `anchor_depth` from each germline's own anchor, and a locus only wins by explaining residues at **both** ends — which is what keeps a TRA junction out of TRD, where the V genes are shared and the J genes are not.

### Measured

522 of VDJdb's curated `chunks` records name neither side (461 distinct keys). All 461 now get a locus and **459 come back `good`**, against none before.

The check is VDJdb's own filing: the proposed locus agrees with the `cdr3.alpha` / `cdr3.beta` column the record was filed under on **457 of 461 (99.13 %)** — 318 TRB, 139 TRA. All four disagreements are `CACD…DKLIF`, which is TRDV2's own anchor and TRDJ1's own ending, in a schema with no δ column.

### The floor is measured too

Each end must explain its **own** anchor residue or no locus is named. Without it a junction agreeing with nothing (`QQQQQQQQQQQQ`) reached depth 0 on both ends of every locus and was still handed TRA. Over the 461 real keys the winning locus clears the floor on every one — 16 at depth 1, 200 at 4, 156 at 5.

### The audit instrument was blind to this

`scripts/audit_cdr3fix.py` required both a V and a J to be named, so the A/B could not see the rows 2.34.0 and this release change. Widened:

- corpus 189,596 → **192,726** keys, digest rebases to `0df8541ed1060fe1`
- on the 189,596 keys the old filter kept, the digest is **unchanged** at `2b75491b380310aa` — nothing that already worked moved

### Why now

`vdjtools` 4.8.0's junction pipeline pins `arda-mapper>=2.36.0`: those 461 keys are the last of VDJdb's corpus that answered nothing.

Gate: 1,339 passed / 9 skipped. `ruff check src/` clean. Docs build with `-W`, zero warnings.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `226f15918c5f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
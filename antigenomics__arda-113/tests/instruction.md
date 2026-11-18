# Issue

**Title:** Productivity: scan FR4 for stop codons — and what the productivity roadmap item was actually aimed at

## Description

Continuing down the roadmap after #112. The item was **Full AIRR productivity** — "`productive` is
currently a heuristic; align it with the complete AIRR rules (start codon, stop-codon scan over
the whole VDJ, frame of the junction)". Measuring first changed what the work turned out to be.

## The real hole

`productive` and `stop_codon` scanned the V-side regions and the junction. The junction ends **at**
[FW]118 — FR4's first residue — so residues 2..n of the J were looked at by neither. A read whose
J carried a stop came out `productive=T`, `stop_codon=F`. AIRR scopes both to the whole
rearrangement, so FR4 is scanned now.

**Measured before changing it.** On the committed IgBLAST fixtures every evaluable row carries an
FR4 (mean 10.1 aa human, 8.6 mouse) and **none of 4,217** contains a stop — so the fix leaves all
4,843 annotated rows **byte-identical**. It closes a real hole without moving a published number.

A hole real data does not exercise is exactly the kind that needs a test written on purpose:
`tests/synthetic/test_fr4_stop.py` plants a stop in FR4's own frame at **codon 1**, not codon 0
(codon 0 is [FW]118 itself, which the old rule already covered and which would prove nothing), and
asserts `junction_aa`, `v_call` and `vj_in_frame` are unchanged so the flip is attributable to the
stop. Checked to fail without the fix.

## The rest of the item was aimed at the wrong thing

A **start codon** is not assessable on a read fragment, and IgBLAST does not require one either.

And arda-vs-IgBLAST productivity, measured on the same fixtures: of **3,601** rows where both
tools were evaluable *and* called the same `junction_aa`, they disagree on **8** — 0.22 %, 3 human
and 5 mouse. In every one arda says `T`, IgBLAST says `F`, and **both report `stop_codon = F`**.

So not one of them would be changed by any productivity rule. All 8 are IgBLAST reporting
`vj_in_frame = F` where arda reports `T`.

## Left open on purpose

`vj_in_frame` on those 8 rows is a **domain call**, not a defect to patch. All three human cases
are `TRAJ31*01`; the mouse ones span TRAJ24/45/9 and TRBJ2-5/1-3. Both tools produce the same
cleanly-translated `junction_aa`, so arda's frame is self-consistent — but IgBLAST has a J-frame
table (`optional_file/<org>_gl.aux`) and disagrees. I have not changed arda to match, because
deciding whose J frame is right is yours. The roadmap entry now carries the evidence.

## Verification

- `ruff check src/` clean, `make -C docs html` (`-W`) zero warnings
- **1,088 passed**, 9 skipped (was 1,086)
- 4,843 annotated rows byte-identical before vs after

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2a4abdc33f1e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
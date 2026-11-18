# Issue

**Title:** 2.17.0 — a truncated junction can be finished from the germline

## Description

## `--complete-junctions N` (off by default)

A read that reaches Cys104, runs into the J and stops before [FW]118 has no observed 3' boundary, so arda declined it. The J's 5' chew-back and the N/P additions all lie **upstream** of the read's last aligned J base, so what is missing is germline-**templated** — and the reference already stores exactly that span (a J's `germline_nt` runs the allele's 5' end through the [FW]118 codon), so the tail is `germline_nt[j_germline_end:]` and nothing has to be aligned to find it.

⛔ There is no V-side counterpart and there will not be one: a read short at the *5'* end is missing bases the V germline does not template either, which is what `v_anchor_prefix` refuses.

| library | junctions | completed | median nt imputed |
|---|---|---|---|
| bulk RNA-seq, 1 M pairs (SRR5233639) | 3,856 → **4,103** (+6.4 %) | 247 | 13 |
| TRA amplicon, 100 k reads | 44,497 → 44,527 (+0.07 %) | 30 | 12 |

The bases are **imputed**, so every completed row carries the count in `junction_completed_nt` (appended last, after the anchor columns) rather than leaving a consumer to infer it. No already-observed junction moves in either arm.

**The refusal is most of the feature.** A read whose alignment stops more than a partial codon short of its own 3' end is declined — on the TRA amplicon **236 of 266 candidates run from the V straight into `TRAC` with no J at all**, while the aligner still names a J off a few coincidental bases. Of the 30 that survive: 30/30 close on [FW]118, 22 of 23 extend the (itself truncated) IgBLAST junction, and 7 are byte-identical to a junction the same library observes in full on other reads.

⚠ On IG the imputed span can hide the SHM the read would have shown, biasing a completed junction's 3' end toward germline — and IG is where the yield is (175 of 247 bulk completions are IGH).

## `_segment_rows` refuses a target-inverted row, as `_best_hits` already did

`_SEGMENT_FORMAT` never asked MMseqs2 for `tend`, so 2.10.0's guard covered one of the two reductions and not the other. A segment row's `tstart` is read as a forward target offset by both consumers; `_cannot_reach_cys104` walks it forward, so an inverted row can answer "unreachable" for a read that *does* reach Cys104 — which is then aligned V-segment-only and emits **no junction**. Measured cost of the extra column: none (same-job alternating A/B, master 9.78–10.08 s vs 9.64–10.05 s).

## Measured, not changed

`--call-level gene` shipped in 2.16.0 with its polyclonal cost unmeasured. Now: IGH −4.39 %, IGK −2.58 %, IGL −3.16 %, TRB 0.00 %, TRA −0.13 %, **reads conserved exactly** on both arms.

## Tests

All three tiers green (738 unit + 62 synthetic/realworld). Every new test verified to fail without its fix.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `94980f78afd2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
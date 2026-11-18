# Issue

**Title:** feat: arda shm-model — the SHM model is parameterised on context, not on per-allele position

## Description

`ROADMAP.md` item 10, which two other entries wait on. `arda.shm` reports **where a read differs**
from its germline; this fits the other half — **where a difference is expected**,
`P(substitution | 5-mer germline context, region)`.

## The roadmap asked for per-allele-per-POSITION. It was measured and refused.

Four bulk IGH libraries, two donors, on arda's own round-30 annotation — no new alignment work and
nothing private (benchmark `results/round33`):

| object | within one donor | between donors |
|---|---:|---:|
| per-allele per-position profile | r .8578 – .9897 | **r .2557 – .5601** |
| pooled positional profile | r .9708 / .9599 | r .5994 – .6224 |
| **5-mer context** | r .9718 / .9785 | **r .7424 – .7854** |

Inside one donor a positional table repeats at r ≈ .99 because the same expanded clones carry the
same mutations at the same positions — it is a portrait of that donor's clonal history, not a
property of the allele. `IGHV3-23*05` transfers at .9301 within SPX6730 and at .2557–.5601 between
donors, with no change of method.

⚠ **And context is the only one of the two that reaches the positions the consumer needs.** The
junction model wants `P(observed nt | V germline)` for the V tail **inside** the junction — exactly
the positions `arda.shm` scopes out as unidentifiable, because a difference there is hypermutation,
chew-back or N-addition and sequence cannot say which. A position there has no clean data ever; a
5-mer takes its rate from every allele that carries it in framework sequence.

## Both parameter families are earned

**Context**: AID's WRCY/RGYW motifs carry **4.66× / 5.00× / 4.77× / 4.69×** the rate of every other
covered position across the four libraries, on an overall rate that itself moves 1.6× between the
donors. Three of the four hottest 5-mers carry `AGCT`, the canonical WRCY.

**A region multiplier**: context does not exhaust the CDR:FWR contrast. Fit contexts on one donor,
predict the other's per-region counts —

| region | fit SPX6730 → test SPX8151 | fit SPX8151 → test SPX6730 |
|---|---:|---:|
| FWR1 | 0.630 | 0.626 |
| CDR2 | 1.389 | 1.291 |

4.65× raw becomes a 2.2× residual that reproduces between people who share no clones. ✅ Run
independently on the two donors, the shipped estimator gives FWR1 **×0.683 against ×0.675**.

**No third family.** Nothing else is measured to be necessary.

## What ships

`arda shm-model -i mapped.airr.tsv -o shm.tsv --locus IGH` — reads what every mode already writes
under the default `--shm framework`, 0.76 s on 4,661 observations. Also fits IGK (.0210) and IGL
(.0182) against IGH's .0324, with the same CDR-over-FWR ordering.

Never: the fitted **scale** is the sample's, not the model's (.031 against .050 with the same
shape) — written as provenance, never applied.

Never: **a region with no observed substitution is OMITTED, never given a multiplier of 0.** Zero
would read as "a substitution in FWR1 is impossible" and silently zero every probability in that
region. This was a live defect, caught by its own test.

Never: **the denominator is capped at `v_anchor_nt`**, because the numerator is framework-scoped.

Never: the table loader skips comments, blanks and the header **by what they are, not by position**
— the `load_d_prior` lesson, pinned with a file carrying a comment above the header, a second
comment lower down, a repeated header mid-file and a malformed row.

Nothing in the annotation path reads the model yet, exactly as `arda scenarios` shipped before
`arda markup --d-prior` existed to consume it. `project/design-shm.md` records what S2 (the
junction model) and S3 (novel-allele discovery) each need, and that **done means measured**.

## Gates

| gate | result |
|---|---|
| `pytest tests/unit tests/synthetic tests/realworld` | **1,239 passed, 9 skipped**, 4 min 43 s |
| `ruff check src/` (0.15.9) | clean |
| `make -C docs html` (`-W`) | zero warnings |

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8c1dd7e329e7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
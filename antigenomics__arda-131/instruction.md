# Issue

**Title:** feat: arda correct --error-rate auto — measure the rate, don't assume Phred 30

## Description

`ROADMAP.md` item 9, which asked for *"a per-library calibration rule, or an estimate off the
data, not a re-tuned constant"* and named the candidate: the observed error-cloud abundance ratio.

## The estimator inverts the model's own definition

`_parents` treats `p_sub = error_rate * L` as the expected fraction of a parent's reads appearing
as **one** 1-substitution child — which, summed over the `3L` neighbours a junction has, is the
**total** 1-substitution error mass. So the matching estimate is

```
error_rate = (reads in 1-sub children) / (reads in parents) / mean junction length
```

with children required to be strictly less abundant than the parent, so each pair's direction is
defined rather than assumed.

## What four real libraries say about themselves

Benchmark `results/round35`:

| library | parents | parent reads | cloud reads | **estimate** | vs `1e-3` |
|---|---:|---:|---:|---:|---:|
| TRA amplicon | 41 | 4,909 | 77 | **3.948e-4** | **0.39×** |
| TRB amplicon | 33 | 3,775 | 95 | **5.865e-4** | **0.59×** |
| MIGEC IGH | 79 | 350,392 | 26,003 | 1.546e-3 | 1.55× |
| IGH 5'RACE | 105 | 34,898 | 6,101 | 3.503e-3 | 3.50× |
| IGH / IGK / IGL bulk | 0 | — | — | **refused** | — |

**An 8.9× spread against one shipped constant**, and both TCR amplicons sit *below* it — the
default over-collapses there. End to end on the TRA amplicon: **87** clonotypes absorbed at the
default against **21** at the measured rate, reads conserved either way (41,262).

## The two refusals that make it safe

Never: **a library too shallow to measure gets no number.** The three bulk RNA-seq arms have no
clonotype at 50 reads; the estimator returns `None` and the run falls back to the default with a
**warning**, because a default wearing a measurement's clothes is worse than a default.

Never: **the resolved rate is recorded** — `error_rate`, `error_rate_source`
(`given` / `measured` / `fallback`) and `error_rate_parents` go into the run's report. A measured
parameter that is not written down makes the run unreproducible.

## What it does not do, and why that is the right answer

⛔ **`auto` does not rescue the MIGEC spike-ins.** On that library it measures **1.164e-3** —
essentially the default — and erases both published variants, exactly as the default does:

| arm | rate | EHEB | V1 | V2 |
|---|---|---:|---:|---:|
| default | 1e-3 | 356,300 | **erased** | **erased** |
| `auto` | 1.164e-3 | 356,300 | **erased** | **erased** |
| forced | 1e-5 | 344,729 | 1,328 | 24 |

This **confirms round 19** rather than competing with it: V2 is less abundant than the worst
2-substitution PCR error, so no abundance threshold separates them and no calibration of one can.
Error *removal* and variant *preservation* are different objectives, and the second needs the
quality gate (`--ec-mode accurate`). That rule is now in `docs/error_correction.rst`.

⚠ On IG the 1-substitution cloud carries real hypermutation, so `auto` is an upper bound there.

## Gates

| gate | result |
|---|---|
| `pytest tests/unit tests/synthetic tests/realworld` | **1,262 passed, 9 skipped**, 5 min 10 s |
| `ruff check src/` (0.15.9) | clean |
| `make -C docs html` (`-W`) | zero warnings |

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `51aa81c5025c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
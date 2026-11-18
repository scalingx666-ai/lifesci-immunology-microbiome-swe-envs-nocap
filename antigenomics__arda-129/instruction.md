# Issue

**Title:** feat: arda scenarios --shm-model — a mutated V tail stops being read as N-region

## Description

`ROADMAP.md` item 10, **S2** — the consumer the SHM model was fitted for.

`scenarios.lattice` bounded the templated V length with an **exact** common prefix, so on IGH one
substitution in the V tail forced the rest of that tail to be explained as insertion — and `delV`
and `insVD` are exactly the two distributions the estimator fits. A templated stretch is now
scored by `Π(1 − μ)` over matches and `μ / 3` over mismatches, with `μ` from `arda shm-model`.

## The exact-match bound turns out to be the `μ = 0` case of the emission

Not a rule that needed replacing — a special case of the new one. With every rate 0 a mismatch
costs 0, so no templated length past the common prefix survives, which is precisely what
`_common_prefix` computes. `tests/unit/test_shm_lattice.py` compares term weights between the two
paths and pins it.

Never: **`shm=None` is the default and byte-identical.** TR, unmutated IG and every shipped caller
are untouched.

Never: **V side only.** The model is fitted on `v_mutations` and has no J rates; reusing V's for J
would be a parameter nothing measured. That restriction is what makes the result below readable.

## Measured: 26,619 real IGH junctions, model fitted on a *different donor*

`arda scenarios`, 3 EM iterations, same input both arms (benchmark `results/round34`):

| parameter | exact | with `--shm-model` | change |
|---|---:|---:|---:|
| **`delV` mean** | 4.148 | **2.708** | **−1.440** |
| **`delV` P(no deletion)** | .1426 | **.2388** | +.0962 |
| **`insVD` mean** | 12.065 | **10.972** | **−1.093** |
| `insDJ` mean | 12.342 | 12.144 | −0.198 |
| `delJ` mean | 12.247 | 12.253 | **+0.006** |

**The exact bound was charging 1.44 nt of V germline per IGH rearrangement to deletion** and
1.09 nt to V-side insertion; `delV`'s mode moves from 1 to 0.

✅ **The specificity is the result's own control.** The model reaches the V side only, so `delJ` at
+0.006 against `delV` at −1.440 says the change moved what it should and nothing else — that
contrast falls out of the design rather than being imposed as a null.

On the D posterior, judged by arda's **independent nucleotide** D caller (10,849 junctions at
`d_support <= 0.05` — the judge round 32b used): .7885 → .7898, **+15 genes net** (32 to, 17
away), concentrated in the most mutated bin (+0.0040) and −0.0019 on unmutated reads where the
model has nothing to contribute. Mean templated V read as N-region: **2.672 → 1.877 bases**.

⛔ **Never compare the two arms' log-likelihoods** (−1,179,678.0 and −1,161,289.3). They are
likelihoods under *different models* — the SHM arm carries an emission term per templated base —
so the difference is not a number at all. Within an arm the EM sequence is meaningful.

Cost: **+4.8 %** wall on a 3-iteration fit (12 m 01 s against 11 m 28 s).

## Also fixed: a tie-group `v_call` silently found no germline

`shmmodel.germline_map` keyed a scaffold's `v_call` verbatim, but that may be a comma-joined
**group** — `IGHV3-23*01` lives inside `IGHV3-23*01,IGHV3-23D*01`. A lookup by single allele found
nothing, silently: it cost the estimator reads, and it made the first SHM-aware lattice score
*exactly* like the exact one, which read as a clean null result rather than a missing key. Every
member is now keyed as well as the group string — 325 human IGH keys become 349.

## Gates

| gate | result |
|---|---|
| `pytest tests/unit tests/synthetic tests/realworld` | **1,248 passed, 9 skipped**, 5 min 16 s |
| `ruff check src/` (0.15.9) | clean |
| `make -C docs html` (`-W`) | zero warnings |

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c35d508d213f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
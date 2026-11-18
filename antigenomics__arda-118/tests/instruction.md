# Issue

**Title:** feat: arda.hmm, and a 4.7x faster estimator — in Python

## Description

ROADMAP's `arda.hmm` item, which predicted it would be "the same project, not a second one". It was.

`scenarios.lattice` **is** the forward-backward pass of the semi-Markov V→N1→D→N2→J model — an E-step and a posterior differ only in what you do with the same term weights. So `lattice` is factored out of `accumulate` and `arda.hmm` is one thin layer over it:

```python
m = model_for("human")                      # or model_for("human", prior="my_prior.tsv")
log_likelihood(junction, v, j, m)           # the MARGINAL, not Viterbi
posterior_d(junction, v, j, m).probabilities
best_scenario(junction, v, j, m)            # the Viterbi path, for reading
```

It does **not** replace `arda.dpost` (that answers the amino-acid question, where there are no nucleotides to run this on) and it **gates nothing** — nothing in the annotation path calls it, because of the two negatives ROADMAP already records.

## Performance: profiled before rewriting, and the hot spot wasn't where it looked

The question was whether this belongs in C++. Per `CLAUDE.md`'s reach order I profiled first. On 2,496 real records, one EM iteration, **byte-identical output**:

| | time | |
|---|---|---|
| before | 17.74 s | |
| flank weight per **span**, not per term | 5.79 s | **3.1×** |
| germline offsets indexed by first base | 3.79 s | **1.5×** |

The dominant cost was **73.5 M `SufficientStats.add` calls** — 45 % of the run, its `dict.get` alone 6.8 s — not the germline matching anyone would profile first. The flank split distribution depends only on the span and the contribution is linear in the posterior, so summing first and distributing once is exactly equivalent.

**Stopped at rung 1.** `_d_placements` is now 21 % of runtime, so even a *free* C++ port of it would buy 1.27× overall. Not a fourth extension.

## Verification

`tests/unit/test_hmm.py` — 7 tests, including that the likelihood really is the partition function of the same lattice (if those ever disagree, one of them is a second model) and that the posterior sums rather than maximises. 1,120 passed, 9 skipped (was 1,113); `ruff` clean; `sphinx-build -W` zero warnings.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b789722c6435`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
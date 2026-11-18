# Issue

**Title:** Improves flow decomposition (apparently one bug too)

## Description

, one commit (`4bad76f`). It fixes a correctness bug that #69
introduced in the flow-decomposition search, then makes the remaining search
much cheaper, and adds four options. Rebases cleanly onto `develop` at
`8f50039`; the nine upstream commits since `277178d` touch only README, docs and
`build_container.yaml`, none of the files changed here.

Everything below was measured on **17,189 real flow networks** extracted from the
logs of a Setonix run over ~10,000 metagenomes, with 1,293 of them re-solved by
the original K = 1, 2, 3, … ladder as ground truth.

---

## 1. Fix: the lower bound from #69 skipped feasible K and returned non-minimal decompositions

`82313fa` (merged in #69) started `FD_Algorithm`'s K search at
`max(stDAG.get_width(), ceil(log2(#distinct flows)))`, both lifted from
flowpaths' `MinFlowDecomp`. **Both terms are invalid for the inexact (interval)
decomposition phables solves:**

- `get_width()` is the minimum path cover of **all** edges. An edge whose lower
  bound is 0 (junction coverage 0 — **28 % of real edges**) need not be covered
  at all, so this over-counts.
- `ceil(log2(#distinct flows))` assumes exact flows (k paths give at most 2^k
  distinct subset sums). With intervals, lows of 20, 21, 22 under an upper bound
  of 30 are all met by **one** path of weight 22, yet the term says K ≥ 2.

On real data the search started above the true minimum in **12 %** of components
(2,054 / 17,189) and returned a non-minimal decomposition in **99 of 1,293
ground-truth networks (7.7 %)** — 2 paths where 1 suffices (21 cases), 3 where 2
(67), and so on. It also saved no measurable time: 1,084 s for the bounded search
vs 1,098 s for the plain ladder over the same networks. **Any results produced
with `develop` between #69 and this PR carry this**: roughly 1 in 13 resolved
components has more paths than the minimum.

Replaced by the maximum antichain over edges that *must* carry flow (lower bound
> 0), which is a valid bound for any interval model — two edges no single
source-to-sink path can both traverse need two paths. One flowpaths quirk is
guarded explicitly: an **empty** `weight_function` means "use defaults" (weight 1
on every edge), which would silently reinstate the invalid all-edges width; found
on a real component whose five edges all had lower bound 0.

## 2. Speed: stop proving the impossible one K at a time

Re-solving the 1,131 largest real components showed where the time goes:

- 86 % of resolvable components are feasible at the first K tried; feasible
  solves are cheap (~0.03 s). Model *construction* is 0.1–0.4 s per attempt; the
  solve is everything at scale.
- **58 % of the largest components have no decomposition within `--maxpaths`.**
  For those the ladder tried every K, and each infeasibility proof was
  exponentially slower than the last — 0.5 s, 3 s, 30 s, 40 s, then hours.
  **91 % of all solver time ended with no result.** One real sample spent over
  ten hours this way.

`FD_Algorithm` now:

1. skips solving entirely when the (valid) bound exceeds `--maxpaths`;
2. tries K = bound — solved means done, the common case, at no extra cost;
3. otherwise asks **once** whether K = `--maxpaths` is feasible. Feasibility is
   monotone in K for this model: a K-path solution extends to K+1 by appending
   a zero-weight duplicate of its last path (the lexicographic symmetry
   breaking is non-strict, and the safety fixings never touch more than Kmin
   paths). Confirmed on 780/780 resolved real networks. So "no" at `--maxpaths`
   proves every K in between infeasible and the climb is skipped. "Yes" means
   the climb proceeds exactly as before; if it reaches `--maxpaths`, the probe's
   own solution is reused rather than solved twice.

The smallest feasible K and the model solved at it are unchanged in every case,
so results are identical to the original ladder. (Not done with
`allow_empty_paths=True`, the textbook way to make the question monotone: on a
real component that variant needed 450 s to prove K = 10 infeasible where the
standard model needed 58 s — empty paths add symmetry and loosen the relaxation.)

| | |
|---|---|
| 1,293 real components vs the original K = 1, 2, … ladder | **identical** paths, weights and K, every one |
| same 1,293, total solve time | 1,098 s → **373 s (2.9×)** |
| 1,131 largest components, 60 s cap per attempt | 2,237 s → 1,197 s; the unresolvable 58 %: 2,014 s → 891 s |
| what remains | one infeasibility proof at K = `--maxpaths` per unresolvable component, instead of a ladder of them |

Also in `resolve_short_parallel`: one component per pool task instead of
`ceil(n / (workers × 4))`. Measured on a real 424,819-vertex assembly (5,307
solver-bound components, max 197 nodes), the worst task's share of total work
drops 2.0 % → 0.7 % (linear cost model), 12.9 % → 6.8 % (quadratic), 24.0 % →
14.1 % (cubic) — 1.7–2.35× on the critical path, and it reaches the floor set by
the single largest component. On that assembly a chunk of nine held eight
components behind one slow one for nine hours. Order is preserved, so the merged
output is unchanged.

## 3. Options

- **`--mfd-time-limit SECONDS`** — cap a single solve. A component that hits it
  is reported unresolved with a WARNING; a timeout is not an infeasibility proof,
  so the search does not continue to a K it could not call minimal. Off by
  default: with no limit every answer is exact.
- **`--mfd-dump-slow SECONDS`** — write the flow network of any component slower
  than that to `<output>/phables/slow_mfd_instances/` as JSON, so a pathological
  component can be reproduced off the cluster.
- **`--job-cpu` / `--job-mem`** — every rule takes `threads` and `nthreads` from
  `config["resources"]["jobCPU"]` (default 8); `--threads` only sets Snakemake's
  total core budget. So `--threads 64` on a 64-core node still ran `coverm`,
  `foldseek`, `hmmsearch` and the flow decomposition 8-wide with 56 cores idle —
  measured on a real run. These override the two config values. Their click
  defaults are `None` on purpose: snaketool merges CLI defaults *over* config
  files, so a non-`None` default would make the config value permanently
  unsettable.

Both MFD options are plumbed through the preflight as `config.get(...)`, so
older config files without the keys still work.

## 4. Logging and small fixes

- `FD_Inexact.py` logged to `logging.getLogger(__name__)`, which is not a child
  of the `"phables 2.0.0"` logger phables attaches its file handler to — so
  nothing from the flow-decomposition module, including its K attempts, ever
  reached `phables_output.log`. It now uses the same named logger as every other
  `phables_utils` module and writes one INFO line per component with its K
  ladder and per-attempt times, e.g.
  `MFD [44 edges, lb=8]: unresolvable within --maxpaths 10; K=9..9 skipped after 2 attempt(s), 56.2s total -- K8:Infeasible/0.3s K10*:Infeasible/55.7s`.
- The startup log said `Minimum unitig count to consider a component` for
  `--compcount`, which is a *maximum* (`len(candidate_nodes) <= compcount`).

---

## Testing

- **Identity:** the new search reproduces the original K = 1, 2, … ladder on all
  1,293 ground-truth networks (paths, weights, K), including the probe-reuse
  path at K = `--maxpaths`.
- **Unit checks** on bound fallback semantics, chunking order preservation and
  cap, the zero-solve exit, the all-zero-lower-bound edge case, time-limit
  behaviour, the slow-instance dump round-trip, and logger routing.
- **Snakemake dry runs** with the new options: `--job-cpu 64` changes every rule's
  `threads` 8 → 64 and the runtime config carries all four values; the DAG is
  otherwise unchanged (7 jobs in a resume scenario, with and without the options).
- **Container:** the image built from `4bad76f` in this repo's CI (run
  33937580446; attempt 1 failed on an Ubuntu mirror `Hash Sum mismatch` during
  `apt-get update`, unrelated, attempt 2 passed).
- **Production:** that image has processed **795 samples** on Setonix over two
  days with no solver-related failures. The new INFO lines are in the logs, and
  one component was seen hitting a 1800 s `--mfd-time-limit` at the K = 10 probe
  and being left unresolved, as designed.

## Not verified / found but not fixed here

- The repository's `phables test` was not run in my local environment (the
  pre-built-env placeholder under `workflow/conda` blocks env creation there);
  the container build's own test passed in CI.
- **`--prostt5-cpu` is broken in this image**: ProstT5 on a CPU device crashes in
  the CNN head with `Input type (c10::Half) and bias type (float) should be the
  same` (the fp16 ProstT5 weights produce half-precision embeddings while the
  predictor stays float on CPU). Hit for real when a CPU node ended up running
  `predict_3di`. Not touched in this PR — worth a separate fix.
- `--mfd-time-limit` deliberately changes outcomes for the components it fires
  on (they become unresolved); the default (no limit) is unchanged behaviour.

Happy to split the correctness fix (§1) from the rest if that is easier to review
— it is the part that matters for anyone who has run `develop` since #69.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8f50039f75ac`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
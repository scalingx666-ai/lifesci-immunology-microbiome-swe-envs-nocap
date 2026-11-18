# Issue

**Title:** Release v2.5.0 — seqtree + vdjmatch become base deps (completes the engine promotion)

## Description

## v2.5.0 — seqtree + vdjmatch become base deps (completes the engine promotion)

v2.4.0 promoted **arda** but left the other half of the *same* stale promotion stranded. vdjtools' own pyproject says parents are promoted *"as the phases that import them land (**model → arda, overlap → vdjmatch**)"*. Phase 4/5 landed long ago; only the arda half was done.

### What was broken on a plain `pip install vdjtools`
Every one of these is an **advertised capability with no fallback** — it raised `ImportError`:

| Capability | Needs |
|---|---|
| `preprocess.correct()` — frequency-based error correction | seqtree |
| `overlap.similarity_overlap()` | seqtree |
| `overlap.tcrnet()` | seqtree + vdjmatch |
| `overlap.fuzzy_overlap()` | vdjmatch |
| `biomarker.metaclonotypes()` | vdjmatch |

### Why this is close to free
- **seqtree 0.3.0 has ZERO runtime dependencies** and ships the same wheel matrix as vdjtools (cp310–313 × macOS arm64 / manylinux / win_amd64).
- **vdjmatch** is a pure-Python `any` wheel whose only deps are `polars` (already ours) + seqtree.
- Both are imported **lazily**, so `import vdjtools` stays light. Across all three engines the only new transitive dep is `requests`.

### The rule (now written down in CLAUDE.md)
> If the README advertises it, a plain `pip install vdjtools` must deliver it.

All three antigenomics engines (arda, seqtree, vdjmatch) are base deps. Genuinely optional things stay extras — because each has a working alternative or is a side integration:
- `[overlap]` now carries **only scikit-learn** — needed just for `cluster_samples(method="mds")`; `method="hclust"` works out of the box on scipy.
- `[sc]` — anndata (scverse bridge), pyyaml, HF fetch.
- `[model]` / `[preprocess]` — kept as **empty no-op aliases** so existing pins (incl. mirpy's `vdjtools[model]`) still resolve.

### Regression guard
`test_smoke.py` now pins the contract: all three engines must be **unconditional** requirements (no `extra ==` marker), and it exercises `load_germline("TRB")` **and** `preprocess.correct()` from a plain install.

### Verification
**396 passed** (+3 contract tests), C++ `ctest` green.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `05d4743ac7ee`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
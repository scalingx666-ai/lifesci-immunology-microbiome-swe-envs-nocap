# Issue

**Title:** release: 2.29.0

## Description

Cuts **2.29.0** — the somatic-hypermutation model and its first consumer, plus a V-call
resolution fix.

### Added: `arda shm-model` — where a mutation is EXPECTED

`P(substitution | 5-mer germline context, region)`, fitted from what every mode already writes
under the default `--shm framework`. 0.76 s on 4,661 observations.

⛔ **`ROADMAP.md` item 10 asked for a per-allele-per-POSITION model; the measurement refused it.**
Across two donors that object transfers at Pearson **r .2557–.5601** against 5-mer context's
**r .7424–.7854**, and within one donor it repeats at **r ≈ .99** — it is a portrait of that
donor's expanded clones, not a property of the allele. ⚠ Context is also the only one of the two
that reaches the V tail **inside** the junction, which is where the consumer needs a rate and
where a position has none by construction.

✅ Both parameter families are earned: AID's WRCY/RGYW motifs run **4.66–5.00×** over every other
covered position in all four libraries, and the CDR:FWR residual *after* context reproduces across
donors (FWR1 .630/.626, CDR2 1.389/1.291).

### Added: `arda scenarios --shm-model` — the consumer

The templated V length was bounded by an **exact** common prefix, so on IGH one substitution in
the V tail forced the rest of it to be read as N-region — and `delV` and `insVD` are the two
distributions being fitted. On 26,619 real IGH junctions, model fitted on a **different donor**:

| parameter | exact | with `--shm-model` | change |
|---|---:|---:|---:|
| `delV` mean | 4.148 | **2.708** | **−1.440** |
| `delV` P(no deletion) | .1426 | **.2388** | +.0962 |
| `insVD` mean | 12.065 | **10.972** | **−1.093** |
| `delJ` mean | 12.247 | 12.253 | **+0.006** |

The exact bound was charging **1.44 nt of V germline per IGH rearrangement** to deletion. ✅ `delJ`
at +0.006 is the result's own control — the model reaches the V side only. `shm=None` stays the
default and byte-identical.

### Fixed: a V/J call naming a FAMILY with one functional gene now resolves

`resolve_allele` never reached a call naming a family whose genes all carry a suffix — nothing is
named `TRBV20`, only `TRBV20-1` — so `markup_cdr3` returned `FailedBadSegment` and dropped the V
end. **6,291 human beta chains in VDJdb** carry such a call. The new rung **refuses rather than
guesses**: the family must hold exactly one *functional* gene, which is why `TRBV3` resolves
(`TRBV3-1` F, `TRBV3-2` P) and `TRBV6`, with five, still returns `""`.

### Fixed: a tie-group `v_call` silently found no germline

`IGHV3-23*01` lives inside `IGHV3-23*01,IGHV3-23D*01`, so a lookup by single allele found nothing —
it cost the estimator reads and made the first SHM-aware lattice look like a clean null result.
325 human IGH keys become 349.

### Gates

| gate | result |
|---|---|
| `pytest tests/unit tests/synthetic tests/realworld` | **1,252 passed, 9 skipped**, 4 min 46 s |
| `ruff check src/` (0.15.9) | clean |
| `make -C docs html` (`-W`) | zero warnings |

All four Nextflow pins move with the version. ⚠ `uv.lock` is deliberately **not** included: it is
untracked on master and not gitignored, so adding it is a structural decision rather than a
release one.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5ace4bef9b08`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** release: 2.28.0

## Description

Cuts **2.28.0**. The minor bump is earned by one breaking change; everything else rides with it.

### Breaking: the integrations speak nf-core/airrflow, not an arda-only vocabulary

`process ARDA` -> **`ARDA_ASSIGN`** (a drop-in for `CHANGEO_ASSIGNGENES` + `CHANGEO_MAKEDB`) and
**`params.regime` is gone** -- the mode comes from `--library_generation_method`. A second arda-only
name for the protocol was a second place to get it wrong, and getting it wrong is a silent 2-4x
slowdown rather than an error. Migration table in the module's README.

### Also in this cut

| change | why it is here |
|---|---|
| `arda markup --d-prior PATH` | using a fitted estimate no longer means overwriting a file inside the installed database |
| `arda resolve-ties --loci` | whether widening the V call helps is a property of the LOCUS: IGK exact-set agreement **.5707 -> .9373**, IGH **-0.6 to -14.9 pt** |
| `arda igblast --receptor ig\|tr\|both` | a library whose receptor is known no longer pays a whole IgBLAST pass over the other type |
| docs: the IG read-coverage floor | `v_gene` recall **.1170 under 60 nt of V germline, .9896 at >= 200 nt** -- and .9896 *is* the TRA amplicon's .9867 |
| fix: a `d_prior` table `arda scenarios` wrote could not be read back | the header was skipped by POSITION and the generator writes a `#` provenance line above it |
| fix: the NF Dockerfile's acceptance check | it grepped `arda rnaseq --help` for flags that moved to `arda map` in 2.16.0, so every `docker build` failed on a correct install |
| fix: the Cys104 junction gate's one-substitution cliff | +144 correct junctions and ONE extra over-extension across 92,466 truth junctions, held-out locus included |
| fix: `build_germline_dbs` ignored `locus.v_shared` | complete chimeric markup 7/483 -> 49/483 with every V call correct |

### Release mechanics

All four Nextflow pins move with the version; `tests/unit/test_nextflow_integration.py` asserts
them against `arda.__version__`, so a forgotten pin fails the gate rather than shipping.

`--receptor` was the one new flag with no surface outside `--help`. It is now in `README.md`,
`docs/usage.rst` and `skills/arda/SKILL.md`, per this repo's documentation invariant that a flag
is not shipped until it is documented.

### Gates, run locally on the release commit

| gate | result |
|---|---|
| `pytest tests/unit tests/synthetic tests/realworld` | **1,224 passed, 9 skipped**, 3 min 59 s |
| `ruff check src/` (0.15.9, the CI pin) | clean |
| `make -C docs html` (`-W --keep-going`) | zero warnings |

CLAUDE.md's own two stale numbers (the gate's test count, the dev binary's version) go with it.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b0726d61d222`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Fix: accept semver primer_set_version values (e.g. 5.3.2)

## Description

## Summary

- Change `primer_set_version` schema type from `"number"` to `["number", "string"]` so semver versions like `5.3.2` pass validation while keeping backward compatibility with integer/decimal versions
- Update default values in `main.nf` from `0` to `''` to match string-based usage
- Fix nanopore config comparison to use `.toString() == '1200'` to avoid type mismatch

## Related Issues



## Context

Issue #288 previously changed `integer` → `number`, which fixed `4.1` but `number` still can't represent `5.3.2`. Nextflow's CLI parser coerces values based on format (`3` → Integer, `4.1` → Double, `5.3.2` → String), so the schema must accept both number and string types. The pipeline code already calls `.toString()` before map lookups, so this change aligns the schema with reality.

## Changes

| File | Change |
|------|--------|
| `nextflow_schema.json` | `"type": "number"` → `"type": ["number", "string"]`, updated description |
| `main.nf` | Default `0` → `''` in two places |
| `conf/modules_nanopore.config` | `== 1200` → `.toString() == '1200'` |

## Test plan

- [ ] New test: illumina amplicon with `--primer_set_version 5.3.2`
- [ ] `nf-core pipelines lint` — no new warnings (matches `dev` branch status)

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] If you've fixed a bug or added code that should be tested, add tests!
- [x] Make sure your code lints (`nf-core pipelines lint`).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c725a5abd4a2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
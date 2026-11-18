# Issue

**Title:** Fix ConcurrentModificationException from in-place sorting of shared channel items

## Description

## Problem

Conda jobs on the 5.5.0 release PR (#1083) fail intermittently with `java.util.ConcurrentModificationException` on `CATPACK_BINS`. 4 of 8 shards failed — a data race, not a determinism bug.

## Cause

Groovy's `List.sort(Closure)` sorts **in place**. Used inside a `map` operator on a list that came straight from a channel, it mutates the object every other consumer of that channel also holds — and a consumer iterating it concurrently throws.

`BIN_QC` used to re-group its input with `groupTuple()`, which allocates a fresh list, so sorting it was harmless. #1066 removed that roundtrip, so the CheckM branch now sorts the list emitted by `ch_input_for_postbinning` while `DEPTHS`, `QUAST_BINS`, `CATPACK`, `PROKKA` and `GTDBTK` hold the same object.

Same failure mode as nextflow-io/nextflow#6589.

Only visible under conda because (a) the conda profile is excluded on `dev` PRs, so #1066 got its first conda run on the release PR, and (b) blocking conda env creation widens the race window. Docker can hit it too, just far more rarely.

## Fix

Every operator-level in-place sort becomes `toSorted`, which returns a new list. Ordering is unchanged, so no snapshots move.

#1066 made the same `groupTuple` removal for QUAST but wrote `[bins].flatten().sort { ... }` — `flatten()` allocates, so that one was accidentally safe. Converted here for consistency.

The remaining conda failures on #1083 are unrelated (Prokka md5 drift between the conda solve and the Wave container) and are being handled separately.

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [ ] Ensure the test suite passes (`nf-test test main.nf.test -profile +docker`). Not run locally — relying on CI.
- [x] `CHANGELOG.md` is updated.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ae30bf909f3b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Let analyze place pipeline intermediates away from the output

## Description

Replaces #2137, which GitHub closed automatically when its base branch was deleted on merging #2136. Same branch and commits, now based on `develop`.

## Problem

`analyze` wrote every step's data output next to the final output and freed none of it. A single-cell clonotyping run accumulated ~30 GB of files that no longer had a reader:

```
2.0G  result.consensus.1.mic
1.5G  result.consensus.2.mic
 13G  result.parsed.mic
 12G  result.refined.mic
```

Nothing relocated them. `--use-local-temp` never governed them — it only moves persistent-sort spills.

## Approach

Every produced file gets its path from one precedence chain:

1. an explicit `--output-path <fileName>=<path>` — always wins
2. the intermediates location, for files a later step reads
3. the positional output prefix — everything else, i.e. today's behaviour

An intermediate is a data output that a later step of the resolved pipeline reads, which is every payload file except the last production step's. The pipeline is fully resolved before any step runs, so this needs no per-step metadata and no new descriptor flag. Reports, QC and exports stay with the output files even for intermediate steps — that divergence is the core of the change.

## Options

- `--intermediates-dir <dir>` / `--intermediates-in-temp` — where intermediates go (mutually exclusive)
- `--remove-intermediates` — free each file once nothing reads it. Peak on the run above drops from a growing ~30 GB to the largest adjacent pair
- `--output-path <fileName>=<path>` — pin one file, which makes it a deliverable that is never freed. A name the pipeline does not produce is rejected up front, listing the ones it does; two pins to the same path are rejected too

## Scratch data

A step whose output was relocated places its scratch next to that output, so the scratch follows the intermediates. This is done by forwarding `--use-local-temp`, and it is deliberately **identical for the steps delegated to mitool and for MiXCR's own** — mitool takes no scratch folder of its own, so this is the only mechanism available to either. The last step is left alone: its output is a deliverable at the output prefix, and its scratch belongs in the system temp folder rather than next to the results.

The default stays the system temp folder, which honours `TMPDIR`, so one env var still governs every step uniformly.

Three temp destinations gained a `.tmp.` name separator (`assemble`, `align`, `refineTagsAndSort`, `assembleCells`). A destination claims every file whose name starts with its prefix and clears them when it is created; that prefix was the output file name, so it also reached files sitting beside the output. `analyze` now points these steps at their own output automatically, which widened that reach.

`qc` is excluded from the terminal-step calculation: it carries the highest non-export order, so with `--add-step qc` it would otherwise stand in for the step that produces the deliverable and the real final `.clns` would become deletable.

The MiTool preset path is passed to mitool exactly as given, relative when the intermediates folder is relative. Resolving it against the working directory would put that directory into the `commandLine` recorded in every output header, and two runs of the same analysis from different folders would stop producing identical files — which is what `case-single_cell_reproducible_hash` checks.

## Accepted limitations

- `--intermediates-in-temp` depends on the system temp folder being provisioned; in a container that is the container's own `/tmp` unless `TMPDIR` is passed in. Callers who cannot rely on that use `--intermediates-dir`.
- Cleanup rides milib's JVM shutdown hook, so it does not fire on SIGKILL or OOM-kill.
- Re-running into the same `--intermediates-dir` needs `-f`, as it would for the output files.

## Tests

`itests/case-intermediates.sh` covers the default layout (the regression guard on the `PlanBuilder` rework), `--intermediates-dir`, `--intermediates-in-temp` with `--remove-intermediates`, both together, `--remove-intermediates` with no relocation at all, `--output-path` surviving removal, sample-split input, and the rejected name. Payload names are spelled out rather than globbed, because a wildcard between two dots cannot match a name with nothing between them and such assertions pass whatever happens.

Reviewed independently across all three PRs after the final state was reached; findings addressed in the second commit.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `57da7092a62b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Pass a temp destination to CloneAssembler

## Description

Replaces #2133, which was on a branch whose name contained `/` — that made the docker publish step fail on an invalid tag (`latest-fix/...` is not a valid docker tag) and stopped CI triggering on push. Same commits, slash-free branch name.

Consumes the mixcr-algo change (milaboratory/mixcr-algo#153) that lets the caller decide where the assembler event log lives.

`AssemblerEventLogger` holds the alignment-to-clone assignment ledger — a working file of the assemble step, not a debug artifact. It used to allocate itself in the system temp folder, so `--use-local-temp` could not move it; on a large run that is hundreds of megabytes in a location the caller cannot choose. `assemble` now hands `CloneAssembler` the same temp destination it uses for the rest of its scratch data.

Changes:

- `mixcrAlgoVersion` bumped to `4.7.0-69-fix-assembler-event-logger-temp-dest`.
- `CommandAssemble` passes its existing `tempDest` into `CloneAssembler`; `CloneAssemblerRunnerTest` passes a system-temp destination.
- assemble's temp destination gets its own `.tmp.` name prefix. A destination claims every file whose name starts with its prefix and clears them when it is created; that prefix was the output file name, so the destination also claimed unrelated files next to the output, such as exports from an earlier run. Passing the destination to `CloneAssembler` makes it materialise on every run rather than only for barcoded and clna output, which widened that reach.

**Do not merge with this `mixcrAlgoVersion`.** It is a branch build for validation. Once the mixcr-algo change is on `develop`, re-point the pin at a develop build and let CI go green again.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1eb18b7bee0a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Update SSHash to fork master (v6 format)

## Description

Moves the `sshash` submodule from `6b4d922` (fork's `archive/master-before-upstream-20261023`, SSHash v5) to fork **`master` `013f8f9`** (jermp/sshash `2ea1f8b` + fork consolidation `1d6e698` + the malformed-input fix from #682).

## On-disk format: **changes (SSHash v5 → v6)**
`sshash::constants::current_version_number` goes 5.0.0 → 6.0.0. Existing `.sshashdbg` graphs **must be rebuilt** from their source sequences, and **so must annotations built on them**, since annotations refer to node IDs. sshash's loader rejects a v5 index with a major-version mismatch, so it can't be silently misread. Other graph representations are unaffected.

## What changed
- Submodule pin → `013f8f9`. pthash moves from ratschlab/pthash (`df96653`) to jermp/pthash `e04a192`, which has upstream "memory mapping" #96. Its bits pin `f5498a8` contains jermp/bits #12 (pod_vector mmap) and uses `owning_span`. The fork's bits differs from it only by clang-format whitespace, so the pthash/bits fork commits are superseded.
- `dbg_sshash.cpp`, the minimal API adaptation (taken from `0705dd95a` on `codex/align_refactor-oct2026`):
  - `#include <src/build.cpp>` → `<src/builder/build.cpp>`
  - `build_config.canonical = mode != BASIC` → `allow_reverse_complement_duplicates = mode == BASIC`. v6 always indexes canonical minimizers; BASIC keeps both orientations as separate IDs.
  - `streaming_query<Dict, true>` → `streaming_query<Dict>`
  - The Debug-only `equal_lookup_result` assert skips k-mers with invalid characters, because v6 streaming lookup accepts ambiguous bases and returns no match.

## Upstream PRs #97–#104 (jermp/sshash, all still open)
All are in fork master. #99 and #104 are verbatim. #97, #98 and #100–#103 are in a later revision; the leftover differences are comment wording, named constants, and `take_chars` / `visit_minimizer_positions` refactors, not missing fixes.

## Verification
- `metagraph` + `unit_tests` build locally with g++-15, Release, for both DNA and Protein. No tests were run locally; I'm relying on CI.
- **Not covered by tests:** SSHash zero-copy mmap loading (#604) on the new pthash/bits. It compiles, and essentials' `generic_loader::set_mmap(base, size, owner)` has the same signature. But no unit test loads an SSHash graph through `mmap_ifstream`.

## Ordering
Merge **after #682**. #682 is the small disk-fill fix; it pins `9124934` (the v5 pin + the parser fix). After #682 merges, I'll rebase this PR: the only conflict is the submodule pointer (take `013f8f9`, which already contains the same parser fix).

Not included, as follow-ups:
- the off-by-one in `generate_succ_pred` that skips the last node (fixed on `codex/align_refactor-oct2026`)
- the aligner-side SSHash changes from that branch

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated description by cubic. -->
---
## Summary by cubic
Updates the `sshash` submodule to fork master, changing the on-disk format from v5 to v6. The loader rejects a v5 index with a major-version mismatch, so old graphs can't be silently misread.

**Migration**
- Rebuild existing `.sshashdbg` graphs from their source sequences, and annotations built on them, since annotations reference node IDs.

pthash moves from ratschlab to jermp, picking up upstream memory mapping support. `dbg_sshash.cpp` adapts to the v6 API: builder include path, `allow_reverse_complement_duplicates` for BASIC mode (v6 always indexes canonical minimizers; BASIC keeps both orientations), single-parameter `streaming_query`, and the debug assert for lookup equality now skips k-mers with invalid characters, which v6 streaming lookup accepts. SSHash zero-copy mmap loading compiles on the new pthash/bits but isn't covered by tests. Merge after #682; the only rebase conflict is the submodule pointer, and this pin already contains the same parser fix.

<sup>Written for commit 7970e3f657a2a62398083214d06ceab0bc8a61ab. Summary will update on new commits.</sup>

<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/684?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/684?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F684&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>

<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `490cb66b74b3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
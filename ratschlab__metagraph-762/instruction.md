# Issue

**Title:** Name the wavelet tree's view types and drop the fork's stream filename()

## Description

The sdsl submodule moves to a fork commit that drops three fork-only view extras. It removes the `select_1_type`/`select_0_type` typedefs on `packed_vector_view`, `shared_mapper_ifstream::filename()`, and the unused `packed_word_iterator` operators. `packed_vector_view::into_owned()` stays, in the version proposed upstream in xxsds/sdsl-lite#197.

MetaGraph changes to match:
- `wavelet_tree_stat` names its rank and select types instead of taking `wt_huff`'s defaults. The types are the same, so the file format does not change.
- `utils::open_ifstream` returns a subclass of `shared_mapper_ifstream` that keeps the file name, and `utils::get_filename` reads it from there.
- `annotation_converters.cpp` opens the RowDisk input through `utils::open_ifstream`, because `RowDisk::load` needs the file name.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated description by cubic. -->
<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/762?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/762?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F762&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>
<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `70f9711739a9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
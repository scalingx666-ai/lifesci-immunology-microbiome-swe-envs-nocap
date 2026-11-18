# Issue

**Title:** Address review findings on sub-k seed labels (#691) and map-only mode

## Description

Follow-up to the cubic review comments on #691 and #692, which were merged before the comments were processed.

**#692, `--align-map-only` with `--map` / `--count-kmers` / `--query-presence`.** Those flags take the k-mer mapping path, so `--align-map-only` was silently ignored. The combination is now rejected in `Config`, with an error naming the flags.

**#691, coordinates in the sub-k seed regression test.** `SubkSeedLabels` now also runs the BASIC case with a coordinate annotation. For every alignment label it checks three things: there is one coordinate set per label, every coordinate is non-negative, and each coordinate points at the aligned sequence in that label. That includes the query that matches only a source dummy k-mer.

**#691, negative coordinates for source dummies (no code change).** The `$…$` source-dummy coordinates are `c - num_dummy`, which is negative at a sequence start. They are stored as `int64_t` (the subtraction wraps in unsigned arithmetic, and the conversion back to `int64_t` gives the intended negative value). They do not reach the output:
- A seed on a source dummy spells no `$`, so its offset is at least `num_dummy`.
- `filter_seeds` adds the offset back, so the seed's coordinate is at least `c`.
- Extension compares only differences of coordinates.

Checks:
- The new coordinate assertions pass.
- On a 24-genome BASIC graph with a `column_coord` annotation, I aligned 252 reads that are bare 20/25/30 bp contig-start prefixes on both strands. No reported coordinate wrapped, at seed length 19 (246 aligned) or 15 (252 aligned).

**#692, two rows per header with `--fwd-and-reverse` (kept).** With that flag the FASTA parser yields each record and its reverse complement as two queries with the same header. Plain `align` prints a row for each, and map-only now does the same. Dropping one in map-only mode would make the two modes disagree on the row contract.

**#691, test for the >16-continuation cap (not added).** Exceeding the cap needs a source dummy with at least 3 `$` and more than 16 distinct continuations. A test for that would mostly assert on graph construction, so I did not add one.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated description by cubic. -->
---
## Summary by cubic
Addresses review comments on the merged PRs #691 and #692.

**Behavior change**
- `--align-map-only` is now rejected when combined with `--map`, `--count-kmers`, or `--query-presence`, since those flags take the k-mer mapping path and previously caused `--align-map-only` to be silently ignored.

**Bug fixes**
- Extends the `SubkSeedLabels` test to run the BASIC case with a coordinate annotation and asserts that every reported coordinate is non-negative and points at the aligned sequence within its label.

<sup>Written for commit 7e87878c08783c94222486af3fa2188e5da90c37. Summary will update on new commits.</sup>

<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/694?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/694?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F694&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>

<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d70c25dfb5bd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
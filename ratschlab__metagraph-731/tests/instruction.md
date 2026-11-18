# Issue

**Title:** pymetagraph: alignment and seed-only label mapping

## Description

Adds alignment and seed-only label mapping to the experimental `pymetagraph` bindings from #698, as the in-process counterparts of `metagraph align`, the server's `/align`, and `metagraph align --align-map-only` (#692).

```python
graph = pymetagraph.AnnotatedGraph("graph.dbg", "graph.column.annodbg", threads=8)

graph.align(seqs, min_exact_match=0.3)
# [[GraphAlignment(labels=['ref_A'], score=612, cigar='300=', orientation=False,
#                  query_begin=0, query_end=300)], []]   best first, per sequence
graph.align(seqs, labeled=False)   # no labels, as the server's /align

graph.map(seqs, min_exact_match=0.3)
# [LabelMapping(labels=['ref_A'], num_matches=287, orientation=False,
#               query_begin=0, query_end=300), None]
```

- `align(seqs, labeled=True, min_exact_match, max_alternative_alignments, min_seed_length, max_seed_length, max_nodes_per_seq_char)`: `LabeledAligner` with `labeled=True` (as `metagraph align -a`), `DBGAligner` otherwise (as `/align`). Each result has the labels, score, max score, CIGAR, orientation and query range.
- `map(seqs, min_exact_match, min_seed_length, max_seed_length)`: `LabeledAligner::map_batch`, the labels whose seeds cover the most query characters, without extension.
- Arguments left unset keep the `metagraph align` defaults: the aligner config comes from `initialize_aligner_config` on a copy of the CLI `Config`, as the server builds it for `/align`, and overrides are checked like the CLI options.
- As in `metagraph align`, primary graphs are aligned through `CanonicalDBG` and succinct graphs get a `NodeFirstCache` (shared by the threads). Sequences are split into one batch per thread, each with its own aligner; both methods release the GIL.

Tests build the fixture from `tests/data` and compare the best alignment (strand, score, CIGAR, labels) with `metagraph align`, labeled and unlabeled, at three `min_exact_match` settings, and the mappings with `metagraph align --align-map-only`. The queries include exact, mutated and reverse-complemented sequences and one that does not align. Version 0.3.0.

Context: we use this for adaptive-sampling decisions on an ONT GridION through the readfish plugin metagraphRF (branch `ak/pymetagraph-only`), which now runs entirely in-process. On our HXB2 check sample, unlabeled `align` makes the same decision as the `metagraph server_query` `/align` backend for all 3000 reads, about 4.5 times faster (0.08 vs 0.36 ms per read on 8 threads). `map` at the same `min_exact_match` agrees with it on 2999 of 3000 reads.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated description by cubic. -->
<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/731?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/731?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F731&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>
<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `011b311864e2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
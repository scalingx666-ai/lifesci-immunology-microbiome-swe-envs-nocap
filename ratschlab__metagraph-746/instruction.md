# Issue

**Title:** Refuse unknown request fields on /search and /align

## Description

`/search` and `/align` now answer 400 to a request with a field they do not know, as `/resolve` and `/traverse` already do. Before, a misspelled field such as `discovery_fracton` was ignored and the default applied.

One helper, `check_request_fields`, lists the fields each route reads. `/search`: `FASTA`, `align`, `discovery_fraction`, `min_exact_match`, `max_num_nodes_per_seq_char`, `top_labels`, `query_coords`, `query_counts`, `with_signature`, `abundance_sum`, `graphs`, `in_ram`. `/align`: `FASTA`, `max_alternative_alignments`, `min_exact_match`, `max_num_nodes_per_seq_char`.

The Python client sent `count_labels`, which the server never read. The client no longer sends it, and `/search` still accepts it so older clients keep working. The web service sends only fields from the list. Any other client that sends an extra field now gets a 400.

Also removes an unused reader from the traversal request parser.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated description by cubic. -->
<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/746?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/746?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F746&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>
<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2b4a13cfd8ca`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
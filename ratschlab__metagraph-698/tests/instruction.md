# Issue

**Title:** Add experimental pymetagraph bindings for in-process queries

## Description

Experimental Python bindings for querying an annotated MetaGraph index in-process, without a running `metagraph server`.

```python
import pymetagraph
graph = pymetagraph.AnnotatedGraph("graph.dbg", "graph.column.annodbg", threads=8)
graph.query(["ACGT...", "TTGA..."], num_top_labels=1, discovery_fraction=0.1)
# [[('ref_A', 412)], []]
```

`query` has the same semantics as `metagraph query` (discovery and presence fractions, top labels) and returns `(label, matching k-mers)` per sequence. It releases the GIL and spreads sequences over the given number of threads.

This is the query part of the bindings from #672, on top of current master. Sayan's original commits (a Readfish aligner plugin) and Andre's rework into a generic query API keep their authorship. Alignment is not exposed; it can follow later on top of the existing aligner.

Changes on top of their commits:
- build: KMC built position-independent, pybind11 found through the configured Python, `$(MAKE)` kept for HTSLIB under Makefile generators, shared Boost for the extension on Linux only;
- query: all worker tasks are joined before an error is rethrown;
- tests compare labels and k-mer counts with `metagraph query`, and fail instead of skipping when the `metagraph` binary is missing;
- CI: a `pymetagraph` workflow builds the extension and runs the tests;
- README trimmed to build and usage.

Known limitations (also in the README):
- one annotation file only;
- a graph or annotation that MetaGraph cannot load ends the Python process, because the loaders call `exit()`;
- built without jemalloc;
- no `pip install` test in CI yet.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated description by cubic. -->
---
## Summary by cubic
Adds experimental `pymetagraph` Python bindings for querying an annotated MetaGraph index in-process, without a running server. `AnnotatedGraph.query()` has the same semantics and defaults as `metagraph query` (all labels, `discovery_fraction=0.7`) and returns per sequence the `(label, matching k-mers)` hits sorted by decreasing count, releasing the GIL and parallelizing over a configurable thread count. Alignment is not exposed yet; these bindings cover the query part only.

The build was adapted so the extension can link: vendored deps (KMC, HTSLIB) are built position-independent, pybind11 is located via the configured Python, and Boost is shared on Linux only. `BUILD_STATIC` cannot be combined with `BUILD_PYTHON_BINDINGS`. A CI workflow builds the extension and runs tests that compare results against `metagraph query`; only tests that need the CLI-built index are skipped when the binary is absent, and CI fails instead when it is missing. The Python API documentation page now describes building and using the bindings and which `metagraph query` features they do not expose.

Worker-thread errors are collected and rethrown after all tasks finish, and non-finite or out-of-range discovery/presence fractions are rejected.

**Known limitations**
- Only one annotation file is supported.
- A graph or annotation MetaGraph cannot load ends the Python process, because the loaders call `exit()`.
- Built without jemalloc.
- No `pip install` test in CI yet.

<sup>Written for commit 91168834a209860df015dcefd65cf2aa0fcc8fc8. Summary will update on new commits.</sup>

<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/698?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/698?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F698&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>

<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cc656d1f277a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
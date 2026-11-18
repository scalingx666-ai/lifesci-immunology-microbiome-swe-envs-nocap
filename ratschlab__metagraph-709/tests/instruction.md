# Issue

**Title:** Traversal v1 (2/4): the labeled traversal walker

## Description

Second of four stacked PRs for labeled traversal, on #708 (merged).

This PR adds `traverse_seed`, which extends a seed through the graph and keeps, on each path, the labels that carry every k-mer walked. The labels are named, or taken from the seed. A seed that no label carries fails with `SeedDerivationError`, so a caller can report it for that seed alone. Each arm returns a tree of segments, one path per leaf, the reason each label left, and `complete_to_bp`: the length up to which every walk is present.

A column label is on every k-mer its column contains. Its path never reuses an edge or steps back into the seed, so walks end on graphs with cycles. A header label follows its record's coordinates. It continues on the successor that holds the record's next coordinate and ends with `record_end` at the record's first or last k-mer, so a repeat inside the record is walked through. If a record holds the seed several times, the place with the lowest coordinate is used.

A label that continues on several successors spends one of its `max_label_branches` (default 0). With none left, it ends there. Fixed caps bound the work: 1,000,000 steps and a time budget per seed, 1000 live paths and 10,000 paths per arm, and 64 splits per path. A cap marks the arm truncated.

`test_walker_reference` checks every label end against a string model of the test records. On 80 seeds from six RefSeq records, compared with the records' sequences, the walker returned each named record's flanks up to 5,000 bp in full and without a wrong base.

In the last two days staging ran 64 traversal jobs, all on record labels. Column labels are kept because both kinds share one walk. #711 documents that column walks have had no use on staging yet.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9851ef8c29b4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
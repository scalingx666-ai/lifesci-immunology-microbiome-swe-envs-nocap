# Issue

**Title:** Rebuild the label encoder's hash table on load

## Description

An annotation written with one C++ standard library and loaded with another decodes its labels but finds none by name. On the published mini RefSeq index, `label_exists("562")` is false although `decode()` returns `"562"`. The cause: LE-v2.0 label encoders save their hash buckets, which were made with the writer's `std::hash`, and libstdc++ (Linux) and libc++ (macOS) hash strings differently.

`load()` now reads the saved record and rebuilds the buckets from the labels. The file format is unchanged. The rebuild takes about 0.1 s per million labels. On the indexes served on mex, the largest encoder holds 47,061 labels, and the rebuild adds at most 0.2% to load time.

The fix is Gunnar's, from `gr/labeled-traversal` (`d5d26baa`). A test loads an encoder saved with a different hash. Traversal v1 (#708) builds on this PR.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e9a5dc06f999`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
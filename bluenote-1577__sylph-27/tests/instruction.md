# Issue

**Title:** Use a `serde` visitor in `inspect` to avoid buffering the full database

## Description

Hi Jim!

In light with the `inspect` release here's a PR to reduce the memory requirements: using a `serde::de::Visitor` to visit the database allows to accumulate the stats over the `GenomeSketch` without having to deserialize the whole `Vec<GenomeSketch>` in memory. This means now you can `sylph inspect gtdb-r220-c200-dbv1.syldb` in about the same time but 60MiB of memory. An example for this kind of things can be found here [in the serde documentation](https://serde.rs/stream-array.html) to process a large JSON file without buffering it first.

NB: I was exploring how to do that with the database during the search as well to avoid having to load the full database, so that it could run on more memory-starved systems. What I had so far worked okay for single threads but didn't parallelize well, however that may be a direction worth exploring.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d85aaf978892`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
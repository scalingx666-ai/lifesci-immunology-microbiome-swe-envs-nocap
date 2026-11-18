# Issue

**Title:** [MRG] add code to remove duplicate prefetch matches when db has duplicate signatures

## Description

This is based on md5sums of the signatures, which as @luizirber pointed out could fail on empty signatures:

> caveat: our MD5 calculation only take ksize and the list of hashes, which means every empty MH has the same MD5 (for a specific k). That shouldn't change results, but it means that we conflate MinHash sketches (even if they have different identifiers)

This is a workaround for large SBTs that contain duplicates  This is not a problem when a non-sbt zip file is used as a DB.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `996df6eaf2b3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
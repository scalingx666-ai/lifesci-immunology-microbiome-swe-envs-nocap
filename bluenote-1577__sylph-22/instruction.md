# Issue

**Title:** Use `serde` custom serialization to handle `SequencesSketch`

## Description

Hi Jim!

As discussed this is a small PR that uses the capabilities of `serde` for custom serialization instead of manually having to create a dedicated extra struct and doing the conversion manually. The `serde` field attributes are documented here: https://serde.rs/field-attrs.html

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7467ee1d74f2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
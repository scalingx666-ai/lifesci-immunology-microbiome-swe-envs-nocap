# Issue

**Title:** Derive default build k-mer lengths from the compiled alphabet

## Description

Compute the `metagraph build` default from the compiled alphabet’s packed 64-bit encoding, rounding nucleotide lengths down to an odd value: DNA/RNA 31, DNA5 21, case-sensitive DNA 15, and protein 12. Previously the default was 3. Pass `-k 3` to retain that behavior; explicit `-k` values still override the default.

The parser and help share the computed constant. The regression builds a graph without `-k` and checks its stored length. The FAQ and release notes explain the rule.

The workflow CLI reads the selected MetaGraph executable’s build default, records it in `config.yaml`, and uses it throughout the build, including KMC stages. Pass `-k 31` to retain the previous workflow default.

Prepared with Claude and Codex.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `451ca344ef12`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
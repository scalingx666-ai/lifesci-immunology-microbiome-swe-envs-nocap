# Issue

**Title:** Genbank compatibility

## Description

Hi George,

The first set of changes to make the Pharokka gbk file compatible with GenBank:
- changed all methods to following format: "[CATEGORY:]TYPE[ (same species)][:EVIDENCE_BASIS]" (see https://www.insdc.org/submitting-standards/feature-table/) and changed "source" to "inference"
- removed the "trans_table" qualifier from tRNA and tmRNA features
- updated the anticodon format in tRNA features to "(pos:<location>,aa:<amino_acid>,seq:<text>)" + other small changes to tRNAs
- updated the CONTRIBUTING.md to markdown from rst to resolve formatting issues on github

I could not get the tests to run properly because of the python version problem I think (#395 #397), but when running the updated `pharokka.py` on a bunch of test genomes containing these features, the output gbk looks as expected.

Best,

Lander

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a286e0c3bfe6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Added support for stdin

## Description

This feature lets Woltka directly read alignments from the standard input (`stdin`). It makes the program more flexible. For example, Woltka can now directly parse BAM files:

```bash
samtools view input.bam | woltka classify -i - -o output.biom
```

It can even directly parse the output of alignment programs without saving the intermediates:

```bash
bowtie2 -x db -U input.fq | woltka classify -i - -o output.biom
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b815c91e9688`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
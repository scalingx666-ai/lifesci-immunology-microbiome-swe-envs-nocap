# Issue

**Title:** Convert depths in a single streaming pass

## Description

## Problem

`CONVERT_DEPTHS` decompressed the depth file into the work directory and then re-read it once per read set:

```bash
gunzip -f ${depth}
...
for i in $(seq 1 $n_abund); do
    bioawk -t '...' ${depth - '.gz'} > ${name}.abund
done
```

Under Fusion the work directory *is* the S3-backed FUSE mount, so this writes a multi-GB plaintext file to S3 and streams it back N times. Small long-read depth files fit in Fusion's cache and cost nothing; larger short-read ones do not, so every pass re-streams from S3.

This aborted two AWS full-size runs. Long-read assemblies finished in ~20 s, while short-read ones stalled for up to two hours and failed with Fusion I/O errors (174) and checkpoint dump failures (175). #1089 raised the memory to 2 GB on the assumption this was resource starvation; the second run had that change and failed anyway.

## Changes

Pipe `gzip -cd` straight into `bioawk` and emit every `.abund` file in a single pass. No plaintext intermediate, one read instead of N, and the staged input is no longer mutated in place.

The 2 GB from #1089 is left in place as a safety margin.

## Verification

Ran the module in the `bioawk:1.0--hed695b0_5` container against a synthetic three-BAM depth file, and the previous implementation over the same input. The `.abund` files are byte-identical and `versions.yml` is unchanged, so existing snapshots should be unaffected.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `171cf3697149`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
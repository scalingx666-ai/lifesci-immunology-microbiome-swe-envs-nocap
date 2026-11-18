# Issue

**Title:** Add optional --dedup flag for PCR duplicate removal

## Description

## Summary

This PR adds an optional `--dedup` command-line flag that enables PCR duplicate removal during the fastp preprocessing step.

## Usage

```bash
# Enable deduplication
EsViritu.py -r reads_R1.fq.gz reads_R2.fq.gz -s sample -o output --dedup True

# Default behavior (no deduplication) - unchanged
EsViritu.py -r reads_R1.fq.gz reads_R2.fq.gz -s sample -o output
```

## Motivation

PCR duplicates can artificially inflate read counts and skew abundance metrics (RPKMF). Providing an optional deduplication flag allows users to obtain more accurate quantification of read support.

## Changes

- **EsViritu.py**: Added `--dedup` argument (default: False)
- **esv_funcs.py**: Added `dedup` parameter to `trim_filter()` function; conditionally appends `--dedup` to fastp commands

## Benchmark Results

Tested on an environmental sample prepared for sequencing with Illumina VSP2 with 168M read pairs:

| Metric | `--dedup False` | `--dedup True` | Change |
|--------|-----------------|----------------|--------|
| Runtime | ~49 min | ~19 min | **2.6x faster** |
| Total reads | 168M | 57.8M | -65.6% |
| Duplication rate | - | 63.9% | - |

Virus detection remained consistent with expected proportional reduction in read counts.

## Backward Compatibility

This change is fully backward compatible. The default behavior (`--dedup False`) is identical to the current release.

## Testing

- [x] Tested with paired-end reads (`--dedup True`)
- [x] Verified default behavior unchanged (`--dedup False`)
- [ ] Single-end reads (same fastp flag, expected to work)

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9daec2570014`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Recover observed paired RNA overlaps with measured base quality

## Description

Paired RNA mode previously mapped overlapping mates independently, while reconstruction was incompatible with the quality columns used by RNA correction. Junctions requiring both observed mates could therefore miss correction despite passing the existing overlap and annotation gates.

Enable the existing overlap merger by default in RNA mode and its scheduled workflows, with `--no-reconstruct` / `reconstruct=False` retaining independent mates. Carry the measured quality of each selected base without boosting agreement, preserve R1's trailing sequence when R2 is contained, and aggregate exact read lengths before rounding across read groups. If a merged J+C hit masks a complete original-mate junction, one bounded native retry restores the original evidence under the existing completeness and score gates, with exact read/fragment accounting. Standalone `map` and amplicon defaults, overlap/mismatch gates and annotation cutoffs remain unchanged.

Merged overlaps are one fragment record, so record/read denominators change; the documentation makes this explicit. This is an observed-sequence union, with no germline completion.

Validation: 1,521 tests passed, 17 optional skips; lint and Sphinx warnings-as-errors passed. Independent review found no blocking issues and ran focused checks of both the initial change and the masking repair. Regressions cover both FASTQ readers, orientation, selected-base quality, missing qualities, contained mates, merged/independent sharding parity, and a reproduced constant-hit masking regression.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2adce094a280`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
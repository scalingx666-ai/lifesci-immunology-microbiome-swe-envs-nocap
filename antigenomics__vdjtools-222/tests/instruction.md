# Issue

**Title:** Fix model conditional support and allele collapse

## Description

Model completion can make a J gene selectable without restoring its deletion distribution. Native generation then indexes an empty categorical and can segfault. Separately, allele collapse can leave tandem-D conditionals unnormalized, and germline scaffolds can retain unreachable deletion/D–J support.

Restore newly reachable conditional groups from the same fitting template while preserving supported fitted probabilities; enforce the existing deletion and D–J bounds; normalize defined tandem-D conditionals during collapse. Native generation rejects an empty required distribution with an actionable exception. Explicit OLGA import remains unchanged.

Validation: regressions fail before the corresponding fixes; 178 focused checker, inference/extension and collapse tests pass. All 12 supported ARDA-reference scaffolds check clean in both allele and gene resolutions. Full CI and replacement fitted-model validation remain separate gates; this PR does not publish or substitute fitted models.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fd807e0881b1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
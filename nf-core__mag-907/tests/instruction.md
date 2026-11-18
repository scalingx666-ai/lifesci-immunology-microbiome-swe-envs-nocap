# Issue

**Title:** include COMEBin in dastool/bins output folder

## Description

I just ran this pipeline, and there weren't any COMEBin bins in the `DASTool/bins` folder! All the others were there, and the .tsv summary files all listed the COMEBin bins, so DASTool definitely processed them. 

I'm pretty sure it's just because they didn't get included with this pattern, so weren't published. They were all present in the relevant work directory, just not the output folder.



<!--
# nf-core/mag pull request

Many thanks for contributing to nf-core/mag!

Please fill in the appropriate checklist below (delete whatever is not relevant).
These are the most common things requested on pull requests (PRs).

Remember that PRs should be made against the dev branch, unless you're preparing a pipeline release.

Learn more about contributing: [CONTRIBUTING.md](https://github.com/nf-core/mag/tree/main/.github/CONTRIBUTING.md)
-->

## PR checklist

- [x] This comment contains a description of changes (with reason).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e5ebf2e57075`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Add `manifest.diagram` to `nextflow.config`

## Description

Adds the new `manifest.diagram` config attribute, pointing at the pipeline overview diagram.

See nf-core/tools#4460 for background: `manifest.diagram` gives a canonical location for the metro map, so that downstream consumers can find it. We'll use it for the nf-core website soon, for example. The new config option won't be released until Nextflow `26.10`, but older versions ignore unknown manifest fields, so it's safe to set in any pipeline today.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `961bcfdc6f30`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
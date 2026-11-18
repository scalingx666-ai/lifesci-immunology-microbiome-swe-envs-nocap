# Issue

**Title:** Add dates validation for ancientmetagenome-hostassociated and fix the previously added samples if necessary

## Description

# Pull Request

This PR is for a

- [ ] [New Publication(s)](#new-publication)
- [x] [Correction](#correction)

For the following list(s):

- [ ] ancientmetagenome-environmental ([README](https://github.com/SPAAM-workshop/AncientMetagenomeDir/tree/master/ancientmetagenome-environmental))
- [x] ancientmetagenome-hostassociated ([README](https://github.com/SPAAM-workshop/AncientMetagenomeDir/tree/master/ancientmetagenome-hostassociated))
- [ ] ancientsinglegenome-hostassociated ([README](https://github.com/SPAAM-workshop/AncientMetagenomeDir/tree/master/ancientsinglegenome-hostassociated))

While adding date information to the `dates.tsv` table of `ancientmetagenome-hostassociated`, no automatic validation of the added data was performed because the `amdirt validate` command for this table was missing in the GitHub workflow `check_dataset.yml`.

This PR adds the `amdirt validate` command to the GitHub workflow `check_dataset.yml` and fixes all previously added entries in the table that did not comply with conventions.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `aa956c6f41de`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
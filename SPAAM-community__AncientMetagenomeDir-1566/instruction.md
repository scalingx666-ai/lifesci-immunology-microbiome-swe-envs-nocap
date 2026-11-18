# Issue

**Title:** Manual workflow activation for generating images

## Description

This PR changes the behaviour of the two workflows, `AncientMetagenomeDir GeoJSON update` and `AncientMetagenomeDir Live Status Update` so that they can be executed manually from the GitHub Actions panel. Furthermore, it adds the information how to triggers these actions to the documentaion.

This change is necessary because we would like to trigger their execution once prior to deploying the latest release of AMDir. This address the issue #1438.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5bed23a34cff`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
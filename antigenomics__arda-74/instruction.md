# Issue

**Title:** Repin the Nextflow module and container refs to 2.5.6

## Description

. `integrations/nextflow/arda/environment.yml` still pinned `arda-mapper==2.5.5`.

That is the pin that matters: **`-profile conda`** — the path the module's own README calls *"works out of the box"* — would have installed the release **without** the reference-fetch lock. Which is precisely the scenario #73 fixes: the Nextflow module launches one process per sample, and on a cold cache all of them fetch the reference into the same path at once.

Also bumps the Dockerfile build/tag/push examples, `main.nf`'s `container`, and the two docs that show the container pin.

The two remaining `2.5.5` mentions are historical statements ("a core dependency **since** 2.5.5", "an optional extra **before** 2.5.5") and are left alone.

Docs build clean under `-W`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `52f041f17f34`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
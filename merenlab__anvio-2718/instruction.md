# Issue

**Title:** Support MUSCLE 5 in the MUSCLE driver

## Description

# Summary
This PR updates anvi'o's MUSCLE integration for MUSCLE 5 while keeping the driver compatible with MUSCLE 3.

The main issue is that MUSCLE 5 changed its CLI compared to MUSCLE 3. Previously, anvi'o could call MUSCLE through the older stdin/stdout style and also had a `clustalw_format` / `-clw` path. After the KEGG HMM build change in #2717, that CLUSTAL output path is no longer used, so this PR removes it and updates the driver to use the right command syntax depending on the installed MUSCLE version. It is a little bet messy but means that the users of the anvio-development branch can continue with their current installed MUSCLE version, whilst all new installs can use v5. 

## Changes include:

- Detect MUSCLE 3 vs MUSCLE 5 in the driver.
- Keep MUSCLE 3 support through the existing stdin/stdout behavior.
- Support MUSCLE 5 `-align ... -output ...`.
- Support MUSCLE 5 `-super5 ... -output ...`.
- Remove the now-unused `clustalw_format` / `-clw` path from the MUSCLE driver.
- Update EcoPhylo's MUSCLE alignment rule to use version-appropriate command syntax.
- Make EcoPhylo's default MUSCLE `additional_params` version-neutral - the CLI commands in the workflow are no longer supported by MSUCLE v5
- Update the main conda environment to require `muscle>=5`.
- Update the Dockerfile install to to require `muscle>=5`.
- Update MUSCLE parameter docs for MUSCLE 5.

`Dockerfiles/anvio-structure/Dockerfile` is left pinned to MUSCLE 3.8 as that Dockerfile installs the old released anvi'o 7.1 code, not this branch's updated MUSCLE driver. Updating it here would break that image rather than help it.

## Testing I ran:

- MUSCLE 3 driver test in an `anvio-dev` environment installed as outlined in the docs.
- MUSCLE 5 driver test in a test environment with all dependencies pinned as outlined in install docs, apart from MUSCLE now being at v5. 
- MUSCLE 5 `MUSCLE_PARAMS=-super5` test.
- KEGG `build_HMM_from_seqs()` with MUSCLE 5 produced a valid `HMMER3/` model.
- EcoPhylo MUSCLE command checks for MUSCLE 3, MUSCLE 5 `-align`, and MUSCLE 5 `-super5`.
- `py_compile` for touched Python modules.
- `anvi-self-test --suite pangenomics --no-interactive` completed successfully

So the fix here is to make anvi'o speak both MUSCLE CLIs in the driver, while moving the main anvi'o environment forward to MUSCLE 5.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8545a97aa51f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
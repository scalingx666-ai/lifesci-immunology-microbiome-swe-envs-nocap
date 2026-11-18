# Issue

**Title:** ci: retry container pulls that drop

## Description

## Summary

CI run 44130690808 failed on a dropped connection while docker pulled an image (`connection reset by peer`), not on a test. This makes image pulls recover on both engines, and lets PRs share the KOfam cache.

```diff
 conf/base.config
-errorStrategy = { task.exitStatus in ((130..145) + 104) ? 'retry' : 'finish' }
+errorStrategy = { task.exitStatus in ((130..145) + 104 + 125) ? 'retry' : 'finish' }
```

Docker pulls inside the task; a failed `docker run` exits 125, so the task (and its pull) is retried once. In `conf/base.config`, so users get it too.

```text
CI test job, Run PR-gate tests
  NXF_APPTAINER_CACHEDIR=$RUNNER_TEMP/apptainer   one image cache for every nf-test (was one per test)
  pixi run test
  failed with "Failed to pull singularity image"? -> pixi run test-nf once more (cached images reused)
```

Apptainer needs the rerun because Nextflow pulls the `.sif` before the task exists: a failed download is fatal and `errorStrategy` never runs.

```diff
 on:
   pull_request:
+  push: [dev]                    # kofam-cache job: saves the KOfam mini database on dev
+.github/actions/kofam-mini-db    # restore-or-build, shared by the test and kofam-cache jobs
```

KOfam's cache was scoped to each PR's ref, so every new PR rebuilt it (~90 s per job). Caches saved on `dev`, the default branch, are restorable by every PR; this takes effect once the workflow is on `dev`.

`docs/contributing.md` gains "Prefer what can't go stale". An earlier commit here pre-pulled images using a hand-kept list of PR-gate processes and a copy of Nextflow's cache-naming rule; both were replaced by the above because they drift.

## Evidence

- **Before:** a failed apptainer pull (tested with a missing image, under apptainer) ends the run with `Failed to pull singularity image`; the `errorStrategy` closure is never called. Docker OWC failed in CI: `docker: failed to copy: ... connection reset by peer`.
- **Before:** apptainer PR-gate tests 449 s with a per-test image cache. With a shared cache (run 44142780125, images already present) the tests took 247 s.
- **After:** see this PR's CI run for the shared-cache timing without pre-pulling.

## Merge Danger

**Door:** two-way

**Blast Radius:** CI, retries

A test failure caused by a failed image pull reruns all nf-tests once (~5 min extra, rare). For users, a task whose `docker run` fails for any reason (not only a pull) is retried once before failing.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2efb10f50e20`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
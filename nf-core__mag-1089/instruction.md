# Issue

**Title:** Increase CONVERT_DEPTHS memory in the full test config

## Description

## Problem

The AWS full-size test run `1VGAEYl9hrOScI` aborted on a `CONVERT_DEPTHS` task that exited with status 174 after sitting in `RUNNING` for 2h04:

```
Caused by:
  Essential container in task exited
Command exit status:
  174
Command output:
  (empty)
```

`.command.out` was never written and `.command.err` contained only the Fusion startup banner, so the script produced nothing. The five sibling `CONVERT_DEPTHS` tasks were also still running when the session aborted.

## Changes

Raise `CONVERT_DEPTHS` from 1 GB to 2 GB in `conf/test_full.config`, so the starting allocation has headroom rather than relying on retry escalation.

The script only streams (`gunzip`, a one-line `awk`, then `bioawk` passes), so peak RSS is small, but the container also hosts the Fusion client and 1 GB left nothing spare. 2 GB matches the tier already used by the other small processes in this config.

## On exit code 174

This PR originally also added 174 to the retriable exit-code lists. Dropped per review — and the docs confirm that was the right call. Seqera documents 174 as `ErrorExitCode`, *"Fusion I/O error, application-level input/output error"*, explicitly not an out-of-memory condition:

> The `sysexits.h` standard uses exit code 74 for "input/output error" and reserves 150-199 for application use. In Fusion's context, 174 means "application input/output error".

The listed causes are all FUSE/mount-level — failing to start or stop the FUSE process, errors during filesystem shutdown or unmount. The OOM codes inherited from the nf-core template are a different category, so 174 does not belong there, in this pipeline or upstream.

That does mean this PR does not address the two-hour stall itself, which still looks like a Fusion or Spot issue worth tracking separately.

Source: [Fusion error codes and exit messages](https://docs.seqera.io/fusion/troubleshooting/error-codes-exit-messages#exit-codes)

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5977159bcec0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
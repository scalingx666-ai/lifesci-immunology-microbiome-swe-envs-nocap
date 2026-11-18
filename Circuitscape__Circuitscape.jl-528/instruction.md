# Issue

**Title:** CI: run downstream Omniscape tests against Omniscape main

## Description

The downstream Omniscape.jl job checks out Omniscape's `cs/circuitscape-6-julia-1.12` branch. That branch was deleted when Circuitscape/Omniscape.jl#171 merged (2026-09-13), so the job now fails at `actions/checkout` on every PR before any test runs (seen on #521–#525). Omniscape `main` (v0.6.4) has Circuitscape compat `6.1`, so this switches the ref to `main`, as the workflow comment intended.

Checked locally: Omniscape `main` tests pass against current Circuitscape (Internals 20/20, `run_omniscape()` 31/31).

After this merges, re-run CI on #521–#525 to clear the red downstream check.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `70f512880240`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
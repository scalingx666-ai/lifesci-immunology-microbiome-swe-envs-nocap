# Issue

**Title:** CI: downstream test against Omniscape.jl

## Description

Adds a `downstream-omniscape` job to CI that checks out Omniscape.jl, develops this checkout of Circuitscape into a scratch environment alongside it, and runs Omniscape's test suite. Omniscape compares moving-window results against its own reference outputs, so a Circuitscape change that alters results in a path it uses fails here.

Omniscape `main` still pins Circuitscape 5.15 and Julia `~1.11`, so the job checks out the branch of Circuitscape/Omniscape.jl#171, which migrates Omniscape to Circuitscape 6 and Julia 1.12. Switch the `ref` to `main` once that PR merges.

The job is `continue-on-error` for now, so it reports but does not block merging. Promote it to required once it has been green on master for a while; a failure on an intended Circuitscape change may mean Omniscape's fixtures need updating instead.

Verified locally: Omniscape's suite (31 tests) on that branch passes against current Circuitscape master with the same develop-and-test recipe.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_016qia6G6xbgffF6ENXzAX8t

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `253a4189296a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
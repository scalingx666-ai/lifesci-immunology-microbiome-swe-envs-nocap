# Issue

**Title:** Set up KEGG data for metabolism workflow tests

## Description

This PR adds the KEGG data setup prior to running the metabolism testing suites. Prior to this, there was an issue runnign the tests as no KEGG data dir was available for the runner, . 

Locally it could be solved by making sure `anvi-setup-kegg-data` had been ran but I wasn't sure whether that was possible here and whether the provided storage was large enough.

I tested adding a pinned KEGG setup step before the metabolism suite using the `v2024-09-08` snapshot. A few findings:

- Disk space is pretty large! In an earlier commit I added some `du` and `df` calls to see how much space is available and was surprised itis around 100G! After the three earlier self-tests, there was still ~81G free before KEGG setup and ~61G free after setup.
- The KEGG archive was ~5.46G, and the installed KEGG directory was ~15G.
- Calling `anvi-setup-kegg-data --kegg-snapshot v2024-09-08` directly failed in Actions with a network error from Python/urllib:
  `[Errno 101] Network is unreachable`
- The same URL worked outside Actions, so I switched the workflow to download the pinned archive with `curl --ipv4 --retry ...`, then run:
  `anvi-setup-kegg-data --kegg-archive ...`
- With that change, KEGG setup completed and the metabolism test suite passed.

Successful run (with the extra diagnostic info not included in this commit/PR):
https://github.com/bcoltman/anvio/actions/runs/27099291702

So the fix is to explicitly prepare KEGG data in the workflow before running the metabolism suite. The only issue being that snapshot download is handled by `curl` with IPv4/retries, then passed to anvi’o as a local archive as opposed to being handled fully by `anvi-setup-kegg-data`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ec4d92905518`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
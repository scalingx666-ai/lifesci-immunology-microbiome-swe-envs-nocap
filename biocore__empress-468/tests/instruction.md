# Issue

**Title:** Rerun GitHub Actions on push events to master; update dev documentation to mention a weird thing with JS tests

## Description

Should fix #467 (I think ... I don't really have a way of testing this).

Also updates `CONTRIBUTING.md` based on discussion with @gibsramen (we figured out the reason #464 was failing, and the errors being emitted from that reason were pretty obscure -- hopefully this helps clarify things for future devs).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a10581561e7d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
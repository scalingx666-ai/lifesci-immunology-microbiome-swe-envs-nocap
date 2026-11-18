# Issue

**Title:** ci: make the FreeBSD test job reliable, and shallow-clone the test suite

## Description

- The FreeBSD job intermittently timed out at 20 minutes: the in-VM
  `git clone` of vsearch-tests would stall on the guest network, and git
  has no transfer timeout by default. Clone the test suite on the Ubuntu
  host instead (reliable network); vmactions syncs it into the VM.
- Add progress banners (Building / Running tests / Tests finished) and a
  fail-fast check that the test suite was synced in, so the job's state is
  visible and a missing checkout errors immediately instead of failing
  obscurely.
- Shallow-clone the test suite (`--depth 1`) in the Linux and macOS jobs
  too — the suite only needs the current snapshot; faster and less prone
  to network stalls.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ad0b38a378ab`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
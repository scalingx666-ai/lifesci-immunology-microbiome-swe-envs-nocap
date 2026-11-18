# Issue

**Title:** ci: run the FreeBSD test suite into a log file to avoid SSH-channel stalls

## Description

The build-and-test workflow's freebsd-x86_64 job runs inside a vmactions/freebsd-vm QEMU guest, driven over an SSH/pty channel. The test suite emits ~7,700 result lines; streaming that volume over the channel wedges the guest after a few minutes, so the job stops responding at a random point and has to be cancelled. The other (native) platforms run the same suite without issue.

Run the suite into a log file inside the VM instead of streaming every line, then print a bounded summary (FAIL lines plus the log tail) and propagate the suite's exit status so CI still gates on failures. Only the FreeBSD job is affected.


Claude-Session: https://claude.ai/code/session_01Y1QDvTPR6e4xgma7Bzf9qB

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `52088e789cd0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
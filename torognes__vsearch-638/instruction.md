# Issue

**Title:** ci: refresh build-and-test and build-all workflows

## Description

# ci: refresh build-and-test and build-all workflows

## Summary

Updates the two CI workflows (`build-and-test.yml`, `build-all.yml`) with
reliability and hygiene improvements accumulated during fork development.
No source or build-system changes — this is CI only.

## Changes

### Both workflows

- Add a `concurrency` group with `cancel-in-progress: true`, so a new push/PR
  run automatically cancels the superseded run on the same ref instead of
  queuing behind it.
- Bump pinned actions to current major versions (`actions/checkout@v6`,
  `actions/upload-artifact@v7`), off the deprecated Node.js 20 runtime.
- macOS jobs: the GitHub runner images ship pre-tapped `aws/tap` and
  `azure/bicep`, which emit Homebrew "tap-trust" warnings on every run. We use
  neither, so they're removed before `brew update`/`install`. `azure/bicep`
  carries an installed `bicep` formula, so it's uninstalled first and the tap
  then removed without `--force` (which would print its own warning). Each step
  is guarded to stay quiet and non-fatal on a future image that no longer ships
  these taps.

### `build-and-test.yml`

- Add `timeout-minutes: 20` to every job so a hung job (notably the FreeBSD VM)
  fails fast instead of burning the full 6-hour default.
- Run the full push/PR matrix: native `linux-x86_64`, a cross-build matrix
  (Windows, aarch64, mips64el, ppc64le, riscv64), macOS arm64 + Intel, and
  FreeBSD.
- FreeBSD job: stream the ~7,700-test suite into a log file inside the VM under
  an unprivileged user, then surface a bounded summary (FAIL lines + log tail).
  Streaming that volume of output over the vmactions SSH channel wedged the
  guest at a random point a few minutes in; logging to a file and printing a
  summary fixes the stall. The unprivileged user is required because root
  bypasses POSIX permission checks, which the suite's "file not
  readable/writable" tests depend on.

### `build-all.yml`

- `concurrency` + updated actions as above; macOS matrix builds release
  binaries for arm64 and Intel with the same tap cleanup.

## Notes

These were validated on the fork's CI (Linux, all cross-builds, macOS
arm64/Intel, FreeBSD all green; macOS install step now annotation-free).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `68f7117c99ee`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
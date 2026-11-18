# Issue

**Title:** Consolidate HLA-HD tests into main nf-test workflow

## Description

## Summary

- Removes standalone `nf-test-hlahd.yml` workflow and consolidates HLA-HD tests as a job within `nf-test.yml`, following the [netmhcpan pattern from epitopeprediction](https://github.com/nf-core/epitopeprediction/blob/dev/.github/workflows/nf-test.yml)
- Fixes broken `--tag !hlahd` negation (not supported in nf-test 0.9.3) by switching to positive `--tag pipeline` matching
- HLA-HD test files now use only `tag "hlahd"` (not `tag "pipeline"`) so they run exclusively in the dedicated `hlahd` job

## Changes

- **`.github/workflows/nf-test.yml`**: Added `hlahd` job (download, decrypt, run via nf-test action), changed main job to `tags: "pipeline"`, added `hlahd` to `confirm-pass` needs
- **`.github/actions/nf-test/action.yml`**: Added `changed_since` input, made `shard`/`total_shards`/`paths` optional with defaults
- **`.github/workflows/nf-test-hlahd.yml`**: Deleted (consolidated into nf-test.yml)
- **`tests/hlahd.nf.test`**: Removed `tag "pipeline"`, kept `tag "hlahd"`
- **`tests/optitype_hlahd.nf.test`**: Changed `tag "pipeline"` to `tag "hlahd"`
- **`.claude/`**, **`CLAUDE.md`**: Added CI rules, skills, and project docs

## Test plan

- [ ] Verify `nf-test` job runs standard pipeline tests with `--tag pipeline` (excludes hlahd tests)
- [ ] Verify `hlahd` job downloads, decrypts, and runs HLA-HD tests on internal PRs
- [ ] Verify `hlahd` job is skipped on fork PRs (no secret access)
- [ ] Verify `confirm-pass` aggregates both `nf-test` and `hlahd` results

Supersedes #203

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `48f20ffc04e6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
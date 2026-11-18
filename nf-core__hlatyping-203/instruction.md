# Issue

**Title:** Add standalone CI workflow for HLA-HD licensed software tests

## Description

Implements automated testing for HLA-HD functionality using encrypted licensed software from test-datasets, following the nf-core/epitopeprediction NetMHCpan reference pattern as a standalone workflow.

## Changes

- **New workflow**: `.github/workflows/nf-test-hlahd.yml`
  - Standalone workflow file following epitopeprediction PR #317 pattern
  - Downloads encrypted HLA-HD 1.7.1 tarball from nf-core/test-datasets
  - Decrypts using GPG with `GPG_PASSPHRASE` secret
  - Runs pipeline with `nextflow run` command using test_hlahd and test_optitype_hlahd profiles
  - Passes `hlahd_path` parameter directly to pipeline execution
  - Tests against Nextflow 25.04.0 and latest-everything with Docker profile
  - Only runs from nf-core/hlatyping repository (not forks) to ensure secret access

## Security

Workflow only executes for PRs from nf-core/hlatyping repository (not forks) to ensure secret access. Uses same conditional pattern as epitopeprediction:

```yaml
if: ${{ ( github.event_name == 'push' && github.repository == 'nf-core/hlatyping' ) || github.event.pull_request.head.repo.full_name == 'nf-core/hlatyping' }}
```

## Integration

- Maintains compatibility with dev branch structure (no changes to reusable nf-test action)
- Leverages existing test configurations (`conf/test_hlahd.config`, `conf/test_optitype_hlahd.config`)
- Test files use standard `tag "pipeline"` at pipeline level
- Uses existing HLAHD_INSTALL module for tarball unpacking during pipeline execution
- Follows established nf-core patterns for licensed software testing

<!-- START COPILOT CODING AGENT SUFFIX -->

<!-- START COPILOT ORIGINAL PROMPT -->

<details>

<summary>Original prompt</summary>

> Implement a CI test that tests the new HLA-HD functionality using the hlahd.nf.test and hlahd_optitype.nf.test scripts. Since HLA-HD is licenced, we need to download it (see https://github.com/nf-core/test-datasets/tree/hlatyping/software) and decrypt it using gpg and GitHub secrets. Then the tarball is unpacked using the already implemented code (see ). Please use as a reference implementation the netmhcpan (licensed) CI tests here https://github.com/nf-core/epitopeprediction/blob/37c08f05dcb0444a859b656545e1ed15c1ea95d1/.github/workflows/ci.yml#L120. NOTE this test does not 100% fit anymore to the current ci, which is handled in https://github.com/nf-core/hlatyping/blob/dev/.github/actions/nf-test/action.yml

</details>

<!-- START COPILOT CODING AGENT TIPS -->
---

💡 You can make Copilot smarter by setting up custom instructions, customizing its development environment and configuring Model Context Protocol (MCP) servers. Learn more [Copilot coding agent tips](https://gh.io/copilot-coding-agent-tips) in the docs.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2d7d92f0e231`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
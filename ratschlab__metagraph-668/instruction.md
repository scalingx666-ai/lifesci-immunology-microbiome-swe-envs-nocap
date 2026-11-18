# Issue

**Title:** Fetch Eigen from its GitHub mirror

## Description

GitLab's overloaded backend is refusing Eigen checkouts before CI can build. Fetch Eigen from its GitHub mirror instead, keeping the pinned commit `d71c30c4` unchanged.

The CI cache key already includes `.gitmodules`, so this URL change starts a fresh dependency cache. Existing local clones can adopt the new URL with:

```sh
git submodule sync -- metagraph/external-libraries/eigen
```

<!-- This is an auto-generated description by cubic. -->
---
## Summary by cubic
Fetches the pinned Eigen submodule from its GitHub mirror instead of GitLab, whose overloaded backend was refusing checkouts before CI could build. The pinned commit `d71c30c4` is unchanged, and the CI cache key includes `.gitmodules`, so this URL change starts a fresh dependency cache.

**Migration**
- Existing local clones can adopt the new URL with `git submodule sync -- metagraph/external-libraries/eigen`.

<sup>Written for commit e4b57b037f72bc79b48f079b2b21f35716d401dd. Summary will update on new commits.</sup>

<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/668?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/668?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F668&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>

<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5abefa307da0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
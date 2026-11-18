# Issue

**Title:** Bump requests from 2.21.0 to 2.22.0

## Description

Bumps [requests](https://github.com/requests/requests) from 2.21.0 to 2.22.0.
<details>
<summary>Changelog</summary>

*Sourced from [requests's changelog](https://github.com/kennethreitz/requests/blob/master/HISTORY.md).*

> 2.22.0 (2019-05-15)
> -------------------
>
> **Dependencies**
>
> - Requests now supports urllib3 v1.25.2.
>   (note: 1.25.0 and 1.25.1 are incompatible)
>
> **Deprecations**
>
> - Requests has officially stopped support for Python 3.4.
</details>
<details>
<summary>Commits</summary>

-  v2.22.0
-  drop 3.4 support
-  adjust pytest pins to fix testing infra
-  Merge pull request  from imikay/patch-1
-  Merge pull request  from zurbrugc/master
-  Linked contribution information in README
-  Update index.rst
-  Update README.md
-  Merge branch 'master' into patch-1
-  Merge pull request  from tomchristie/patch-1
- Additional commits viewable in [compare view](https://github.com/requests/requests/compare/v2.21.0...v2.22.0)
</details>
<br />

[![Dependabot compatibility score](https://api.dependabot.com/badges/compatibility_score?dependency-name=requests&package-manager=pip&previous-version=2.21.0&new-version=2.22.0)](https://dependabot.com/compatibility-score.html?dependency-name=requests&package-manager=pip&previous-version=2.21.0&new-version=2.22.0)

Dependabot will resolve any conflicts with this PR as long as you don't alter it yourself. You can also trigger a rebase manually by commenting `@dependabot rebase`.

[//]: # (dependabot-automerge-start)
[//]: # (dependabot-automerge-end)

---

<details>
<summary>Dependabot commands and options</summary>
<br />

You can trigger Dependabot actions by commenting on this PR:
- `@dependabot rebase` will rebase this PR
- `@dependabot recreate` will recreate this PR, overwriting any edits that have been made to it
- `@dependabot merge` will merge this PR after your CI passes on it
- `@dependabot squash and merge` will squash and merge this PR after your CI passes on it
- `@dependabot cancel merge` will cancel a previously requested merge and block automerging
- `@dependabot reopen` will reopen this PR if it is closed
- `@dependabot ignore this [patch|minor|major] version` will close this PR and stop Dependabot creating any more for this minor/major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)
- `@dependabot use these labels` will set the current labels as the default for future PRs for this repo and language
- `@dependabot use these reviewers` will set the current reviewers as the default for future PRs for this repo and language
- `@dependabot use these assignees` will set the current assignees as the default for future PRs for this repo and language
- `@dependabot use this milestone` will set the current milestone as the default for future PRs for this repo and language
- `@dependabot badge me` will comment on this PR with code to add a "Dependabot enabled" badge to your readme

Additionally, you can set the following in your Dependabot [dashboard](https://app.dependabot.com):
- Update frequency (including time of day and day of week)
- Automerge options (never/patch/minor, and dev/runtime dependencies)
- Pull request limits (per update run and/or open at any time)
- Out-of-range updates (receive only lockfile updates, if desired)
- Security updates (receive only security updates, if desired)

Finally, you can contact us by mentioning @dependabot.

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b53c0b86a2df`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
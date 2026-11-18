# Issue

**Title:** Bump codecov from 2.1.3 to 2.1.4

## Description

Bumps [codecov](https://github.com/codecov/codecov-python) from 2.1.3 to 2.1.4.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/codecov/codecov-python/blob/master/CHANGELOG.md">codecov's changelog</a>.</em></p>
<blockquote>
<h3><code>2.1.4</code></h3>
<ul>
<li><a href="https://github-redirect.dependabot.com/codecov/codecov-python/pull/260">#260</a> Enforce black formatting</li>
<li><a href="https://github-redirect.dependabot.com/codecov/codecov-python/pull/169">#169</a> Fix command line quoting on Windows</li>
<li><a href="https://github-redirect.dependabot.com/codecov/codecov-python/pull/216">#216</a> Fix GitLab CI project directory detection on Windows</li>
<li><a href="https://github-redirect.dependabot.com/codecov/codecov-python/pull/264">#264</a> Fix GitLab CI post version 9</li>
<li><a href="https://github-redirect.dependabot.com/codecov/codecov-python/pull/262">#262</a> Check text for NoneType on writes</li>
<li><a href="https://github-redirect.dependabot.com/codecov/codecov-python/pull/266">#266</a> Include the cacert in the PUT call when uploading to S3</li>
<li><a href="https://github-redirect.dependabot.com/codecov/codecov-python/pull/263">#263</a> Fixed gcov not being found in certain instances</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li>See full diff in <a href="https://github.com/codecov/codecov-python/commits/v2.1.4">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://api.dependabot.com/badges/compatibility_score?dependency-name=codecov&package-manager=pip&previous-version=2.1.3&new-version=2.1.4)](https://dependabot.com/compatibility-score/?dependency-name=codecov&package-manager=pip&previous-version=2.1.3&new-version=2.1.4)

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
- `@dependabot close` will close this PR and stop Dependabot recreating it. You can achieve the same result by closing it manually
- `@dependabot ignore this major version` will close this PR and stop Dependabot creating any more for this major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this minor version` will close this PR and stop Dependabot creating any more for this minor version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)
- `@dependabot use these labels` will set the current labels as the default for future PRs for this repo and language
- `@dependabot use these reviewers` will set the current reviewers as the default for future PRs for this repo and language
- `@dependabot use these assignees` will set the current assignees as the default for future PRs for this repo and language
- `@dependabot use this milestone` will set the current milestone as the default for future PRs for this repo and language
- `@dependabot badge me` will comment on this PR with code to add a "Dependabot enabled" badge to your readme

Additionally, you can set the following in your Dependabot [dashboard](https://app.dependabot.com):
- Update frequency (including time of day and day of week)
- Pull request limits (per update run and/or open at any time)
- Automerge options (never/patch/minor, and dev/runtime dependencies)
- Out-of-range updates (receive only lockfile updates, if desired)
- Security updates (receive only security updates, if desired)

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cb956798c56a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
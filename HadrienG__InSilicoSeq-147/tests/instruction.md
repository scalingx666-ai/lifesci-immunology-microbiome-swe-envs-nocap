# Issue

**Title:** Bump requests from 2.22.0 to 2.23.0

## Description

[//]: # (dependabot-start)
⚠️  **Dependabot is rebasing this PR** ⚠️

If you make any changes to it yourself then they will take precedence over the rebase.

---

[//]: # (dependabot-end)

Bumps [requests](https://github.com/psf/requests) from 2.22.0 to 2.23.0.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/psf/requests/blob/master/HISTORY.md">requests's changelog</a>.</em></p>
<blockquote>
<h2>2.23.0 (2020-02-19)</h2>
<p><strong>Improvements</strong></p>
<ul>
<li>Remove defunct reference to <code>prefetch</code> in Session <code>__attrs__</code> (<a href="https://github-redirect.dependabot.com/psf/requests/issues/5110">#5110</a>)</li>
</ul>
<p><strong>Bugfixes</strong></p>
<ul>
<li>Requests no longer outputs password in basic auth usage warning. (<a href="https://github-redirect.dependabot.com/psf/requests/issues/5099">#5099</a>)</li>
</ul>
<p><strong>Dependencies</strong></p>
<ul>
<li>Pinning for <code>chardet</code> and <code>idna</code> now uses major version instead of minor.
This hopefully reduces the need for releases everytime a dependency is updated.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>c7e0fc0</code></a> v2.23.0</li>
<li><a href=""><code>fd13816</code></a> Revert &quot;Fix for response with UTF-8 BOM <a href="https://github-redirect.dependabot.com/psf/requests/issues/4976">#4976</a>&quot;</li>
<li><a href=""><code>24bcb9e</code></a> Revert &quot;Use urllib for chunked requests&quot;</li>
<li><a href=""><code>b15056d</code></a> Revert &quot;<a href="https://github-redirect.dependabot.com/psf/requests/issues/4965">#4965</a> fix: Accessing response.content twice removes forgets read error.&quot;</li>
<li><a href=""><code>80011a7</code></a> Remove an obsolete attribute from <strong>attrs</strong></li>
<li><a href=""><code>c46f55b</code></a> Limit dependencies to major instead of minor (<a href="https://github-redirect.dependabot.com/psf/requests/issues/5342">#5342</a>)</li>
<li><a href=""><code>e113020</code></a> Fix the syntax highlighting in the example (<a href="https://github-redirect.dependabot.com/psf/requests/issues/5276">#5276</a>)</li>
<li><a href=""><code>23f6faa</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/psf/requests/issues/5346">#5346</a> from stock1218/master</li>
<li><a href=""><code>ae0a497</code></a> Update link to pipenv in installation guide.</li>
<li><a href=""><code>b1631b0</code></a> Update link to pipenv in README.</li>
<li>Additional commits viewable in <a href="https://github.com/psf/requests/compare/v2.22.0...v2.23.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://api.dependabot.com/badges/compatibility_score?dependency-name=requests&package-manager=pip&previous-version=2.22.0&new-version=2.23.0)](https://dependabot.com/compatibility-score/?dependency-name=requests&package-manager=pip&previous-version=2.22.0&new-version=2.23.0)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `03bfa5a5a2e3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
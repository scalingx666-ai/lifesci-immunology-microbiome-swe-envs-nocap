# Issue

**Title:** Bump codecov from 2.0.15 to 2.0.22

## Description

Bumps [codecov](https://github.com/codecov/codecov-python) from 2.0.15 to 2.0.22.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/codecov/codecov-python/blob/v2.0.22/CHANGELOG.md">codecov's changelog</a>.</em></p>
<blockquote>
<h3>`2.0.22</h3>
<ul>
<li>Cleaning TOC generation</li>
</ul>
<h3><code>2.0.21</code></h3>
<ul>
<li>fixed string issues</li>
</ul>
<h3><code>2.0.20</code></h3>
<ul>
<li>fixed broken subprocess handling</li>
</ul>
<h3><code>2.0.19</code></h3>
<ul>
<li>fixed broken subprocess handling</li>
</ul>
<h3><code>2.0.18</code></h3>
<ul>
<li>fixed broken subprocess handling</li>
</ul>
<h3><code>2.0.17</code></h3>
<ul>
<li>fixed reported command injection vulnerability.</li>
</ul>
<h3><code>2.0.16</code></h3>
<ul>
<li>fixed reported command injection vulnerability.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>06c2522</code></a> bump version</li>
<li><a href=""><code>800d1ad</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/codecov/codecov-python/issues/242">#242</a> from codecov/clean-toc-generation</li>
<li><a href=""><code>bc18afd</code></a> Cleaning TOC generation</li>
<li><a href=""><code>046b4fa</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/codecov/codecov-python/issues/241">#241</a> from codecov/string-processing</li>
<li><a href=""><code>93c9903</code></a> Bump version</li>
<li><a href=""><code>3ad07c2</code></a> bump version</li>
<li><a href=""><code>9518ea6</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/codecov/codecov-python/issues/240">#240</a> from codecov/2020</li>
<li><a href=""><code>47c8206</code></a> generic exception</li>
<li><a href=""><code>51e421e</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/codecov/codecov-python/issues/239">#239</a> from codecov/fix-subprocess</li>
<li><a href=""><code>38f2303</code></a> Exception</li>
<li>Additional commits viewable in <a href="https://github.com/codecov/codecov-python/compare/v2.0.15...v2.0.22">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://api.dependabot.com/badges/compatibility_score?dependency-name=codecov&package-manager=pip&previous-version=2.0.15&new-version=2.0.22)](https://dependabot.com/compatibility-score/?dependency-name=codecov&package-manager=pip&previous-version=2.0.15&new-version=2.0.22)

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
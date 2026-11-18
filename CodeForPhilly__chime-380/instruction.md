# Issue

**Title:** Bump bleach from 3.1.3 to 3.1.4

## Description

Bumps [bleach](https://github.com/mozilla/bleach) from 3.1.3 to 3.1.4.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/mozilla/bleach/blob/master/CHANGES">bleach's changelog</a>.</em></p>
<blockquote>
<h2>Version 3.1.4 (March 24th, 2020)</h2>
<p><strong>Security fixes</strong></p>
<ul>
<li>
<p><code>bleach.clean</code> behavior parsing style attributes could result in a
regular expression denial of service (ReDoS).</p>
<p>Calls to <code>bleach.clean</code> with an allowed tag with an allowed
<code>style</code> attribute were vulnerable to ReDoS. For example,
<code>bleach.clean(..., attributes={'a': ['style']})</code>.</p>
<p>This issue was confirmed in Bleach versions v3.1.3, v3.1.2, v3.1.1,
v3.1.0, v3.0.0, v2.1.4, and v2.1.3. Earlier versions used a similar
regular expression and should be considered vulnerable too.</p>
<p>Anyone using Bleach &lt;=v3.1.3 is encouraged to upgrade.</p>
<p><a href="https://bugzilla.mozilla.org/show_bug.cgi?id=1623633">https://bugzilla.mozilla.org/show_bug.cgi?id=1623633</a></p>
</li>
</ul>
<p><strong>Backwards incompatible changes</strong></p>
<ul>
<li>Style attributes with dashes, or single or double quoted values are
cleaned instead of passed through.</li>
</ul>
<p><strong>Features</strong></p>
<p>None</p>
<p><strong>Bug fixes</strong></p>
<p>None</p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>6e74a50</code></a> Update for v3.1.4 release</li>
<li><a href=""><code>d6018f2</code></a> fix bug 1623633</li>
<li>See full diff in <a href="https://github.com/mozilla/bleach/compare/v3.1.3...v3.1.4">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=bleach&package-manager=pip&previous-version=3.1.3&new-version=3.1.4)](https://help.github.com/articles/configuring-automated-security-fixes)

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

You can disable automated security fix PRs for this repo from the [Security Alerts page](https://github.com/CodeForPhilly/chime/network/alerts).

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d5ed9d58b20a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** build(deps): bump mako from 1.3.11 to 1.3.12

## Description

Bumps [mako](https://github.com/sqlalchemy/mako) from 1.3.11 to 1.3.12.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/sqlalchemy/mako/releases">mako's releases</a>.</em></p>
<blockquote>
<h1>1.3.12</h1>
<p>Released: Tue Apr 28 2026</p>
<h2>bug</h2>
<ul>
<li>
<p><strong>[bug] [template]</strong> Fixed issue in <code>TemplateLookup</code> where a URI with backslash path
separators (e.g. <code>\..\secret.txt</code>) could bypass the directory traversal
check on Windows, allowing reads of arbitrary files outside of the template
directory.  Backslash characters in URIs are now normalized to forward
slashes before path resolution.</p>
<p>References: <a href="">#435</a></p>
</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li>See full diff in <a href="https://github.com/sqlalchemy/mako/commits">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=mako&package-manager=uv&previous-version=1.3.11&new-version=1.3.12)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
- `@dependabot show <dependency name> ignore conditions` will show all of the ignore conditions of the specified dependency
- `@dependabot ignore this major version` will close this PR and stop Dependabot creating any more for this major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this minor version` will close this PR and stop Dependabot creating any more for this minor version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)
You can disable automated security fix PRs for this repo from the [Security Alerts page](https://github.com/lisphilar/covid19-sir/network/alerts).

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5601615a0399`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
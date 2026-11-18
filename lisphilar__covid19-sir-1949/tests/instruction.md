# Issue

**Title:** build(deps): bump mako from 1.3.12 to 1.4.2

## Description

Bumps [mako](https://github.com/sqlalchemy/mako) from 1.3.12 to 1.4.2.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/sqlalchemy/mako/releases">mako's releases</a>.</em></p>
<blockquote>
<h1>1.4.2</h1>
<p>Released: Tue Sep 22 2026</p>
<h2>bug</h2>
<ul>
<li>
<p><strong>[bug] [tests]</strong> Adjusted the test suite to accommodate for a change in Pygments 2.21.0
where the <code>HtmlFormatter</code> now renders <code>&quot;</code> and <code>'</code> characters
literally rather than as HTML entities, which caused failures in tests
that assert against the rendered output of
<code>html_error_template()</code>.</p>
<p>References: <a href="">#440</a></p>
</li>
<li>
<p><strong>[bug] [template]</strong> Fixed issue in <code>TemplateLookup</code> where a URI beginning with a drive
designator (e.g. <code>C:/../../secret.txt</code>) could bypass the directory
traversal check on Windows, allowing reads of arbitrary files outside of
the template directory.  The check in <code>Template</code> normalized the URI
using <code>os.path</code>, which on Windows is <code>ntpath</code>; as <code>ntpath</code> splits the
drive designator off and treats the remainder as rooted, the <code>..</code>
segments were absorbed before the check could inspect them.  Normalization
is now performed with <code>posixpath</code>, which is the same module used by
<code>TemplateLookup.get_template()</code> to resolve the URI to a file.</p>
<p>References: <a href="">#441</a></p>
</li>
</ul>
<h1>1.4.1</h1>
<p>Released: Wed Aug 5 2026</p>
<h2>bug</h2>
<ul>
<li>
<p><strong>[bug] [installation]</strong> Fixed issue in the 1.4.0 packaging where the repository's internal
<code>tools/</code> directory was detected by setuptools package discovery and
installed as a top-level <code>tools</code> package into site-packages, shadowing
unrelated <code>tools</code> packages belonging to other applications.  Package
discovery is now limited to the <code>mako</code> package explicitly.</p>
<p>References: <a href="">#438</a></p>
</li>
</ul>
<h1>1.4.0</h1>
<p>Released: Tue Aug 4 2026</p>
<h2>changed</h2>
<ul>
<li><strong>[changed] [examples]</strong> The <code>examples/bench</code> folder has been removed as it used mostly</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li>See full diff in <a href="https://github.com/sqlalchemy/mako/commits">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=mako&package-manager=uv&previous-version=1.3.12&new-version=1.4.2)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b54e40018ebe`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
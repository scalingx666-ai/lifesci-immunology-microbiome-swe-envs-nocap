# Issue

**Title:** build(deps): bump bleach from 6.3.0 to 6.4.0

## Description

Bumps [bleach](https://github.com/mozilla/bleach) from 6.3.0 to 6.4.0.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/mozilla/bleach/blob/main/CHANGES">bleach's changelog</a>.</em></p>
<blockquote>
<h2>Version 6.4.0 (June 5th, 2026)</h2>
<p><strong>NOTE: 2026-06-05: Bleach is no longer maintained. There will be no future
releases including for security issues.</strong>
See issue: <code>&lt;</code>__</p>
<p><strong>Backwards incompatible changes</strong></p>
<ul>
<li>Dropped support for pypy 3.10. (<a href="">#764</a>)</li>
</ul>
<p><strong>Security fixes</strong></p>
<ul>
<li>
<p>Fix bug 2023812 / GHSA-8rfp-98v4-mmr6.</p>
<p>Fix XSS issue with sanitize_uri_value where disallowed schemes with
Unicode invisible characters wouldn't be rejected.</p>
<p>For example::</p>
<p>import bleach
payload1 = '<!-- raw HTML omitted -->Click<!-- raw HTML omitted -->'
result1 = bleach.clean(payload1)
print(repr(result1))</p>
<p>outputs::</p>
<p>'<!-- raw HTML omitted -->Click<!-- raw HTML omitted -->'</p>
<p>See the advisory for details.</p>
</li>
<li>
<p>Fix GHSA-gj48-438w-jh9v.</p>
<p>Fix issue where URI sanitization wasn't happening in formaction attributes.</p>
<p>See the advisory for details.</p>
</li>
</ul>
<p><strong>Bug fixes</strong></p>
<ul>
<li>
<p>Add support for pypy 3.11. (<a href="">#764</a>)</p>
</li>
<li>
<p>Drop version max in tinycss2 pin. (<a href="">#772</a>)</p>
<p>This removes one of the things we had to keep checking and updating. Users
now own the responsibility for correctness with the version of tinycss2
they're using.</p>
</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>f0355a7</code></a> fix: fix last release date in CHANGES</li>
<li><a href=""><code>ae4e8a2</code></a> chore: bleach 6.4.0 and final release</li>
<li><a href=""><code>970df58</code></a> fix: uri-sanitization in formaction attributes</li>
<li><a href=""><code>7c4867c</code></a> fix: xss bypass in allowed protocol test using unicode invisible characters</li>
<li><a href=""><code>913ab75</code></a> fix: reduce redundancy in workflow jobs</li>
<li><a href=""><code>218c15a</code></a> fix: rework pip caching</li>
<li><a href=""><code>4f0b097</code></a> fix: fix tox platform restrictions</li>
<li><a href=""><code>e95a79d</code></a> chore: update pytest</li>
<li><a href=""><code>91539d4</code></a> Bump actions/cache from 5.0.3 to 5.0.4</li>
<li><a href=""><code>cd47b4c</code></a> fix: handle left-angle-bracket that's not a tag (<a href="">#733</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/mozilla/bleach/compare/v6.3.0...v6.4.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=bleach&package-manager=uv&previous-version=6.3.0&new-version=6.4.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `47c0b4c76ff5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
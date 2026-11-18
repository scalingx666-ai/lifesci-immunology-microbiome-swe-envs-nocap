# Issue

**Title:** build(deps): bump typing-extensions from 4.14.0 to 4.14.1

## Description

Bumps [typing-extensions](https://github.com/python/typing_extensions) from 4.14.0 to 4.14.1.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/python/typing_extensions/releases">typing-extensions's releases</a>.</em></p>
<blockquote>
<h2>4.14.1</h2>
<h1>Release 4.14.1 (July 4, 2025)</h1>
<ul>
<li>Fix usage of <code>typing_extensions.TypedDict</code> nested inside other types
(e.g., <code>typing.Type[typing_extensions.TypedDict]</code>). This is not allowed by the
type system but worked on older versions, so we maintain support.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/python/typing_extensions/blob/main/CHANGELOG.md">typing-extensions's changelog</a>.</em></p>
<blockquote>
<h1>Release 4.14.1 (July 4, 2025)</h1>
<ul>
<li>Fix usage of <code>typing_extensions.TypedDict</code> nested inside other types
(e.g., <code>typing.Type[typing_extensions.TypedDict]</code>). This is not allowed by the
type system but worked on older versions, so we maintain support.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>42027ab</code></a> Prepare release 4.14.1 (<a href="">#620</a>)</li>
<li><a href=""><code>59d2c20</code></a> Fix off by one in pickle protocol tests (<a href="">#618</a>)</li>
<li><a href=""><code>40e22eb</code></a> Do not use slots for <code>_TypedDictSpecialForm</code> (<a href="">#616</a>)</li>
<li><a href=""><code>d17c456</code></a> allow TypedDict as a type argument (<a href="">#614</a>)</li>
<li>See full diff in <a href="https://github.com/python/typing_extensions/compare/4.14.0...4.14.1">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=typing-extensions&package-manager=pip&previous-version=4.14.0&new-version=4.14.1)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
- `@dependabot show <dependency name> ignore conditions` will show all of the ignore conditions of the specified dependency
- `@dependabot ignore this major version` will close this PR and stop Dependabot creating any more for this major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this minor version` will close this PR and stop Dependabot creating any more for this minor version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)

</details>

## Summary by Sourcery

Bump typing-extensions dependency from 4.14.0 to 4.14.1 to incorporate the latest fixes

Enhancements:
- Include fix for nested TypedDict usage within other types

Build:
- Update typing-extensions version to 4.14.1

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5a656f0d8384`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
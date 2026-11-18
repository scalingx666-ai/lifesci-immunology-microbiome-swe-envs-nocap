# Issue

**Title:** build(deps-dev): bump pytest from 8.4.0 to 8.4.1

## Description

Bumps [pytest](https://github.com/pytest-dev/pytest) from 8.4.0 to 8.4.1.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/pytest-dev/pytest/releases">pytest's releases</a>.</em></p>
<blockquote>
<h2>8.4.1</h2>
<h1>pytest 8.4.1 (2025-06-17)</h1>
<h2>Bug fixes</h2>
<ul>
<li>
<p><a href="">#13461</a>: Corrected <code>_pytest.terminal.TerminalReporter.isatty</code> to support
being called as a method. Before it was just a boolean which could
break correct code when using <code>-o log_cli=true</code>).</p>
</li>
<li>
<p><a href="">#13477</a>: Reintroduced <code>pytest.PytestReturnNotNoneWarning</code>{.interpreted-text role=&quot;class&quot;} which was removed by accident in pytest [8.4]{.title-ref}.</p>
<p>This warning is raised when a test functions returns a value other than <code>None</code>, which is often a mistake made by beginners.</p>
<p>See <code>return-not-none</code>{.interpreted-text role=&quot;ref&quot;} for more information.</p>
</li>
<li>
<p><a href="">#13497</a>: Fixed compatibility with <code>Twisted 25+</code>.</p>
</li>
</ul>
<h2>Improved documentation</h2>
<ul>
<li><a href="">#13492</a>: Fixed outdated warning about <code>faulthandler</code> not working on Windows.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>8d99211</code></a> Prepare release version 8.4.1</li>
<li><a href=""><code>5dc5880</code></a> docs: update pytest.ini addopts example to use separate -p entries (<a href="">#13529</a>) (...</li>
<li><a href=""><code>d0c7ed0</code></a> Reintroduce PytestReturnNotNoneWarning (<a href="">#13495</a>) (<a href="">#13527</a>)</li>
<li><a href=""><code>a1b3a78</code></a> Fix compatibility with Twisted 25 (<a href="">#13502</a>) (<a href="">#13531</a>)</li>
<li><a href=""><code>4c161ab</code></a> pytester: avoid unraisableexception gc collects in inline runs to speed up te...</li>
<li><a href=""><code>a86ee09</code></a> Fix typo in parametrize.rst (<a href="">#13514</a>) (<a href="">#13516</a>)</li>
<li><a href=""><code>1a0581b</code></a> Remove outdated warning about faulthandler_timeout on Windows (<a href="">#13492</a>) (<a href="">#13493</a>)</li>
<li><a href=""><code>4e631a7</code></a> Merge pull request <a href="">#13486</a> from hosmir/fixtypo (<a href="">#13487</a>)</li>
<li><a href=""><code>b49745e</code></a> fix: support TerminalReporter.isatty being called (<a href="">#13462</a>) (<a href="">#13483</a>)</li>
<li><a href=""><code>cc5ceed</code></a> RELEASING: remove pytest mailing list (<a href="">#13472</a>) (<a href="">#13473</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/pytest-dev/pytest/compare/8.4.0...8.4.1">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=pytest&package-manager=pip&previous-version=8.4.0&new-version=8.4.1)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Build:
- Upgrade pytest to version 8.4.1

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e61cb3e8f3bf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
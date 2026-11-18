# Issue

**Title:** build(deps-dev): bump pytest from 8.3.3 to 8.3.4

## Description

[//]: # (dependabot-start)
⚠️  **Dependabot is rebasing this PR** ⚠️

Rebasing might not happen immediately, so don't worry if this takes some time.

Note: if you make any changes to this PR yourself, they will take precedence over the rebase.

---

[//]: # (dependabot-end)

Bumps [pytest](https://github.com/pytest-dev/pytest) from 8.3.3 to 8.3.4.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/pytest-dev/pytest/releases">pytest's releases</a>.</em></p>
<blockquote>
<h2>8.3.4</h2>
<h1>pytest 8.3.4 (2024-12-01)</h1>
<h2>Bug fixes</h2>
<ul>
<li>
<p><a href="">#12592</a>: Fixed <code>KeyError</code>{.interpreted-text role=&quot;class&quot;} crash when using <code>--import-mode=importlib</code> in a directory layout where a directory contains a child directory with the same name.</p>
</li>
<li>
<p><a href="">#12818</a>: Assertion rewriting now preserves the source ranges of the original instructions, making it play well with tools that deal with the <code>AST</code>, like <a href="https://github.com/alexmojaki/executing">executing</a>.</p>
</li>
<li>
<p><a href="">#12849</a>: ANSI escape codes for colored output now handled correctly in <code>pytest.fail</code>{.interpreted-text role=&quot;func&quot;} with [pytrace=False]{.title-ref}.</p>
</li>
<li>
<p><a href="">#9353</a>: <code>pytest.approx</code>{.interpreted-text role=&quot;func&quot;} now uses strict equality when given booleans.</p>
</li>
</ul>
<h2>Improved documentation</h2>
<ul>
<li>
<p><a href="">#10558</a>: Fix ambiguous docstring of <code>pytest.Config.getoption</code>{.interpreted-text role=&quot;func&quot;}.</p>
</li>
<li>
<p><a href="">#10829</a>: Improve documentation on the current handling of the <code>--basetemp</code> option and its lack of retention functionality (<code>temporary directory location and retention</code>{.interpreted-text role=&quot;ref&quot;}).</p>
</li>
<li>
<p><a href="">#12866</a>: Improved cross-references concerning the <code>recwarn</code>{.interpreted-text role=&quot;fixture&quot;} fixture.</p>
</li>
<li>
<p><a href="">#12966</a>: Clarify <code>filterwarnings</code>{.interpreted-text role=&quot;ref&quot;} docs on filter precedence/order when using multiple <code>@pytest.mark.filterwarnings &lt;pytest.mark.filterwarnings ref&gt;</code>{.interpreted-text role=&quot;ref&quot;} marks.</p>
</li>
</ul>
<h2>Contributor-facing changes</h2>
<ul>
<li><a href="">#12497</a>: Fixed two failing pdb-related tests on Python 3.13.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>53f8b4e</code></a> Update pypa/gh-action-pypi-publish to v1.12.2</li>
<li><a href=""><code>98dff36</code></a> Prepare release version 8.3.4</li>
<li><a href=""><code>1b474e2</code></a> approx: use exact comparison for bool (<a href="">#13013</a>)</li>
<li><a href=""><code>b541721</code></a> docs: Fix wrong statement about sys.modules with importlib import mode (<a href="">#1298</a>...</li>
<li><a href=""><code>16cb87b</code></a> pytest.fail: fix ANSI escape codes for colored output (<a href="">#12959</a>) (<a href="">#12990</a>)</li>
<li><a href=""><code>be6bc81</code></a> Issue <a href="">#12966</a> Clarify filterwarnings docs on precedence when using multiple ma...</li>
<li><a href=""><code>7aeb72b</code></a> Improve docs on basetemp and retention (<a href="">#12912</a>) (<a href="">#12928</a>)</li>
<li><a href=""><code>c875841</code></a> Merge pull request <a href="">#12917</a> from pytest-dev/patchback/backports/8.3.x/ded1f44e5...</li>
<li><a href=""><code>6502816</code></a> Merge pull request <a href="">#12913</a> from jakkdl/dontfailonbadpath</li>
<li><a href=""><code>52135b0</code></a> Merge pull request <a href="">#12885</a> from The-Compiler/pdb-py311 (<a href="">#12887</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/pytest-dev/pytest/compare/8.3.3...8.3.4">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=pytest&package-manager=pip&previous-version=8.3.3&new-version=8.3.4)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
- Bump pytest from version 8.3.3 to 8.3.4 in the development dependencies.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9fcc6ea391a6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
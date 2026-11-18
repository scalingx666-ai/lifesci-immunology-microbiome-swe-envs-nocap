# Issue

**Title:** build(deps-dev): bump pytest from 8.4.1 to 8.4.2

## Description

[//]: # (dependabot-start)
⚠️  **Dependabot is rebasing this PR** ⚠️

Rebasing might not happen immediately, so don't worry if this takes some time.

Note: if you make any changes to this PR yourself, they will take precedence over the rebase.

---

[//]: # (dependabot-end)

Bumps [pytest](https://github.com/pytest-dev/pytest) from 8.4.1 to 8.4.2.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/pytest-dev/pytest/releases">pytest's releases</a>.</em></p>
<blockquote>
<h2>8.4.2</h2>
<h1>pytest 8.4.2 (2025-09-03)</h1>
<h2>Bug fixes</h2>
<ul>
<li>
<p><a href="">#13478</a>: Fixed a crash when using <code>console_output_style</code>{.interpreted-text role=&quot;confval&quot;} with <code>times</code> and a module is skipped.</p>
</li>
<li>
<p><a href="">#13530</a>: Fixed a crash when using <code>pytest.approx</code>{.interpreted-text role=&quot;func&quot;} and <code>decimal.Decimal</code>{.interpreted-text role=&quot;class&quot;} instances with the <code>decimal.FloatOperation</code>{.interpreted-text role=&quot;class&quot;} trap set.</p>
</li>
<li>
<p><a href="">#13549</a>: No longer evaluate type annotations in Python <code>3.14</code> when inspecting function signatures.</p>
<p>This prevents crashes during module collection when modules do not explicitly use <code>from __future__ import annotations</code> and import types for annotations within a <code>if TYPE_CHECKING:</code> block.</p>
</li>
<li>
<p><a href="">#13559</a>: Added missing [int]{.title-ref} and [float]{.title-ref} variants to the [Literal]{.title-ref} type annotation of the [type]{.title-ref} parameter in <code>pytest.Parser.addini</code>{.interpreted-text role=&quot;meth&quot;}.</p>
</li>
<li>
<p><a href="">#13563</a>: <code>pytest.approx</code>{.interpreted-text role=&quot;func&quot;} now only imports <code>numpy</code> if NumPy is already in <code>sys.modules</code>. This fixes unconditional import behavior introduced in [8.4.0]{.title-ref}.</p>
</li>
</ul>
<h2>Improved documentation</h2>
<ul>
<li><a href="">#13577</a>: Clarify that <code>pytest_generate_tests</code> is discovered in test modules/classes; other hooks must be in <code>conftest.py</code> or plugins.</li>
</ul>
<h2>Contributor-facing changes</h2>
<ul>
<li><a href="">#13480</a>: Self-testing: fixed a few test failures when run with <code>-Wdefault</code> or a similar override.</li>
<li><a href="">#13547</a>: Self-testing: corrected expected message for <code>test_doctest_unexpected_exception</code> in Python <code>3.14</code>.</li>
<li><a href="">#13684</a>: Make pytest's own testsuite insensitive to the presence of the <code>CI</code> environment variable -- by <code>ogrisel</code>{.interpreted-text role=&quot;user&quot;}.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>bfae422</code></a> Prepare release version 8.4.2</li>
<li><a href=""><code>8990538</code></a> Fix passenv CI in tox ini and make tests insensitive to the presence of the C...</li>
<li><a href=""><code>ca676bf</code></a> Merge pull request <a href="">#13687</a> from pytest-dev/patchback/backports/8.4.x/e63f6e51c...</li>
<li><a href=""><code>975a60a</code></a> Merge pull request <a href="">#13686</a> from pytest-dev/patchback/backports/8.4.x/12bde8af6...</li>
<li><a href=""><code>7723ce8</code></a> Merge pull request <a href="">#13683</a> from even-even/fix_Exeption_to_Exception_in_errorMe...</li>
<li><a href=""><code>b7f0568</code></a> Merge pull request <a href="">#13685</a> from CoretexShadow/fix/docs-pytest-generate-tests</li>
<li><a href=""><code>2c94c4a</code></a> add missing colon (<a href="">#13640</a>) (<a href="">#13641</a>)</li>
<li><a href=""><code>c3d7684</code></a> Merge pull request <a href="">#13606</a> from pytest-dev/patchback/backports/8.4.x/5f9938563...</li>
<li><a href=""><code>dc6e3be</code></a> Merge pull request <a href="">#13605</a> from The-Compiler/training-update-2025-07</li>
<li><a href=""><code>f87289c</code></a> Fix crash with <code>times</code> output style and skipped module (<a href="">#13573</a>) (<a href="">#13579</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/pytest-dev/pytest/compare/8.4.1...8.4.2">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=pytest&package-manager=pip&previous-version=8.4.1&new-version=8.4.2)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2f8b3d76c29a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** build(deps-dev): bump sympy from 1.13.2 to 1.13.3

## Description

Bumps [sympy](https://github.com/sympy/sympy) from 1.13.2 to 1.13.3.
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>b4ce69a</code></a> Merge pull request <a href="">#27081</a> from oscarbenjamin/pr_113_backport_fixes</li>
<li><a href=""><code>575dbfa</code></a> author: update AUTHORS file</li>
<li><a href=""><code>408b571</code></a> author: add Matt Wang to .mailmap</li>
<li><a href=""><code>77fffbf</code></a> remove unnecessary parentheses in func role from docstring</li>
<li><a href=""><code>2101e6d</code></a> remove unnecessary parentheses in func role from <code>doc</code></li>
<li><a href=""><code>09f4810</code></a> maint(ci): don't use ruff to check files outside sympy</li>
<li><a href=""><code>31623f0</code></a> release: bump version to 1.13.3</li>
<li><a href=""><code>766458c</code></a> fix(quantum): sympify inputs to clebsch_gordan</li>
<li><a href=""><code>e34f10e</code></a> test(stats): fix Markov tests for empty matrices</li>
<li><a href=""><code>6db23e6</code></a> fix(matrices): Matrix([[], []]) -&gt; Matrix(2, 0, [])</li>
<li>See full diff in <a href="https://github.com/sympy/sympy/compare/sympy-1.13.2...sympy-1.13.3">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=sympy&package-manager=pip&previous-version=1.13.2&new-version=1.13.3)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `09e0418d5c19`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
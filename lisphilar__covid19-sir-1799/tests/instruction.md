# Issue

**Title:** build(deps): bump autots from 0.6.17 to 0.6.19

## Description

Bumps [autots](https://github.com/winedarksea/AutoTS) from 0.6.17 to 0.6.19.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/winedarksea/AutoTS/releases">autots's releases</a>.</em></p>
<blockquote>
<h1>0.6.19 🇺🇦 🇺🇦 🇺🇦</h1>
<ul>
<li>bug fix for transformer_list=&quot;all&quot;</li>
</ul>
<h1>0.6.18 🇺🇦 🇺🇦 🇺🇦</h1>
<ul>
<li>minor tweaks and bug fixes</li>
<li>updated python version required to 3.9 to allow more typing options</li>
<li>validation_indexes can now be a list of tuples with mixed forecast lengths</li>
<li>&quot;mixed_length&quot; validation option, for limited testing of longer forecast lengths</li>
<li>kalman method for ensemble aggregation (ala sensor fusion)</li>
<li>UpscaleDownscaleTransformer added</li>
<li>PreprocessingExperts model added (experimental)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>1da01ee</code></a> Merge pull request <a href="">#254</a> from winedarksea/dev</li>
<li><a href=""><code>b4307dc</code></a> 0.6.19</li>
<li><a href=""><code>c6540e4</code></a> 0.6.19 a4</li>
<li><a href=""><code>1704d22</code></a> 0.6.19 a3</li>
<li><a href=""><code>5e8c2f2</code></a> 0.6.19 a2</li>
<li><a href=""><code>28a864e</code></a> 0.6.19 a1</li>
<li><a href=""><code>787d3e7</code></a> Merge pull request <a href="">#253</a> from winedarksea/dev</li>
<li><a href=""><code>64fc360</code></a> 0.6.18</li>
<li><a href=""><code>a75cd0f</code></a> 0.6.18 a38</li>
<li><a href=""><code>4c65b90</code></a> 0.6.18 a37</li>
<li>Additional commits viewable in <a href="https://github.com/winedarksea/AutoTS/compare/0.6.17...0.6.19">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=autots&package-manager=pip&previous-version=0.6.17&new-version=0.6.19)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Update AutoTS from 0.6.17 to 0.6.19.

New Features:
- Add "mixed_length" validation option.
- Add kalman method for ensemble aggregation.
- Add UpscaleDownscaleTransformer.
- Add PreprocessingExperts model (experimental).

Enhancements:
- Upgrade minimum Python version to 3.9.

Build:
- Bump autots dependency to 0.6.19.

Tests:
- Fix bug in transformer_list="all".
- Implement minor tweaks and bug fixes.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1c9cbdbeeec9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
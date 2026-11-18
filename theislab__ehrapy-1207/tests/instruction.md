# Issue

**Title:** Bump release-drafter/release-drafter from 7.7.0 to 7.9.0 in the actions-deps group

## Description

Bumps the actions-deps group with 1 update: [release-drafter/release-drafter](https://github.com/release-drafter/release-drafter).

Updates `release-drafter/release-drafter` from 7.7.0 to 7.9.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/release-drafter/release-drafter/releases">release-drafter/release-drafter's releases</a>.</em></p>
<blockquote>
<h2>v7.9.0</h2>
<h1>What's Changed</h1>
<h2>New</h2>
<ul>
<li>feat(autolabeler): sync configured pull request labels (<a href="">#1787</a>) <a href="https://github.com/jetersen"><code>@​jetersen</code></a></li>
<li>feat(autolabeler): support multiple labels, stop rules and fallback (<a href="">#1785</a>) <a href="https://github.com/jetersen"><code>@​jetersen</code></a></li>
<li>feat: expose PR labels in Drafter and Check PR outputs (<a href="">#1782</a>) <a href="https://github.com/jetersen"><code>@​jetersen</code></a></li>
<li>feat: add resolved tag template variable (<a href="">#1784</a>) <a href="https://github.com/jetersen"><code>@​jetersen</code></a></li>
</ul>
<h2>Dependency Updates</h2>
<ul>
<li>ci(deps): update reviewdog/action-actionlint action to v1.77.0 (<a href="">#1781</a>) <a href="https://github.com/apps/renovate"><code>@​renovate[bot]</code></a></li>
</ul>
<h2>Bug Fixes</h2>
<ul>
<li>fix(config): provide standard loading for the programmatic API (<a href="">#1783</a>) <a href="https://github.com/jetersen"><code>@​jetersen</code></a></li>
<li>fix: skip the missing-baseline warning when <code>from</code> is set (<a href="">#1789</a>) <a href="https://github.com/jmeridth"><code>@​jmeridth</code></a></li>
</ul>
<h2>Maintenance</h2>
<ul>
<li>ci: dogfood Release Drafter and stage npm publishing (<a href="">#1778</a>) <a href="https://github.com/jetersen"><code>@​jetersen</code></a></li>
<li>ci: lint GitHub Actions workflows with actionlint (<a href="">#1780</a>) <a href="https://github.com/jetersen"><code>@​jetersen</code></a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li>No new contributors</li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/release-drafter/release-drafter/compare/v7.8.0...v7.9.0">https://github.com/release-drafter/release-drafter/compare/v7.8.0...v7.9.0</a></p>
<h2>v7.8.0</h2>
<h1>What's Changed</h1>
<h2>Token authentication change</h2>
<p>The <code>token</code> action input now takes precedence over <code>env.GITHUB_TOKEN</code> and defaults to <code>${{ github.token }}</code>. Pass a PAT or GitHub App token through <code>with.token</code>, especially when publishing releases that should trigger downstream workflows:</p>
<pre lang="yaml"><code>with:
  token: ${{ secrets.PAT }}
  publish: true
</code></pre>
<h2>New</h2>
<ul>
<li>feat: merge repeated changes with group-changes (<a href="">#1725</a>) <a href="https://github.com/slawekjaranowski"><code>@​slawekjaranowski</code></a>, <a href="https://github.com/claude"><code>@​claude</code></a></li>
<li>feat(facade): wire multiforge adapters (<a href="">#1709</a>) <a href="https://github.com/jetersen"><code>@​jetersen</code></a></li>
<li>feat(adapters): add GitLab REST adapter (<a href="">#1708</a>) <a href="https://github.com/jetersen"><code>@​jetersen</code></a></li>
<li>feat(adapters): add Gitea and Forgejo REST adapters (<a href="">#1707</a>) <a href="https://github.com/jetersen"><code>@​jetersen</code></a></li>
<li>feat: add config-driven check-pr validation (<a href="">#1706</a>) <a href="https://github.com/jetersen"><code>@​jetersen</code></a></li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>72967cd</code></a> chore: release v7.9.0 (<a href="">#1790</a>)</li>
<li><a href=""><code>43cd2a9</code></a> feat(autolabeler): sync configured pull request labels (<a href="">#1787</a>)</li>
<li><a href=""><code>a99850f</code></a> feat(autolabeler): support multiple labels, stop rules and fallback (<a href="">#1785</a>)</li>
<li><a href=""><code>26b7080</code></a> feat: expose PR labels in Drafter and Check PR outputs (<a href="">#1782</a>)</li>
<li><a href=""><code>58b89af</code></a> feat: add resolved tag template variable (<a href="">#1784</a>)</li>
<li><a href=""><code>7aa25ba</code></a> fix(config): provide standard loading for the programmatic API (<a href="">#1783</a>)</li>
<li><a href=""><code>1e80012</code></a> fix: skip the missing-baseline warning when <code>from</code> is set (<a href="">#1789</a>)</li>
<li><a href=""><code>57f4179</code></a> ci: dogfood Release Drafter and stage npm publishing (<a href="">#1778</a>)</li>
<li><a href=""><code>75620c0</code></a> ci(deps): update reviewdog/action-actionlint action to v1.77.0 (<a href="">#1781</a>)</li>
<li><a href=""><code>fb48a58</code></a> ci: lint GitHub Actions workflows with actionlint (<a href="">#1780</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/release-drafter/release-drafter/compare/34d80673e067bdc0c24568d3af899c216adcfaa9...72967cdc98ddd3160f1fc3dff619de365e137dd0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=release-drafter/release-drafter&package-manager=github_actions&previous-version=7.7.0&new-version=7.9.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
- `@dependabot ignore <dependency name> major version` will close this group update PR and stop Dependabot creating any more for the specific dependency's major version (unless you unignore this specific dependency's major version or upgrade to it yourself)
- `@dependabot ignore <dependency name> minor version` will close this group update PR and stop Dependabot creating any more for the specific dependency's minor version (unless you unignore this specific dependency's minor version or upgrade to it yourself)
- `@dependabot ignore <dependency name>` will close this group update PR and stop Dependabot creating any more for the specific dependency (unless you unignore this specific dependency or upgrade to it yourself)
- `@dependabot unignore <dependency name>` will remove all of the ignore conditions of the specified dependency
- `@dependabot unignore <dependency name> <ignore condition>` will remove the ignore condition of the specified dependency and ignore conditions

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `28c875fb8886`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
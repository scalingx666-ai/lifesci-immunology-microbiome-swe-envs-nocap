# Issue

**Title:** Build(ci): Bump prefix-dev/setup-pixi from 0.11.0 to 0.11.2

## Description

Bumps [prefix-dev/setup-pixi](https://github.com/prefix-dev/setup-pixi) from 0.11.0 to 0.11.2.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/prefix-dev/setup-pixi/releases">prefix-dev/setup-pixi's releases</a>.</em></p>
<blockquote>
<h2>v0.11.2</h2>
<!-- raw HTML omitted -->
<h2>What's Changed</h2>
<h3>🤷🏻 Other changes</h3>
<ul>
<li>docs: Adjust workload-identity-audience section by <a href="https://github.com/pavelzw"><code>@​pavelzw</code></a> in <a href="">prefix-dev/setup-pixi#293</a></li>
<li>fix: Don't delete preinstalled pixi bin in cleanup by <a href="https://github.com/pavelzw"><code>@​pavelzw</code></a> in <a href="">prefix-dev/setup-pixi#297</a></li>
<li>fix(deps): bump undici, brace-expansion and handlebars by <a href="https://github.com/wolfv"><code>@​wolfv</code></a> in <a href="">prefix-dev/setup-pixi#295</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/prefix-dev/setup-pixi/compare/v0.11.1...v0.11.2">https://github.com/prefix-dev/setup-pixi/compare/v0.11.1...v0.11.2</a></p>
<h2>v0.11.1</h2>
<!-- raw HTML omitted -->
<h2>What's Changed</h2>
<h3>🤷🏻 Other changes</h3>
<ul>
<li>feat: Add auth-workload-identity inputs for OIDC login by <a href="https://github.com/pavelzw"><code>@​pavelzw</code></a> in <a href="">prefix-dev/setup-pixi#292</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/prefix-dev/setup-pixi/compare/v0.11.0...v0.11.1">https://github.com/prefix-dev/setup-pixi/compare/v0.11.0...v0.11.1</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>ad1da64</code></a> fix(deps): bump undici, brace-expansion and handlebars (<a href="">#295</a>)</li>
<li><a href=""><code>05a7f7a</code></a> fix: Don't delete preinstalled pixi bin in cleanup (<a href="">#297</a>)</li>
<li><a href=""><code>f549d46</code></a> ci: use pixi exec instead of choco to install yq (<a href="">#294</a>)</li>
<li><a href=""><code>4578022</code></a> docs: Adjust workload-identity-audience section (<a href="">#293</a>)</li>
<li><a href=""><code>a2789fe</code></a> feat: Add auth-workload-identity inputs for OIDC login (<a href="">#292</a>)</li>
<li>See full diff in <a href="https://github.com/prefix-dev/setup-pixi/compare/v0.11.0...v0.11.2">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=prefix-dev/setup-pixi&package-manager=github_actions&previous-version=0.11.0&new-version=0.11.2)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f4cfdd7f088c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
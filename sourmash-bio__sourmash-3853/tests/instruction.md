# Issue

**Title:** Build(ci): Bump DeterminateSystems/nix-installer-action from 20 to 21

## Description

Bumps [DeterminateSystems/nix-installer-action](https://github.com/determinatesystems/nix-installer-action) from 20 to 21.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/determinatesystems/nix-installer-action/releases">DeterminateSystems/nix-installer-action's releases</a>.</em></p>
<blockquote>
<h2>v21</h2>
<h2>What's Changed</h2>
<ul>
<li>
<p>Update to determinate by default by <a href="https://github.com/grahamc"><code>@​grahamc</code></a> in <a href="">DeterminateSystems/nix-installer-action#208</a></p>
</li>
<li>
<p>If determinate is false, pass --prefer-upstream by <a href="https://github.com/grahamc"><code>@​grahamc</code></a> in <a href="">DeterminateSystems/nix-installer-action#202</a></p>
</li>
<li>
<p>Drop x86_64-darwin by <a href="https://github.com/grahamc"><code>@​grahamc</code></a> in <a href="">DeterminateSystems/nix-installer-action#207</a></p>
</li>
<li>
<p>Update <code>detsys-ts</code>: Merge pull request <a href="">#109</a> from DeterminateSystems/tsup-to-tsdown by <a href="https://github.com/detsys-pr-bot"><code>@​detsys-pr-bot</code></a> in <a href="">DeterminateSystems/nix-installer-action#203</a></p>
</li>
<li>
<p>Update <code>detsys-ts</code>: Merge pull request <a href="">#114</a> from DeterminateSystems/dependabot/npm_and_yarn/npm-deps-47c548f420 by <a href="https://github.com/detsys-pr-bot"><code>@​detsys-pr-bot</code></a> in <a href="">DeterminateSystems/nix-installer-action#206</a></p>
</li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/DeterminateSystems/nix-installer-action/compare/v20...v21">https://github.com/DeterminateSystems/nix-installer-action/compare/v20...v21</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>c5a866b</code></a> Update to determinate by default (<a href="">#208</a>)</li>
<li><a href=""><code>89b1f59</code></a> Drop x86_64-darwin (<a href="">#207</a>)</li>
<li><a href=""><code>86a5f59</code></a> Merge pull request <a href="">#206</a> from detsys-pr-bot/detsys-ts-update-cb28f5861548d8a85...</li>
<li><a href=""><code>64a1e1d</code></a> Update <code>detsys-ts</code> for: `Merge pull request <a href="">#114</a> from DeterminateSystems/depe...</li>
<li><a href=""><code>2fd3724</code></a> If determinate is false, pass --prefer-upstream (<a href="">#202</a>)</li>
<li><a href=""><code>45a18a6</code></a> Merge pull request <a href="">#203</a> from detsys-pr-bot/detsys-ts-update-285768c0d657f9709...</li>
<li><a href=""><code>d3ddf02</code></a> Update <code>detsys-ts</code> for: `Merge pull request <a href="">#109</a> from DeterminateSystems/tsup...</li>
<li>See full diff in <a href="https://github.com/determinatesystems/nix-installer-action/compare/v20...v21">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=DeterminateSystems/nix-installer-action&package-manager=github_actions&previous-version=20&new-version=21)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

You can trigger a rebase of this PR by commenting `@dependabot rebase`.

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

> **Note**
> Automatic rebases have been disabled on this pull request as it has been open for over 30 days.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f65130f5d54a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Build(ci): Bump DeterminateSystems/nix-installer-action from 19 to 20

## Description

Bumps [DeterminateSystems/nix-installer-action](https://github.com/determinatesystems/nix-installer-action) from 19 to 20.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/determinatesystems/nix-installer-action/releases">DeterminateSystems/nix-installer-action's releases</a>.</em></p>
<blockquote>
<h2>v20</h2>
<h2>What's Changed</h2>
<ul>
<li>Update <code>detsys-ts</code>: Merge pull request <a href="">#106</a> from DeterminateSystems/fix-dependabot-warning by <a href="https://github.com/detsys-pr-bot"><code>@​detsys-pr-bot</code></a> in <a href="">DeterminateSystems/nix-installer-action#194</a></li>
<li>Update <code>detsys-ts</code>: Capture the version of Nix in addition to the nix store version (<a href="">#108</a>) by <a href="https://github.com/detsys-pr-bot"><code>@​detsys-pr-bot</code></a> in <a href="">DeterminateSystems/nix-installer-action#197</a></li>
<li>Report the number of nix builds that passed / failed by <a href="https://github.com/grahamc"><code>@​grahamc</code></a> in <a href="">DeterminateSystems/nix-installer-action#196</a></li>
<li>Record events if authentication is skipped by <a href="https://github.com/gustavderdrache"><code>@​gustavderdrache</code></a> in <a href="">DeterminateSystems/nix-installer-action#198</a></li>
<li>Treat FlakeHub logins as a funnel by <a href="https://github.com/gustavderdrache"><code>@​gustavderdrache</code></a> in <a href="">DeterminateSystems/nix-installer-action#199</a></li>
<li>Apply fixups from CodeRabbit review by <a href="https://github.com/gustavderdrache"><code>@​gustavderdrache</code></a> in <a href="">DeterminateSystems/nix-installer-action#200</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/DeterminateSystems/nix-installer-action/compare/v19...v20">https://github.com/DeterminateSystems/nix-installer-action/compare/v19...v20</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>786fff0</code></a> Apply fixups from CodeRabbit review (<a href="">#200</a>)</li>
<li><a href=""><code>f161ab0</code></a> Treat FlakeHub logins as a funnel (<a href="">#199</a>)</li>
<li><a href=""><code>61ce789</code></a> Merge pull request <a href="">#198</a> from DeterminateSystems/gustavderdrache/push-mzwwpswk...</li>
<li><a href=""><code>44f3801</code></a> Improve messages for when auth isn't available</li>
<li><a href=""><code>cb6d4e8</code></a> Standardize login failure events</li>
<li><a href=""><code>e686131</code></a> Record events if authentication is skipped</li>
<li><a href=""><code>2c3a298</code></a> Report the number of nix builds that passed / failed (<a href="">#196</a>)</li>
<li><a href=""><code>18b667a</code></a> Update <code>detsys-ts</code> for: `Capture the version of Nix in addition to the nix st...</li>
<li><a href=""><code>428f3c6</code></a> Update <code>detsys-ts</code> for: `Merge pull request <a href="">#106</a> from DeterminateSystems/fix-...</li>
<li>See full diff in <a href="https://github.com/determinatesystems/nix-installer-action/compare/v19...v20">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=DeterminateSystems/nix-installer-action&package-manager=github_actions&previous-version=19&new-version=20)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `953139227426`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
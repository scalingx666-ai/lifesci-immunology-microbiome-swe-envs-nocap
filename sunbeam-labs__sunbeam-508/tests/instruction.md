# Issue

**Title:** Bump docker/build-push-action from 5 to 6 in /.github/workflows

## Description

Bumps [docker/build-push-action](https://github.com/docker/build-push-action) from 5 to 6.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/docker/build-push-action/releases">docker/build-push-action's releases</a>.</em></p>
<blockquote>
<h2>v6.0.0</h2>
<ul>
<li>Export build record and generate <a href="https://docs.docker.com/build/ci/github-actions/build-summary/">build summary</a> by <a href="https://github.com/crazy-max"><code>@​crazy-max</code></a> in <a href="">docker/build-push-action#1120</a></li>
<li>Bump <code>@​docker/actions-toolkit</code> from 0.24.0 to 0.26.0 in <a href="">docker/build-push-action#1132</a> <a href="">docker/build-push-action#1136</a> <a href="">docker/build-push-action#1138</a></li>
<li>Bump braces from 3.0.2 to 3.0.3 in <a href="">docker/build-push-action#1137</a></li>
</ul>
<blockquote>
<p>[!NOTE]
This major release adds support for generating <a href="https://docs.docker.com/build/ci/github-actions/build-summary/">Build summary</a> and exporting build record for your build. You can disable this feature by setting <a href="https://docs.docker.com/build/ci/github-actions/build-summary/#disable-job-summary"> <code>DOCKER_BUILD_SUMMARY: false</code> environment variable in your workflow</a>.</p>
</blockquote>
<p><strong>Full Changelog</strong>: <a href="https://github.com/docker/build-push-action/compare/v5.4.0...v6.0.0">https://github.com/docker/build-push-action/compare/v5.4.0...v6.0.0</a></p>
<h2>v5.4.0</h2>
<ul>
<li>Show builder information before building by <a href="https://github.com/crazy-max"><code>@​crazy-max</code></a> in <a href="">docker/build-push-action#1128</a></li>
<li>Handle attestations correctly with provenance and sbom inputs by <a href="https://github.com/crazy-max"><code>@​crazy-max</code></a> in <a href="">docker/build-push-action#1086</a></li>
<li>Bump <code>@​docker/actions-toolkit</code> from 0.19.0 to 0.24.0 in <a href="">docker/build-push-action#1088</a> <a href="">docker/build-push-action#1105</a> <a href="">docker/build-push-action#1121</a> <a href="">docker/build-push-action#1127</a></li>
<li>Bump undici from 5.28.3 to 5.28.4 in <a href="">docker/build-push-action#1090</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/docker/build-push-action/compare/v5.3.0...v5.4.0">https://github.com/docker/build-push-action/compare/v5.3.0...v5.4.0</a></p>
<h2>v5.3.0</h2>
<ul>
<li>Bump <code>@​docker/actions-toolkit</code> from 0.18.0 to 0.19.0 in <a href="">docker/build-push-action#1080</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/docker/build-push-action/compare/v5.2.0...v5.3.0">https://github.com/docker/build-push-action/compare/v5.2.0...v5.3.0</a></p>
<h2>v5.2.0</h2>
<ul>
<li>Disable quotes detection for <code>outputs</code> input by <a href="https://github.com/crazy-max"><code>@​crazy-max</code></a> in <a href="">docker/build-push-action#1074</a></li>
<li>Warn about ignored inputs by <a href="https://github.com/favonia"><code>@​favonia</code></a> in <a href="">docker/build-push-action#1019</a></li>
<li>Bump <code>@​docker/actions-toolkit</code> from 0.14.0 to 0.18.0 in <a href="">docker/build-push-action#1070</a></li>
<li>Bump undici from 5.26.3 to 5.28.3 in <a href="">docker/build-push-action#1057</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/docker/build-push-action/compare/v5.1.0...v5.2.0">https://github.com/docker/build-push-action/compare/v5.1.0...v5.2.0</a></p>
<h2>v5.1.0</h2>
<ul>
<li>Add <code>annotations</code> input by <a href="https://github.com/crazy-max"><code>@​crazy-max</code></a> in <a href="">docker/build-push-action#992</a></li>
<li>Add <code>secret-envs</code> input by <a href="https://github.com/elias-lundgren"><code>@​elias-lundgren</code></a> in <a href="">docker/build-push-action#980</a></li>
<li>Bump <code>@​babel/traverse</code> from 7.17.3 to 7.23.2 in <a href="">docker/build-push-action#991</a></li>
<li>Bump <code>@​docker/actions-toolkit</code> from 0.13.0-rc.1 to 0.14.0 in <a href="">docker/build-push-action#990</a> <a href="">docker/build-push-action#1006</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/docker/build-push-action/compare/v5.0.0...v5.1.0">https://github.com/docker/build-push-action/compare/v5.0.0...v5.1.0</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>14487ce</code></a> Merge pull request <a href="">#1343</a> from crazy-max/fix-no-default-attest</li>
<li><a href=""><code>0ec9126</code></a> Merge pull request <a href="">#1366</a> from crazy-max/pr-assign-author</li>
<li><a href=""><code>b749522</code></a> pr-assign-author workflow</li>
<li><a href=""><code>c566248</code></a> Merge pull request <a href="">#1363</a> from crazy-max/fix-codecov</li>
<li><a href=""><code>13275dd</code></a> ci: fix missing source for codecov</li>
<li><a href=""><code>67dc78b</code></a> Merge pull request <a href="">#1361</a> from mschoettle/patch-1</li>
<li><a href=""><code>0760504</code></a> docs: add validating build configuration example</li>
<li><a href=""><code>1c198f4</code></a> chore: update generated content</li>
<li><a href=""><code>288d9e2</code></a> handle no default attestations env var</li>
<li><a href=""><code>88844b9</code></a> Merge pull request <a href="">#1353</a> from crazy-max/summary-secret-keys</li>
<li>Additional commits viewable in <a href="https://github.com/docker/build-push-action/compare/v5...v6">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=docker/build-push-action&package-manager=github_actions&previous-version=5&new-version=6)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `59e2ab2f4f9b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
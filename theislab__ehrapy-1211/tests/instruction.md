# Issue

**Title:** Bump the actions-deps group across 1 directory with 3 updates

## Description

Bumps the actions-deps group with 3 updates in the / directory: [astral-sh/setup-uv](https://github.com/astral-sh/setup-uv), [pypa/gh-action-pypi-publish](https://github.com/pypa/gh-action-pypi-publish) and [release-drafter/release-drafter](https://github.com/release-drafter/release-drafter).

Updates `astral-sh/setup-uv` from 10.2.0 to 10.3.2
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/astral-sh/setup-uv/releases">astral-sh/setup-uv's releases</a>.</em></p>
<blockquote>
<h2>v10.3.2 🌈 update known checksums for 0.13.5</h2>
<h2>Changes</h2>
<h2>🧰 Maintenance</h2>
<ul>
<li>chore: update known checksums for 0.13.5 @<a href="https://github.com/apps/github-actions">github-actions[bot]</a> (<a href="">#1103</a>)</li>
</ul>
<h2>📚 Documentation</h2>
<ul>
<li>docs: update version references to v10.3.1 @<a href="https://github.com/apps/github-actions">github-actions[bot]</a> (<a href="">#1102</a>)</li>
</ul>
<h2>v10.3.1 🌈 preserve cache error class names in save-cache bundle</h2>
<h2>Changes</h2>
<p>This release includes a fix so that multiple concurrent workflows trying to upload the same cache no longer warn</p>
<p><code>##[warning]Failed to save: Unable to reserve cache with key ..., another job may be creating this cache.</code></p>
<h2>🐛 Bug fixes</h2>
<ul>
<li>fix: preserve cache error class names in save-cache bundle <a href="https://github.com/dannyward630"><code>@​dannyward630</code></a> (<a href="">#1093</a>)</li>
</ul>
<h2>🧰 Maintenance</h2>
<ul>
<li>chore: update known checksums for 0.13.4 @<a href="https://github.com/apps/github-actions">github-actions[bot]</a> (<a href="">#1099</a>)</li>
<li>chore: update known checksums for 0.13.2/0.13.3 @<a href="https://github.com/apps/github-actions">github-actions[bot]</a> (<a href="">#1098</a>)</li>
<li>chore: update known checksums for 0.13.1 @<a href="https://github.com/apps/github-actions">github-actions[bot]</a> (<a href="">#1094</a>)</li>
<li>Verify npm dependency signatures before builds <a href="https://github.com/zaniebot"><code>@​zaniebot</code></a> (<a href="">#1027</a>)</li>
</ul>
<h2>📚 Documentation</h2>
<ul>
<li>docs: cache-dependency-glob matches relative to the working directory <a href="https://github.com/flange-ipb"><code>@​flange-ipb</code></a> (<a href="">#1092</a>)</li>
<li>docs: update version references to v10.3.0 @<a href="https://github.com/apps/github-actions">github-actions[bot]</a> (<a href="">#1090</a>)</li>
</ul>
<h2>⬆️ Dependency updates</h2>
<ul>
<li>chore(deps): roll up Dependabot updates <a href="https://github.com/eifinger"><code>@​eifinger</code></a> (<a href="">#1101</a>)</li>
</ul>
<h2>v10.3.0 🌈 Add Python architecture selection</h2>
<h2>Changes</h2>
<p>This release adds the <code>python-arch</code> input to select a Python architecture independently of the Python version. With <code>uv</code> 0.13.0 or later, set <code>python-arch: x86_64</code> to use x64 Python on Windows ARM64 runners.</p>
<p>It also includes embedded checksums for <code>uv</code> releases through 0.13.0.</p>
<ul>
<li>Use macOS 15 runners for tests <a href="https://github.com/charliermarsh"><code>@​charliermarsh</code></a> (<a href="">#1081</a>)</li>
</ul>
<h2>🚀 Enhancements</h2>
<ul>
<li>Add <code>python-arch</code> support <a href="https://github.com/zanieb"><code>@​zanieb</code></a> (<a href="">#1079</a>)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>07a047e</code></a> chore: update known checksums for 0.13.5 (<a href="">#1103</a>)</li>
<li><a href=""><code>e1b8536</code></a> docs: update version references to v10.3.1 (<a href="">#1102</a>)</li>
<li><a href=""><code>18d369b</code></a> chore(deps): roll up Dependabot updates (<a href="">#1101</a>)</li>
<li><a href=""><code>4ad2329</code></a> chore: update known checksums for 0.13.4 (<a href="">#1099</a>)</li>
<li><a href=""><code>4bc6759</code></a> chore: update known checksums for 0.13.2/0.13.3 (<a href="">#1098</a>)</li>
<li><a href=""><code>c97f06e</code></a> fix: preserve cache error class names in save-cache bundle (<a href="">#1093</a>)</li>
<li><a href=""><code>8ca4be0</code></a> chore: update known checksums for 0.13.1 (<a href="">#1094</a>)</li>
<li><a href=""><code>b627d85</code></a> docs: cache-dependency-glob matches relative to the working directory (<a href="">#1092</a>)</li>
<li><a href=""><code>f8c8897</code></a> Verify npm dependency signatures before builds (<a href="">#1027</a>)</li>
<li><a href=""><code>f64d32b</code></a> docs: update version references to v10.3.0 (<a href="">#1090</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/astral-sh/setup-uv/compare/c18668ad3cf93ea998bef934396af7bb5c839dc7...07a047e608db84b3d8c06cd9a7c7dcc9c355c18e">compare view</a></li>
</ul>
</details>
<br />

Updates `pypa/gh-action-pypi-publish` from 1.14.2 to 1.14.3
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/pypa/gh-action-pypi-publish/releases">pypa/gh-action-pypi-publish's releases</a>.</em></p>
<blockquote>
<h2>v1.14.3</h2>
<!-- raw HTML omitted -->
<blockquote>
<p>[!important]
🚨 This release includes fixes for <a href="https://github.com/pypa/gh-action-pypi-publish/security/advisories/GHSA-5xjx-3w67-w9x9">GHSA-5xjx-3w67-w9x9</a> patched up by <a href="https://github.com/sethmlarson"><code>@​sethmlarson</code></a><a href="https://github.com/sponsors/sethmlarson">💰</a> in <a href="">#427</a> and in other places across the ecosystem.</p>
<p>Additional ecosystem and related mitigations beyond you might want to watch out for:</p>
<ul>
<li><a href="https://discuss.python.org/t/information-for-python-users-regarding-emudhra-emsign-ca-certificate-security-incident/109576">https://discuss.python.org/t/information-for-python-users-regarding-emudhra-emsign-ca-certificate-security-incident/109576</a></li>
<li><a href="https://emudhra.we-have-a-problem.com">https://emudhra.we-have-a-problem.com</a></li>
</ul>
</blockquote>
<h2>🛠️ Security Tightening</h2>
<p><a href="https://github.com/webknjaz"><code>@​webknjaz</code></a><a href="https://github.com/sponsors/webknjaz">💰</a> made sure the dependency tree within the action runtime uses hash-checking from now on via <a href="">pypa/gh-action-pypi-publish#420</a>.</p>
<p><strong>🪞 Full Diff</strong>: <a href="https://github.com/pypa/gh-action-pypi-publish/compare/v1.14.2...v1.14.3">https://github.com/pypa/gh-action-pypi-publish/compare/v1.14.2...v1.14.3</a></p>
<p><strong>🧔‍♂️ Release Manager:</strong> <a href="https://github.com/sponsors/webknjaz"><code>@​webknjaz</code></a> <a href="https://stand-with-ukraine.pp.ua">🇺🇦</a></p>
<p><strong>💬 Discuss</strong> <a href="https://bsky.app/profile/webknjaz.me/post/3mydcjweyak2f">on Bluesky 🦋</a>, <a href="https://mastodon.social/@webknjaz/117474743338290807">on Mastodon 🐘</a> and <a href="https://github.com/pypa/gh-action-pypi-publish/discussions/429">on GitHub</a>.</p>
<p><a href="https://github.com/sponsors/webknjaz"><img src="https://img.shields.io/badge/%40webknjaz-transparent?logo=githubsponsors&amp;logoColor=%23EA4AAA&amp;label=Sponsor&amp;color=2a313c" alt="GH Sponsors badge" /></a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>7245906</code></a> Merge pull request <a href="">#427</a> from sethmlarson/certifi-sigstore</li>
<li><a href=""><code>331eccb</code></a> Upgrade certifi and sigstore</li>
<li><a href=""><code>f68fee4</code></a> 💰 Sync the FUNDING config</li>
<li><a href=""><code>c0d6f8e</code></a> Merge branch 'integrity/runtime/deptree' into unstable/v1</li>
<li><a href=""><code>9090099</code></a> 🧪 Make smoke test deps hash-pinned in CI</li>
<li><a href=""><code>34e40c2</code></a> 📌 Bump pip-tools managed transitive deptrees</li>
<li><a href=""><code>e800ed5</code></a> 👷 Enable hash-checking in the runtime deptree 🔗</li>
<li><a href=""><code>dd8c5f4</code></a> 🔧 Make pip-tools config available in container</li>
<li>See full diff in <a href="https://github.com/pypa/gh-action-pypi-publish/compare/dc37677b2e1c63e2034f94d8a5b11f265b73ba33...7245906fb61fa33a13554f9d5fb856fe61758086">compare view</a></li>
</ul>
</details>
<br />

Updates `release-drafter/release-drafter` from 7.9.0 to 7.10.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/release-drafter/release-drafter/releases">release-drafter/release-drafter's releases</a>.</em></p>
<blockquote>
<h2>v7.10.0</h2>
<h1>What's Changed</h1>
<h2>New</h2>
<ul>
<li>feat(check-pr): validate base and proposed configuration (<a href="">#1809</a>) <a href="https://github.com/jetersen"><code>@​jetersen</code></a></li>
<li>feat(replacers): select PR body sections by heading (<a href="">#1808</a>) <a href="https://github.com/jetersen"><code>@​jetersen</code></a></li>
<li>feat: scope replacers to change titles (<a href="">#1805</a>) <a href="https://github.com/jetersen"><code>@​jetersen</code></a></li>
<li>feat: scope replacers to pull request bodies (<a href="">#1804</a>) <a href="https://github.com/jetersen"><code>@​jetersen</code></a></li>
<li>feat: add change-body-escapes (<a href="">#1797</a>) <a href="https://github.com/jetersen"><code>@​jetersen</code></a></li>
</ul>
<h2>Dependency Updates</h2>
<!-- raw HTML omitted -->
<ul>
<li>chore(deps): update dependency knip to 6.39.0 (<a href="">#1830</a>) <a href="https://github.com/apps/renovate"><code>@​renovate[bot]</code></a></li>
<li>chore(deps): update dependency <code>@​biomejs/biome</code> to 2.5.15 (<a href="">#1829</a>) <a href="https://github.com/apps/renovate"><code>@​renovate[bot]</code></a></li>
<li>chore(deps): update vitest to 5.0.3 (<a href="">#1827</a>) <a href="https://github.com/apps/renovate"><code>@​renovate[bot]</code></a></li>
<li>chore(deps): lock file maintenance (<a href="">#1826</a>) <a href="https://github.com/apps/renovate"><code>@​renovate[bot]</code></a></li>
<li>fix(deps): update dependency <code>@​octokit/plugin-paginate-rest</code> to 16.0.0 (<a href="">#1813</a>) <a href="https://github.com/apps/renovate"><code>@​renovate[bot]</code></a></li>
<li>chore(deps): update dependency <code>@​graphql-codegen/typescript-operations</code> to 6.1.9 (<a href="">#1818</a>) <a href="https://github.com/apps/renovate"><code>@​renovate[bot]</code></a></li>
<li>chore(deps): update dependency testcontainers to 12.2.0 (<a href="">#1812</a>) <a href="https://github.com/apps/renovate"><code>@​renovate[bot]</code></a></li>
<li>chore(deps): update graphql-codegen (<a href="">#1810</a>) <a href="https://github.com/apps/renovate"><code>@​renovate[bot]</code></a></li>
<li>fix(deps): update dependency undici to 6.29.0 (<a href="">#1796</a>) <a href="https://github.com/apps/renovate"><code>@​renovate[bot]</code></a></li>
<li>chore(deps): update dependency <code>@​types/node</code> to 24.19.0 (<a href="">#1798</a>) <a href="https://github.com/apps/renovate"><code>@​renovate[bot]</code></a></li>
<li>chore(deps): update vitest to 5.0.2 (<a href="">#1795</a>) <a href="https://github.com/apps/renovate"><code>@​renovate[bot]</code></a></li>
</ul>
<!-- raw HTML omitted -->
<h2>Maintenance</h2>
<ul>
<li>fix: authorize publication at the original release commit (<a href="">#1793</a>) <a href="https://github.com/jetersen"><code>@​jetersen</code></a></li>
<li>fix: handle missing release tags during discovery (<a href="">#1792</a>) <a href="https://github.com/jetersen"><code>@​jetersen</code></a></li>
<li>fix: publish merged release PRs from main pushes (<a href="">#1791</a>) <a href="https://github.com/jetersen"><code>@​jetersen</code></a></li>
<li>test: run GitLab conformance against GitLab CE 19.4.1 (<a href="">#1825</a>) <a href="https://github.com/jetersen"><code>@​jetersen</code></a></li>
<li>test: use the GitLab image that caches Mustermann's encoded characters (<a href="">#1824</a>) <a href="https://github.com/jetersen"><code>@​jetersen</code></a></li>
<li>ci: speed up forge conformance with a preseeded GitLab image (<a href="">#1819</a>) <a href="https://github.com/jetersen"><code>@​jetersen</code></a></li>
<li>ci: run workflows on Ubuntu 26.04 and cache node_modules (<a href="">#1823</a>) <a href="https://github.com/jetersen"><code>@​jetersen</code></a></li>
<li>test: expand coverage and reduce test runtime (<a href="">#1794</a>) <a href="https://github.com/jetersen"><code>@​jetersen</code></a></li>
<li>ci: report actionlint findings on its workflow job (<a href="">#1817</a>) <a href="https://github.com/jetersen"><code>@​jetersen</code></a></li>
<li>build: simplify tooling validation and coverage reporting (<a href="">#1816</a>) <a href="https://github.com/jetersen"><code>@​jetersen</code></a></li>
<li>build: simplify workspace dependency checks (<a href="">#1815</a>) <a href="https://github.com/jetersen"><code>@​jetersen</code></a></li>
<li>refactor: use runtime fetch in the public facade (<a href="">#1800</a>) <a href="https://github.com/jetersen"><code>@​jetersen</code></a></li>
<li>test: allow dependency version updates in package consumer contract (<a href="">#1799</a>) <a href="https://github.com/jetersen"><code>@​jetersen</code></a></li>
</ul>
<h2>Documentation</h2>
<ul>
<li>docs: simplify agent guidance and require the PR template (<a href="">#1807</a>) <a href="https://github.com/jetersen"><code>@​jetersen</code></a></li>
<li>docs: summarize deployment options and add npm branding (<a href="">#1802</a>) <a href="https://github.com/jetersen"><code>@​jetersen</code></a></li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>978bb0b</code></a> chore: release v7.10.0 (<a href="">#1828</a>)</li>
<li><a href=""><code>7875ba4</code></a> chore(deps): update dependency knip to 6.39.0 (<a href="">#1830</a>)</li>
<li><a href=""><code>cab3fb0</code></a> chore(deps): update dependency <code>@​biomejs/biome</code> to 2.5.15 (<a href="">#1829</a>)</li>
<li><a href=""><code>eea1614</code></a> chore(deps): update vitest to 5.0.3 (<a href="">#1827</a>)</li>
<li><a href=""><code>c91bcd7</code></a> chore(deps): lock file maintenance (<a href="">#1826</a>)</li>
<li><a href=""><code>9fece4e</code></a> test: run GitLab conformance against GitLab CE 19.4.1 (<a href="">#1825</a>)</li>
<li><a href=""><code>f8732bf</code></a> test: use the GitLab image that caches Mustermann's encoded characters (<a href="">#1824</a>)</li>
<li><a href=""><code>20ee3a7</code></a> feat(check-pr): validate base and proposed configuration (<a href="">#1809</a>)</li>
<li><a href=""><code>4248c85</code></a> fix(deps): update dependency <code>@​octokit/plugin-paginate-rest</code> to 16.0.0 (<a href="">#1813</a>)</li>
<li><a href=""><code>988dde1</code></a> feat(replacers): select PR body sections by heading (<a href="">#1808</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/release-drafter/release-drafter/compare/72967cdc98ddd3160f1fc3dff619de365e137dd0...978bb0b30c5ee8cdd332ced253758157150d43f0">compare view</a></li>
</ul>
</details>
<br />

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `de0271386b79`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
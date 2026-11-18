# Issue

**Title:** build(deps): bump ruptures from 1.1.9 to 1.1.10

## Description

Bumps [ruptures](https://github.com/deepcharles/ruptures) from 1.1.9 to 1.1.10.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/deepcharles/ruptures/releases">ruptures's releases</a>.</em></p>
<blockquote>
<h2>v1.1.10 🌈</h2>
<h2>Changes</h2>
<ul>
<li>CI add macos arm64 to cibw <a href="https://github.com/MatthewSZhang"><code>@​MatthewSZhang</code></a> (<a href="">#340</a>)</li>
</ul>
<h2>📚 Documentation</h2>
<ul>
<li>docs: correct Latex formatting <a href="https://github.com/deepcharles"><code>@​deepcharles</code></a> (<a href="">#348</a>)</li>
</ul>
<h2>🧰 Maintenance</h2>
<ul>
<li>ci(build-wheel): remove py314 from wheels (aarch64) <a href="https://github.com/deepcharles"><code>@​deepcharles</code></a> (<a href="">#358</a>)</li>
<li>ci(upload-pypi): bump versions of gha and manage supported python versions <a href="https://github.com/deepcharles"><code>@​deepcharles</code></a> (<a href="">#356</a>)</li>
<li>build: add python 3.13 wheels <a href="https://github.com/dudustri"><code>@​dudustri</code></a> (<a href="">#352</a>)</li>
<li>build: Solve the version error <a href="https://github.com/deepcharles"><code>@​deepcharles</code></a> (<a href="">#354</a>)</li>
<li>ci(codecov): update codecov gha version number <a href="https://github.com/oboulant"><code>@​oboulant</code></a> (<a href="">#330</a>)</li>
<li>ci(tests): use new version of the coverage uploader <a href="https://github.com/oboulant"><code>@​oboulant</code></a> (<a href="">#345</a>)</li>
<li>ci(codecov): Update run-test.yml <a href="https://github.com/deepcharles"><code>@​deepcharles</code></a> (<a href="">#327</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>a3f8c43</code></a> ci(build-wheel): remove py314 from wheels (<a href="">#358</a>)</li>
<li><a href=""><code>89105fc</code></a> ci(upload-pypi): bump versions of gha and manage supported python versions (#...</li>
<li><a href=""><code>684b2ed</code></a> chore: pre-commit autoupdate (<a href="">#329</a>)</li>
<li><a href=""><code>e88da13</code></a> build: add python 3.13 wheels (<a href="">#352</a>)</li>
<li><a href=""><code>f0b04b5</code></a> build: Solve the version error (<a href="">#354</a>)</li>
<li><a href=""><code>39a837b</code></a> docs: correct Latex formatting (<a href="">#348</a>)</li>
<li><a href=""><code>aa53c74</code></a> CI: add macos arm64 to cibw (<a href="">#340</a>)</li>
<li><a href=""><code>44045b0</code></a> ci(codecov): update codecov gha version number (<a href="">#330</a>)</li>
<li><a href=""><code>ae23aad</code></a> ci(tests): use new version of the coverage uploader (<a href="">#345</a>)</li>
<li><a href=""><code>f83b808</code></a> docs: update readme with latest news</li>
<li>Additional commits viewable in <a href="https://github.com/deepcharles/ruptures/compare/v1.1.9...v1.1.10">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=ruptures&package-manager=pip&previous-version=1.1.9&new-version=1.1.10)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ce073f64092b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
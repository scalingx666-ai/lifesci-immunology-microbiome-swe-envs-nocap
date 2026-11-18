# Issue

**Title:** build(deps-dev): bump pillow from 11.0.0 to 11.1.0

## Description

Bumps [pillow](https://github.com/python-pillow/Pillow) from 11.0.0 to 11.1.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/python-pillow/Pillow/releases">pillow's releases</a>.</em></p>
<blockquote>
<h2>11.1.0</h2>
<p><a href="https://pillow.readthedocs.io/en/stable/releasenotes/11.1.0.html">https://pillow.readthedocs.io/en/stable/releasenotes/11.1.0.html</a></p>
<h2>Documentation</h2>
<ul>
<li>Added release notes for writing XMP bytes to JPEG and MPO <a href="">#8627</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Added release notes for using zlib-ng instead of zlib <a href="">#8599</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Replace python-pillow.org with python-pillow.github.io <a href="">#8586</a> [<a href="https://github.com/hugovk"><code>@​hugovk</code></a>]</li>
<li>ImageFile tile is never None <a href="">#8582</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Only use start year in copyright, remove end years <a href="">#8577</a> [<a href="https://github.com/hugovk"><code>@​hugovk</code></a>]</li>
<li>Python 3.12 is tested on MinGW <a href="">#8575</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Use brew formula to install libraqm <a href="">#8574</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Added link to GitHub releases in CHANGES <a href="">#8571</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Release drafter: move removals, deprecations, documentation up, and uncategorised changes last <a href="">#8570</a> [<a href="https://github.com/hugovk"><code>@​hugovk</code></a>]</li>
<li>Updated macOS tested Pillow versions <a href="">#8538</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Use test image filename <a href="">#8534</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Update Windows 11 Arm64 tested versions <a href="">#8523</a> [<a href="https://github.com/nulano"><code>@​nulano</code></a>]</li>
<li>Move MPO into &quot;Fully supported formats&quot; <a href="">#8504</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Update license to MIT-CMU <a href="">#8490</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
</ul>
<h2>Dependencies</h2>
<ul>
<li>Update dependency mypy to v1.14.1 <a href="">#8643</a> [<a href="https://github.com/renovate"><code>@​renovate</code></a>]</li>
<li>Update dependency mypy to v1.14.0 <a href="">#8613</a> [<a href="https://github.com/renovate"><code>@​renovate</code></a>]</li>
<li>Updated libwebp to 1.5.0 <a href="">#8612</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Updated libXau to 1.0.12 <a href="">#8598</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Updated libjpeg-turbo to 3.1.0 <a href="">#8595</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Updated harfbuzz to 10.1.0 <a href="">#8533</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Updated openjpeg to 2.5.3 <a href="">#8591</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Update dependency cibuildwheel to v2.22.0 <a href="">#8580</a> [<a href="https://github.com/renovate"><code>@​renovate</code></a>]</li>
<li>Update codecov/codecov-action action to v5 <a href="">#8557</a> [<a href="https://github.com/renovate"><code>@​renovate</code></a>]</li>
<li>Migrate renovate config <a href="">#8527</a> [<a href="https://github.com/renovate"><code>@​renovate</code></a>]</li>
<li>Update dependency mypy to v1.13.0 <a href="">#8491</a> [<a href="https://github.com/renovate"><code>@​renovate</code></a>]</li>
<li>Update dependency mypy to v1.12.1 <a href="">#8487</a> [<a href="https://github.com/renovate"><code>@​renovate</code></a>]</li>
</ul>
<h2>Testing</h2>
<ul>
<li>Added CentOS Stream 10 <a href="">#8646</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Use monkeypatch <a href="">#8628</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Pass file handle to ContainerIO <a href="">#8625</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Use register_handler <a href="">#8499</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Use monkeypatch <a href="">#8626</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Test libjpeg-turbo on macOS <a href="">#8596</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Test 3.13t (free-threaded) from Quansight-Labs/setup-python on Linux and macOS <a href="">#8565</a> [<a href="https://github.com/hugovk"><code>@​hugovk</code></a>]</li>
<li>Run gcc problem matcher on Python 3.13 <a href="">#8541</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Add trove-classifiers&gt;=2024.10.12 to 'tests' extra and use for Windows CI <a href="">#8514</a> [<a href="https://github.com/hugovk"><code>@​hugovk</code></a>]</li>
<li>Apply security fixes to GitHub Actions <a href="">#8526</a> [<a href="https://github.com/hugovk"><code>@​hugovk</code></a>]</li>
<li>Remove unused <code>gcov: true</code> for codecov-action@v4 <a href="">#8521</a> [<a href="https://github.com/hugovk"><code>@​hugovk</code></a>]</li>
<li>Added Fedora 41 <a href="">#8520</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Do not repeatedly save to the same path <a href="">#8512</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/python-pillow/Pillow/blob/main/CHANGES.rst">pillow's changelog</a>.</em></p>
<blockquote>
<h2>11.1.0 and newer</h2>
<p>See GitHub Releases:</p>
<ul>
<li><a href="https://github.com/python-pillow/Pillow/releases">https://github.com/python-pillow/Pillow/releases</a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>4c1aed8</code></a> 11.1.0 version bump</li>
<li><a href=""><code>dfb368a</code></a> Merge pull request <a href="">#8651</a> from radarhere/blp</li>
<li><a href=""><code>5d998d3</code></a> Improved coverage</li>
<li><a href=""><code>6b75e06</code></a> Do not reread start of header in decoder</li>
<li><a href=""><code>b89cc09</code></a> Corrected BLP1 alpha depth handling</li>
<li><a href=""><code>aa0f412</code></a> Merge pull request <a href="">#8646</a> from radarhere/centos</li>
<li><a href=""><code>e344271</code></a> Added CentOS Stream 10</li>
<li><a href=""><code>17f09f3</code></a> Merge pull request <a href="">#8644</a> from radarhere/c99</li>
<li><a href=""><code>d42f22b</code></a> Added release notes</li>
<li><a href=""><code>c7026d9</code></a> Merge pull request <a href="">#8642</a> from radarhere/bigtiff</li>
<li>Additional commits viewable in <a href="https://github.com/python-pillow/Pillow/compare/11.0.0...11.1.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=pillow&package-manager=pip&previous-version=11.0.0&new-version=11.1.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Build:
- Bump Pillow from 11.0.0 to 11.1.0.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0d84e40d3f24`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
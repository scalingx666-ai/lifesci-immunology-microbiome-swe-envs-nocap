# Issue

**Title:** Build(deps): Bump roaring from 0.10.12 to 0.11.0

## Description

Bumps [roaring](https://github.com/RoaringBitmap/roaring-rs) from 0.10.12 to 0.11.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/RoaringBitmap/roaring-rs/releases">roaring's releases</a>.</em></p>
<blockquote>
<h2>v0.11.0</h2>
<h2>What's Changed</h2>
<ul>
<li>Add fuzzing to compare against croaring-rs by <a href="https://github.com/Dr-Emann"><code>@​Dr-Emann</code></a> in <a href="">RoaringBitmap/roaring-rs#321</a></li>
<li>Include license files in published crate by <a href="https://github.com/ankane"><code>@​ankane</code></a> in <a href="">RoaringBitmap/roaring-rs#323</a></li>
<li>Run containers part 2 by <a href="https://github.com/Kerollmops"><code>@​Kerollmops</code></a> in <a href="">RoaringBitmap/roaring-rs#66</a></li>
<li>Run containers attempt 3 by <a href="https://github.com/lucascool12"><code>@​lucascool12</code></a> in <a href="">RoaringBitmap/roaring-rs#320</a></li>
<li>Change the API of the push method to return a result by <a href="https://github.com/Kerollmops"><code>@​Kerollmops</code></a> in <a href="">RoaringBitmap/roaring-rs#325</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/ankane"><code>@​ankane</code></a> made their first contribution in <a href="">RoaringBitmap/roaring-rs#323</a></li>
<li><a href="https://github.com/lucascool12"><code>@​lucascool12</code></a> made their first contribution in <a href="">RoaringBitmap/roaring-rs#320</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/RoaringBitmap/roaring-rs/compare/v0.10.12...v0.11.0">https://github.com/RoaringBitmap/roaring-rs/compare/v0.10.12...v0.11.0</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>5c1134c</code></a> Merge pull request <a href="">#325</a> from RoaringBitmap/clarify-push-api</li>
<li><a href=""><code>5e2d93e</code></a> Fix documentation</li>
<li><a href=""><code>86a7821</code></a> Introduce a new try_push method</li>
<li><a href=""><code>dec5564</code></a> Change the API of the push method to return a Result</li>
<li><a href=""><code>589cb8f</code></a> Merge pull request <a href="">#326</a> from RoaringBitmap/bump-version</li>
<li><a href=""><code>06230d1</code></a> Make cargo nightly happy</li>
<li><a href=""><code>9e5cee4</code></a> Bump version to 0.11.0</li>
<li><a href=""><code>6535a82</code></a> Merge pull request <a href="">#320</a> from lucascool12/run-containers</li>
<li><a href=""><code>5427897</code></a> test: remove <code>dbg!</code> statement</li>
<li><a href=""><code>5b9372a</code></a> chore: update croaring to 2.3.1 for fuzzing</li>
<li>Additional commits viewable in <a href="https://github.com/RoaringBitmap/roaring-rs/compare/v0.10.12...v0.11.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=roaring&package-manager=cargo&previous-version=0.10.12&new-version=0.11.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d4cad5160bc7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
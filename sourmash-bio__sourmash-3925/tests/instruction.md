# Issue

**Title:** Build(ci): Bump softprops/action-gh-release from 2 to 3

## Description

Bumps [softprops/action-gh-release](https://github.com/softprops/action-gh-release) from 2 to 3.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/softprops/action-gh-release/releases">softprops/action-gh-release's releases</a>.</em></p>
<blockquote>
<h2>v3.0.0</h2>
<p><code>3.0.0</code> is a major release that moves the action runtime from Node 20 to Node 24.
Use <code>v3</code> on GitHub-hosted runners and self-hosted fleets that already support the
Node 24 Actions runtime. If you still need the last Node 20-compatible line, stay on
<code>v2.6.2</code>.</p>
<h2>What's Changed</h2>
<h3>Other Changes 🔄</h3>
<ul>
<li>Move the action runtime and bundle target to Node 24</li>
<li>Update <code>@types/node</code> to the Node 24 line and allow future Dependabot updates</li>
<li>Keep the floating major tag on <code>v3</code>; <code>v2</code> remains pinned to the latest <code>2.x</code> release</li>
</ul>
<h2>v2.6.2</h2>
<!-- raw HTML omitted -->
<h2>What's Changed</h2>
<h3>Other Changes 🔄</h3>
<ul>
<li>chore(deps): bump picomatch from 4.0.3 to 4.0.4 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">softprops/action-gh-release#775</a></li>
<li>chore(deps): bump brace-expansion from 5.0.4 to 5.0.5 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">softprops/action-gh-release#777</a></li>
<li>chore(deps): bump vite from 8.0.0 to 8.0.5 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">softprops/action-gh-release#781</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/softprops/action-gh-release/compare/v2...v2.6.2">https://github.com/softprops/action-gh-release/compare/v2...v2.6.2</a></p>
<h2>v2.6.1</h2>
<p><code>2.6.1</code> is a patch release focused on restoring linked discussion thread creation when
<code>discussion_category_name</code> is set. It fixes <code></code>, where the draft-first publish flow
stopped carrying the discussion category through the final publish step.</p>
<p>If you still hit an issue after upgrading, please open a report with the bug template and include a minimal repro or sanitized workflow snippet where possible.</p>
<h2>What's Changed</h2>
<h3>Bug fixes 🐛</h3>
<ul>
<li>fix: preserve discussion category on publish by <a href="https://github.com/chenrui333"><code>@​chenrui333</code></a> in <a href="">softprops/action-gh-release#765</a></li>
</ul>
<h2>v2.6.0</h2>
<p><code>2.6.0</code> is a minor release centered on <code>previous_tag</code> support for <code>generate_release_notes</code>,
which lets workflows pin GitHub's comparison base explicitly instead of relying on the default range.
It also includes the recent concurrent asset upload recovery fix, a <code>working_directory</code> docs sync,
a checked-bundle freshness guard for maintainers, and clearer immutable-prerelease guidance where
GitHub platform behavior imposes constraints on how prerelease asset uploads can be published.</p>
<p>If you still hit an issue after upgrading, please open a report with the bug template and include a minimal repro or sanitized workflow snippet where possible.</p>
<h2>What's Changed</h2>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/softprops/action-gh-release/blob/master/CHANGELOG.md">softprops/action-gh-release's changelog</a>.</em></p>
<blockquote>
<h2>0.1.13</h2>
<ul>
<li>fix issue with multiple runs concatenating release bodies <a href="">#145</a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>b430933</code></a> release: cut v3.0.0 for Node 24 upgrade (<a href="">#670</a>)</li>
<li><a href=""><code>c2e35e0</code></a> chore(deps): bump the npm group across 1 directory with 7 updates (<a href="">#783</a>)</li>
<li>See full diff in <a href="https://github.com/softprops/action-gh-release/compare/v2...v3">compare view</a></li>
</ul>
</details>
<br />

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `64e527f2384b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Build(deps-py): Update cachetools requirement from <7,>=4 to >=4,<8 in the dependencies group

## Description

Updates the requirements on [cachetools](https://github.com/tkem/cachetools) to permit the latest version.
Updates `cachetools` to 7.0.0
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/tkem/cachetools/blob/master/CHANGELOG.rst">cachetools's changelog</a>.</em></p>
<blockquote>
<h1>v7.0.0 (2026-02-01)</h1>
<ul>
<li>
<p>Require Python 3.10 or later (breaking change).</p>
</li>
<li>
<p>Drop support for passing <code>info</code> as fourth positional parameter to
<code>@cached</code> (breaking change).</p>
</li>
<li>
<p>Drop support for <code>cache(self)</code> returning <code>None</code> with
<code>@cachedmethod</code> (breaking change).</p>
</li>
<li>
<p>Convert the <code>@cachedmethod</code> wrappers to descriptors, deprecating
its use with class methods and instances that do not provide a
mutable <code>__dict__</code> attribute (potentially breaking change).</p>
</li>
<li>
<p>Convert the previously undocumented <code>@cachedmethod</code> attributes
(<code>cache</code>, <code>cache_lock</code>, etc.) to properties for instance
methods, providing official support and documentation (potentially
breaking change).</p>
</li>
<li>
<p>Add an optional <code>info</code> parameter to the <code>@cachedmethod</code>
decorator for reporting per-instance cache statistics.  Note that
this requires the instance's <code>__dict__</code> attribute to be a mutable
mapping.</p>
</li>
</ul>
<h1>v6.2.6 (2026-01-27)</h1>
<ul>
<li>
<p>Improve typedkey performance.</p>
</li>
<li>
<p>Minor documentation improvements.</p>
</li>
<li>
<p>Minor testing improvements.</p>
</li>
<li>
<p>Minor code readability improvements.</p>
</li>
</ul>
<h1>v6.2.5 (2026-01-25)</h1>
<ul>
<li>
<p>Improve documentation regarding <code>@cachedmethod</code> with <code>lock</code>
parameter.</p>
</li>
<li>
<p>Add test cases for cache stampede scenarios.</p>
</li>
<li>
<p>Update CI environment.</p>
</li>
</ul>
<p>v6.2.4 (2025-12-15)</p>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>28bbcba</code></a> Release v7.0.0.</li>
<li><a href=""><code>45776b2</code></a> Minor code and documentation improvements.</li>
<li><a href=""><code>51a70a9</code></a> Fix <a href="">#357</a>: Update documentation.</li>
<li><a href=""><code>bb72c21</code></a> Fix <a href="">#357</a>: Add cache_info() support for <a href="https://github.com/cachedmethod"><code>@​cachedmethod</code></a>.</li>
<li><a href=""><code>86352ae</code></a> Fix <a href="">#357</a>: Convert <a href="https://github.com/cachedmethod"><code>@​cachedmethod</code></a> decorators to descriptors.</li>
<li><a href=""><code>263cf31</code></a> Prepare v7.0.0.</li>
<li><a href=""><code>59d4db2</code></a> Drop support for cache(self) returning None in <a href="https://github.com/cachedmethod"><code>@​cachedmethod</code></a>.</li>
<li><a href=""><code>c933a97</code></a> Drop support for passing &quot;info&quot; as fourth positional parameter of <a href="https://github.com/cached"><code>@​cached</code></a>.</li>
<li><a href=""><code>ae3d6bd</code></a> Drop support for Python 3.9.</li>
<li><a href=""><code>a12c3b0</code></a> Bump actions/checkout from 6.0.1 to 6.0.2</li>
<li>Additional commits viewable in <a href="https://github.com/tkem/cachetools/compare/v4.0.0...v7.0.0">compare view</a></li>
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
- `@dependabot merge` will merge this PR after your CI passes on it
- `@dependabot squash and merge` will squash and merge this PR after your CI passes on it
- `@dependabot cancel merge` will cancel a previously requested merge and block automerging
- `@dependabot reopen` will reopen this PR if it is closed
- `@dependabot close` will close this PR and stop Dependabot recreating it. You can achieve the same result by closing it manually
- `@dependabot show <dependency name> ignore conditions` will show all of the ignore conditions of the specified dependency
- `@dependabot ignore <dependency name> major version` will close this group update PR and stop Dependabot creating any more for the specific dependency's major version (unless you unignore this specific dependency's major version or upgrade to it yourself)
- `@dependabot ignore <dependency name> minor version` will close this group update PR and stop Dependabot creating any more for the specific dependency's minor version (unless you unignore this specific dependency's minor version or upgrade to it yourself)
- `@dependabot ignore <dependency name>` will close this group update PR and stop Dependabot creating any more for the specific dependency (unless you unignore this specific dependency or upgrade to it yourself)
- `@dependabot unignore <dependency name>` will remove all of the ignore conditions of the specified dependency
- `@dependabot unignore <dependency name> <ignore condition>` will remove the ignore condition of the specified dependency and ignore conditions

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9981e4288556`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
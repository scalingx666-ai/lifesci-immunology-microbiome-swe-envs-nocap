# Issue

**Title:** Build(deps-py): Update maturin requirement from <1.11.0,>=1 to >=1,<1.12.0 in the dependencies group

## Description

Updates the requirements on [maturin](https://github.com/pyo3/maturin) to permit the latest version.
Updates `maturin` to 1.11.5
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/pyo3/maturin/releases">maturin's releases</a>.</em></p>
<blockquote>
<h2>v1.11.5</h2>
<h2>1.11.5</h2>
<ul>
<li>Allow combining <code>--compatibility pypi</code> with other <code>--compatibility</code> values (<a href="">#2928</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/PyO3/maturin/blob/main/Changelog.md">maturin's changelog</a>.</em></p>
<blockquote>
<h2>1.11.5</h2>
<ul>
<li>Allow combining <code>--compatibility pypi</code> with other <code>--compatibility</code> values (<a href="">#2928</a>)</li>
</ul>
<h2>1.11.4</h2>
<ul>
<li>Support armv6l and armv7l in pypi compatibility (<a href="">#2926</a>)</li>
<li>Improve the reliability of maturin's own CI</li>
</ul>
<h2>1.11.3</h2>
<ul>
<li>Fix manylinux2014 compliance check (<a href="">#2922</a>)</li>
</ul>
<h2>1.11.2</h2>
<ul>
<li>Fix failed release</li>
</ul>
<h2>1.11.1</h2>
<ul>
<li>Fix compiled artifacts being excluded by source path matching (<a href="">#2910</a>)</li>
<li>Better error reporting for missing interpreters (<a href="">#2918</a>)</li>
<li>Ignore unreadable excluded directories (<a href="">#2916</a>)</li>
</ul>
<h2>[1.11.0] - Yanked</h2>
<p>Note: This release was yanked to a regression: <a href="">PyO3/maturin#2909</a></p>
<ul>
<li>Refactor <code>ModuleWriter</code> to be easier to implement and use</li>
<li>Add Android cross compilation support, fix wheel tags for Android</li>
<li>Update generate-ci to macos-15-intel and add windows arm support</li>
<li>Deprecate 'upload' and 'publish' CLI commands</li>
</ul>
<h2>[1.10.2]</h2>
<ul>
<li>Fix tagging for iOS x86_64 simulator wheels.</li>
<li>Set entry type when adding to the tar file.</li>
</ul>
<h2>[1.10.1]</h2>
<ul>
<li>Fix wrong dependency on Homebrew liblzma on macOS by static linking liblama</li>
</ul>
<h2>[1.10.0]</h2>
<ul>
<li>Add <code>tool.maturin.editable-profile</code> option to override profile for editable package installations.</li>
<li>Add support for Cygwin.</li>
<li>When building <code>abi3</code> wheels on non-Windows platforms that aren't cross-compiling, the <code>sysconfigdata</code> of the interpreter used to run maturin will now be used, rather than a dummy interpreter.</li>
<li>Allow iOS cross-platform virtual environments, such as those used by cibuildwheel, to imply an iOS target.</li>
<li>Fix iOS wheel naming to be compliant with PEP 730.</li>
<li>Fix generated WHEEL Tag metadata to be spec compliant.</li>
<li>Fix incorrect warning about missing <code>extension-module</code> feature on PyO3 0.26+.</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>5d50051</code></a> Release 1.11.5 (<a href="">#2930</a>)</li>
<li><a href=""><code>5b54ce4</code></a> Allow combining <code>--compatibility pypi</code> with other <code>--compatibility</code> values (#...</li>
<li><a href=""><code>b80ab1f</code></a> Release 1.11.4 (<a href="">#2927</a>)</li>
<li><a href=""><code>e5fa277</code></a> Support armv6l and armv7l in pypi compatibility (<a href="">#2926</a>)</li>
<li><a href=""><code>ff7f3ef</code></a> Use uv instead of sudo pip and pin release bootstrapping version (<a href="">#2925</a>)</li>
<li><a href=""><code>a4f232d</code></a> Automate release dry runs (<a href="">#2924</a>)</li>
<li><a href=""><code>795565d</code></a> Release 1.11.3 (<a href="">#2923</a>)</li>
<li><a href=""><code>67a59de</code></a> Fix manylinux2014 compliance check (<a href="">#2922</a>)</li>
<li><a href=""><code>3034dfc</code></a> Release 1.11.2 (<a href="">#2921</a>)</li>
<li><a href=""><code>9a0942a</code></a> Release 0.11.1 (<a href="">#2920</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/pyo3/maturin/compare/v1.0.0...v1.11.5">compare view</a></li>
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `531a4c22b744`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
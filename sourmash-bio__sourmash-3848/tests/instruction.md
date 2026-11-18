# Issue

**Title:** Build(deps-py): Bump the dependencies group with 2 updates

## Description

Updates the requirements on [pytest](https://github.com/pytest-dev/pytest) and [maturin](https://github.com/pyo3/maturin) to permit the latest version.
Updates `pytest` to 9.0.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/pytest-dev/pytest/releases">pytest's releases</a>.</em></p>
<blockquote>
<h2>9.0.0</h2>
<h1>pytest 9.0.0 (2025-11-05)</h1>
<h2>New features</h2>
<ul>
<li>
<p><a href="">#1367</a>: <strong>Support for subtests</strong> has been added.</p>
<p><code>subtests &lt;subtests&gt;</code> are an alternative to parametrization, useful in situations where the parametrization values are not all known at collection time.</p>
<p>Example:</p>
<pre lang="python"><code>def contains_docstring(p: Path) -&gt; bool:
    &quot;&quot;&quot;Return True if the given Python file contains a top-level docstring.&quot;&quot;&quot;
    ...
<p>def test_py_files_contain_docstring(subtests: pytest.Subtests) -&gt; None:
for path in Path.cwd().glob(&quot;*.py&quot;):
with subtests.test(path=str(path)):
assert contains_docstring(path)
</code></pre></p>
<p>Each assert failure or error is caught by the context manager and reported individually, giving a clear picture of all files that are missing a docstring.</p>
<p>In addition, <code>unittest.TestCase.subTest</code> is now also supported.</p>
<p>This feature was originally implemented as a separate plugin in <a href="https://github.com/pytest-dev/pytest-subtests">pytest-subtests</a>, but since then has been merged into the core.</p>
<blockquote>
<p>[!NOTE]
This feature is experimental and will likely evolve in future releases. By that we mean that we might change how subtests are reported on failure, but the functionality and how to use it are stable.</p>
</blockquote>
</li>
<li>
<p><a href="">#13743</a>: Added support for <strong>native TOML configuration files</strong>.</p>
<p>While pytest, since version 6, supports configuration in <code>pyproject.toml</code> files under <code>[tool.pytest.ini_options]</code>,
it does so in an &quot;INI compatibility mode&quot;, where all configuration values are treated as strings or list of strings.
Now, pytest supports the native TOML data model.</p>
<p>In <code>pyproject.toml</code>, the native TOML configuration is under the <code>[tool.pytest]</code> table.</p>
<pre lang="toml"><code># pyproject.toml
[tool.pytest]
minversion = &quot;9.0&quot;
addopts = [&quot;-ra&quot;, &quot;-q&quot;]
testpaths = [
    &quot;tests&quot;,
    &quot;integration&quot;,
]
</code></pre>
</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>f4b0fd2</code></a> Prepare release version 9.0.0</li>
<li><a href=""><code>52d8e68</code></a> Merge pull request <a href="">#13889</a> from bluetech/regendoc-restore</li>
<li><a href=""><code>d6d3e4a</code></a> doc: fixes for regendoc</li>
<li><a href=""><code>7cb3974</code></a> doc: restore missing &quot;# content of pytest.toml&quot; regendoc commands</li>
<li><a href=""><code>5ae9e47</code></a> build(deps): Bump django in /testing/plugins_integration (<a href="">#13881</a>)</li>
<li><a href=""><code>adb3658</code></a> Merge pull request <a href="">#13864</a> from bluetech/config-cleanups-2</li>
<li><a href=""><code>a28c08e</code></a> Merge pull request <a href="">#13875</a> from bluetech/ci-tweaks</li>
<li><a href=""><code>a250954</code></a> ci: split publish-to-pypi and push-tag jobs</li>
<li><a href=""><code>ebc152f</code></a> ci: update setup python's from 3.11 or 3.* to 3.13</li>
<li><a href=""><code>dfd796f</code></a> ci: move running update-plugin-list script to tox</li>
<li>Additional commits viewable in <a href="https://github.com/pytest-dev/pytest/compare/6.2.4...9.0.0">compare view</a></li>
</ul>
</details>
<br />

Updates `maturin` to 1.10.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/pyo3/maturin/releases">maturin's releases</a>.</em></p>
<blockquote>
<h2>v1.10.0</h2>
<h2>What's Changed</h2>
<ul>
<li>Fix generated WHEEL Tag metadata to be spec compliant. by <a href="https://github.com/jsirois"><code>@​jsirois</code></a> in <a href="">PyO3/maturin#2762</a></li>
<li>Export all Cargo URL metadata items to Python by <a href="https://github.com/chrysn"><code>@​chrysn</code></a> in <a href="">PyO3/maturin#2760</a></li>
<li>Update maximum Python version to 3.14 by <a href="https://github.com/messense"><code>@​messense</code></a> in <a href="">PyO3/maturin#2763</a></li>
<li>Remove shebang from non-executable <strong>init</strong>.py file by <a href="https://github.com/musicinmybrain"><code>@​musicinmybrain</code></a> in <a href="">PyO3/maturin#2775</a></li>
<li>Stop warning about missing <code>extension-module</code> feature on pyo3 0.26+ by <a href="https://github.com/messense"><code>@​messense</code></a> in <a href="">PyO3/maturin#2789</a></li>
<li><code>--profile</code> conflicts with <code>--release</code> (and/or <code>--debug</code>) by <a href="https://github.com/davidhewitt"><code>@​davidhewitt</code></a> in <a href="">PyO3/maturin#2793</a></li>
<li>Bump MSRV to 1.83.0 by <a href="https://github.com/messense"><code>@​messense</code></a> in <a href="">PyO3/maturin#2790</a></li>
<li>respect CLI profile over pyproject.toml by <a href="https://github.com/davidhewitt"><code>@​davidhewitt</code></a> in <a href="">PyO3/maturin#2794</a></li>
<li>chore: add FreeBSD 14.3 amd64 sysconfig by <a href="https://github.com/fleetingbytes"><code>@​fleetingbytes</code></a> in <a href="">PyO3/maturin#2805</a></li>
<li>Add Cygwin support by <a href="https://github.com/lazka"><code>@​lazka</code></a> in <a href="">PyO3/maturin#2819</a></li>
<li>PyO3: do not add <code>extension-module</code> feature in template and tutorial by <a href="https://github.com/Tpt"><code>@​Tpt</code></a> in <a href="">PyO3/maturin#2821</a></li>
<li>Remove add_directory() from ModuleWriter trait by <a href="https://github.com/e-nomem"><code>@​e-nomem</code></a> in <a href="">PyO3/maturin#2824</a></li>
<li>Correct wheel naming when targeting iOS by <a href="https://github.com/freakboy3742"><code>@​freakboy3742</code></a> in <a href="">PyO3/maturin#2827</a></li>
<li>Add support for iOS cross-platform virtual environments by <a href="https://github.com/freakboy3742"><code>@​freakboy3742</code></a> in <a href="">PyO3/maturin#2828</a></li>
<li>add <code>editable-profile</code> option by <a href="https://github.com/davidhewitt"><code>@​davidhewitt</code></a> in <a href="">PyO3/maturin#2826</a></li>
<li>Make sdist reproducible by <a href="https://github.com/e-nomem"><code>@​e-nomem</code></a> in <a href="">PyO3/maturin#2831</a></li>
<li>always use &quot;library&quot; mode to generate uniffi bindings by <a href="https://github.com/davidhewitt"><code>@​davidhewitt</code></a> in <a href="">PyO3/maturin#2840</a></li>
<li>If an interpreter is available, use it, even when building ABI3. by <a href="https://github.com/freakboy3742"><code>@​freakboy3742</code></a> in <a href="">PyO3/maturin#2829</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/jsirois"><code>@​jsirois</code></a> made their first contribution in <a href="">PyO3/maturin#2762</a></li>
<li><a href="https://github.com/chrysn"><code>@​chrysn</code></a> made their first contribution in <a href="">PyO3/maturin#2760</a></li>
<li><a href="https://github.com/ddelange"><code>@​ddelange</code></a> made their first contribution in <a href="">PyO3/maturin#2769</a></li>
<li><a href="https://github.com/vvsagar"><code>@​vvsagar</code></a> made their first contribution in <a href="">PyO3/maturin#2783</a></li>
<li><a href="https://github.com/MatthijsKok"><code>@​MatthijsKok</code></a> made their first contribution in <a href="">PyO3/maturin#2799</a></li>
<li><a href="https://github.com/fleetingbytes"><code>@​fleetingbytes</code></a> made their first contribution in <a href="">PyO3/maturin#2805</a></li>
<li><a href="https://github.com/linkmauve"><code>@​linkmauve</code></a> made their first contribution in <a href="">PyO3/maturin#2811</a></li>
<li><a href="https://github.com/lazka"><code>@​lazka</code></a> made their first contribution in <a href="">PyO3/maturin#2819</a></li>
<li><a href="https://github.com/e-nomem"><code>@​e-nomem</code></a> made their first contribution in <a href="">PyO3/maturin#2824</a></li>
<li><a href="https://github.com/freakboy3742"><code>@​freakboy3742</code></a> made their first contribution in <a href="">PyO3/maturin#2827</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/PyO3/maturin/compare/v1.9.6...v1.10.0">https://github.com/PyO3/maturin/compare/v1.9.6...v1.10.0</a></p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/PyO3/maturin/blob/main/Changelog.md">maturin's changelog</a>.</em></p>
<blockquote>
<h2>[1.10.0]</h2>
<ul>
<li>Add <code>tool.maturin.editable-profile</code> option to override profile for editable package installations.</li>
<li>Add support for Cygwin.</li>
<li>When building <code>abi3</code> wheels on non-Windows platforms that aren't cross-compiling, the <code>sysconfigdata</code> of the interpreter used to run maturin will now be used, rather than a dummy interpreter.</li>
<li>Allow iOS cross-platform virtual environments, such as those used by cibuildwheel, to imply an iOS target.</li>
<li>Fix iOS wheel naming to be compliant with PEP 730.</li>
<li>Fix generated WHEEL Tag metadata to be spec compliant.</li>
<li>Fix incorrect warning about missing <code>extension-module</code> feature on PyO3 0.26+.</li>
<li>Remove <code>add_directory()</code> from ModuleWriter and make it an implementation detail for the specific impl.</li>
<li>Clear out uid/gid and set deterministic mtime for files in sdist.</li>
<li>Always use &quot;library&quot; mode to build uniffi bindings.</li>
</ul>
<h2>[1.9.6]</h2>
<ul>
<li>Fix regressions to interpreter platform detection on Windows from 1.9.5</li>
<li>Further fixes to interpreter detection for Windows ARM64</li>
</ul>
<h2>[1.9.5]</h2>
<ul>
<li>Add builtin sysconfig for FreeBSD 14.2 amd64</li>
<li>Fix issue searching lib dir containing Python 3.14 <code>build-details.json</code></li>
<li>Fix detection of compatible interpreters on Windows ARM64</li>
</ul>
<h2>[1.9.4]</h2>
<ul>
<li>Add a <code>use-base-python</code> option to <code>pyproject.toml</code> with the same behaviour as <code>MATURIN_PEP517_USE_BASE_PYTHON</code>.</li>
<li>Add builtin sysconfigs for GraalPy</li>
<li>Fix calculation of platform tag for FreeBSD</li>
</ul>
<h2>[1.9.3]</h2>
<ul>
<li>Fix adding <code>project.license-files</code> to source distributions.</li>
<li>Fix relative Readme rewrite of the root crate in source distributions.</li>
</ul>
<h2>[1.9.2]</h2>
<ul>
<li>Fix PEP 639 implementation, use <code>License-Expression</code> over <code>License</code>.</li>
</ul>
<h2>[1.9.1]</h2>
<ul>
<li>Fix absolute license file path from <code>Cargo.toml</code> in <a href="">#2667</a></li>
</ul>
<h2>[1.9.0]</h2>
<ul>
<li>Add full PEP 639 support for <code>project.license</code> and <code>project.license-files</code> in <a href="">#2647</a>.</li>
<li>Add <code>--compatibility pypi</code> to only build wheels with platform tags that can also be uploaded to PyPI. This blocks e.g. building for riscv64, which is supported by manylinux, but not by PyPI.</li>
</ul>
<h2>[1.8.7]</h2>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>c3093d1</code></a> release: 1.10.0 (<a href="">#2841</a>)</li>
<li><a href=""><code>a41bc86</code></a> If an interpreter is available, use it, even when building ABI3. (<a href="">#2829</a>)</li>
<li><a href=""><code>e753052</code></a> always use &quot;library&quot; mode to generate uniffi bindings (<a href="">#2840</a>)</li>
<li><a href=""><code>216b643</code></a> Update manylinux/musllinux policies to the latest main (<a href="">#2836</a>)</li>
<li><a href=""><code>044ba83</code></a> Revert &quot;Upgrade goblin to 0.10&quot; (<a href="">#2837</a>)</li>
<li><a href=""><code>bb3d629</code></a> Upgrade goblin to 0.10 (<a href="">#2833</a>)</li>
<li><a href=""><code>8375496</code></a> Use <code>serial_test</code> for tests that modifies env vars (<a href="">#2832</a>)</li>
<li><a href=""><code>9dc2f5f</code></a> Make sdist reproducible (<a href="">#2831</a>)</li>
<li><a href=""><code>685efba</code></a> ci: bump to Python 3.14, update runners (<a href="">#2830</a>)</li>
<li><a href=""><code>57aa6ed</code></a> add <code>editable-profile</code> option (<a href="">#2826</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/pyo3/maturin/compare/v1.0.0...v1.10.0">compare view</a></li>
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2e70ecb91a3c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
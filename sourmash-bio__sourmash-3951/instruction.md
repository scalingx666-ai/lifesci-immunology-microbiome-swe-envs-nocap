# Issue

**Title:** Build(deps-py): Bump the dependencies group with 2 updates

## Description

Updates the requirements on [pytest](https://github.com/pytest-dev/pytest) and [maturin](https://github.com/pyo3/maturin) to permit the latest version.
Updates `pytest` to 9.1.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/pytest-dev/pytest/releases">pytest's releases</a>.</em></p>
<blockquote>
<h2>9.1.0</h2>
<h1>pytest 9.1.0 (2026-06-13)</h1>
<h2>Removals and backward incompatible breaking changes</h2>
<ul>
<li>
<p><a href="">#14533</a>: When using <code>--doctest-modules</code>, autouse fixtures with <code>module</code>, <code>package</code> or <code>session</code> scope that are defined inline in Python test modules (not plugins or conftests) will now possibly execute twice.</p>
<p>If this is undesirable, move the fixture definition to a <code>conftest.py</code> file if possible.</p>
<p>Technical explanation for those interested:
When using <!-- raw HTML omitted -->--doctest-modules<!-- raw HTML omitted -->, pytest possibly collects Python modules twice, once as <code>pytest.Module</code> and once as a <code>DoctestModule</code> (depending on the configuration).
Due to improvements in pytest's fixture implementation, if e.g. the <code>DoctestModule</code> collects a fixture, it is now visible to it only, and not to the <code>Module</code>.
This means that both need to register the fixtures independently.</p>
</li>
</ul>
<h2>Deprecations (removal in next major release)</h2>
<ul>
<li>
<p><a href="">#10819</a>: Added a deprecation warning for class-scoped fixtures defined as instance methods (without <code>@classmethod</code>). Such fixtures set attributes on a different instance than the test methods use, leading to unexpected behavior. Use <code>@classmethod</code> decorator instead -- by <code>yastcher</code>.</p>
<p>See <code>10819</code> and <code>14011</code>.</p>
</li>
<li>
<p><a href="">#12882</a>: Calling <code>request.getfixturevalue() &lt;pytest.FixtureRequest.getfixturevalue&gt;</code> during teardown to request a fixture that was not already requested is now deprecated and will become an error in pytest 10.</p>
<p>See <code>dynamic-fixture-request-during-teardown</code> for details.</p>
</li>
<li>
<p><a href="">#13409</a>: Using non-<code>~collections.abc.Collection</code> iterables (such as generators, iterators, or custom iterable objects) for the <code>argvalues</code> parameter in <code>@pytest.mark.parametrize &lt;pytest.mark.parametrize ref&gt;</code> and <code>metafunc.parametrize &lt;pytest.Metafunc.parametrize&gt;</code> is now deprecated.</p>
<p>These iterables get exhausted after the first iteration,
leading to tests getting unexpectedly skipped in cases such as running <code>pytest.main()</code> multiple times,
using class-level parametrize decorators,
or collecting tests multiple times.</p>
<p>See <code>parametrize-iterators</code> for details and suggestions.</p>
</li>
<li>
<p><a href="">#13946</a>: The private <code>config.inicfg</code> attribute is now deprecated.
Use <code>config.getini() &lt;pytest.Config.getini&gt;</code> to access configuration values instead.</p>
<p>See <code>config-inicfg</code> for more details.</p>
</li>
<li>
<p><a href="">#14004</a>: Passing <code>baseid</code> to <code>~pytest.FixtureDef</code> or <code>nodeid</code> strings to fixture registration APIs is now deprecated. These are internal pytest APIs that are used by some plugins.</p>
<p>Use the <code>node</code> parameter instead for fixture scoping. This enables more robust node-based
matching instead of string prefix matching.
If you've used <code>nodeid=None</code>, pass <code>node=session</code> instead.</p>
<p>This will be removed in pytest 10.</p>
</li>
<li>
<p><a href="">#14335</a>: The method of configuring hooks using markers, deprecated since pytest 7.2, is now scheduled to be removed in pytest 10.
See <code>hook-markers</code> for more details.</p>
</li>
<li>
<p><a href="">#14434</a>: The <code>--pastebin</code> option is now deprecated.</p>
</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>b2522cf</code></a> Prepare release version 9.1.0</li>
<li><a href=""><code>368d2fc</code></a> [refactor] Tighten <code>SetComparisonFunction</code> to <code>Iterator[str]</code> (<a href="">#14587</a>)</li>
<li><a href=""><code>ff77cd8</code></a> [refactor] Make base assertion comparisons return an iterator instead of a li...</li>
<li><a href=""><code>0d8491a</code></a> build(deps): Bump actions/stale from 10.2.0 to 10.3.0</li>
<li><a href=""><code>4a809d9</code></a> Merge pull request <a href="">#14568</a> from pytest-dev/register-fixture</li>
<li><a href=""><code>5dfa385</code></a> Fix recursion traceback test to cover all styles (<a href="">#14582</a>)</li>
<li><a href=""><code>f52ff0c</code></a> Add <code>pytest.register_fixture</code></li>
<li><a href=""><code>a8ac094</code></a> Merge pull request <a href="">#14567</a> from pytest-dev/more-visibility-deprecate</li>
<li><a href=""><code>e5620cd</code></a> [pre-commit.ci] pre-commit autoupdate (<a href="">#14577</a>)</li>
<li><a href=""><code>2ce9c6d</code></a> Merge pull request <a href="">#14540</a> from minbang930/fix-14533-doctest-module-fixtures</li>
<li>Additional commits viewable in <a href="https://github.com/pytest-dev/pytest/compare/6.2.4...9.1.0">compare view</a></li>
</ul>
</details>
<br />

Updates `maturin` to 1.14.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/pyo3/maturin/releases">maturin's releases</a>.</em></p>
<blockquote>
<h2>v1.14.0</h2>
<h2>What's Changed</h2>
<ul>
<li>Support parent-relative pyproject metadata in sdists by <a href="https://github.com/Copilot"><code>@​Copilot</code></a> in <a href="">PyO3/maturin#3182</a></li>
<li>Update PyPI platform tag validation by <a href="https://github.com/messense"><code>@​messense</code></a> in <a href="">PyO3/maturin#3187</a></li>
<li>maint: update setup emsdk action in generate-ci by <a href="https://github.com/ManonMarchand"><code>@​ManonMarchand</code></a> in <a href="">PyO3/maturin#3194</a></li>
<li>fix: only shim bin wheels during auditwheel repair by <a href="https://github.com/messense"><code>@​messense</code></a> in <a href="">PyO3/maturin#3197</a></li>
<li>fix: avoid editable ELF truncation from stale hardlinks by <a href="https://github.com/messense"><code>@​messense</code></a> in <a href="">PyO3/maturin#3199</a></li>
<li>Fix Pyodide Emscripten platform tags by <a href="https://github.com/messense"><code>@​messense</code></a> in <a href="">PyO3/maturin#3191</a></li>
<li>build(deps): bump openssl from 0.10.79 to 0.10.80 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">PyO3/maturin#3200</a></li>
<li>Use pax instead of GNU headers for tar by <a href="https://github.com/konstin"><code>@​konstin</code></a> in <a href="">PyO3/maturin#3203</a></li>
<li>feat: add default exclude <strong>pycache</strong> and *.pyc files by <a href="https://github.com/GuYeying"><code>@​GuYeying</code></a> in <a href="">PyO3/maturin#3202</a></li>
<li>Documentation: fix the update_readme script by <a href="https://github.com/ManonMarchand"><code>@​ManonMarchand</code></a> in <a href="">PyO3/maturin#3186</a></li>
<li>Fix python versions used in integration_pyo3_mixed_conda by <a href="https://github.com/ngoldbaum"><code>@​ngoldbaum</code></a> in <a href="">PyO3/maturin#3208</a></li>
<li>Add support for finding free-threaded interpreters for --find-interpreters by <a href="https://github.com/ngoldbaum"><code>@​ngoldbaum</code></a> in <a href="">PyO3/maturin#3206</a></li>
<li>build(deps): bump tar from 0.4.45 to 0.4.46 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">PyO3/maturin#3209</a></li>
<li>Stubs: also generate them for mixed PyO3 projects by <a href="https://github.com/Tpt"><code>@​Tpt</code></a> in <a href="">PyO3/maturin#3211</a></li>
<li>Don't depend on CFFI on PyPy by <a href="https://github.com/ngoldbaum"><code>@​ngoldbaum</code></a> in <a href="">PyO3/maturin#3213</a></li>
<li>resolve_platform_tags: remove a redundant case by <a href="https://github.com/Tpt"><code>@​Tpt</code></a> in <a href="">PyO3/maturin#3214</a></li>
<li>GeneratorOutput::additional_files remove Option by <a href="https://github.com/Tpt"><code>@​Tpt</code></a> in <a href="">PyO3/maturin#3215</a></li>
<li>Support pyo3 abi3t features on Python3.15 and PyO3 0.29 by <a href="https://github.com/ngoldbaum"><code>@​ngoldbaum</code></a> in <a href="">PyO3/maturin#3113</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/GuYeying"><code>@​GuYeying</code></a> made their first contribution in <a href="">PyO3/maturin#3202</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/PyO3/maturin/compare/v1.13.3...v1.14.0">https://github.com/PyO3/maturin/compare/v1.13.3...v1.14.0</a></p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/PyO3/maturin/blob/main/Changelog.md">maturin's changelog</a>.</em></p>
<blockquote>
<h2>1.14.0</h2>
<ul>
<li>Support parent-relative pyproject metadata in sdists (<a href="">#3182</a>)</li>
<li>Update PyPI platform tag validation (<a href="">#3187</a>)</li>
<li>Maint: update setup emsdk action in generate-ci (<a href="">#3194</a>)</li>
<li>Fix: only shim bin wheels during auditwheel repair (<a href="">#3197</a>)</li>
<li>Fix: avoid editable ELF truncation from stale hardlinks (<a href="">#3199</a>)</li>
<li>Fix Pyodide Emscripten platform tags (<a href="">#3191</a>)</li>
<li>Use pax instead of GNU headers for tar (<a href="">#3203</a>)</li>
<li>Feat: add default exclude <code>__pycache__</code> and <code>*.pyc</code> files (<a href="">#3202</a>)</li>
<li>Add support for finding free-threaded interpreters for <code>--find-interpreters</code> (<a href="">#3206</a>)</li>
<li>Stubs: also generate them for mixed PyO3 projects (<a href="">#3211</a>)</li>
<li>Don't depend on CFFI on PyPy (<a href="">#3213</a>)</li>
<li>Support pyo3 abi3t features on Python3.15 and PyO3 0.29 (<a href="">#3113</a>)</li>
</ul>
<h2>1.13.3</h2>
<ul>
<li>Fix: disable abi3 in pyo3 config for version-specific fallback builds (<a href="">#3180</a>)</li>
</ul>
<h2>1.13.2</h2>
<ul>
<li>Fix: resolve test failures in distro packaging environments (<a href="">#3129</a>)</li>
<li>Fix: redirect tracing output to stderr to avoid breaking PEP 517 (<a href="">#3131</a>)</li>
<li>Fix: skip interpreters with empty output for WSL2 cross-compile (<a href="">#3137</a>)</li>
<li>Fix: set explicit lib_name in pyo3 config for Android abi3 cross-compilation (<a href="">#3130</a>)</li>
<li>Chore: add sysconfig/cpython-freebsd-15.0-amd64.txt (<a href="">#3140</a>)</li>
<li>Quote python-version in generated GitHub Actions workflow</li>
<li>Update rustls-webpki</li>
<li>Fix: two-phase bridge detection for conditional abi3 features (<a href="">#3144</a>)</li>
<li>Update cargo-zigbuild to 0.22.2</li>
<li>Update pyo3 to 0.28.3</li>
<li>Treat pyo3 0.29.0+ as having Windows import lib support (raw-dylib) (<a href="">#3145</a>)</li>
<li>Fix bin bindings with external shared library dependencies (<a href="">#3147</a>)</li>
<li>Upgrade MSRV to 1.89.0 (<a href="">#3149</a>)</li>
<li>Musllinux oci image (<a href="">#3152</a>)</li>
<li>Remove Cirrus CI for FreeBSD (<a href="">#3156</a>)</li>
<li>Perf: defer stage_artifact copy-back, finalize via rename when unpatched (<a href="">#3155</a>)</li>
<li>Perf: eliminate stage_artifact double-copy, drop was_patched flag (<a href="">#3157</a>)</li>
<li>Fix release pipeline (<a href="">#3158</a>)</li>
<li>Auditwheel: copy unpatched cargo output back before in-place patching (<a href="">#3159</a>)</li>
<li>Develop: fail loudly when pip leaves a stale <code>~</code> install behind (<a href="">#1922</a>) (<a href="">#3161</a>)</li>
<li>Provide a link for the <code>lib.name</code> in Cargo.toml (<a href="">#3167</a>)</li>
<li>Fix duplicated version in changelog (<a href="">#3171</a>)</li>
<li>Switch to actions/attest from attest-build-provenance (<a href="">#3169</a>)</li>
<li>Switch generation to actions/attest action, upgrade to v4 (<a href="">#3170</a>)</li>
<li>Fix: avoid duplicate <code>--interpreter</code> panic in PEP 517 backend (<a href="">#3175</a>)</li>
<li>Add trusted publishing options to <code>generate-ci</code> (<a href="">#3176</a>)</li>
<li>Fix(sdist): handle symlinked <code>Cargo.toml</code> pointing outside project root (<a href="">#3178</a>)</li>
<li>Stop install cffi for Python 3.8 in Dockerfile</li>
<li>Fix: support pixi-managed virtualenvs in maturin develop (<a href="">#3165</a>)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>eb745e0</code></a> Release v1.14.0</li>
<li><a href=""><code>6cdd0aa</code></a> fix cargo fmt</li>
<li><a href=""><code>e18aba6</code></a> Support pyo3 abi3t features on Python3.15 and PyO3 0.29 (<a href="">#3113</a>)</li>
<li><a href=""><code>8786c59</code></a> [pre-commit.ci] pre-commit autoupdate (<a href="">#3217</a>)</li>
<li><a href=""><code>c76018b</code></a> GeneratorOutput::additional_files remove Option (<a href="">#3215</a>)</li>
<li><a href=""><code>a493701</code></a> resolve_platform_tags: remove a redundant case (<a href="">#3214</a>)</li>
<li><a href=""><code>7fb5648</code></a> Don't depend on CFFI on PyPy (<a href="">#3213</a>)</li>
<li><a href=""><code>ea07638</code></a> Stubs: also generate them for mixed PyO3 projects (<a href="">#3211</a>)</li>
<li><a href=""><code>2770b0d</code></a> build(deps): bump tar from 0.4.45 to 0.4.46 (<a href="">#3209</a>)</li>
<li><a href=""><code>96198a8</code></a> [pre-commit.ci] pre-commit autoupdate (<a href="">#3210</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/pyo3/maturin/compare/v1.0.0...v1.14.0">compare view</a></li>
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5fc4ef01023f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
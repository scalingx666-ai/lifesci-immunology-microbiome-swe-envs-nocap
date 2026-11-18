# Issue

**Title:** Build(deps): Update maturin requirement from <1.9.0,>=1 to >=1,<1.10.0

## Description

Updates the requirements on [maturin](https://github.com/pyo3/maturin) to permit the latest version.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/pyo3/maturin/releases">maturin's releases</a>.</em></p>
<blockquote>
<h2>v1.9.0</h2>
<h2>What's Changed</h2>
<ul>
<li>Update pyproject-toml to 0.13.5 by <a href="https://github.com/konstin"><code>@​konstin</code></a> in <a href="">PyO3/maturin#2645</a></li>
<li>Fix clippy lints by <a href="https://github.com/konstin"><code>@​konstin</code></a> in <a href="">PyO3/maturin#2648</a></li>
<li><code>ZipWriter</code> requires a compression level of <code>None</code> for the <code>stored</code> method by <a href="https://github.com/jatoben"><code>@​jatoben</code></a> in <a href="">PyO3/maturin#2644</a></li>
<li>Implement PEP 639 Support by <a href="https://github.com/konstin"><code>@​konstin</code></a> in <a href="">PyO3/maturin#2647</a></li>
<li>Don't go through Display for platform tag to policy by <a href="https://github.com/konstin"><code>@​konstin</code></a> in <a href="">PyO3/maturin#2652</a></li>
<li>Add <code>--compatibility pypi</code> to avoid building for unsupported architectures by <a href="https://github.com/konstin"><code>@​konstin</code></a> in <a href="">PyO3/maturin#2650</a></li>
<li>Fix self bootstrap without Rust installed by <a href="https://github.com/messense"><code>@​messense</code></a> in <a href="">PyO3/maturin#2653</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/jatoben"><code>@​jatoben</code></a> made their first contribution in <a href="">PyO3/maturin#2644</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/PyO3/maturin/compare/v1.8.7...v1.9.0">https://github.com/PyO3/maturin/compare/v1.8.7...v1.9.0</a></p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/PyO3/maturin/blob/main/Changelog.md">maturin's changelog</a>.</em></p>
<blockquote>
<h2>[1.9.0]</h2>
<ul>
<li>Add full PEP 639 support for <code>project.license</code> and <code>project.license-files</code> in <a href="">#2647</a>.</li>
<li>Add <code>--compatiblity pypi</code> to only build wheels with platform tags that can also be uploaded to PyPI. This blocks e.g. building for riscv64, which is supported by manylinux, but not by PyPI.</li>
</ul>
<h2>[1.8.7]</h2>
<ul>
<li>Allow specifying compression method and level, in both <code>build</code> and <code>develop</code> modes, in <a href="">#2625</a>.</li>
<li>Fix Windows free-threaded builds on Python 3.14 in <a href="">#2632</a></li>
</ul>
<h2>[1.8.6]</h2>
<ul>
<li>Print a message when overriding platform tag from <code>_PYTHON_HOST_PLATFORM</code> in <a href="">#2594</a></li>
<li>Use the current python interpreter's version when the abi3 feature is set with no explicit version in <a href="">#2597</a></li>
</ul>
<h2>[1.8.5]</h2>
<ul>
<li>Fix release CI build</li>
</ul>
<h2>[1.8.4]</h2>
<ul>
<li>Install a Rust toolchain into a temporary directory when building maturin itself or a package and a Rust toolchain is
missing. Set <code>MATURIN_NO_INSTALL_RUST</code> to disable this behavior. <a href="">#2421</a></li>
<li>Fix broken <code>maturin develop</code> with latest uv in <a href="">#2584</a></li>
<li>Add <code>PYO3_PYTHON</code> env var support in <a href="">#2534</a></li>
<li>Sort RECORD file in wheel archives to make them deterministic in <a href="">#2550</a></li>
<li>Publish wheel for loongarch64 in <a href="">#2548</a></li>
<li>Add --compression-level option to build command in <a href="">#2572</a></li>
</ul>
<h2>[1.8.3]</h2>
<ul>
<li>Fix relocating shared library for namespace modules in <a href="">#2513</a></li>
<li>Don't install dependencies when running <code>maturin develop --skip-install</code> in <a href="">#2504</a></li>
<li>Use emcc.bat to query version on Windows in <a href="">#2478</a></li>
<li>Bump the attest-build-provenance version in the generated ci file in <a href="">#2484</a></li>
<li>Fix platform tag on Solaris/Illumos in <a href="">#2483</a></li>
<li>Fix cargo run uniffi-bindgen when cross compiling in <a href="">#2476</a></li>
</ul>
<h2>[1.8.2]</h2>
<ul>
<li>Exclude packages not in the dependency tree when finding bindings in <a href="">#2426</a></li>
<li>Use uv automatically when running maturin develop inside uv-created virtualenv in <a href="">#2433</a></li>
<li>Consider abi3 minor version when resolving Python interpreters in <a href="">#2437</a></li>
<li>Handle archived dylibs on AIX in <a href="">#2442</a></li>
<li>Fix unnecessary rebuilds due to pyo3 config file modified time change in <a href="">#2446</a></li>
<li>Fix the name of the .data directory in the generated wheel in <a href="">#2449</a></li>
<li>Update minimal manylinux version for loongarch64 in <a href="">#2451</a></li>
</ul>
<h2>[1.8.1]</h2>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>46dbaff</code></a> Release v1.9.0 (<a href="">#2657</a>)</li>
<li><a href=""><code>2543958</code></a> Install python3.13t on Windows before building free-threaded wheels in genera...</li>
<li><a href=""><code>4e58964</code></a> Fix self bootstrap without Rust installed (<a href="">#2653</a>)</li>
<li><a href=""><code>ea5adfc</code></a> Add <code>--compatibility pypi</code> to avoid building for unsupported architectures (#...</li>
<li><a href=""><code>cee86ff</code></a> Don't go through Display for platform tag to policy (<a href="">#2652</a>)</li>
<li><a href=""><code>a0ae4e8</code></a> Fix changelog entry for <a href="">#2647</a></li>
<li><a href=""><code>3707717</code></a> Implement PEP 639 Support (<a href="">#2647</a>)</li>
<li><a href=""><code>800fb6a</code></a> <code>ZipWriter</code> requires a compression level of <code>None</code> for the <code>stored</code> method (#...</li>
<li><a href=""><code>e0c499f</code></a> Fix clippy lints (<a href="">#2648</a>)</li>
<li><a href=""><code>1cbf263</code></a> Update pyproject-toml to 0.13.5 (<a href="">#2645</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/pyo3/maturin/compare/v1.0.0...v1.9.0">compare view</a></li>
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
- `@dependabot ignore this major version` will close this PR and stop Dependabot creating any more for this major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this minor version` will close this PR and stop Dependabot creating any more for this minor version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0c847750a722`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
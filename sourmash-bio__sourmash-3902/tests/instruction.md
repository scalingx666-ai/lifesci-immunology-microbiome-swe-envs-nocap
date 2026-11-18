# Issue

**Title:** Build(deps-py): Update maturin requirement from <1.12.0,>=1 to >=1,<1.13.0 in the dependencies group

## Description

[//]: # (dependabot-start)
⚠️  **Dependabot is rebasing this PR** ⚠️

Rebasing might not happen immediately, so don't worry if this takes some time.

Note: if you make any changes to this PR yourself, they will take precedence over the rebase.

---

[//]: # (dependabot-end)

[//]: # (dependabot-start)
⚠️  **Dependabot is rebasing this PR** ⚠️

Rebasing might not happen immediately, so don't worry if this takes some time.

Note: if you make any changes to this PR yourself, they will take precedence over the rebase.

---

[//]: # (dependabot-end)

[//]: # (dependabot-start)
⚠️  **Dependabot is rebasing this PR** ⚠️

Rebasing might not happen immediately, so don't worry if this takes some time.

Note: if you make any changes to this PR yourself, they will take precedence over the rebase.

---

[//]: # (dependabot-end)

[//]: # (dependabot-start)
⚠️  **Dependabot is rebasing this PR** ⚠️

Rebasing might not happen immediately, so don't worry if this takes some time.

Note: if you make any changes to this PR yourself, they will take precedence over the rebase.

---

[//]: # (dependabot-end)

[//]: # (dependabot-start)
⚠️  **Dependabot is rebasing this PR** ⚠️

Rebasing might not happen immediately, so don't worry if this takes some time.

Note: if you make any changes to this PR yourself, they will take precedence over the rebase.

---

[//]: # (dependabot-end)

[//]: # (dependabot-start)
⚠️  **Dependabot is rebasing this PR** ⚠️

Rebasing might not happen immediately, so don't worry if this takes some time.

Note: if you make any changes to this PR yourself, they will take precedence over the rebase.

---

[//]: # (dependabot-end)

Updates the requirements on [maturin](https://github.com/pyo3/maturin) to permit the latest version.
Updates `maturin` to 1.12.2
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/pyo3/maturin/releases">maturin's releases</a>.</em></p>
<blockquote>
<h2>v1.12.2</h2>
<h2>What's Changed</h2>
<ul>
<li>fix: allow absolute paths for <code>--sbom-include</code> by <a href="https://github.com/messense"><code>@​messense</code></a> in <a href="">PyO3/maturin#3004</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/PyO3/maturin/compare/v1.12.1...v1.12.2">https://github.com/PyO3/maturin/compare/v1.12.1...v1.12.2</a></p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/PyO3/maturin/blob/main/Changelog.md">maturin's changelog</a>.</em></p>
<blockquote>
<h2>1.12.2</h2>
<ul>
<li>Fix: allow absolute paths for <code>--sbom-include</code> (<a href="">#3004</a>)</li>
</ul>
<h2>1.12.1</h2>
<ul>
<li>Replace addnab/docker-run-action with direct docker run command</li>
<li>Add <code>--sbom-include</code> CLI argument for additional SBOM files (<a href="">#2999</a>)</li>
<li>Fix: resolve include patterns relative to python-source for sdist and wheel (<a href="">#3000</a>)</li>
<li>Feat: log external shared libraries and their dependents before patchelf</li>
<li>Feat: support including <code>OUT_DIR</code> assets in wheel builds (<a href="">#3001</a>)</li>
<li>Add test case for uniffi with multiple crates (<a href="">#2839</a>)</li>
</ul>
<h2>1.12.0</h2>
<ul>
<li>Use pypi compatibility validation for own CI (<a href="">#2929</a>)</li>
<li>Update toml crates for toml 1.1 support (<a href="">#2934</a>)</li>
<li>Use a single location for MSRV (<a href="">#2936</a>)</li>
<li>Fix editable install for binary projects with Python modules (<a href="">#2938</a>)</li>
<li>Release to crates.io only after the builds passed (<a href="">#2939</a>)</li>
<li>Use <code>mymindstorm/setup-emsdk@v14</code> in generated GitHub Actions workflow (<a href="">#2941</a>)</li>
<li>Use trusted publishing for crates.io (<a href="">#2943</a>)</li>
<li>Filter linked_paths by KIND and linked_libs (<a href="">#2949</a>)</li>
<li>Update bytes to 1.11.1 (<a href="">#2960</a>)</li>
<li>Normalize wheel distribution names to match the PyPA spec (<a href="">#2954</a>)</li>
<li>Allow build loongarch64 and riscv64 for musllinux (<a href="">#2963</a>)</li>
<li>Strip excluded cargo targets in sdist (<a href="">#2964</a>)</li>
<li>Normalize wheel <code>RECORD</code> paths (on Windows) (<a href="">#2965</a>)</li>
<li>Bump MSRV to 1.88.0 (<a href="">#2966</a>)</li>
<li>Support MATURIN_STRIP env var and --strip true/false to override pyproject.toml (<a href="">#2968</a>)</li>
<li>Fix: copy bin artifacts before auditwheel repair to avoid rerun failures (<a href="">#2969</a>)</li>
<li>Fix: rewrite python-source in pyproject.toml when building sdist (<a href="">#2972</a>)</li>
<li>Fix: resolve wheel include patterns relative to project root (<a href="">#2973</a>)</li>
<li>Fix: always include workspace Cargo.toml in sdist (<a href="">#2974</a>)</li>
<li>Refactor: simplify source_distribution.rs (<a href="">#2976</a>)</li>
<li>Feat: support PEP 735 dependency groups in develop command (<a href="">#2978</a>)</li>
<li>Fix license file handling for workspace-level license files (<a href="">#2970</a>)</li>
<li>Support PEP 739 build-details.json when cross compiling (<a href="">#2979</a>)</li>
<li>Fix .libs directory name for namespace packages (<a href="">#2981</a>)</li>
<li>Fix: exclude duplicate python source files from sdist for workspace members (<a href="">#2982</a>)</li>
<li>Fix: remove default-members from workspace Cargo.toml in sdist (<a href="">#2983</a>)</li>
<li>Fix: correctly filter workspace members in sdist by directory path (<a href="">#2984</a>)</li>
<li>Feat: Add PEP 770 SBOM support (<a href="">#2980</a>)</li>
<li>Error when python-source is set but Python module is missing (<a href="">#2986</a>)</li>
<li>Feat: add auditwheel SBOM for grafted shared libraries (<a href="">#2985</a>)</li>
<li>Fix sdist duplicate README error when readme is in both Cargo.toml and pyproject.toml (<a href="">#2987</a>)</li>
<li>Fix: support python-source pointing outside Rust source directory (<a href="">#2988</a>)</li>
<li>Relax ziglang dependency version requirement (<a href="">#2990</a>)</li>
<li>Stop adding link-native-libraries flag by default in Emscripten platform in latest Rust (<a href="">#2991</a>)</li>
<li>Fix docker build github workflow</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>adb2906</code></a> Release v1.12.2</li>
<li><a href=""><code>6473568</code></a> fix: allow absolute paths for <code>--sbom-include</code> (<a href="">#3004</a>)</li>
<li><a href=""><code>e772489</code></a> Release v1.12.1</li>
<li><a href=""><code>0672082</code></a> add test case for uniffi with multiple crates (<a href="">#2839</a>)</li>
<li><a href=""><code>f201566</code></a> feat: support including <code>OUT_DIR</code> assets in wheel builds (<a href="">#3001</a>)</li>
<li><a href=""><code>66b4869</code></a> feat: log external shared libraries and their dependents before patchelf</li>
<li><a href=""><code>8f8f9f7</code></a> fix: resolve include patterns relative to python-source for sdist and wheel (...</li>
<li><a href=""><code>1688a73</code></a> netlify: update mdbook to 0.5.2</li>
<li><a href=""><code>aefe09d</code></a> Add <code>--sbom-include</code> CLI argument for additional SBOM files (<a href="">#2999</a>)</li>
<li><a href=""><code>8a688ca</code></a> Document SBOM support in user guide</li>
<li>Additional commits viewable in <a href="https://github.com/pyo3/maturin/compare/v1.0.0...v1.12.2">compare view</a></li>
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `959d9ca51a4a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
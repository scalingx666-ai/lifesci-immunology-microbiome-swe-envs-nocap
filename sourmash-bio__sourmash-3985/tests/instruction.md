# Issue

**Title:** Build(deps-py): Update maturin requirement from <1.15.0,>=1 to >=1,<1.16.0 in the dependencies group across 1 directory

## Description

Updates the requirements on [maturin](https://github.com/pyo3/maturin) to permit the latest version.
Updates `maturin` to 1.15.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/pyo3/maturin/releases">maturin's releases</a>.</em></p>
<blockquote>
<h2>v1.15.0</h2>
<h2>What's Changed</h2>
<ul>
<li>set <code>UV_PYTHON</code> when running <code>maturin develop</code> with uv by <a href="https://github.com/davidhewitt"><code>@​davidhewitt</code></a> in <a href="">PyO3/maturin#3236</a></li>
<li>Set UID and GID headers in pax by <a href="https://github.com/konstin"><code>@​konstin</code></a> in <a href="">PyO3/maturin#3241</a></li>
<li>[pre-commit.ci] pre-commit autoupdate by <a href="https://github.com/pre-commit-ci"><code>@​pre-commit-ci</code></a>[bot] in <a href="">PyO3/maturin#3238</a></li>
<li>Replace unguarded panics with explicit errors on fallible input by <a href="https://github.com/messense"><code>@​messense</code></a> in <a href="">PyO3/maturin#3242</a></li>
<li>Harden PEP 517 build-wheel and fix unreachable OIDC 404 fallback by <a href="https://github.com/messense"><code>@​messense</code></a> in <a href="">PyO3/maturin#3244</a></li>
<li>docs: add pdfcrate and quebec to examples by <a href="https://github.com/ratazzi"><code>@​ratazzi</code></a> in <a href="">PyO3/maturin#3245</a></li>
<li>Fix abi3t PyModExport entrypoint check by <a href="https://github.com/messense"><code>@​messense</code></a> in <a href="">PyO3/maturin#3246</a></li>
<li>[pre-commit.ci] pre-commit autoupdate by <a href="https://github.com/pre-commit-ci"><code>@​pre-commit-ci</code></a>[bot] in <a href="">PyO3/maturin#3247</a></li>
<li>fix <code>maturin build --pgo -i &lt;version&gt;</code> with <code>uv</code> install by <a href="https://github.com/davidhewitt"><code>@​davidhewitt</code></a> in <a href="">PyO3/maturin#3237</a></li>
<li>refactor: apply some mechanical cleanups by <a href="https://github.com/messense"><code>@​messense</code></a> in <a href="">PyO3/maturin#3250</a></li>
<li>refactor: BuildOrchestrator pipeline deduplication by <a href="https://github.com/messense"><code>@​messense</code></a> in <a href="">PyO3/maturin#3251</a></li>
<li>refactor: improve context and environment hygiene by <a href="https://github.com/messense"><code>@​messense</code></a> in <a href="">PyO3/maturin#3252</a></li>
<li>fix(ci): honor ~= and ==X.* in requires-python for generate-ci by <a href="https://github.com/teddytennant"><code>@​teddytennant</code></a> in <a href="">PyO3/maturin#3249</a></li>
<li>refactor: type cleanup for options, tags, and wheel metadata by <a href="https://github.com/messense"><code>@​messense</code></a> in <a href="">PyO3/maturin#3253</a></li>
<li>refactor: InstallDest, single BridgeModel, and ui output facade by <a href="https://github.com/messense"><code>@​messense</code></a> in <a href="">PyO3/maturin#3254</a></li>
<li>Don’t specify generate-import-lib for PyO3 0.29 by <a href="https://github.com/musicinmybrain"><code>@​musicinmybrain</code></a> in <a href="">PyO3/maturin#3258</a></li>
<li>[pre-commit.ci] pre-commit autoupdate by <a href="https://github.com/pre-commit-ci"><code>@​pre-commit-ci</code></a>[bot] in <a href="">PyO3/maturin#3259</a></li>
<li>ci: fix clippy errors on rust 1.97 by <a href="https://github.com/davidhewitt"><code>@​davidhewitt</code></a> in <a href="">PyO3/maturin#3263</a></li>
<li>refactor build so that pgo is part of normal pathway by <a href="https://github.com/davidhewitt"><code>@​davidhewitt</code></a> in <a href="">PyO3/maturin#3257</a></li>
<li>fix: verify bindings detection with cargo tree in workspaces by <a href="https://github.com/messense"><code>@​messense</code></a> in <a href="">PyO3/maturin#3264</a></li>
<li>fix: harden cargo tree verification of bindings detection by <a href="https://github.com/messense"><code>@​messense</code></a> in <a href="">PyO3/maturin#3266</a></li>
<li>ci: cut test wall time without losing coverage by <a href="https://github.com/messense"><code>@​messense</code></a> in <a href="">PyO3/maturin#3267</a></li>
<li>test: share cargo target dirs per fixture family by <a href="https://github.com/messense"><code>@​messense</code></a> in <a href="">PyO3/maturin#3268</a></li>
<li>ci: cut fixed setup overhead in test jobs by <a href="https://github.com/messense"><code>@​messense</code></a> in <a href="">PyO3/maturin#3269</a></li>
<li>feat: support --pgo for maturin develop by <a href="https://github.com/messense"><code>@​messense</code></a> in <a href="">PyO3/maturin#3270</a></li>
<li>feat: support MATURIN_PGO env var to activate --pgo by <a href="https://github.com/messense"><code>@​messense</code></a> in <a href="">PyO3/maturin#3271</a></li>
<li>[pre-commit.ci] pre-commit autoupdate by <a href="https://github.com/pre-commit-ci"><code>@​pre-commit-ci</code></a>[bot] in <a href="">PyO3/maturin#3272</a></li>
<li>feat: type the bindings input with a single-source-of-truth enum by <a href="https://github.com/messense"><code>@​messense</code></a> in <a href="">PyO3/maturin#3273</a></li>
<li>Don't force export of the PyInit_{module_name} in UniFfi mode by <a href="https://github.com/badboy"><code>@​badboy</code></a> in <a href="">PyO3/maturin#3275</a></li>
<li>[pre-commit.ci] pre-commit autoupdate by <a href="https://github.com/pre-commit-ci"><code>@​pre-commit-ci</code></a>[bot] in <a href="">PyO3/maturin#3279</a></li>
<li>switch musllinux images to musllinux_1_2 as musllinux_1_1 is EOL by <a href="https://github.com/Joshix-1"><code>@​Joshix-1</code></a> in <a href="">PyO3/maturin#3280</a></li>
<li>fix(generate-stubs): write stubs into the module's package directory by <a href="https://github.com/jonasdedden"><code>@​jonasdedden</code></a> in <a href="">PyO3/maturin#3282</a></li>
<li>[pre-commit.ci] pre-commit autoupdate by <a href="https://github.com/pre-commit-ci"><code>@​pre-commit-ci</code></a>[bot] in <a href="">PyO3/maturin#3286</a></li>
<li>Fix group not cwd by <a href="https://github.com/kraktus"><code>@​kraktus</code></a> in <a href="">PyO3/maturin#3284</a></li>
<li>docs: document missing [tool.maturin] config fields by <a href="https://github.com/teddytennant"><code>@​teddytennant</code></a> in <a href="">PyO3/maturin#3287</a></li>
<li>[pre-commit.ci] pre-commit autoupdate by <a href="https://github.com/pre-commit-ci"><code>@​pre-commit-ci</code></a>[bot] in <a href="">PyO3/maturin#3288</a></li>
<li>docs: fix cross compiling heading level by <a href="https://github.com/BD103"><code>@​BD103</code></a> in <a href="">PyO3/maturin#3290</a></li>
<li>[pre-commit.ci] pre-commit autoupdate by <a href="https://github.com/pre-commit-ci"><code>@​pre-commit-ci</code></a>[bot] in <a href="">PyO3/maturin#3292</a></li>
<li>Release v1.15.0 by <a href="https://github.com/messense"><code>@​messense</code></a> in <a href="">PyO3/maturin#3294</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/ratazzi"><code>@​ratazzi</code></a> made their first contribution in <a href="">PyO3/maturin#3245</a></li>
<li><a href="https://github.com/teddytennant"><code>@​teddytennant</code></a> made their first contribution in <a href="">PyO3/maturin#3249</a></li>
<li><a href="https://github.com/jonasdedden"><code>@​jonasdedden</code></a> made their first contribution in <a href="">PyO3/maturin#3282</a></li>
<li><a href="https://github.com/kraktus"><code>@​kraktus</code></a> made their first contribution in <a href="">PyO3/maturin#3284</a></li>
<li><a href="https://github.com/BD103"><code>@​BD103</code></a> made their first contribution in <a href="">PyO3/maturin#3290</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/PyO3/maturin/compare/v1.14.1...v1.15.0">https://github.com/PyO3/maturin/compare/v1.14.1...v1.15.0</a></p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/PyO3/maturin/blob/main/Changelog.md">maturin's changelog</a>.</em></p>
<blockquote>
<h2>1.15.0</h2>
<ul>
<li>Set <code>UV_PYTHON</code> when running <code>maturin develop</code> with uv (<a href="">#3236</a>)</li>
<li>Set UID and GID headers in pax (<a href="">#3241</a>)</li>
<li>Replace unguarded panics with explicit errors on fallible input (<a href="">#3242</a>)</li>
<li>Harden PEP 517 build-wheel and fix unreachable OIDC 404 fallback (<a href="">#3244</a>)</li>
<li>Fix abi3t PyModExport entrypoint check (<a href="">#3246</a>)</li>
<li>Fix <code>maturin build --pgo -i &lt;version&gt;</code> with <code>uv</code> install (<a href="">#3237</a>)</li>
<li>Refactor: apply some mechanical cleanups (<a href="">#3250</a>)</li>
<li>Refactor: BuildOrchestrator pipeline deduplication (<a href="">#3251</a>)</li>
<li>Refactor: improve context and environment hygiene (<a href="">#3252</a>)</li>
<li>Fix(ci): honor ~= and ==X.* in requires-python for generate-ci (<a href="">#3249</a>)</li>
<li>Refactor: type cleanup for options, tags, and wheel metadata (<a href="">#3253</a>)</li>
<li>Refactor: InstallDest, single BridgeModel, and ui output facade (<a href="">#3254</a>)</li>
<li>Don’t specify generate-import-lib for PyO3 0.29 (<a href="">#3258</a>)</li>
<li>Refactor build so that pgo is part of normal pathway (<a href="">#3257</a>)</li>
<li>Fix: verify bindings detection with cargo tree in workspaces (<a href="">#3264</a>)</li>
<li>Fix: harden cargo tree verification of bindings detection (<a href="">#3266</a>)</li>
<li>Feat: support --pgo for maturin develop (<a href="">#3270</a>)</li>
<li>Feat: support <code>MATURIN_PGO</code> env var to activate --pgo (<a href="">#3271</a>)</li>
<li>Docs: correct crate feature documentation; remove stale clippy allow</li>
<li>Fix: deduplicate SBOM includes across full merged list, preserving first-seen order</li>
<li>Feat: type the bindings input with a single-source-of-truth enum (<a href="">#3273</a>)</li>
<li>Don't force export of the <code>PyInit_{module_name}</code> in UniFfi mode (<a href="">#3275</a>)</li>
<li>Switch musllinux images to <code>musllinux_1_2</code> as <code>musllinux_1_1</code> is EOL (<a href="">#3280</a>)</li>
<li>Fix(generate-stubs): write stubs into the module's package directory (<a href="">#3282</a>)</li>
<li>Fix group not cwd (<a href="">#3284</a>)</li>
<li>Docs: document missing [tool.maturin] config fields (<a href="">#3287</a>)</li>
<li>Update cargo-zigbuild &amp; cargo-xwin to 0.23.1</li>
</ul>
<h2>1.14.1</h2>
<ul>
<li>Bump uraimo/run-on-arch-action to v3 to fix pytest job (<a href="">#3221</a>)</li>
<li>Fix platform tag logic to generate the same as cpython on AIX (<a href="">#3220</a>)</li>
<li>Bump pyo3-introspection (<a href="">#3227</a>)</li>
<li>Upgrade cargo-zigbuild &amp; cargo-xwin (<a href="">#3228</a>)</li>
<li>Fix issues around crates enabling abi3 and abi3t features (<a href="">#3226</a>)</li>
<li>Add PEP 740 publish attestations to PyPI releases (<a href="">#3230</a>)</li>
<li>Set PYO3_PYTHON to run scripts for stable ABI builds (<a href="">#3233</a>)</li>
<li>Fix shell quoting in CI scripts (<a href="">#3231</a>)</li>
</ul>
<h2>1.14.0</h2>
<ul>
<li>Support parent-relative pyproject metadata in sdists (<a href="">#3182</a>)</li>
<li>Update PyPI platform tag validation (<a href="">#3187</a>)</li>
<li>Maint: update setup emsdk action in generate-ci (<a href="">#3194</a>)</li>
<li>Fix: only shim bin wheels during auditwheel repair (<a href="">#3197</a>)</li>
<li>Fix: avoid editable ELF truncation from stale hardlinks (<a href="">#3199</a>)</li>
<li>Fix Pyodide Emscripten platform tags (<a href="">#3191</a>)</li>
<li>Use pax instead of GNU headers for tar (<a href="">#3203</a>)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>479658a</code></a> Release v1.15.0 (<a href="">#3294</a>)</li>
<li><a href=""><code>dd7b95d</code></a> [pre-commit.ci] pre-commit autoupdate (<a href="">#3292</a>)</li>
<li><a href=""><code>35e9a4d</code></a> docs: fix cross compiling heading level (<a href="">#3290</a>)</li>
<li><a href=""><code>181c0b5</code></a> Update cargo-zigbuild &amp; cargo-xwin to 0.23.1</li>
<li><a href=""><code>a6743cd</code></a> [pre-commit.ci] pre-commit autoupdate (<a href="">#3288</a>)</li>
<li><a href=""><code>15c064a</code></a> docs: document missing [tool.maturin] config fields (<a href="">#3287</a>)</li>
<li><a href=""><code>c30aa84</code></a> Fix group not cwd (<a href="">#3284</a>)</li>
<li><a href=""><code>704b73b</code></a> Fix ruff check for ruff 0.16</li>
<li><a href=""><code>d81b8ce</code></a> [pre-commit.ci] pre-commit autoupdate (<a href="">#3286</a>)</li>
<li><a href=""><code>cf57dff</code></a> fix(generate-stubs): write stubs into the module's package directory (<a href="">#3282</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/pyo3/maturin/compare/v1.0.0...v1.15.0">compare view</a></li>
</ul>
</details>
<br />

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d603dbc2d64c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
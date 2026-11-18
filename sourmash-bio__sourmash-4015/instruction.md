# Issue

**Title:** Build(deps-rs): Bump the dependencies group with 2 updates

## Description

Bumps the dependencies group with 2 updates: [memmap2](https://github.com/RazrFalcon/memmap2-rs) and [codspeed-criterion-compat](https://github.com/CodSpeedHQ/codspeed-rust).

Updates `memmap2` from 0.9.11 to 0.9.12
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/RazrFalcon/memmap2-rs/blob/master/CHANGELOG.md">memmap2's changelog</a>.</em></p>
<blockquote>
<h2>[0.9.12] - 2026-10-21</h2>
<h3>Added</h3>
<ul>
<li>Add <code>MmapOptions::map_if_safe()</code> to allow creation read-only mappings of a file from safe code if the kernel can guarantee the file is immutable and large enough.
<a href="https://github.com/alexlarsson"><code>@​alexlarsson</code></a></li>
<li>Add <code>MmapOptions::no_probe_handle()</code> to disable probing of file handles on Windows to improve performance, at the cost of no longer being able to remap later with more capabilities.
<a href="https://github.com/mat-gas"><code>@​mat-gas</code></a></li>
<li>Add support for OpenHarmony targets (<code>*-unknown-linux-ohos</code>).
<a href="https://github.com/hiyms"><code>@​hiyms</code></a></li>
</ul>
<h3>Changed</h3>
<ul>
<li>Cache allocation granularity on Windows to prevent repeated syscalls.
<a href="https://github.com/mat-gas"><code>@​mat-gas</code></a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>4692b05</code></a> Merge pull request <a href="">#180</a> from RazrFalcon/release/v0.9.12</li>
<li><a href=""><code>9e5c0ee</code></a> Bump version to 0.9.12.</li>
<li><a href=""><code>b98035d</code></a> Merge pull request <a href="">#177</a> from JaskRendix/extract-test-suite</li>
<li><a href=""><code>0986677</code></a> Merge branch 'master' into extract-test-suite</li>
<li><a href=""><code>d26cc84</code></a> Fix map_if_safe() stub.</li>
<li><a href=""><code>145ee36</code></a> Silence clippy warning about trivial identical match arms.</li>
<li><a href=""><code>b402ef2</code></a> Fix check_safe_to_map() on Apple targets.</li>
<li><a href=""><code>b544238</code></a> Fix formatting.</li>
<li><a href=""><code>f50e480</code></a> Move tests to test/ folder.</li>
<li><a href=""><code>0994bf7</code></a> Merge pull request <a href="">#176</a> from hiyms/feat/support-ohos</li>
<li>Additional commits viewable in <a href="https://github.com/RazrFalcon/memmap2-rs/compare/v0.9.11...v0.9.12">compare view</a></li>
</ul>
</details>
<br />

Updates `codspeed-criterion-compat` from 5.0.3 to 6.0.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/CodSpeedHQ/codspeed-rust/releases">codspeed-criterion-compat's releases</a>.</em></p>
<blockquote>
<h2>v6.0.0</h2>
<p>CodSpeed for Rust 6.0.0 removes a source of measurement noise from your CPU Simulation benchmarks, so you can spend less time investigating unexpected changes in unrelated results.</p>
<h3>Highlights</h3>
<p>Your Divan and Criterion benchmarks now run in separate processes. Changes to one benchmark no longer carry allocator state into the benchmarks that follow it, improving consistency as your benchmark suite evolves.</p>
<p>Early results showed lower run-to-run variance, with roughly 70% fewer benchmarks varying by more than 1%.
No benchmark code changes required. Your WallTime results are unaffected.</p>
<h3>Breaking Changes</h3>
<ul>
<li>Some benchmark values may shift when you upgrade</li>
<li>Each benchmark adds small process startup overhead to the run</li>
</ul>
<p>Set <code>CODSPEED_PROCESS_ISOLATION=false</code> to revert to the previous behavior.</p>
<h2>What's Changed</h2>
<ul>
<li>fix(criterion): avoid duplicate setup in simulation iter_batched by <a href="https://github.com/not-matthias"><code>@​not-matthias</code></a> in <a href="">CodSpeedHQ/codspeed-rust#198</a></li>
<li>feat(divan): run each benchmark in its own process by <a href="https://github.com/not-matthias"><code>@​not-matthias</code></a> in <a href="">CodSpeedHQ/codspeed-rust#194</a></li>
<li>feat(codspeed): declare a Symposium plugin by <a href="https://github.com/adriencaccia"><code>@​adriencaccia</code></a> in <a href="">CodSpeedHQ/codspeed-rust#200</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/CodSpeedHQ/codspeed-rust/compare/v5.0.3...v6.0.0">https://github.com/CodSpeedHQ/codspeed-rust/compare/v5.0.3...v6.0.0</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>5caa8dc</code></a> Release 6.0.0</li>
<li><a href=""><code>a9d5d46</code></a> feat(codspeed): declare a Symposium plugin (<a href="">#200</a>)</li>
<li><a href=""><code>fce04a6</code></a> fix(criterion): send benchmark markers around iter_manual rounds</li>
<li><a href=""><code>fef0566</code></a> ci: time out the analysis integration tests</li>
<li><a href=""><code>3218867</code></a> test(divan): add allocator ripple benchmark</li>
<li><a href=""><code>9ee5ae0</code></a> test(cargo-codspeed): cover process isolation end to end</li>
<li><a href=""><code>5622bb3</code></a> feat(criterion): run each benchmark in its own process</li>
<li><a href=""><code>43916f8</code></a> feat(divan): run each benchmark in its own process</li>
<li><a href=""><code>06d80d9</code></a> feat(codspeed): add per-benchmark process isolation</li>
<li><a href=""><code>b250112</code></a> chore(codspeed): drop unused libc dependency</li>
<li>Additional commits viewable in <a href="https://github.com/CodSpeedHQ/codspeed-rust/compare/v5.0.3...v6.0.0">compare view</a></li>
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fbc0fea5eb13`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
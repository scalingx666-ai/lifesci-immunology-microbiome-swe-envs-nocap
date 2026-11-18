# Issue

**Title:** Build(ci): Bump CodSpeedHQ/action from 4 to 5

## Description

Bumps [CodSpeedHQ/action](https://github.com/codspeedhq/action) from 4 to 5.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/codspeedhq/action/releases">CodSpeedHQ/action's releases</a>.</em></p>
<blockquote>
<h2>v4.19.1</h2>
<h2>Release Notes</h2>
<p>This release ships improvements for the memory instrument.</p>
<p>The memory instrument now lazily attaches to allocators, which lowers the startup time to a few seconds (down from minutes on certain systems). Additionally, we shipped a series of serialization improvements, removing in some large benchmarks 3+ minutes of extra CI time.</p>
<h3><!-- raw HTML omitted -->🐛 Bug Fixes</h3>
<ul>
<li>Track successful posix_memalign allocations (<a href="">#470</a>) by <a href="https://github.com/not-matthias"><code>@​not-matthias</code></a> in <a href="">#470</a></li>
<li>Prompt sudo on interactive stdin (<a href="">#459</a>) by <a href="https://github.com/not-matthias"><code>@​not-matthias</code></a> in <a href="">#459</a></li>
<li>Reject empty command before executor setup (<a href="">#467</a>) by <a href="https://github.com/not-matthias"><code>@​not-matthias</code></a> in <a href="">#467</a></li>
</ul>
<h3><!-- raw HTML omitted -->⚙️ Internals</h3>
<ul>
<li>chore: bump runner version to 4.19.1 by <a href="https://github.com/github-actions"><code>@​github-actions</code></a>[bot] in <a href="">CodSpeedHQ/action#225</a></li>
</ul>
<h3><!-- raw HTML omitted -->💼 Other</h3>
<ul>
<li>Bump the memtrack pin to 1.3.0 by <a href="https://github.com/adriencaccia"><code>@​adriencaccia</code></a> in <a href="">#474</a></li>
</ul>
<h2>Install codspeed-runner 4.19.1</h2>
<h3>Install prebuilt binaries via shell script</h3>
<pre lang="sh"><code>curl --proto '=https' --tlsv1.2 -LsSf https://github.com/CodSpeedHQ/codspeed/releases/download/v4.19.1/codspeed-runner-installer.sh | sh
</code></pre>
<h2>Download codspeed-runner 4.19.1</h2>
<table>
<thead>
<tr>
<th>File</th>
<th>Platform</th>
<th>Checksum</th>
</tr>
</thead>
<tbody>
<tr>
<td><a href="https://github.com/CodSpeedHQ/codspeed/releases/download/v4.19.1/codspeed-runner-aarch64-apple-darwin.tar.gz">codspeed-runner-aarch64-apple-darwin.tar.gz</a></td>
<td>Apple Silicon macOS</td>
<td><a href="https://github.com/CodSpeedHQ/codspeed/releases/download/v4.19.1/codspeed-runner-aarch64-apple-darwin.tar.gz.sha256">checksum</a></td>
</tr>
<tr>
<td><a href="https://github.com/CodSpeedHQ/codspeed/releases/download/v4.19.1/codspeed-runner-aarch64-unknown-linux-musl.tar.gz">codspeed-runner-aarch64-unknown-linux-musl.tar.gz</a></td>
<td>ARM64 MUSL Linux</td>
<td><a href="https://github.com/CodSpeedHQ/codspeed/releases/download/v4.19.1/codspeed-runner-aarch64-unknown-linux-musl.tar.gz.sha256">checksum</a></td>
</tr>
<tr>
<td><a href="https://github.com/CodSpeedHQ/codspeed/releases/download/v4.19.1/codspeed-runner-x86_64-unknown-linux-musl.tar.gz">codspeed-runner-x86_64-unknown-linux-musl.tar.gz</a></td>
<td>x64 MUSL Linux</td>
<td><a href="https://github.com/CodSpeedHQ/codspeed/releases/download/v4.19.1/codspeed-runner-x86_64-unknown-linux-musl.tar.gz.sha256">checksum</a></td>
</tr>
</tbody>
</table>
<p><strong>Full Runner Changelog</strong>: <a href="https://github.com/CodSpeedHQ/codspeed/blob/main/CHANGELOG.md">https://github.com/CodSpeedHQ/codspeed/blob/main/CHANGELOG.md</a></p>
<p><strong>Full Changelog</strong>: <a href="https://github.com/CodSpeedHQ/action/compare/v4.19.0...v4.19.1">https://github.com/CodSpeedHQ/action/compare/v4.19.0...v4.19.1</a></p>
<h2>v4.19.0</h2>
<h2>Release Notes</h2>
<p>This release adds a new <code>--experimental-exclude-allocations</code> feature to remove allocator time from Simulation benchmarks.</p>
<h3><!-- raw HTML omitted -->🚀 Features</h3>
<ul>
<li>Remove eager allocator discovery by <a href="https://github.com/not-matthias"><code>@​not-matthias</code></a></li>
<li>Attach allocator probes on demand via exec-mapping watcher by <a href="https://github.com/not-matthias"><code>@​not-matthias</code></a></li>
<li>Add exec-mapping watcher BPF prog and inode maps by <a href="https://github.com/not-matthias"><code>@​not-matthias</code></a></li>
<li>Add experimental --exclude-allocations setting by <a href="https://github.com/not-matthias"><code>@​not-matthias</code></a></li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>373d686</code></a> Release v5.2.1 🚀</li>
<li><a href=""><code>5659c65</code></a> chore: bump runner version to 5.2.1 (<a href="">#236</a>)</li>
<li><a href=""><code>22d40ad</code></a> feat: add simulation-track-subprocess input (<a href="">#235</a>)</li>
<li><a href=""><code>47f7ceb</code></a> Release v5.2.0 🚀</li>
<li><a href=""><code>d9ce15a</code></a> chore: bump runner version to 5.2.0 (<a href="">#234</a>)</li>
<li><a href=""><code>994a9cf</code></a> chore: bump runner version to 5.1.0 (<a href="">#232</a>)</li>
<li><a href=""><code>15e6538</code></a> fix: add the distribution to the instruments cache key</li>
<li><a href=""><code>4296e51</code></a> Release v5.0.3 🚀</li>
<li><a href=""><code>271ae6a</code></a> chore: bump runner version to 5.0.2 (<a href="">#230</a>)</li>
<li><a href=""><code>0ca9cbb</code></a> Release v5.0.2 🚀</li>
<li>Additional commits viewable in <a href="https://github.com/codspeedhq/action/compare/v4...v5">compare view</a></li>
</ul>
</details>
<br />

> **Note**
> Automatic rebases have been disabled on this pull request as it has been open for over 30 days.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d603dbc2d64c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
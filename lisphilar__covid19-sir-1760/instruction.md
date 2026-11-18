# Issue

**Title:** build(deps-dev): bump pillow from 10.4.0 to 11.0.0

## Description

Bumps [pillow](https://github.com/python-pillow/Pillow) from 10.4.0 to 11.0.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/python-pillow/Pillow/releases">pillow's releases</a>.</em></p>
<blockquote>
<h2>11.0.0</h2>
<p><a href="https://pillow.readthedocs.io/en/stable/releasenotes/11.0.0.html">https://pillow.readthedocs.io/en/stable/releasenotes/11.0.0.html</a></p>
<h2>Changes</h2>
<ul>
<li>Do not create core image in TIFF seek() <a href="">#8392</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Removed custom build_openjpeg <a href="">#8365</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Support writing LONG8 offsets in AppendingTiffWriter <a href="">#8417</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Use ImageFile.MAXBLOCK when saving TIFF images <a href="">#8461</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Always raise warnings for deprecated feature checks <a href="">#8459</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Do not close provided file handles with libtiff when saving <a href="">#8458</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Revert &quot;Skip QEMU-emulated wheels on workflow dispatch event&quot; <a href="">#8455</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Support ImageFilter.BuiltinFilter for I;16* images <a href="">#8438</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>[pre-commit.ci] pre-commit autoupdate <a href="">#8448</a> [<a href="https://github.com/pre-commit-ci"><code>@​pre-commit-ci</code></a>]</li>
<li>Use ImagingCore.ptr instead of ImagingCore.id <a href="">#8341</a> [<a href="https://github.com/homm"><code>@​homm</code></a>]</li>
<li>Simplified code <a href="">#8445</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Removed unused code <a href="">#8447</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Updated EPS mode when opening images without transparency <a href="">#8281</a> [<a href="https://github.com/Yay295"><code>@​Yay295</code></a>]</li>
<li>Use transparency when combining P frames from APNGs <a href="">#8443</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Generate and upload attestations to PyPI <a href="">#8441</a> [<a href="https://github.com/hugovk"><code>@​hugovk</code></a>]</li>
<li>Do not convert images unnecessarily in ImageEnhance <a href="">#8431</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Raise an error if path is compacted during mapping <a href="">#8416</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Support all resampling filters when resizing I;16* images <a href="">#8422</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Free memory on early return <a href="">#8413</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Cast int before potentially exceeding INT_MAX <a href="">#8402</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Prevent division by zero <a href="">#8408</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Check image value before use <a href="">#8400</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Use ruff check <a href="">#8423</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Change harfbuzz versions in wheels <a href="">#8421</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Use Capsule for WebP saving <a href="">#8386</a> [<a href="https://github.com/homm"><code>@​homm</code></a>]</li>
<li>Fixed writing multiple StripOffsets to TIFF <a href="">#8317</a> [<a href="https://github.com/Yay295"><code>@​Yay295</code></a>]</li>
<li>Updated macOS deployment target for PyPy on Intel to 10.15 <a href="">#8414</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Fix dereference before checking for NULL in ImagingTransformAffine <a href="">#8398</a> [<a href="https://github.com/PavlNekrasov"><code>@​PavlNekrasov</code></a>]</li>
<li>Use transposed size after opening for TIFF images <a href="">#8390</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Improve ImageFont error messages <a href="">#8338</a> [<a href="https://github.com/yngvem"><code>@​yngvem</code></a>]</li>
<li>Mention MAX_TEXT_CHUNK limit in PNG error message <a href="">#8391</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Cast Dib handle to int <a href="">#8385</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Updated macOS deployment target for Python &gt;= 3.12 on Intel to 10.13 <a href="">#8379</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Removed unused ImagePath variable <a href="">#8377</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Change macos-14 to macos-latest <a href="">#8376</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Accept float stroke widths <a href="">#8369</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Remove comments <a href="">#8370</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Removed libffi-dev <a href="">#8368</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Improved handling of RGBA palettes when saving GIF images <a href="">#8366</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Support converting more modes to LAB by converting to RGBA first <a href="">#8358</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Optimize getbbox() and getextrema() routines <a href="">#8194</a> [<a href="https://github.com/homm"><code>@​homm</code></a>]</li>
<li>Removed unused TiffImagePlugin IFD_LEGACY_API <a href="">#8355</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
<li>Handle duplicate EXIF header <a href="">#8350</a> [<a href="https://github.com/zakajd"><code>@​zakajd</code></a>]</li>
<li>Use (void) for empty function parameters <a href="">#8002</a> [<a href="https://github.com/Yay295"><code>@​Yay295</code></a>]</li>
<li>Return early from BoxBlur if either width or height is zero <a href="">#8347</a> [<a href="https://github.com/radarhere"><code>@​radarhere</code></a>]</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/python-pillow/Pillow/blob/main/CHANGES.rst">pillow's changelog</a>.</em></p>
<blockquote>
<h2>11.0.0 (2024-10-15)</h2>
<ul>
<li>
<p>Update licence to MIT-CMU <a href="">#8460</a>
[hugovk]</p>
</li>
<li>
<p>Conditionally define ImageCms type hint to avoid requiring core <a href="">#8197</a>
[radarhere]</p>
</li>
<li>
<p>Support writing LONG8 offsets in AppendingTiffWriter <a href="">#8417</a>
[radarhere]</p>
</li>
<li>
<p>Use ImageFile.MAXBLOCK when saving TIFF images <a href="">#8461</a>
[radarhere]</p>
</li>
<li>
<p>Do not close provided file handles with libtiff when saving <a href="">#8458</a>
[radarhere]</p>
</li>
<li>
<p>Support ImageFilter.BuiltinFilter for I;16* images <a href="">#8438</a>
[radarhere]</p>
</li>
<li>
<p>Use ImagingCore.ptr instead of ImagingCore.id <a href="">#8341</a>
[homm, radarhere, hugovk]</p>
</li>
<li>
<p>Updated EPS mode when opening images without transparency <a href="">#8281</a>
[Yay295, radarhere]</p>
</li>
<li>
<p>Use transparency when combining P frames from APNGs <a href="">#8443</a>
[radarhere]</p>
</li>
<li>
<p>Support all resampling filters when resizing I;16* images <a href="">#8422</a>
[radarhere]</p>
</li>
<li>
<p>Free memory on early return <a href="">#8413</a>
[radarhere]</p>
</li>
<li>
<p>Cast int before potentially exceeding INT_MAX <a href="">#8402</a>
[radarhere]</p>
</li>
<li>
<p>Check image value before use <a href="">#8400</a>
[radarhere]</p>
</li>
<li>
<p>Improved copying imagequant libraries <a href="">#8420</a>
[radarhere]</p>
</li>
<li>
<p>Use Capsule for WebP saving <a href="">#8386</a>
[homm, radarhere]</p>
</li>
<li>
<p>Fixed writing multiple StripOffsets to TIFF <a href="">#8317</a>
[Yay295, radarhere]</p>
</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>204aae6</code></a> 11.0.0 version bump</li>
<li><a href=""><code>f2cc87b</code></a> Update CHANGES.rst [ci skip]</li>
<li><a href=""><code>c855e8e</code></a> Merge pull request <a href="">#8464</a> from radarhere/imagemath_type_hint</li>
<li><a href=""><code>dc37515</code></a> Merge pull request <a href="">#8463</a> from hugovk/update-3.13-date</li>
<li><a href=""><code>c3d81d6</code></a> Update Python 3.13 release date</li>
<li><a href=""><code>a60610c</code></a> Added type hints</li>
<li><a href=""><code>a5c58f2</code></a> Merge pull request <a href="">#8460</a> from hugovk/mit-cmu</li>
<li><a href=""><code>e74994e</code></a> Update licence to MIT-CMU</li>
<li><a href=""><code>b5e1115</code></a> Update CHANGES.rst [ci skip]</li>
<li><a href=""><code>686b5e2</code></a> Merge pull request <a href="">#8392</a> from radarhere/tiff_seek</li>
<li>Additional commits viewable in <a href="https://github.com/python-pillow/Pillow/compare/10.4.0...11.0.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=pillow&package-manager=pip&previous-version=10.4.0&new-version=11.0.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cb1c07f7e8b1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
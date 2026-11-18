# Issue

**Title:** build(deps): update loguru requirement from <0.8.0,>=0.7.2 to >=0.7.2,<0.9.0

## Description

Updates the requirements on [loguru](https://github.com/Delgan/loguru) to permit the latest version.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/Delgan/loguru/releases">loguru's releases</a>.</em></p>
<blockquote>
<h2>0.8.0</h2>
<ul>
<li>Change the default log format to include the timezone offset since it produces less ambiguous logs (<a href="">#856</a>, thanks <a href="https://github.com/tim-x-y-z"><code>@​tim-x-y-z</code></a>).</li>
<li>Add new <code>logger.reinstall()</code> method to automatically set up the <code>logger</code> in spawned child processes (<a href="">#818</a>, thanks <a href="https://github.com/monchin"><code>@​monchin</code></a>).</li>
<li>Add support for template strings used as log messages (<a href="">#1397</a>, thanks <a href="https://github.com/TurtleOrangina"><code>@​TurtleOrangina</code></a>).</li>
<li>Add <code>record[&quot;template&quot;]</code> that includes the raw, unformatted message (<a href="">#1349</a>, thanks <a href="https://github.com/sentrivana"><code>@​sentrivana</code></a>).</li>
<li>Fix incorrect microsecond value when formatting the log timestamp using <code>{time:x}</code> (<a href="">#1440</a>).</li>
<li>Fix parsing of 12-hour rotation times without seconds (<a href="">#1474</a>, thanks <a href="https://github.com/c-tonneslan"><code>@​c-tonneslan</code></a>).</li>
<li>Fix a <code>&quot;&lt;weekday&gt; at &lt;time&gt;&quot;</code> rotation firing its first rotation on the creation day instead of the requested weekday when the time of day was later than the creation time (<a href="">#1484</a>, thanks <a href="https://github.com/gaoflow"><code>@​gaoflow</code></a>).</li>
<li>Fix hex color short code expansion (<a href="">#1426</a>, thanks <a href="https://github.com/turkoid"><code>@​turkoid</code></a>).</li>
<li>Fix possible regular expression denial of service (ReDoS) when parsing color markups in strings containing long sequences of backslashes (<a href="">#1537</a>).</li>
<li>Fix possible internal error when dealing with (rare) frame objects missing a <code>f_lineno</code> value (<a href="">#1435</a>).</li>
<li>Fix a regression preventing formatting of <code>record[&quot;time&quot;]</code> when using <code>zoneinfo.ZoneInfo</code> timezones (<a href="">#1260</a>, thanks <a href="https://github.com/bijlpieter"><code>@​bijlpieter</code></a>).</li>
<li>Fix possible <code>ValueError</code> raised on Windows when system clock was set far ahead in the future (<a href="">#1291</a>).</li>
<li>Fix externally raised <code>Exception</code> possibly causing invalid state generating repeated <code>RuntimeError</code> of avoided deadlock (<a href="">#1335</a>).</li>
<li>Fix incorrect formatting of negative timezone offsets with sub-minute components (<a href="">#1500</a>).</li>
<li>Fix incorrect formatting of negative timestamps (<a href="">#1501</a>).</li>
<li>Fix incorrect thread and process identifiers of standard logging <code>Handler</code> records when using <code>enqueue=True</code> (<a href="">#1527</a>).</li>
<li>Fix <code>catch=True</code> being ignored for exceptions raised during sink termination, such as file retention or compression triggered by <code>logger.remove()</code> (<a href="">#1532</a>).</li>
<li>Fix <code>logger.parse()</code> decoding log files with the locale encoding instead of UTF-8 when given a path, which failed on non-ASCII logs written using the file sink default encoding on Windows (<a href="">#1540</a>).</li>
<li>Fix formatting of truncated <code>ExceptionGroup</code> errors, which used a plural for a single remaining exception and could miss the closing ruler (<a href="">#1541</a>, thanks <a href="https://github.com/JeremyL691"><code>@​JeremyL691</code></a>).</li>
<li>Respect the <code>.level</code> attribute of standard logging <code>Handler</code> used as sink, which was previously ignored (<a href="">#1409</a>).</li>
<li>Allow the <code>rotation</code> argument of file sinks to accept a list of rotation conditions, any of which can trigger the rotation (<a href="">#1174</a>, thanks <a href="https://github.com/CollinHeist"><code>@​CollinHeist</code></a>).</li>
<li>Honor the <code>NO_COLOR</code> environment variable which disables color output by default if <code>colorize</code> is not provided (<a href="">#1178</a>).</li>
<li>Honor the <code>FORCE_COLOR</code> environment variable which enables color output by default if <code>colorize</code> is not provided (<a href="">#1305</a>, thanks <a href="https://github.com/nhurden"><code>@​nhurden</code></a>).</li>
<li>Add requirement for <code>TERM</code> environment variable not to be <code>&quot;dumb&quot;</code> to enable colorization (<a href="">#1287</a>, thanks <a href="https://github.com/snosov1"><code>@​snosov1</code></a>).</li>
<li>Make <code>logger.catch()</code> usable as an asynchronous context manager (<a href="">#1084</a>).</li>
<li>Make <code>logger.catch()</code> compatible with asynchronous generators (<a href="">#1302</a>).</li>
<li>Improve feedback for invalid format keys in logger format strings (<a href="">#1450</a>, thanks <a href="https://github.com/Krishnachaitanyakc"><code>@​Krishnachaitanyakc</code></a>).</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/Delgan/loguru/blob/master/CHANGELOG.rst">loguru's changelog</a>.</em></p>
<blockquote>
<h1><code>0.8.0</code>_ (2026-11-11)</h1>
<ul>
<li>Change the default log format to include the timezone offset since it produces less ambiguous logs (<code> &lt;</code><em>, thanks <code>@tim-x-y-z &lt;https://github.com/tim-x-y-z&gt;</code></em>).</li>
<li>Add new <code>logger.reinstall()</code> method to automatically set up the <code>logger</code> in spawned child processes (<code> &lt;</code><em>, thanks <code>@monchin &lt;https://github.com/monchin&gt;</code></em>).</li>
<li>Add support for template strings used as log messages (<code> &lt;</code><em>, thanks <code>@TurtleOrangina &lt;https://github.com/TurtleOrangina&gt;</code></em>).</li>
<li>Add <code>record[&quot;template&quot;]</code> that includes the raw, unformatted message (<code> &lt;</code><em>, thanks <code>@sentrivana &lt;https://github.com/sentrivana&gt;</code></em>).</li>
<li>Fix incorrect microsecond value when formatting the log timestamp using <code>{time:x}</code> (<code> &lt;</code>_).</li>
<li>Fix parsing of 12-hour rotation times without seconds (<code> &lt;</code><em>, thanks <code>@c-tonneslan &lt;https://github.com/c-tonneslan&gt;</code></em>).</li>
<li>Fix a <code>&quot;&lt;weekday&gt; at &lt;time&gt;&quot;</code> rotation firing its first rotation on the creation day instead of the requested weekday when the time of day was later than the creation time (<code> &lt;</code><em>, thanks <code>@gaoflow &lt;https://github.com/gaoflow&gt;</code></em>).</li>
<li>Fix hex color short code expansion (<code> &lt;</code><em>, thanks <code>@turkoid &lt;https://github.com/turkoid&gt;</code></em>).</li>
<li>Fix possible regular expression denial of service (ReDoS) when parsing color markups in strings containing long sequences of backslashes (<code> &lt;</code>_).</li>
<li>Fix possible internal error when dealing with (rare) frame objects missing a <code>f_lineno</code> value (<code> &lt;</code>_).</li>
<li>Fix a regression preventing formatting of <code>record[&quot;time&quot;]</code> when using <code>zoneinfo.ZoneInfo</code> timezones (<code> &lt;</code><em>, thanks <code>@bijlpieter &lt;https://github.com/bijlpieter&gt;</code></em>).</li>
<li>Fix possible <code>ValueError</code> raised on Windows when system clock was set far ahead in the future (<code> &lt;</code>_).</li>
<li>Fix externally raised <code>Exception</code> possibly causing invalid state generating repeated <code>RuntimeError</code> of avoided deadlock (<code> &lt;</code>_).</li>
<li>Fix incorrect formatting of negative timezone offsets with sub-minute components (<code> &lt;</code>_).</li>
<li>Fix incorrect formatting of negative timestamps (<code> &lt;</code>_).</li>
<li>Fix incorrect thread and process identifiers of standard logging <code>Handler</code> records when using <code>enqueue=True</code> (<code> &lt;</code>_).</li>
<li>Fix <code>catch=True</code> being ignored for exceptions raised during sink termination, such as file retention or compression triggered by <code>logger.remove()</code> (<code> &lt;</code>_).</li>
<li>Fix <code>logger.parse()</code> decoding log files with the locale encoding instead of UTF-8 when given a path, which failed on non-ASCII logs written using the file sink default encoding on Windows (<code> &lt;</code>_).</li>
<li>Fix formatting of truncated <code>ExceptionGroup</code> errors, which used a plural for a single remaining exception and could miss the closing ruler (<code> &lt;</code><em>, thanks <code>@JeremyL691 &lt;https://github.com/JeremyL691&gt;</code></em>).</li>
<li>Respect the <code>.level</code> attribute of standard logging <code>Handler</code> used as sink, which was previously ignored (<code> &lt;</code>_).</li>
<li>Allow the <code>rotation</code> argument of file sinks to accept a list of rotation conditions, any of which can trigger the rotation (<code> &lt;</code><em>, thanks <code>@CollinHeist &lt;https://github.com/CollinHeist&gt;</code></em>).</li>
<li>Honor the <code>NO_COLOR</code> environment variable which disables color output by default if <code>colorize</code> is not provided (<code> &lt;</code>_).</li>
<li>Honor the <code>FORCE_COLOR</code> environment variable which enables color output by default if <code>colorize</code> is not provided (<code> &lt;</code><em>, thanks <code>@nhurden &lt;https://github.com/nhurden&gt;</code></em>).</li>
<li>Add requirement for <code>TERM</code> environment variable not to be <code>&quot;dumb&quot;</code> to enable colorization (<code> &lt;</code><em>, thanks <code>@snosov1 &lt;https://github.com/snosov1&gt;</code></em>).</li>
<li>Make <code>logger.catch()</code> usable as an asynchronous context manager (<code> &lt;</code>_).</li>
<li>Make <code>logger.catch()</code> compatible with asynchronous generators (<code> &lt;</code>_).</li>
<li>Improve feedback for invalid format keys in logger format strings (<code> &lt;</code><em>, thanks <code>@Krishnachaitanyakc &lt;https://github.com/Krishnachaitanyakc&gt;</code></em>).</li>
</ul>
<h1><code>0.7.3</code>_ (2024-12-06)</h1>
<ul>
<li>Fix Cython incompatibility caused by the absence of underlying stack frames, which resulted in a <code>ValueError</code> during logging (<code> &lt;</code>_).</li>
<li>Fix possible <code>RuntimeError</code> when removing all handlers with <code>logger.remove()</code> due to thread-safety issue (<code> &lt;</code><em>, thanks <code>@jeremyk &lt;https://github.com/jeremyk&gt;</code></em>).</li>
<li>Fix <code>diagnose=True</code> option of exception formatting not working as expected with Python 3.13 (<code> &lt;</code><em>, thanks <code>@etianen &lt;https://github.com/etianen&gt;</code></em>).</li>
<li>Fix non-standard level names not fully compatible with <code>logging.Formatter()</code> (<code> &lt;</code><em>, thanks <code>@yechielb2000 &lt;https://github.com/yechielb2000&gt;</code></em>).</li>
<li>Fix inability to display a literal <code>&quot;\&quot;</code> immediately before color markups (<code> &lt;</code>_).</li>
<li>Fix possible infinite recursion when an exception is raised from a <code>__repr__</code>  method decorated with <code>logger.catch()</code> (<code> &lt;</code>_).</li>
<li>Improve performance of <code>datetime</code> formatting while logging messages (<code> &lt;</code><em>, thanks <code>@trim21 &lt;https://github.com/trim21&gt;</code></em>).</li>
<li>Reduce startup time in the presence of installed but unused <code>IPython</code> third-party library (<code> &lt;</code><em>, thanks <code>@zakstucke &lt;https://github.com/zakstucke&gt;</code></em>).</li>
</ul>
<h1><code>0.7.2</code>_ (2023-09-11)</h1>
<ul>
<li>Add support for formatting of <code>ExceptionGroup</code> errors (<code> &lt;</code>_).</li>
<li>Fix possible <code>RuntimeError</code> when using <code>multiprocessing.set_start_method()</code> after importing the <code>logger</code> (<code> &lt;</code>_).</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>28349be</code></a> Bump version to 0.8.0</li>
<li><a href=""><code>f6869a7</code></a> Evaluate every rotation condition so a skipped one cannot fire spuriously (<a href="">#1</a>...</li>
<li><a href=""><code>f85a973</code></a> Fix formatting of truncated &quot;ExceptionGroup&quot; to match traceback (<a href="">#1541</a>)</li>
<li><a href=""><code>26fc3e4</code></a> Fix logger.parse() decoding paths with the locale encoding (<a href="">#1540</a>)</li>
<li><a href=""><code>d776b42</code></a> Use stable Python 3.15 in tests workflow</li>
<li><a href=""><code>4e7762b</code></a> Fix greedy regex causing quadratic scans and possible reDoS (<a href="">#1538</a>)</li>
<li><a href=""><code>874aa41</code></a> Document common causes of <code>OsError</code> at file sink stop (<a href="">#1534</a>)</li>
<li><a href=""><code>f738c2a</code></a> Add capture of exceptions raised during sink termination (<a href="">#1533</a>)</li>
<li><a href=""><code>bce5dfd</code></a> Fix thread/process info in standard handlers with <code>enqueue=True</code> (<a href="">#1529</a>)</li>
<li><a href=""><code>12b0479</code></a> Reject bool for retention, rotation, and handler ids (<a href="">#1514</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/Delgan/loguru/compare/0.7.2...0.8.0">compare view</a></li>
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
- `@dependabot ignore this major version` will close this PR and stop Dependabot creating any more for this major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this minor version` will close this PR and stop Dependabot creating any more for this minor version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4ff8f56b17b7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
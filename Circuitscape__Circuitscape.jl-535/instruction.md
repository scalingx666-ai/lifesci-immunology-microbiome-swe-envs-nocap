# Issue

**Title:** Config: state each fact about the options once; trim long-tail tests

## Description

. That PR removed the five per-key lists, but some facts about the options were still stated in more than one place. This PR states each of them once.

## Changes
1. **The raster inputs that may need GDAL** were listed in `validate` and again in the tests' `requires_gdal`. Both now use `RASTER_FILES`.
2. **`validate` named every key twice**, once as a string and once as a field (`need("mask_file", cfg.mask_file)`), and paired each `use_*` flag with its file by hand. It now calls `need(:mask_file)` and loops over two small tables, `OPTIONAL_FILES` and `UNIMPLEMENTED`. The messages and their order are unchanged.
3. **What counts as an unset path** was decided in two places: the text parser and `validate`. The `validate` check relied on every placeholder starting with `(`. There is now one `_is_unset`, next to the placeholders, and a test checks that every placeholder counts as unset.
4. **The docs restated the tables.** The docstrings now point to the tables or the options reference instead of re-listing the enumerated options, the ignored Circuitscape 4 keys and the defaults. `options.md` keeps its full reference, and a new test checks its rows, defaults and accepted spellings against the code. The test found three undocumented spellings, which are now added: `one_to_all` and `all_to_one` for `scenario`, and `not entered` for `remove_src_or_gnd`.
5. **The REPL INI builder's menus** (data types, modes, solvers) and its `"true"` values now come from the value tables. It still offers only `cg+amg` and `cholmod`, the solvers that need no extra package.
6. **Key folding** was written out three times; it is now one `_ini_key` helper.
7. **Values were stripped up to three times.** They are now stripped once, in `_parse_fields`. `normalize_config` still strips too, because it compares values.
8. **`write_config(dict)`** parsed the dict twice when called without a path. It now parses once.
9. **`[Version]`** in written INI files said `5.0.0`. It now records the version that wrote the file, via `pkgversion`.

`config.jl` grows by 13 lines (446 to 459) for the tables and their comments, because the goal here was one statement per fact rather than fewer lines. `CSConfig(dict)` is unchanged at about 3 µs and 560 bytes.

## Tests
The config tests from #533 and this PR are cut to the cases that guard behaviour users depend on:
- **Parser fixes:** comments and blank lines skipped, the `:` delimiter, key case, a Windows `C:\` path, CRLF line endings, and a malformed line being an error.
- **Case-insensitivity:** value case for one enum, one boolean and one path; key folding in `update!` and in `CSConfig(dict)`; the conflicting-duplicate error.
- **Typos still rejected**, and `INI_SECTIONS` covering every field.
- **The new docs check**, and `write_config(dict)` with and without a path.

Cut: the same parser exercised for five more enums, and one-off edge cases (non-ASCII and empty keys, `NONE`, `AUTO`, same-value duplicates, whitespace in `normalize_config`). The REPL menu lists and the `[Version]` line are cut too.

**Not covered:** the REPL builder's interactive steps. Only loading the extension is tested. A scripted run with a fake terminal would be the next useful test.

## Test plan
- [x] Full `Pkg.test()` passes: 1460 unit tests, 680 for each of the four CG+AMG/CHOLMOD × single/double runs, and 54 for issue 341. The GeoTIFF, Accelerate, Pardiso and AMGX tests were skipped because those packages aren't available locally.
- [x] `validate` gives the same messages, in the same order, for an advanced-mode configuration with no files, a mask and both unimplemented options set. The existing validation tests cover the GDAL and output-directory checks.
- [x] `normalize_config`'s docstring is still attached to it after the helper was added.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5a8baa92664c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
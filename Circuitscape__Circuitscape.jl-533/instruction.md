# Issue

**Title:** Drive INI config from tables; case-insensitive keys and values; read INI files as Circuitscape 4 did

## Description

Two commits, rebased on master (including #532's `amgx` solver):
1. **Drive INI config from tables.** Also reads INI files the way Circuitscape 4 did.
2. **#534, folded in.** Keys and option values become case-insensitive. The commit is adapted to the table design and keeps its own commit and authorship.

.

## 1. Tables instead of five per-key lists
Every option used to be listed in five places: the `CSConfig` struct, `CSConfig(dict)`, `Dict(cfg)`, `init_config` and the `write_config` template. Defaults were stated three times. With tables, `config.jl` drops from 610 lines to 446 (`src/` is 187 lines smaller), and the spelling constants in `consts.jl` go away.

- **Defaults:** the `CSConfig` field defaults are the only place defaults are written. `init_config()` is those defaults as INI strings, plus `INI_PLACEHOLDERS`: the INI Builder's `(Browse for …)` paths, `scenario = not entered`, and the Circuitscape 4 keys that are accepted but do nothing.
- **`INI_NAMES`** lists the accepted spellings of each boolean and enum value. The first spelling is the one written out. It replaces the spelling constants in `consts.jl`, including #532's `AMGX_GPU`, and the per-enum `_parse_*` / `_*_str` functions. Error messages are unchanged.
- **`INI_SECTIONS`** describes Circuitscape 4's section layout. `write_config`, `CSConfig(dict)`, `Dict(cfg)` and `policy` are built from these tables instead of listing the keys.

## 2. Case-insensitive keys and values (#534)
`solver = CHOLMOD`, `Solver = cholmod` and `write_cur_maps = TRUE` all work, in an INI file or in a dictionary. File paths keep their case. A key given twice in different case with different values is an error. Typos are still errors.

Changes from #534's implementation:
- **Values** are matched in any case by the parsers, which compare ASCII case without allocating, instead of being lowercased up front. The `String` fields of `CSConfig` are exactly #534's `CASE_SENSITIVE_KEYS`, and they keep their case, so the separate list isn't needed.
- **`INI_NAMES`** drops its case variants, as #534 did in `consts.jl`. Values are still written in their usual spelling (`True`, `DEBUG`).
- **Keys** are lowercased by `parse_config` and `update!`. `normalize_config` folds key case and strips keys and values. It runs only when a dict has a key that `init_config` doesn't, so the common path (`init_config` + `update!`, once per Omniscape window) copies nothing.
- **Tests:** a new "Case-insensitive configuration" testset; #534 had no tests.

## INI parsing now follows Circuitscape 4 (Python's ConfigParser)
- **Comment and blank lines are skipped.** Before, they were read as a key named `""`, which produced a spurious `Ignoring unrecognised configuration keys: , ...` warning.
- **`key: value` is read.** Before, `precision: single` was silently dropped and the run used double precision.
- **Any other line is an error** that gives the file and line number; before, such lines were silently dropped. This is the one change that can break a hand-edited INI file, so it is listed under breaking changes in `docs/src/migration.md`. Circuitscape 4 also rejected such lines.

## Other visible changes
- **Written INI files** use `True`/`False` instead of `true`/`false`, and `solver = pardiso` instead of `mklpardiso`. Both spellings are still read.
- **`init_config()`** returns `double` instead of `Double`, and `False` instead of `false` for three keys. Every field parses to the same value; this was checked field by field against master.
- **`None` for any file path, in any case, means not set.** Before, this applied only to `log_file`.
- **Partial dictionaries:** when `CSConfig(dict)` is given a dict without a path key, that path now takes its `init_config` placeholder instead of `""`. `validate` treats both as unset.
- **Bad values** for `cholmod_batch_size` or `residual_tolerance` now give an error that names the key.
- **`update!`** now returns `cfg`, as its docstring always said.

## Performance
| | master | this PR |
|---|---|---|
| `CSConfig(dict)` from `init_config` + `update!` | 2.9 µs, 8.8 KB | 2.9 µs, 560 B |
| `Dict(cfg)` (only tests and user scripts call it) | 1.2 µs | 4.7 µs |

## Test plan
- [x] "INI syntax" testset: comment, blank and section lines; `:` delimiter; mixed-case keys; a Windows path with `C:` in the value; CRLF line endings; a non-ASCII key; malformed lines rejected with the line number; `INI_SECTIONS` lists every field exactly once.
- [x] "Case-insensitive configuration" testset: values in any case for every option type, `update!` and `CSConfig(dict)` key folding, the conflicting-duplicate error, paths keeping their case, `None` in any case, and typos still rejected.
- [x] Compared against master: `init_config` keys are identical, every field parses the same from both versions of `init_config`, error messages are unchanged, and `write_config` output differs only in the case of booleans.
- [x] Full `Pkg.test()` passes locally: 1463 unit tests, 680 for each of the four CG+AMG/CHOLMOD × single/double runs, and 54 for issue 341. The GeoTIFF, Accelerate, Pardiso and AMGX tests were skipped because those packages aren't available locally.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bceaaee815c6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
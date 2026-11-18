# Issue

**Title:** Read and write INI files with IniFile.jl 0.6

## Description

## Summary

Circuitscape's hand-written INI reader and writer are replaced by [IniFile.jl](https://github.com/JuliaIO/IniFile.jl) 0.6.

- **`parse_config`** is now one call, merged over the defaults:
  ```julia
  ini = read(Inifile, path; lowercase_keys = true, inline_comment_prefixes = (";",), strict = true)
  CSConfig(merge!(init_config(), merged(ini)))
  ```
- **`write_config`** builds an `Inifile` from `INI_SECTIONS` and writes it.
- **Dependency:** `IniFile = "0.6"` is added. Its only dependency is OrderedCollections.

IniFile's defaults fit Circuitscape. Continuation lines are off (`multiline_values = false`), so an indented `  solver = cholmod` is still read as its own key and not joined onto the line above. Repeated keys are never an error, so a `solver = ...` appended at the end of a file still overrides an earlier one.

## What changes for users

- **Byte order mark:** a UTF-8 byte order mark at the start of the file (Windows Notepad adds one) is ignored. Since #533 it made line 1 an error. That regression was never released (the latest release is v6.1.0).
- **Inline comments:** a `;` after a space or tab starts a comment, as in Circuitscape 4. `solver = cholmod ; faster` now works; before, it was rejected as an unknown solver.
- **Malformed lines:** they are still an error that names the file and line. The wording now comes from IniFile: `malformed line 2 of job.ini: "precision single"; expected ...`.
- **Repeated keys:** when a key is set more than once, the later setting wins. The one exception is a file that repeats a section header. Its lines are added to the first section of that name, as in Circuitscape 4, so a key set in a section in between is read as coming later than them. Before, plain line order decided.

Docs: the options reference and the migration guide mention inline comments.

## Test plan

- [x] All 88 INI files under `test/` give the same `CSConfig` with the new parser as with the old one. `write_config` output is byte-identical for each.
- [x] The "INI syntax" test now writes its fixture with a leading byte order mark and an inline `; comment`. It also checks the new malformed-line message.
- [x] `Pkg.test()` passes locally: 1460 unit tests plus the cg+amg and cholmod runs. Apple Accelerate, Pardiso and AMGX were skipped because they aren't available on this machine.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3bd8916f05c3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
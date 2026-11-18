# Issue

**Title:** MRG: adjust warnings around tax abund and provide v5 upgrades to `tax metagenome`

## Description

Add new command line arguments to `tax metagenome` around abundances. `--use-abundances` turns on the use of sketch abundances for `krona` and maybe other output formats, while `--ignore-abundances/--no-abundances` turns them off.  To add to the complexity, by default, the `human` and `kreport` output formats _do_ use abundances when present 😭 .

Here's a chart to disambiguate 😆 

| output format | v4 behavior | v5 default behavior | notes |
| -------- | -------- | -------- | -- |
| human     | abund     | abund     | default output in v5
| csv_summary     | provides both     | provides both     | default output in v4
| lineage_summary     | no abund     | abund     |
| krona     | no abund    | abund     |
| kreport     | abund | abund     |

This PR provides a warning if no abundances are available for `tax metagenome` to use, or if `--use-abundances/--ignore-abundances` is not explicitly set (for sourmash v4).

For sourmash v5, `--use-abundances` becomes default and it is an error to not have abundances. This can be overridden with `--ignore-abundances`.

For sourmash v5, this PR also changes the default output format for `tax genome` and `tax metagenome` to `-F human` from `-F csv_summary` ().

Uses `--v4`/`--v5` command line switches and test infrastructure, ref 

As of this PR,

sourmash v4 - all tax metagenome commands _warn_ if abundances are not available.
sourmash v5 - all tax metagenome commands _require_ abund, unless --ignore-abund is set.

TODO:
- [x] finish writing tests
- [x] test: warning if no abundances provided/used (v4)
- [x] test: no warning if --ignore-abund, and no abundances used (v4/v5)
- [x] test: error if no abundances provided & no ignore (v5)
- [x] test: error if no abundances provided and `--use-abund`
- [x] test: abundances used if `--use-abund` (v4/v5)
- [x] test: abundances used if v5
- [x] test: default output format for metagenome is human (v5)
- [x] test: default output format for genome is csv_summary (v4)
- [x] test: abundances not used with `tax genome`
- [x] fix @CTB and XXX notes stuff
- [x] actually test & examine the krona and kreport output formats ;)
- [x] test: default output format for metagenome is human (v5)
- [x] test: default output format for genome is csv_summary (v4)
- [x] add tests and checks for human output format: --use-abund, --ignore-abund, and defaults (use abund).
- [x] add comments to #3577 and #3598
- [x] add documentation
- [ ] check bioboxes and lingroup output formats to see if changes are required

Fixes 
Fixes 
Fixes 

**UPDATE:** I created a validation workflow here: https://github.com/sourmash-bio/2025-validate-sourmash-tax-formats. It converts everything to the new taxburst JSON format and then does a tree comparison. The new krona format passes 🎉 !

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c94f1438c442`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Handle CLI programs with modes

## Description

This is a small . My agent noticed that two programs only got part of their parameters on their help pages: `anvi-setup-kegg-data` and `anvi-cluster-contigs`. Both of them have argparse modes, which is the problem.

`anvi-setup-kegg-data` takes `--mode` and `anvi-cluster-contigs` takes `--driver`, and each mode keeps its own parameters in a separate parser. The programs parse their own parameters first, and then hand the leftovers to the parser of the chosen mode. Since `get_parser_for_program` grabs the parser at the very first `parse_known_args` call, it only ever saw the top-level one. So `anvi-setup-kegg-data` was listing 6 of its 18 parameters (no `--kegg-archive`, `--kegg-snapshot`, `--only-download`, etc.), and `anvi-cluster-contigs` was listing 7 of 41 (none of the binner-specific ones).

My purpose with this PR is to just surface the issue, and propose this AI fix. The `--help` output of both programs is identical to master. I also built the help pages on master and on this branch and compared them, and these two are the only pages that change. I have not checked how the modes render and if it's suitable.

A few caveats:

- In `anvi-cluster-contigs` claude moved the "is this binner installed" check below the lines that add the driver's parameters. Before, a driver's parameters only existed if its binary was on the PATH, and the environment that builds anvio.org has none of the binners, so the website would have still shown nothing for them. One side effect: running `--driver concoct --clusters 5` without CONCOCT installed now tells you CONCOCT isn't installed, instead of complaining about unrecognized parameters. I think that's an improvement, but it is a behavior change.
- `--mode all` in `anvi-setup-kegg-data` also accepts the `KOfam` and `modules` parameters. The help page lists each mode's own parameters the same way `--help` does, so that detail still only lives in the program's logic.
- **Nothing enforces `add_mode_parsers`. A new program with modes that doesn't call it will quietly list only its top-level parameters, same as before this PR.**
- The flag that picks the mode (`--mode`, `--driver`) only shows up in the group title, not in its own field. Fine for the help pages, but worth keeping in mind if we build more on top of `documentation.json`.
- I also didn't bump the schema version of `documentation.json`

Two unrelated things I noticed while comparing builds, happy to handle them separately: `--palindrome-search-algorithm` keeps its choices in a set, so its usage line flips between `{numba,BLAST}` and `{BLAST,numba}` from one build to the next, which means the nightly anvio.org sync will commit noise. And `anvi-setup-modelseed-database` has an absolute path into the anvi'o installation as its default, so its page will show the path on whatever machine built it.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e54b7db41855`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
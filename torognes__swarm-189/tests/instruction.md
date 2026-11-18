# Issue

**Title:** Add bash and zsh shell auto-completion for swarm

## Description

Implements tab-completion of swarm's command-line options and file arguments for bash and zsh, as requested in the enhancement issue.

- completion/swarm.bash: bash completion (complete -F)
- completion/_swarm: zsh completion (#compdef, _arguments)
- FILENAME options complete file names; INTEGER options offer no value suggestion; the positional FASTA argument completes file names
- Makefile: install/uninstall the scripts to standard locations (bash-completion completions dir and zsh site-functions); paths overridable via bashcompdir/zshcompdir
- README: document installation and manual enablement

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4023185f4ec1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
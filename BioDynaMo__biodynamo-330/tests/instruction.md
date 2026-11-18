# Issue

**Title:** Singularity fix

## Description

On most HPC users don't have root privileges and thus must build their containers with the `--fakeroot` option. When building with fakeroot, the user has root privileges inside the container (at build time only) and thus the home directory is set to /root. Once the user runs the container, he/she is no longer root and thus can't access the /root folder, preventing the initialisation of pyenv (since /root can't be accessed by non-root users). To avoid this, one simple option would be to run the container with the `--fakeroot` option as well, but this would convert the SIF file to a temporary sandbox at every run,  making it slow. As an alternative, pyenv can be installed in another directory where every user (with or without root privileges) has read access, such as /opt. However, the Singularity file system is read-only, and although the /opt directory can be accessed by every user, running the commands `eval "$(pyenv init --path)"` and  `eval "$(pyenv init -)"` would trigger `eval "$(pyenv rehash)"` that might try to write in /opt/.pyenv/shims, resulting in errors when the BioDynaMo environment is sourced (via `source biodynamo/build/bin/thisbdm.sh`). To avoid this, the option `--no-rehash` can be specified in the two commands previously mentioned, keeping in mind that the Singularity environment can't be changed definitively when running the container, and therefore the rehash of pyenv should not be needed. Installing pyenv in /opt/.pyenv and adding the `--no-rehash` option should be enough to prevent the failure of the sourcing of the BioDynaMo environment. Finally, to make sure no host machine environment variable will conflict with the container ones, we tell the users  to run the container with the option `--cleanenv`.
The Singularity build script was also updated to move to a newer Ubuntu version (18.04 -> 20.04).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1fa436f2aa4f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
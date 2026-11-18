# Issue

**Title:** Make `clap` an optional dependency

## Description

Hi Jim,

This PR makes `clap` an optional dependency, only required when building the `skani` binary. 

Since in `pyskani` I'm vendoring the Rust crates for reproducible compilation from source, I have to download the transitive dependencies for `skani` on all platforms. Unfortunately, on Windows, `clap` requires `winapi`, which is a huge crate. I end up with around 130MB of extra dependencies for `clap` which I don't really need for the Python bindings:

![image](https://user-images.githubusercontent.com/8660647/217608917-83ebfb8d-3f67-4a03-923f-af0c330e43b9.png)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `de16b9c6aed6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Switch Cython backend to vambcore package

## Description

Remove the Cython backend _vambtools in favor of a separately installable Rust package.
This is a reversible change, since it does not alter Vamb's API. If things go horribly wrong, we can switch it back to the Cython version.

The advantages of the new backend are:
* Hopefully, the inevitable installation problems caused by adding a `maturin`- based Python package written in Rust will be less bad than the existing ones caused by having a mandatory Cython compilation step during installation.

* Since Rust is a much nicer, and safer language than Cython, this change will encourage me to incrementally move components of Vamb into Rust, if I want. It's not yet clear that I want to do so, as the computational bottlenecks of Vamb are not really in the Python parts anyway.

* Python scripts like the ones in src/ can depend on vambcore instead of the whole of Vamb, and will therefore load faster and consume less memory.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `79ae2facc7aa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
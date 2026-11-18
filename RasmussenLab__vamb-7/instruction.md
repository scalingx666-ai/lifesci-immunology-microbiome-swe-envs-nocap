# Issue

**Title:** Add setup.py, make pip installable

## Description

Hello! Thank you for vamb!

This PR makes a few changes to make vamb pip installable, which is necessary (or at least a good idea :) for building a bioconda package and/or making vamb available via PyPI (e.g. https://pypi.org/project/vamb/). For developers, it also means you can run 'pip install -e .' to run vamb in developer mode, so as to avoid mucking around with paths etc. etc.

Briefly, I did the following:

- removed `.so` and `__pycache__` files from repository as platform specific and/or generated;
- created a `vamb` package directory;
- moved `run.py` to __main__.py and encapsulated the top level commands in a function that can be used as a setuptools entrypoint;
- created a `setup.py` with a version string and setuptools commands to build the Cython extension from scratch;

This changes the install & run instructions, too. There are a few new ways to install & run vamb from this branch:

## Installing

(requires pytorch and pysam installs; see [my draft quickstart guide](https://hackmd.io/mpWlv3jeR3uoYCIh4h-7sQ?both) for those commands.)

### Install 1 - user mode

This is for users who don't want to edit or view the source code:
```
pip install Cython
pip install -U https://github.com/ctb/vamb/archive/add_setup.zip
```

### Install 2 - developer mode

This is for developers who want to be able to edit Python files and have the changes show up directly in the running command:

```
# clone repo
git clone https://github.com/ctb/vamb -b add_setup

# dev install
cd vamb
pip install -e .
```

Note that any changes you make to the .pyx file requires that you run `python setup.py build_ext -i` to update the compiled files.

## Running

You can now do either
```
python -m vamb
```
or just straight up
```
vamb
```
-- the former is nice because you can nail down the version of Python you want to run, whereas the latter is nice for users who don't care that it's written in Python!

Note that vamb is also importable as you'd expect: `import vamb`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a94f10671e1d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
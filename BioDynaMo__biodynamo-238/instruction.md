# Issue

**Title:** Add CLI wrapper for `bdm-config`

## Description

Usage:
```
. <path_to_bdm>/build/bin/thisbdm.sh
bdm config
```

Example output:
```
<bdm config> Loading BioDynaMo configuration ...

version (The BioDynaMo version)
'v1.03.6-e9439619'

root-version (The version of ROOT used to build BioDynaMo)
'6.25/01'

cxxflags (Compiler flags and header path)
[ '-DUSE_DICT',
 '-std=c++14',
 '-Wall',
 '-Wno-missing-braces',
 '-m64',
 '-fPIC',
 '-Xclang',
 '-fopenmp',
 '-Wno-undefined-var-template',
 '-stdlib=libc++',
 '-pthread',
 '-std=c++14',
 '-m64']

[ ... ]

<bdm config> Finished successfully ...
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e9439619ce36`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
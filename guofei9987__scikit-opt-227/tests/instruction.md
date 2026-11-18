# Issue

**Title:** fix: ACA complains 'np.int' not found in new nump version

## Description

1.20以后的numpy不再提供np.int，运行报错，修改为创建数组时直接传入buildin的int类型。
参考numpy文档：
https://numpy.org/devdocs/release/1.20.0-notes.html#deprecations

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f7e6f065f267`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
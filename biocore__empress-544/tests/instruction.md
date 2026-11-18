# Issue

**Title:** Update setup.py PyPI classifiers

## Description

Not a big deal, but the python versions listed here were out of date. I'm basing the versions listed here on the python versions we currently test against in the standalone CI:

https://github.com/biocore/empress/blob/95848b854d3703c539972ed407d7722b61fad2c2/.github/workflows/standalone.yml#L23

I'm not sure if we ever decided officially to not support Python 3.5 or if we just quietly abandoned testing against it. In any case, I don't see a reason to maintain support for it (for reference [the latest version of QIIME 2 is already on Python 3.8.8](https://raw.githubusercontent.com/qiime2/environment-files/master/2021.4/release/qiime2-2021.4-py38-osx-conda.yml)).

Aside from updating the python version classifiers I also added a few relevant classifiers from Qurro's [setup.py](https://github.com/biocore/qurro/blob/master/setup.py) (bioinformatics, visualization, etc), and removed the application framework classifier. (I don't *think* Empress qualifies as an "application framework," but I just spent a solid minute staring at the first sentence of [this Wikipedia article](https://en.wikipedia.org/wiki/Application_framework) and I'm still not sure so IDK.)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `95848b854d37`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
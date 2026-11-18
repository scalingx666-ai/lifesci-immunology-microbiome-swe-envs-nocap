# Issue

**Title:** Fix clhash checkout command

## Description

Hello,

while trying to build dashing using the [instructions](https://github.com/dnbaker/dashing#build):
```
git clone https://github.com/dnbaker/dashing
cd dashing && make update dashing
```
I got an error (on an Arch Linux system running zsh) during the `clhash`compilation:
```
cd bonsai/bonsai && make clhash.o && cd ../..
make[1]: Entering directory 'dashing/bonsai/bonsai'
ls clhash.o 2>/dev/null || mv ../clhash/clhash.o . 2>/dev/null || (cd ../clhash "&& git checkout master" && make && cd ../bonsai && ln -s ../clhash/clhash.o .)
/bin/sh: line 0: cd: too many arguments
make[1]: *** [Makefile:88: clhash.o] Error 1
```

Removing the quotes fixes the problem. (I also saw a similar line is in the [dashing Makefile](https://github.com/dnbaker/dashing/blob/8edc8d55bda1a367fd1d101b3b98217fdc5b5f6a/Makefile#L7), but it is not used so it doesn't trigger the problem).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `647b977fe57d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
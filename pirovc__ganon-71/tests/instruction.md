# Issue

**Title:** Feature/add gcc 8 to travis plan

## Description

Let's add now **gcc-8** to the build plan in order to guarantee a smooth transition into newer versions of the compiler (or event into c++20) in the future. In exchange, the plan will become, of course, a bit slower.

Since Travis has Ubuntu 16.04, we cannot unfortunately easily add clang version above 6 for the moment. But let's keep an eye on this...

ps.: minha fita do Raven quebrou!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `10786bc7af07`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
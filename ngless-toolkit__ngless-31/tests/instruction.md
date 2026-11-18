# Issue

**Title:** Build ngless nighlies on Ubuntu (glibc instead of muslc)

## Description

I recently ran into an issue with the bwa binary bundled with ngless which was compiled on alpine linux (muslc). The symptom is an "Out of memory" error and happens regardless of how much free memory the machine has. The actual amount of memory being allocated (or reallocated) varies but is frequently 256 bytes. Usually small numbers.

Retrying the same command would sometimes fail on a different code path resulting in slightly different error messages and tracebacks but always resulting in "Out of memory". It also took over 8 hours on average to trigger the error and only when using a large database (20GB+). Writing a test for this scenario is unfeasible.

Monitoring memory did not reveal any spike or strange usage.

At this point I'm convinced the error is _falsely_ showing the "Out of memory" message. I got as far as tracing it to a call to the memory allocation machinery (malloc). Discussing the issue with some alpine maintainers/users lead to blaming muslc. Possibly a hard to trace bug since there aren't many causes for an malloc failure.

Using a static version compiled against glibc did not trigger the error.

For this reason, this pull request now adds support to building on Ubuntu in addition to Alpine.

A few changes were also included that affect how the static binary is created. Without them I couldn't get a stable static binary. Workarounds such as [this](https://bugs.launchpad.net/ubuntu/+source/gcc-4.4/+bug/640734/comments/6) produced a binary but would lead to SIGABRT during execution.

Compilation of a static binary against glibc leads to warnings with code that makes use of name resolution (DNS) which is the case for both bwa and ngless. These static binaries may not work on non-glibc systems (not tested).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1b72d3f077ed`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
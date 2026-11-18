# Issue

**Title:** anvi-run-kegg-kofams KeyError fix

## Description

With the new changes in  we started seeing non-fatal `KeyErrors` in the output of `anvi-run-kegg-kofams`, but only when running it on HPCs.

This PR fixes that.

Basically, there is a resource tracker (RT) that is in charge of cleaning up SharedMemory objects if a worker crashes. 

When on Mac (where I tested this PR initially), workers are generated with the `spawn` method, which gives them their own isolated resource tracker, so the "main" one isn't supposed to take care of their stuff. Meaning that workers on Mac have to explicitly unregister their SharedMemory objects from the main RT so that when they finish normally, the main RT doesn't try to clean up things that don't exist anymore.

But on Linux, workers are generated with `fork` and they inherit their parent processes RT (the "main" one). That means the main RT always tries to clean up their stuff after workers are done, and unregister() is called twice -- first by the worker, and then by the main RT. The second time unregister() is called, the SharedMemory object is already unregistered and hence we get a KeyError because it cannot be found :)

The fix was to explicitly check how the worker was spawned (fork or not), and from there decide whether or not the worker will unregister its SharedMemory object itself.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `25aedd82257a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
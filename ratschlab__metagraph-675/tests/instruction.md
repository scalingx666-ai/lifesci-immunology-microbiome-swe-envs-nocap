# Issue

**Title:** Handle SIGTERM and SIGINT in the query server

## Description

Restore SIGTERM and SIGINT handling for the query server, which lost its Asio signal handlers in the HTTP API rewrite (#155). Without a handler, Linux leaves a container's PID 1 running until Docker escalates to SIGKILL.

Register the signals before index loading, stop HTTP handling from the waiting main thread, and let the workers and loader finish before releasing the index. The wait adds no polling or query-worker thread.

In a local Docker test with deliberately delayed cleanup, `docker stop --timeout 30` completed normally after 12–14 seconds; a ten-second timeout escalated to SIGKILL. Existing connections close during shutdown, and loading already in progress finishes before exit.

Implemented with OpenAI Codex.

<!-- This is an auto-generated description by cubic. -->
---
## Summary by cubic
Restores SIGTERM and SIGINT handling in the query server, so `docker stop` and Ctrl+C now shut it down cleanly instead of waiting for Docker to SIGKILL it.

- Registers signal handlers before index loading and waits without polling, so termination works when running as PID 1.
- Stops HTTP handling from the main thread and lets the workers and loader finish before releasing the index.
- Adds integration tests covering both signals, multiple threads, mmap mode, and shutdown during startup; the startup tests hold the server at an index-list FIFO read, synchronized from the reading end on macOS, to verify shutdown while loading is still pending.

<sup>Written for commit 984eb7b520cea4130370b204a49242c895aafc7b. Summary will update on new commits.</sup>

<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/675?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/675?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F675&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>

<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ceb83b2ab077`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Fix crash on server shutdown racing HTTP workers

## Description

Fixes the intermittent `test_shutdown_1_term_multiple_threads` failure (`AssertionError: -11 != 0`) on master: master run 40606635554 (`b7f51b0f`, Protein Debug) and 40110252632 (`98291431`, Protein Release static noAVX). It is not caused by #671, which only changes `tests/test_all.cpp`.

## Root cause

The SIGTERM/SIGINT handler added in #675 calls `server.stop()` on the main thread while the HTTP worker threads are still running `io_service->run()`. `stop()` closes the acceptor and shuts down every open connection socket. Asio sockets must not be used concurrently, so:

- an accept handler on a worker re-arms `acceptor->async_accept` (`server_http.hpp:859`) while the main thread runs `acceptor->close()`. `epoll_reactor::start_op` then dereferences the released descriptor state, which is the SIGSEGV;
- `Connection::close()` (socket `shutdown`/`cancel`) races with the accept operation assigning that connection's socket (`do_assign`).

The test sends an incomplete request right before the signal, so a just-accepted connection's handlers are often in flight at that moment.

## Fix

The signal handler now only calls `io_service->stop()`, which is thread-safe. The acceptor and the connections are closed with `server.stop()` after `server_thread.join()`, when no worker is left. Shutdown behaviour is otherwise unchanged: in-flight handlers still finish, and an incomplete request still does not keep a worker alive.

A new `term_while_connecting` case keeps clients connecting (RST on close, capped, so it leaves no TIME_WAIT) while the signal arrives, so accept handlers are in flight during shutdown.

## Evidence

- **Standalone harness**: the same Simple-Web-Server/asio pins and the same shutdown sequence, with a client connecting during shutdown.
  - Old sequence: ThreadSanitizer reports 5 data races (`acceptor` close vs `async_accept`, `shutdown` vs `do_assign`, …). AddressSanitizer reports a SEGV in `epoll_reactor::start_op` ← `async_accept` ← the accept handler, with both `-p 4` and `-p 1`.
  - New sequence: 0 TSan races; ASan 2000/2000 clean with `-p 4` and 2000/2000 with `-p 1`.
- **End to end, master Release binary at `b7f51b0f`**:
  - The plain test scenario was clean in 300 + 4×150 (pinned to 2 cores) + 400 runs.
  - With clients connecting during the signal it reproduced the CI failure once (`rc=-11`) in about 250 runs.
  - The crash is too rare on a 32-core workstation for the end-to-end loops to separate the two builds: after switching the storm to RST-closed sockets, both master and the fix were 400/400 clean.
- **Fixed build (Release)**: repro loop 400/400 plain and 400/400 with connecting clients. `test_server_shutdown.py` passed 6/6 runs, 7/7 tests each.

Not run locally: the unit tests and the rest of the integration suite (left to CI). No unit test covers `server.cpp`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated description by cubic. -->
---
## Summary by cubic
Fixes the intermittent crash on server shutdown where SIGTERM/SIGINT raced with running HTTP workers. The signal handler previously called `server.stop()`, which closed the acceptor and all connection sockets from the main thread while accept and read handlers were still running on worker threads, occasionally crashing in asio.

- The signal handler now only stops the io_service; `server.stop()` is called after the worker threads have been joined.
- Adds a `term_while_connecting` shutdown test that keeps clients connecting while the signal arrives and only sends the signal after the first connection is accepted, so accept handlers are in flight during shutdown.

Shutdown behavior is unchanged otherwise: in-flight handlers still finish and an incomplete request still does not keep a worker alive.

<sup>Written for commit f52876b5440cbc2acd6f06922ee5d644b8114030. Summary will update on new commits.</sup>

<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/681?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/681?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F681&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>

<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b7f51b0f125a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
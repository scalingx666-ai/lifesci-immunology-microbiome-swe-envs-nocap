# Issue

**Title:** Cache results in the metagraph server

## Description

Cache serialized `/search` responses for single-graph and multi-graph queries. Concurrent identical requests share one computation, and retries after a dropped connection can reuse the result.

`--cache-size` sets the estimated memory budget in GB per server process (default 1; 0 disables caching). Accounting includes request keys, response allocations and entry overhead. Results are evicted by LRU, with preference for responses whose delivery failed. Active entries can temporarily exceed the budget. Oversized results serve existing waiters without displacing other cached results.

Failed or abandoned computations wake existing waiters and leave the cache so later requests can retry. Multi-graph errors wait for launched tasks before releasing request data. Request options are resolved once for execution and cache keys. Keys retain complete FASTA, distinguish graph paths containing delimiters, and preserve floating-point precision independently of locale. Cache hits preserve request validation. Disabling caching skips key construction and cache allocation; invalid or overflowing cache sizes are rejected.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `12b779636b43`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
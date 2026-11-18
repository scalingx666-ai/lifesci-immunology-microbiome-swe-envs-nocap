# Issue

**Title:** enable websocket communication

## Description

Addressing #3361 
extend the nginx example configuration file such that communication through WebSockets is automatically enabled.
I am not 100% sure if
  - [ ] the location definition is comprehensive. There might be more endpoints that need WebSocket communication
  - [x] the current settings cause unintended side effects

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `58e15a470919`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
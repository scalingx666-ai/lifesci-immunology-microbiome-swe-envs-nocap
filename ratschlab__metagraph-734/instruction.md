# Issue

**Title:** Bump writing-rules to 376b4f3 and keep the cubic mapping

## Description

Moves the `tools/writing-rules` pin from 1e2060d to 376b4f3 and updates the guide links to match.

The new revision carries fixes from an independent review of the guides: corrected citations, narrower rules in the LLM code guide, and clearer checklists. The linter code is unchanged.

The shared engineering guide still defines the review severity scale, but a project now has to adopt it and state the cubic priority mapping itself. `AGENTS.md` therefore does both, so reviews here keep working as before: findings use Must, Should and Nit, and cubic's P0 and P1 read as Must, P2 as Should and P3 as Nit.

Prepared with Claude Code.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `77dc4f026525`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
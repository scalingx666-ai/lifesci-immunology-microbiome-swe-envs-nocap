# Issue

**Title:** refactor(stage_logger): issue #669 , migrate to dataclass for step de…

## Description

**Refactor of step and logger classes:**

* Replaced all `pydantic.BaseModel` step classes (`Steps`, `ANIScreenStep`, `IdentifyStep`, etc.) with Python `@dataclass`es, providing default values and improved type annotations.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ae81c75c35dd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
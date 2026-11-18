# Issue

**Title:** Save to/load from urls and additional callbacks refactor

## Description

* Move callbacks into `src/chime_dash/app/services/callbacks.py`
* Create Page class that inherits from Component and specifies a `ComponentCallbacks` subclass that defines the callbacks for the class
*  Modified callbacks to support `dash_core_components.Store` rather than storing state in hidden Div
* Moved Body class from `components/__init__.py` to `pages/root.py` and renamed to Root
* Moved singleton decorator function from `components/__init__.py` to `utils/__init__.py`
* Removed hidden Div from Sidebar that stored Parameters JSON string
* Implemented initial automatic save to/load from URL 

Big thanks for @pjhoberman and @emmanuelle for their work on the fix for #146

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `88f69adbf8c9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
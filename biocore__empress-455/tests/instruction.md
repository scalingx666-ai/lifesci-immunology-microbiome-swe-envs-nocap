# Issue

**Title:** DOC: Remove Emperor installation note, and also bump the version number in setup.py to 1.0.1-dev

## Description

This note was there to caution readers that the
`pip uninstall --yes emperor` line would only temporarily uninstall
Emperor, since Emperor would immediately get reinstalled when
installing Empress afterwards.

Now that the Emperor uninstallation line isn't present in the
README instructions any more, we should just remove this note.

(Sorry for not catching this in review, I just realized it ._.)

edit: I also bumped up the version number in setup.py to `1.0.1-dev` now that i think about it

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ba5b7d46ef5d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
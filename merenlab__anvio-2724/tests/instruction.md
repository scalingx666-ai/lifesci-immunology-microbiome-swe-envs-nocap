# Issue

**Title:** restore setting panel closing annimation

## Description

The left "Settings" pill stopped working when using anvi-interactive (#2721): it disappeared on load and couldn't close/open the panel. Issue coming from from #2704 (853eecdce), which moved toggleLeftPanel() to depend on CSS hooks (transition, .panel-closed, pill z-index) that only exist in pangraph.css but was never loaded by index.html. With no transition, transitionend never fired, so the slide flag wedged and the panel never closed.

  - main.css: add the missing transition + .panel-closed rules and keep the pill positioned/on top in both states (slide -560px to clear the wider #sidebar).
  - animations.js: harden toggleLeftPanel() with a one-time cleanup() + fallback timer so the slide flag can never get permanently stuck, even if no transition fires.

@meren mentioned the idea to merge things into shared js library, which they are with the animation.js. The differences is in the individual .css files. Don't know if it is worth merging anything there and for now, I kept it to the minimal fix which restore the expected interactive behavior and not touched anything on the pangraph side.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ece955ae7d76`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
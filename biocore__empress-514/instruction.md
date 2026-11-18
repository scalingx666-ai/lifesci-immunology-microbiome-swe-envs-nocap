# Issue

**Title:** Small side panel formatting fix: hide button <p> containers instead of buttons; fix prev/next frame animation buttons

## Description

This doesn't entirely fix the problems brought up in #513, but it is a start -- it removes some unnecessary whitespace in the sample/feature metadata coloring and animation panels.

Hiding the button(s) inside a `<p>` tag still leaves some extra whitespace, since empty `<p>` tags still take up some space. Hiding the `<p>` tag directly (instead of the button(s)) fixes this, so now for example the default state of the animation panel looks a bit nicer:

| previous | now |
| -- | -- |
| ![image](https://user-images.githubusercontent.com/4177727/116771395-e3e32180-a9ff-11eb-99ab-0285b8d6f3a1.png) | ![image](https://user-images.githubusercontent.com/4177727/116771384-d5950580-a9ff-11eb-8fdd-84cee4525131.png) |

This PR also adjusts the animation panel so that:

- disabled buttons (prev frame / next frame, when on the first/last frame) are now given a special style to indicate they're disabled
- the next frame button is correctly disabled when on the last frame. It was off by 1 before, apparently.

| prev frame button disabled | next frame button disabled |
| -- | -- |
| ![image](https://user-images.githubusercontent.com/4177727/116773608-1e9e8700-aa0b-11eb-8ccd-7ccfca15b136.png) | ![image](https://user-images.githubusercontent.com/4177727/116773612-265e2b80-aa0b-11eb-9c6d-a98404f17dda.png) |

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3d60a2941bea`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
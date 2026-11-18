# Issue

**Title:** Fixed bugs in parameters check for decay in diffusion

## Description

## Fix diffusion grid decay parameter checks

### Summary
- Correct the decay safety condition to apply the time step to both the decay and diffusion terms.
- Fix the calculation of `max_dt` so that it matches the stability condition.

### Changes
1. **Decay safety check:** Multiply the sum of the decay constant and the diffusion term by `dt`, ensuring consistency with the derived condition:
`   1 - (mu_ + 6 * D / (dx * dx)) * dt >= 0`
2. **Maximum stable time step:** Correct the placement of `box_length_ * box_length_` in the `max_dt` calculation, so the reported maximum time step is consistent with the stability criterion:
  `max_dt = 2 / (mu_ + 12 * D / (dx * dx))`
  where `D = 1 - dc_[0] and dx = box_length_`.

### Motivation
These changes fix inconsistencies in the diffusion grid's parameter checks. The decay safety check now correctly evaluates the intended condition, while the stability error message reports the appropriate maximum time step when the stability criterion is violated.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ab57824239b6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
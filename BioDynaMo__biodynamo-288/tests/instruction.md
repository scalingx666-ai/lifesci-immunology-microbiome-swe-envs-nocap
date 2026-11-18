# Issue

**Title:** Modify stability condition and decay check

## Description

$$
( \frac{\partial }{\partial t} - D\ \nabla^2 + \lambda)\ u = 0, \ \ \ D, \lambda \in \mathbb{R}, 
$$

**Stability condition:**

Derived via von Neumann stability analysis (https://en.wikipedia.org/wiki/Von_Neumann_stability_analysis) 

$$
\left( \lambda + \frac{12 \cdot D}{h^2} \right) \Delta t \leq 2
$$

**Decay check:**

Derived by assuming positivity of u^n and demanding positivity of u^{n+1}

$$
1 - \left( \lambda + \frac{6 \cdot D} {h^2} \right) \Delta t \geq 0
$$

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `21051b24b5d0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
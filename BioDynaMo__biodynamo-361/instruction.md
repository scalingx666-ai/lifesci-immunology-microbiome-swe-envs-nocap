# Issue

**Title:** Periodic boundaries

## Description

This is the pull request for adding periodic boundaries to the diffusion grid. This is simply an extra function on top of Neumann, Dirichlet, open and closed boundaries that the user can choose from. This also includes a unit test to confirm the boundary conditions work. 

Periodic boundaries allows a diffusive substance to move from one boundary to another. This feature is the same as the taurus boundaries for agents, except it is for diffusion. An illustration can be seen below:

    |                                                               |
    | u0    u1    u2    ............     uN-2    uN-1 |
    |                                                               |

When calculating diffusion in u0, it will look at the concentration in u1 and uN-1 to determine the change. If the concentration in uN-1 is lower/higher than u0 then concentration will be transferred from/to u0. Likewise when calculating diffusion in uN-1, it will look at uN-2 and u0, and determine the change in the same way. This transfer through the boundary does not modify the total concentration in the system: it only affects how the concentration can move through the simulation space. Many biological systems simulated with BioDynaMo represent small slices of the much larger system. Periodic boundaries promotes the idea of concentration coming from "other parts" of the biological system. There is a subtle but important difference between a diffusive substance colliding with a large concentration of substances vs colliding with a solid wall.

@TobiasDuswald and @nicogno since you two implemented the Neumann and Dirichlet boundaries, I figured you would be the right people to review this update. Feel free to take a look at this request and potentially do any stress testing when you have time.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a7e48d45fd4a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
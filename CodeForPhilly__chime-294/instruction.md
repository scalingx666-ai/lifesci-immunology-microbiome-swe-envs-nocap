# Issue

**Title:** [Dash] layout update and refactor

## Description

![image](https://user-images.githubusercontent.com/17688672/77816730-5574d180-7082-11ea-87bd-8d4d88e734ae.png)

### `./src/chime_dash/app/components`
* `navbar.py` Change navbar to fixed position at top of window. Fix nested anchor elements. Move Penn Medicine logo and link from header to navbar
* `container.py` Create component that wraps sidebar and content. Add children callback inputs/outputs to own, call child callbacks, re-calculate (temporarily?) model
* `__init__.py` refactor out container class that holds sidebar and main content. Remove model re-calculation code
* `content.py` Create component that wraps all of the model presentation. Add children callback inputs/outputs to own, call child callbacks
* `sidebar.py` Style to be fixed position. Fix lint issues
* `header.py` Remove Penn Medicine anchor w/ logo moved to navbar
 
### `./src/chime_dash/app/templates/en`
* `header.yml` remove `logo-title` and `logo-text` moved to navbar

### Possible todo before merge:
* Generalize `__init__.py`, `content.py`, and `container.py` into container class.
* Move model re-calculation logic out of `container.py` callback function into ?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `51c037f2e050`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
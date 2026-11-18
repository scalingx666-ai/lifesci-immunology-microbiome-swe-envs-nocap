# Issue

**Title:** ENH: Allow users to set custom visualization settings from the Python API

## Description

When working in the Jupyter notebook, users can now set visibility, coloring, scaling and shapes from the Python API. This is perhaps better explained by the following animated gif:

![custom-settings-3](https://cloud.githubusercontent.com/assets/375307/24739091/fcc35250-1a4e-11e7-942f-87cf416a8a2d.gif)

The above demonstration is intended to show how users can call `emp.color_by('host_subject_id')` and the result will translate in the displayed plot coloring *by default* using the `host_subject_id` category. It also shows how you can put many of these calls together, for example by changing the coloring category (to `age`) and then changing the visibility (to hide one of the subjects - `M9`).

Open points
=========

- [x] Needs to add control for axes controller.
- [x] There are references from the Python documentation to the JavaScript documentation, how pertinent is this?
- [x] In order to load the user-defined-settings right now we are waiting 1 second after the UI is loaded and then we trigger a *refresh*, this is fragile and could be better.
- [x] Individual values for the different methods do not check the validity of the data i.e. the `color_by` method doesn't verify that '#fexxxx' is a valid CSS color, so this might result in a failure when loading the plot, it however, checks that the color itself is represented as a string.
- [x] All these methods return the object itself, which is not a very common thing to do in Python, but I think makes the chaining and plotting more natural, thoughts?
- [x] Probably need to add more tests that ensure multiple settings modifications work well.
- [x] Save/load settings (view, colors, etc) via commands (serialize and deserialize the `settings` property into a JSON object).

#### During code review, these points were brought up:

##### Visibility-specific

- [x] Add a negate parameter to `visibility_by`.
- [x] Visibilities would make more sense as a list

##### New feature

- [x] ~~Add a strict mode to these methods~~. This doesn't make a lot of sense for some methods.

##### Settings related

- [x] Have a global reset.
- [x] ~~Use None to clean up a category~~ this was ultimately ignored as the interface became a bit confusing.
- [x] Include a `set_settings` method.
- [x] Be able to load a set of settings altogether

##### Other

- [x] Colormaps should be listed in a table.

-------------

Please wait to merge after Code Review on Monday April 10, 2017. 🏁

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `89d521853d57`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
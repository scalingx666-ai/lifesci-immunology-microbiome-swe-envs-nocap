# Issue

**Title:** Use toastr to support showing multiple toast messages at once, with a fancy UI

## Description

This . It adds the [toastr](https://codeseven.github.io/toastr/) JS/CSS dependency, which is called from EMPress' existing `util.toastMsg()` function.

It is now possible for many toast messages to be active at once, which make the general "error message" UI much more pleasant: (note that in this GIF I'm clicking on the buttons causing each error a bunch of times, normally the user will just see at most 1-2 toast messages at a time)

![toast](https://user-images.githubusercontent.com/4177727/119764509-624bab80-be66-11eb-8d33-cc1594c4019b.gif)

It's also possible to show different "types" of toast messages, e.g. distinguishing errors from successes from warnings. Below is what an `Animation complete.` message, which we classify as `success`, looks like:

![Peek 2021-05-26 21-09](https://user-images.githubusercontent.com/4177727/119764747-d1c19b00-be66-11eb-80fd-37f8cf92f69a.gif)

This GIF also shows that it's possible to dismiss a toast by clicking on it, which is a nice feature to have.

Lastly (and unrelated to the above stuff), this PR changes the `Main CI` title to be `Main CI + McHelper`. This makes it clearer that the cause for this CI failing (as is currently shown on the README) is McHelper, not the actual CI (all the actual tests/checks pass) -- not a big deal or anything, but this hopefully gives users some confidence that our tests aren't entirely broken ;)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c950cb462246`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
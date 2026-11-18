# Issue

**Title:** Add social handles

## Description

Addressing #3404, I have extended the user profile edit page with three additional input fields to store social network handles for google scholar, research gate and orcid.
![image](https://github.com/qiita-spots/qiita/assets/11960616/9de5dd14-0a04-44b2-8608-0da76f33743e)
becomes:
![image](https://github.com/qiita-spots/qiita/assets/11960616/f987019b-8e80-4caf-8994-751b3eb9c5bc)

Note that I have added WTForm validators to check user input and provide hints if he/she provides wrong inputs. That required a bit of changes in the HTML template as well as in the UserProfileHandler.post method. I've also added small icons for the social networks, which made be use CSS flex box mechanisms to properly align the icon with the label (are we legally allowed to display those?).

Since qiita already uses WTForm mechanism, I opted to simple extend the qiita.qiita_user table by three additional columns, namely those defined by adding additional `StringField` elements. Everything else (storing, retrieving, updating) came out of the box with existing code.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ffe1ec8c40a2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
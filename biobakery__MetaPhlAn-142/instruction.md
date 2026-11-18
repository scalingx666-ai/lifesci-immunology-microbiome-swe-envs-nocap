# Issue

**Title:** Add install of database folder in setup because if database folder is…

## Description

Hello Francesco, We noticed a couple times in the past (and we ran into it again in class today) that when a user tries to uninstall MetaPhlAn it will not uninstall the databases. This can make it hard for a user to figure out how to remove the databases if they have issues with their install. On the other hand it is not straight forward or simple to figure out how to remove the databases when we remove the pip or conda packages but I think after some digging I found a small change that should work. Please review and let me know what you think.

It looks like pip will not remove any folders/files that were not originally installed with the package by setuptools. The conda packages we build are skeletons of the pypi packages so I think the same logic applies here as well with conda not removing the database folder because setuptools had not installed it. I have tested this works with pip but not yet tested with conda.

I modified the setup to install the database folder plus a small readme. I needed to change the package name in the `package_data` dictionary to get it to sync up with the package name. The build will still have the same name of "MetaPhlAn" for pypi and the package name (for python imports) will still be "metaphlan". The change will now package and install all of the files in the utility folder instead of just the *.py (module files) that were installed prior with the find_packages call. I think this is what you might have originally intended for the utils folder (to also install the R file and the nwk tree) but it was not installing these files because of the package name disconnect (because of the case change). If it is not and you did not want to include the non-python files then remove the `utils` from the package_data dictionary and you will have the same packaging as prior to my change. A non-ideal part of the change is that the database folder name "metaphlan_databases" is hard coded in two places in the code. If you wanted to I think you could add a global variable to the metaphlan.py module and import it in the setup.py file so the folder name is just in one place.

Please ping me on slack with any questions. And sorry for such a long note for a tiny change; I just wanted to pass on all the details to save you time in your review.

Thank you,
Lauren

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1bcd86f639a7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
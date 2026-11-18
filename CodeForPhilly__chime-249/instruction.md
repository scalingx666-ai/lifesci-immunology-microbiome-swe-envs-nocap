# Issue

**Title:** Add setup.py for package publishing

## Description

This PR adds a setup.py script so that `penn_chime` can be a published package that is `pip install`-able.

I tested on my local machine by running:

```
pip3 install .
```

And in a python console I'm able to import things like `penn_chime.models` and see the output of `pydoc3`

```
$ pydoc3 penn_chime.models
Help on module penn_chime.models in penn_chime:

NAME
    penn_chime.models - Models.

DESCRIPTION
    Changes affecting results or their presentation should also update
    parameters.py `change_date`, so users can see when results have last
    changed

CLASSES
    builtins.object
        SimSirModel

    class SimSirModel(builtins.object)
     |  SimSirModel(p: 'Parameters') -> 'SimSirModel'
```

I also moved the `cli.py` script into the `penn_chime` module so that it can be installed along with the package. After running the pip install, you can execute `penn_chime`

```
$ penn_chime -h
usage: penn_chime [-h] [--file FILE] [--prefix PREFIX]
                  [--current-hospitalized CURRENT_HOSPITALIZED]
                  [--doubling-time DOUBLING_TIME]
                  [--hospitalized-los HOSPITALIZED_LOS]
                  [--hospitalized-rate HOSPITALIZED_RATE] [--icu-los ICU_LOS]
                  [--icu-rate ICU_RATE] [--known-infected KNOWN_INFECTED]
                  [--market_share MARKET_SHARE] [--n-days N_DAYS]
                  [--relative-contact-rate RELATIVE_CONTACT_RATE]
                  [--susceptible SUSCEPTIBLE]
                  [--ventilated-los VENTILATED_LOS]
                  [--ventilated-rate VENTILATED_RATE]

CHIME

optional arguments:
  -h, --help            show this help message and exit
  --file FILE
  --prefix PREFIX
  --current-hospitalized CURRENT_HOSPITALIZED
  --doubling-time DOUBLING_TIME
  --hospitalized-los HOSPITALIZED_LOS
  --hospitalized-rate HOSPITALIZED_RATE
  --icu-los ICU_LOS
  --icu-rate ICU_RATE
  --known-infected KNOWN_INFECTED
  --market_share MARKET_SHARE
  --n-days N_DAYS
  --relative-contact-rate RELATIVE_CONTACT_RATE
  --susceptible SUSCEPTIBLE
  --ventilated-los VENTILATED_LOS
  --ventilated-rate VENTILATED_RATE
```

## Still to-do

This PR just adds the scripting to create the package. Running `python3 setup.py sdist bdist_wheel` in the project root will create the files in a `dist/` directory.

To complete this, someone will still need to upload the package to pypi, I _believe_ this should be accomplished by following the packaging guide: https://packaging.python.org/tutorials/packaging-projects/#uploading-the-distribution-archives

Since I'm not a maintainer, I don't want to be in control of those credentials 😄 but perhaps @quinn-dougherty or @mdbecker would be good candidates to create the account so that it can be uploaded.

Closes

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0bc279d57120`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
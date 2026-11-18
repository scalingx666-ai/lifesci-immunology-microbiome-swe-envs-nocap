# Issue

**Title:** Installation

## Description

Recently, some users had trouble with building BioDynaMo. One of them was having trouble providing the right python environment on ubuntu. To avoid that in the future, I noted down the commands that are used ubuntu/centos CI to set the right environment. Ultimately, that's what also resolved the problem for the user back than.

Another user forgot to install Xcode on macOS which we did not test for so far. Now there is a check in place to test for an Xcode installation. The same user had the problem that the homebrew package manager was not working properly and did not install all necessary packages. I added two loops that check for each brew formula individually if it has been installed or not. (Note that this adds some additional runtime to the prerequisites script.) The output is a little more verbose such that the user can now see if brew was successful or not.

1. updated error message if python not found 
  ```
  We did not find the Python interpreter from PyEnv.  Make sure you executed
    "pyenv shell " before running cmake.  If that doesn't work, run
    ./prerequisites.sh again.  The Python interpreter is required in order to
    successfully use BioDynaMo.You may also try the following sequence of
    commands that has often resolvedthe problem:
  
    export PATH="$HOME/.pyenv/bin:$PATH"
  
    eval "$(pyenv init --path)"
  
    eval "$(pyenv init -)"
  
    pyenv shell
  ```
2. MacOS output 
```
[...]
All required brew fomulae were installed successfully.
All optional brew fomulae were installed successfully.

Maybe you have seen errors of the type 'Error: <package> is already
installed'. If such an error occured in the context of one of the packages
listed on top, consider upgrading with 'brew upgrade <package>'.
```
or if something is actually missing
```
[...]
All required brew fomulae were installed successfully.
Warning: optional brew formula gsl was not installed.
Some optional brew formulae could not be installed. Please check your
log and make sure your homebrew works properly.
[...]
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3cf0a7d3a551`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
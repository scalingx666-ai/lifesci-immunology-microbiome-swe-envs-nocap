# Issue

**Title:** demonstrate mac os x problem w/bcalm

## Description

To generate problem with this branch:
```
git clone https://github.com/spacegraphcats/spacegraphcats/ -b mac_bcalm_problem
conda env create -f spacegraphcats/environment.yml -n sgc-broke2
conda activate sgc-broke2
cd spacegraphcats
make twofoo-test
```

This will generate the following error:

```
  File "/private/tmp/sgc-broke2/spacegraphcats/spacegraphcats/cdbg/bcalm_to_gxt.py", line 215, in read_bcalm
    assert not fail
AssertionError
[Tue Jul 21 06:42:06 2020]
Error in rule bcalm_catlas_input:
    jobid: 3
    output: twofoo_k31_r1/cdbg.gxt, twofoo_k31_r1/contigs.fa.gz, twofoo_k31_r1/contigs.fa.gz.info.csv
    shell:
        /Users/t/miniconda3/envs/sgc-broke2/bin/python -m spacegraphcats.cdbg.bcalm_to_gxt  -k 31 twofoo/bcalm.twofoo.k31.unitigs.fa twofoo_k31_r1/cdbg.gxt twofoo_k31_r1/contigs.fa.gz
        (one of the commands exited with non-zero exit code; note that snakemake uses bash strict mode!)
```

## the specific commands

Once all the files etc are downloaded, you can repeat just the bcalm execution and the check like so:

```
bcalm -in twofoo/bcalm.twofoo.k31.inputlist.txt -out twofoo/bcalm.twofoo.k31 -kmer-size 31 -abundance-min 1
python -m spacegraphcats.cdbg.bcalm_to_gxt  -k 31 twofoo/bcalm.twofoo.k31.unitigs.fa twofoo_k31_r1/cdbg.gxt twofoo_k31_r1/contigs.fa.gz
```

The latter command outputs a list of "broken" links in the cDBG built by bcalm --

```
reading unitigs from twofoo/bcalm.twofoo.k31.unitigs.fa
...read 206855 unitigs
19 -> 38729, but not 38729 -> 19
19 -> 115514, but not 115514 -> 19
19 -> 206484, but not 206484 -> 19
19 -> 137741, but not 137741 -> 19
18 -> 136528, but not 136528 -> 18
```
the relevant script is [bcalm_to_gxt.py](https://github.com/spacegraphcats/spacegraphcats/blob/master/spacegraphcats/cdbg/bcalm_to_gxt.py) and the errors are checking that links are bidirectional; see [specific code here](https://github.com/spacegraphcats/spacegraphcats/blob/master/spacegraphcats/cdbg/bcalm_to_gxt.py#L208).

## the conda packages in question

the bcalm package in question is `bcalm=2.2.1=hd28b015_0`; full results of conda export below.

```
name: sgc-broke2
channels:
  - r
  - bioconda
  - conda-forge
  - defaults
dependencies:
  - appdirs=1.4.3=py_1
  - attrs=19.3.0=py_0
  - bcalm=2.2.1=hd28b015_0
  - brotlipy=0.7.0=py37h9bfed18_1000
  - bz2file=0.98=py_0
  - ca-certificates=2020.6.20=hecda079_0
  - certifi=2020.6.20=py37hc8dfbb8_0
  - cffi=1.14.0=py37h356ff06_0
  - chardet=3.0.4=py37hc8dfbb8_1006
  - configargparse=1.2.3=pyh9f0ad1d_0
  - cryptography=2.9.2=py37he655712_0
  - cycler=0.10.0=py_2
  - cython=0.29.14=py37h4a8c4bd_0
  - datrie=0.8.2=py37h9bfed18_0
  - docutils=0.16=py37hc8dfbb8_1
  - freetype=2.10.2=h8da9a1a_0
  - gitdb=4.0.5=py_0
  - gitpython=3.1.3=py_0
  - idna=2.10=pyh9f0ad1d_0
  - importlib-metadata=1.7.0=py37hc8dfbb8_0
  - importlib_metadata=1.7.0=0
  - jpeg=9d=h0b31af3_0
  - jsonschema=3.2.0=py37hc8dfbb8_1
  - khmer=3.0.0a3=py37h0a44026_0
  - kiwisolver=1.2.0=py37ha1cc60f_0
  - lcms2=2.11=h174193d_0
  - libblas=3.8.0=17_openblas
  - libcblas=3.8.0=17_openblas
  - libcxx=10.0.0=h1af66ff_2
  - libffi=3.2.1=h4a8c4bd_1007
  - libgfortran=4.0.0=2
  - liblapack=3.8.0=17_openblas
  - libopenblas=0.3.10=openmp_h63d9170_3
  - libpng=1.6.37=hbbe82c9_1
  - libtiff=4.1.0=h2ae36a8_6
  - libwebp-base=1.1.0=h0b31af3_3
  - llvm-openmp=10.0.0=h28b9765_0
  - lz4-c=1.9.2=h4a8c4bd_1
  - matplotlib=3.3.0=0
  - matplotlib-base=3.3.0=py37h886f89f_0
  - more-itertools=8.4.0=py_0
  - mypy=0.750=py_0
  - mypy_extensions=0.4.3=py37hc8dfbb8_1
  - ncurses=6.2=hb1e8313_1
  - numpy=1.17.3=py37hde6bac1_0
  - olefile=0.46=py_0
  - openssl=1.1.1g=h0b31af3_0
  - packaging=20.4=pyh9f0ad1d_0
  - pandas=0.25.3=py37h4f17bb1_0
  - pillow=7.2.0=py37hfd78ece_1
  - pip=20.1.1=py_1
  - pluggy=0.13.1=py37hc8dfbb8_2
  - psutil=5.7.2=py37h60d8a13_0
  - py=1.9.0=pyh9f0ad1d_0
  - pycparser=2.20=pyh9f0ad1d_2
  - pyopenssl=19.1.0=py_1
  - pyparsing=2.4.7=pyh9f0ad1d_0
  - pyrsistent=0.16.0=py37h9bfed18_0
  - pysocks=1.7.1=py37hc8dfbb8_1
  - pytest=5.3.2=py37_0
  - python=3.7.6=cpython_h1fd5dd1_6
  - python-dateutil=2.8.1=py_0
  - python_abi=3.7=1_cp37m
  - pytz=2020.1=pyh9f0ad1d_0
  - pyyaml=5.3.1=py37h9bfed18_0
  - ratelimiter=1.2.0=py37hc8dfbb8_1001
  - readline=8.0=h0678c8f_2
  - requests=2.24.0=pyh9f0ad1d_0
  - scipy=1.5.1=py37hce1b9e5_0
  - screed=1.0.1=py_0
  - setuptools=49.2.0=py37hc8dfbb8_0
  - six=1.15.0=pyh9f0ad1d_0
  - smmap=3.0.4=pyh9f0ad1d_0
  - snakemake-minimal=5.8.1=py_0
  - sortedcontainers=2.1.0=py_0
  - sourmash=2.3.0=py37h6de7cb9_0
  - sqlite=3.32.3=h93121df_1
  - tk=8.6.10=hbbe82c9_0
  - tornado=6.0.4=py37h9bfed18_1
  - typed-ast=1.4.1=py37h0b31af3_0
  - typing_extensions=3.7.4.2=py_0
  - urllib3=1.25.9=py_0
  - wcwidth=0.2.5=pyh9f0ad1d_0
  - wheel=0.34.2=py_1
  - wrapt=1.12.1=py37h9bfed18_1
  - xz=5.2.5=h0b31af3_1
  - yajl=2.1.0=0
  - yaml=0.2.5=h0b31af3_0
  - zipp=3.1.0=py_0
  - zlib=1.2.11=h0b31af3_1006
  - zstd=1.4.5=h0384e3a_1
  - pip:
    - bbhash==0.2
    - ijson==3.1.post0
    - spacegraphcats==1.2.dev26+g6ad95ec
prefix: /Users/t/miniconda3/envs/sgc-broke2
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6ad95eca3426`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
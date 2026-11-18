# Issue

**Title:** [WIP] Add dockerfile

## Description

Hello! I kept getting lost trying to install dashing and decided to make a dockerfile for portability. I'm using Ubuntu 16.04 and used the installation commands from the README and the `.travis.yml`. Here is the build output:

<details>

```
 Tue 22 Jan - 15:10  ~/code/dashing   origin ☊ olgabot/dockerfile ✔ 
  docker build .
Sending build context to Docker daemon  321.5kB
Step 1/19 : FROM ubuntu:16.04
 ---> ccc7a11d65b1
Step 2/19 : MAINTAINER olga.botvinnik@czbiohub.org
 ---> Using cache
 ---> 83a735a5df85
Step 3/19 : WORKDIR /tmp
 ---> Using cache
 ---> c535f1546143
Step 4/19 : USER root
 ---> Using cache
 ---> c4d9ae7bee6a
Step 5/19 : ENV PACKAGES git make ca-certificates zlib1g-dev build-essential curl wget cmake
 ---> Using cache
 ---> efb5e3765624
Step 6/19 : WORKDIR /home
 ---> Using cache
 ---> 4645a55a2845
Step 7/19 : RUN apt-get update &&     apt-get install -y --no-install-recommends ${PACKAGES} &&     apt-get clean
 ---> Using cache
 ---> 10ae0f8783f1
Step 8/19 : RUN apt-get update
 ---> Using cache
 ---> 5a00d027c8e4
Step 9/19 : RUN apt-get install -y software-properties-common
 ---> Using cache
 ---> 847c08ff04f9
Step 10/19 : RUN add-apt-repository ppa:ubuntu-toolchain-r/test
 ---> Using cache
 ---> 1ab3dbcd27ae
Step 11/19 : RUN apt-get update && apt-get install -y g++-6
 ---> Using cache
 ---> 9dc0fdca6883
Step 12/19 : RUN g++ --version
 ---> Running in 30e3429c0b7d
g++ (Ubuntu 5.4.0-6ubuntu1~16.04.11) 5.4.0 20160609
Copyright (C) 2015 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

Removing intermediate container 30e3429c0b7d
 ---> 9c9833cb0e86
Step 13/19 : RUN update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-6 60 --slave /usr/bin/g++ g++ /usr/bin/g++-6
 ---> Running in 570523415cc9
update-alternatives: using /usr/bin/gcc-6 to provide /usr/bin/gcc (gcc) in auto mode
Removing intermediate container 570523415cc9
 ---> 8775ba3dd7e6
Step 14/19 : WORKDIR /
 ---> Running in 78b1aeeea61f
Removing intermediate container 78b1aeeea61f
 ---> 9eb23b7dfac4
Step 15/19 : RUN git clone https://github.com/dnbaker/dashing/
 ---> Running in 2b5c9e5f4ef9
Cloning into 'dashing'...
Removing intermediate container 2b5c9e5f4ef9
 ---> dc416750bc63
Step 16/19 : WORKDIR /dashing
 ---> Running in aa7d65a04a23
Removing intermediate container aa7d65a04a23
 ---> fa4710ae78a0
Step 17/19 : RUN pwd
 ---> Running in 705437fb45ca
/dashing
Removing intermediate container 705437fb45ca
 ---> e7751519965c
Step 18/19 : RUN make update dashing
 ---> Running in 1688b3fcf6aa
git submodule update --init --remote --recursive . && cd bonsai && git checkout master && git pull && make update && \
    cd linear && git checkout master && git pull && cd .. && cd .. && cd distmat && git checkout master && git pull && cd ..
Submodule 'bonsai' (https://github.com/dnbaker/bonsai) registered for path 'bonsai'
Submodule 'distmat' (https://github.com/dnbaker/distmat) registered for path 'distmat'
Cloning into 'bonsai'...
Submodule path 'bonsai': checked out 'd1dac2a5910153a3a13c35585c01ffd365bb4fe9'
Submodule 'circularqueue' (https://github.com/dnbaker/circularqueue) registered for path 'circularqueue'
Submodule 'clhash' (https://github.com/lemire/clhash) registered for path 'clhash'
Submodule 'hll' (https://github.com/dnbaker/sketch) registered for path 'hll'
Submodule 'klib' (https://github.com/dnbaker/klib) registered for path 'klib'
Submodule 'kspp' (https://github.com/dnbaker/kspp) registered for path 'kspp'
Submodule 'lazy' (https://github.com/dnbaker/lazy) registered for path 'lazy'
Submodule 'libpopcnt' (https://github.com/kimwalisch/libpopcnt) registered for path 'libpopcnt'
Submodule 'linear' (https://github.com/dnbaker/linear) registered for path 'linear'
Submodule 'pdqsort' (https://github.com/orlp/pdqsort) registered for path 'pdqsort'
Cloning into 'circularqueue'...
Submodule path 'bonsai/circularqueue': checked out '131e12b00541cae9b62007dc33061e0df47e540e'
Cloning into 'clhash'...
Submodule path 'bonsai/clhash': checked out '5511441cf3ae2c4f064e2e2950e754eb2033b56c'
Cloning into 'hll'...
Submodule path 'bonsai/hll': checked out 'a514ad82914c4a5a152c70f32e579adbb4f20f4e'
Submodule 'aesctr' (https://github.com/dnbaker/aesctr) registered for path 'aesctr'
Submodule 'compact_vector' (https://github.com/gmarcais/compact_vector) registered for path 'compact_vector'
Submodule 'libpopcnt' (https://github.com/kimwalisch/libpopcnt) registered for path 'libpopcnt'
Submodule 'pybind11' (https://github.com/pybind/pybind11) registered for path 'pybind11'
Submodule 'vec' (https://github.com/dnbaker/vec) registered for path 'vec'
Cloning into 'aesctr'...
Submodule path 'bonsai/hll/aesctr': checked out 'ffdfd2ad949b90d6b286ef97308fdcd1c17f63d9'
Cloning into 'compact_vector'...
Submodule path 'bonsai/hll/compact_vector': checked out '87301b3cf5120676fa8e122ac1054aa038ee78ca'
Cloning into 'libpopcnt'...
Submodule path 'bonsai/hll/libpopcnt': checked out '79219c154c72550ec8bc325a7e5db004db6041cc'
Cloning into 'pybind11'...
Submodule path 'bonsai/hll/pybind11': checked out '085a29436a8c472caaaf7157aa644b571079bcaa'
Submodule 'tools/clang' (https://github.com/wjakob/clang-cindex-python3) registered for path 'tools/clang'
Cloning into 'tools/clang'...
Submodule path 'bonsai/hll/pybind11/tools/clang': checked out '6a00cbc4a9b8e68b71caf7f774b3f9c753ae84d5'
Cloning into 'vec'...
Submodule path 'bonsai/hll/vec': checked out '9c27d421cf32aacfe8516572381adeaebb6cf921'
Submodule 'blaze' (https://bitbucket.org/blaze-lib/blaze.git) registered for path 'blaze'
Submodule 'sleef' (https://github.com/shibatch/sleef) registered for path 'sleef'
Cloning into 'blaze'...
Submodule path 'bonsai/hll/vec/blaze': checked out '92ef7875b49177e428c872e7e31ca7813fd35bd3'
Cloning into 'sleef'...
Submodule path 'bonsai/hll/vec/sleef': checked out 'ae55d715d79f79ca01fbb367b96a89e74ffffcff'
Cloning into 'klib'...
Submodule path 'bonsai/klib': checked out 'f0f7639be2dd75a56a885df8bddea4f86bba7bee'
Cloning into 'kspp'...
Submodule path 'bonsai/kspp': checked out '6a49a53a986e0e96f93443549251de6cff777aae'
Submodule 'klib' (https://github.com/attractivechaos/klib) registered for path 'klib'
Cloning into 'klib'...
Submodule path 'bonsai/kspp/klib': checked out '5fc2090766753bdaa9e53e0cc0734b285a891c85'
Cloning into 'lazy'...
Submodule path 'bonsai/lazy': checked out '2234ed49decbe628054f13dc45216139cb8a51b0'
Cloning into 'libpopcnt'...
Submodule path 'bonsai/libpopcnt': checked out '79219c154c72550ec8bc325a7e5db004db6041cc'
Cloning into 'linear'...
Submodule path 'bonsai/linear': checked out '0aa224367a0f09b5c3e5c90c715e3ff8fb2ffad3'
Cloning into 'pdqsort'...
Submodule path 'bonsai/pdqsort': checked out '08879029ab8dcb80a70142acb709e3df02de5d37'
Cloning into 'distmat'...
Submodule path 'distmat': checked out '3ffee11dc51a4cfeb562ca6d04ce46d3cb42db39'
Switched to branch 'master'
M	hll
Your branch is up-to-date with 'origin/master'.
Already up-to-date.
make[1]: Entering directory '/dashing/bonsai'
make update -C bonsai
make[2]: Entering directory '/dashing/bonsai/bonsai'
for i in circularqueue clhash cppitertools hll klib kspp libpopcnt linear pdqsort tinythreadpp; \
        do cd ../$i && git checkout master && git pull && cd ../bonsai; done; \
cd ../hll/vec && git checkout master && git pull && cd ../../bonsai
Switched to branch 'master'
Your branch is up-to-date with 'origin/master'.
Already up-to-date.
Switched to branch 'master'
Your branch is up-to-date with 'origin/master'.
Already up-to-date.
/bin/sh: 2: cd: can't cd to ../cppitertools
Switched to branch 'master'
M	aesctr
Your branch is up-to-date with 'origin/master'.
Already up-to-date.
Switched to branch 'master'
Your branch is up-to-date with 'origin/master'.
Already up-to-date.
Switched to branch 'master'
Your branch is up-to-date with 'origin/master'.
Already up-to-date.
Switched to branch 'master'
Your branch is up-to-date with 'origin/master'.
Already up-to-date.
Switched to branch 'master'
Your branch is up-to-date with 'origin/master'.
Already up-to-date.
Switched to branch 'master'
Your branch is up-to-date with 'origin/master'.
Already up-to-date.
Already on 'master'
M	hll
Your branch is up-to-date with 'origin/master'.
Already up-to-date.
Switched to branch 'master'
Your branch is up-to-date with 'origin/master'.
Already up-to-date.
make[2]: Leaving directory '/dashing/bonsai/bonsai'
make[1]: Leaving directory '/dashing/bonsai'
Already on 'master'
Your branch is up-to-date with 'origin/master'.
Already up-to-date.
Switched to branch 'master'
Your branch is up-to-date with 'origin/master'.
Already up-to-date.
cd bonsai/bonsai && make libzstd.a && cp libzstd.a ../../
make[1]: Entering directory '/dashing/bonsai/bonsai'
cd .. && git clone --recursive https://github.com/facebook/zstd
Cloning into 'zstd'...
cd ../zstd && make lib && mv lib/libzstd.a ../bonsai && cd ../bonsai
make[2]: Entering directory '/dashing/bonsai/zstd'
make[3]: Entering directory '/dashing/bonsai/zstd/lib'
cc -O3 -Wall -Wextra -Wcast-qual -Wcast-align -Wshadow -Wstrict-aliasing=1 -Wswitch-enum -Wdeclaration-after-statement -Wstrict-prototypes -Wundef -Wpointer-arith -Wformat-security -Wvla -Wformat=2 -Winit-self -Wfloat-equal -Wwrite-strings -Wredundant-decls -Wmissing-prototypes -Wc++-compat  -I. -I./common -DXXH_NAMESPACE=ZSTD_ -I./legacy -DZSTD_LEGACY_SUPPORT=5  -c -o common/debug.o common/debug.c
cc -O3 -Wall -Wextra -Wcast-qual -Wcast-align -Wshadow -Wstrict-aliasing=1 -Wswitch-enum -Wdeclaration-after-statement -Wstrict-prototypes -Wundef -Wpointer-arith -Wformat-security -Wvla -Wformat=2 -Winit-self -Wfloat-equal -Wwrite-strings -Wredundant-decls -Wmissing-prototypes -Wc++-compat  -I. -I./common -DXXH_NAMESPACE=ZSTD_ -I./legacy -DZSTD_LEGACY_SUPPORT=5  -c -o common/entropy_common.o common/entropy_common.c
cc -O3 -Wall -Wextra -Wcast-qual -Wcast-align -Wshadow -Wstrict-aliasing=1 -Wswitch-enum -Wdeclaration-after-statement -Wstrict-prototypes -Wundef -Wpointer-arith -Wformat-security -Wvla -Wformat=2 -Winit-self -Wfloat-equal -Wwrite-strings -Wredundant-decls -Wmissing-prototypes -Wc++-compat  -I. -I./common -DXXH_NAMESPACE=ZSTD_ -I./legacy -DZSTD_LEGACY_SUPPORT=5  -c -o common/error_private.o common/error_private.c
cc -O3 -Wall -Wextra -Wcast-qual -Wcast-align -Wshadow -Wstrict-aliasing=1 -Wswitch-enum -Wdeclaration-after-statement -Wstrict-prototypes -Wundef -Wpointer-arith -Wformat-security -Wvla -Wformat=2 -Winit-self -Wfloat-equal -Wwrite-strings -Wredundant-decls -Wmissing-prototypes -Wc++-compat  -I. -I./common -DXXH_NAMESPACE=ZSTD_ -I./legacy -DZSTD_LEGACY_SUPPORT=5  -c -o common/fse_decompress.o common/fse_decompress.c
cc -O3 -Wall -Wextra -Wcast-qual -Wcast-align -Wshadow -Wstrict-aliasing=1 -Wswitch-enum -Wdeclaration-after-statement -Wstrict-prototypes -Wundef -Wpointer-arith -Wformat-security -Wvla -Wformat=2 -Winit-self -Wfloat-equal -Wwrite-strings -Wredundant-decls -Wmissing-prototypes -Wc++-compat  -I. -I./common -DXXH_NAMESPACE=ZSTD_ -I./legacy -DZSTD_LEGACY_SUPPORT=5  -c -o common/pool.o common/pool.c
cc -O3 -Wall -Wextra -Wcast-qual -Wcast-align -Wshadow -Wstrict-aliasing=1 -Wswitch-enum -Wdeclaration-after-statement -Wstrict-prototypes -Wundef -Wpointer-arith -Wformat-security -Wvla -Wformat=2 -Winit-self -Wfloat-equal -Wwrite-strings -Wredundant-decls -Wmissing-prototypes -Wc++-compat  -I. -I./common -DXXH_NAMESPACE=ZSTD_ -I./legacy -DZSTD_LEGACY_SUPPORT=5  -c -o common/threading.o common/threading.c
cc -O3 -Wall -Wextra -Wcast-qual -Wcast-align -Wshadow -Wstrict-aliasing=1 -Wswitch-enum -Wdeclaration-after-statement -Wstrict-prototypes -Wundef -Wpointer-arith -Wformat-security -Wvla -Wformat=2 -Winit-self -Wfloat-equal -Wwrite-strings -Wredundant-decls -Wmissing-prototypes -Wc++-compat  -I. -I./common -DXXH_NAMESPACE=ZSTD_ -I./legacy -DZSTD_LEGACY_SUPPORT=5  -c -o common/xxhash.o common/xxhash.c
cc -O3 -Wall -Wextra -Wcast-qual -Wcast-align -Wshadow -Wstrict-aliasing=1 -Wswitch-enum -Wdeclaration-after-statement -Wstrict-prototypes -Wundef -Wpointer-arith -Wformat-security -Wvla -Wformat=2 -Winit-self -Wfloat-equal -Wwrite-strings -Wredundant-decls -Wmissing-prototypes -Wc++-compat  -I. -I./common -DXXH_NAMESPACE=ZSTD_ -I./legacy -DZSTD_LEGACY_SUPPORT=5  -c -o common/zstd_common.o common/zstd_common.c
cc -O3 -Wall -Wextra -Wcast-qual -Wcast-align -Wshadow -Wstrict-aliasing=1 -Wswitch-enum -Wdeclaration-after-statement -Wstrict-prototypes -Wundef -Wpointer-arith -Wformat-security -Wvla -Wformat=2 -Winit-self -Wfloat-equal -Wwrite-strings -Wredundant-decls -Wmissing-prototypes -Wc++-compat  -I. -I./common -DXXH_NAMESPACE=ZSTD_ -I./legacy -DZSTD_LEGACY_SUPPORT=5  -c -o compress/fse_compress.o compress/fse_compress.c
cc -O3 -Wall -Wextra -Wcast-qual -Wcast-align -Wshadow -Wstrict-aliasing=1 -Wswitch-enum -Wdeclaration-after-statement -Wstrict-prototypes -Wundef -Wpointer-arith -Wformat-security -Wvla -Wformat=2 -Winit-self -Wfloat-equal -Wwrite-strings -Wredundant-decls -Wmissing-prototypes -Wc++-compat  -I. -I./common -DXXH_NAMESPACE=ZSTD_ -I./legacy -DZSTD_LEGACY_SUPPORT=5  -c -o compress/hist.o compress/hist.c
cc -O3 -Wall -Wextra -Wcast-qual -Wcast-align -Wshadow -Wstrict-aliasing=1 -Wswitch-enum -Wdeclaration-after-statement -Wstrict-prototypes -Wundef -Wpointer-arith -Wformat-security -Wvla -Wformat=2 -Winit-self -Wfloat-equal -Wwrite-strings -Wredundant-decls -Wmissing-prototypes -Wc++-compat  -I. -I./common -DXXH_NAMESPACE=ZSTD_ -I./legacy -DZSTD_LEGACY_SUPPORT=5  -c -o compress/huf_compress.o compress/huf_compress.c
cc -O3 -Wall -Wextra -Wcast-qual -Wcast-align -Wshadow -Wstrict-aliasing=1 -Wswitch-enum -Wdeclaration-after-statement -Wstrict-prototypes -Wundef -Wpointer-arith -Wformat-security -Wvla -Wformat=2 -Winit-self -Wfloat-equal -Wwrite-strings -Wredundant-decls -Wmissing-prototypes -Wc++-compat  -I. -I./common -DXXH_NAMESPACE=ZSTD_ -I./legacy -DZSTD_LEGACY_SUPPORT=5  -c -o compress/zstd_compress.o compress/zstd_compress.c
cc -O3 -Wall -Wextra -Wcast-qual -Wcast-align -Wshadow -Wstrict-aliasing=1 -Wswitch-enum -Wdeclaration-after-statement -Wstrict-prototypes -Wundef -Wpointer-arith -Wformat-security -Wvla -Wformat=2 -Winit-self -Wfloat-equal -Wwrite-strings -Wredundant-decls -Wmissing-prototypes -Wc++-compat  -I. -I./common -DXXH_NAMESPACE=ZSTD_ -I./legacy -DZSTD_LEGACY_SUPPORT=5  -c -o compress/zstd_double_fast.o compress/zstd_double_fast.c
cc -O3 -Wall -Wextra -Wcast-qual -Wcast-align -Wshadow -Wstrict-aliasing=1 -Wswitch-enum -Wdeclaration-after-statement -Wstrict-prototypes -Wundef -Wpointer-arith -Wformat-security -Wvla -Wformat=2 -Winit-self -Wfloat-equal -Wwrite-strings -Wredundant-decls -Wmissing-prototypes -Wc++-compat  -I. -I./common -DXXH_NAMESPACE=ZSTD_ -I./legacy -DZSTD_LEGACY_SUPPORT=5  -c -o compress/zstd_fast.o compress/zstd_fast.c
cc -O3 -Wall -Wextra -Wcast-qual -Wcast-align -Wshadow -Wstrict-aliasing=1 -Wswitch-enum -Wdeclaration-after-statement -Wstrict-prototypes -Wundef -Wpointer-arith -Wformat-security -Wvla -Wformat=2 -Winit-self -Wfloat-equal -Wwrite-strings -Wredundant-decls -Wmissing-prototypes -Wc++-compat  -I. -I./common -DXXH_NAMESPACE=ZSTD_ -I./legacy -DZSTD_LEGACY_SUPPORT=5  -c -o compress/zstd_lazy.o compress/zstd_lazy.c
cc -O3 -Wall -Wextra -Wcast-qual -Wcast-align -Wshadow -Wstrict-aliasing=1 -Wswitch-enum -Wdeclaration-after-statement -Wstrict-prototypes -Wundef -Wpointer-arith -Wformat-security -Wvla -Wformat=2 -Winit-self -Wfloat-equal -Wwrite-strings -Wredundant-decls -Wmissing-prototypes -Wc++-compat  -I. -I./common -DXXH_NAMESPACE=ZSTD_ -I./legacy -DZSTD_LEGACY_SUPPORT=5  -c -o compress/zstd_ldm.o compress/zstd_ldm.c
cc -O3 -Wall -Wextra -Wcast-qual -Wcast-align -Wshadow -Wstrict-aliasing=1 -Wswitch-enum -Wdeclaration-after-statement -Wstrict-prototypes -Wundef -Wpointer-arith -Wformat-security -Wvla -Wformat=2 -Winit-self -Wfloat-equal -Wwrite-strings -Wredundant-decls -Wmissing-prototypes -Wc++-compat  -I. -I./common -DXXH_NAMESPACE=ZSTD_ -I./legacy -DZSTD_LEGACY_SUPPORT=5  -c -o compress/zstd_opt.o compress/zstd_opt.c
cc -O3 -Wall -Wextra -Wcast-qual -Wcast-align -Wshadow -Wstrict-aliasing=1 -Wswitch-enum -Wdeclaration-after-statement -Wstrict-prototypes -Wundef -Wpointer-arith -Wformat-security -Wvla -Wformat=2 -Winit-self -Wfloat-equal -Wwrite-strings -Wredundant-decls -Wmissing-prototypes -Wc++-compat  -I. -I./common -DXXH_NAMESPACE=ZSTD_ -I./legacy -DZSTD_LEGACY_SUPPORT=5  -c -o compress/zstdmt_compress.o compress/zstdmt_compress.c
cc -O3 -Wall -Wextra -Wcast-qual -Wcast-align -Wshadow -Wstrict-aliasing=1 -Wswitch-enum -Wdeclaration-after-statement -Wstrict-prototypes -Wundef -Wpointer-arith -Wformat-security -Wvla -Wformat=2 -Winit-self -Wfloat-equal -Wwrite-strings -Wredundant-decls -Wmissing-prototypes -Wc++-compat  -I. -I./common -DXXH_NAMESPACE=ZSTD_ -I./legacy -DZSTD_LEGACY_SUPPORT=5  -c -o decompress/huf_decompress.o decompress/huf_decompress.c
cc -O3 -Wall -Wextra -Wcast-qual -Wcast-align -Wshadow -Wstrict-aliasing=1 -Wswitch-enum -Wdeclaration-after-statement -Wstrict-prototypes -Wundef -Wpointer-arith -Wformat-security -Wvla -Wformat=2 -Winit-self -Wfloat-equal -Wwrite-strings -Wredundant-decls -Wmissing-prototypes -Wc++-compat  -I. -I./common -DXXH_NAMESPACE=ZSTD_ -I./legacy -DZSTD_LEGACY_SUPPORT=5  -c -o decompress/zstd_ddict.o decompress/zstd_ddict.c
cc -O3 -Wall -Wextra -Wcast-qual -Wcast-align -Wshadow -Wstrict-aliasing=1 -Wswitch-enum -Wdeclaration-after-statement -Wstrict-prototypes -Wundef -Wpointer-arith -Wformat-security -Wvla -Wformat=2 -Winit-self -Wfloat-equal -Wwrite-strings -Wredundant-decls -Wmissing-prototypes -Wc++-compat  -I. -I./common -DXXH_NAMESPACE=ZSTD_ -I./legacy -DZSTD_LEGACY_SUPPORT=5  -c -o decompress/zstd_decompress.o decompress/zstd_decompress.c
cc -O3 -Wall -Wextra -Wcast-qual -Wcast-align -Wshadow -Wstrict-aliasing=1 -Wswitch-enum -Wdeclaration-after-statement -Wstrict-prototypes -Wundef -Wpointer-arith -Wformat-security -Wvla -Wformat=2 -Winit-self -Wfloat-equal -Wwrite-strings -Wredundant-decls -Wmissing-prototypes -Wc++-compat  -I. -I./common -DXXH_NAMESPACE=ZSTD_ -I./legacy -DZSTD_LEGACY_SUPPORT=5  -c -o decompress/zstd_decompress_block.o decompress/zstd_decompress_block.c
cc -O3 -Wall -Wextra -Wcast-qual -Wcast-align -Wshadow -Wstrict-aliasing=1 -Wswitch-enum -Wdeclaration-after-statement -Wstrict-prototypes -Wundef -Wpointer-arith -Wformat-security -Wvla -Wformat=2 -Winit-self -Wfloat-equal -Wwrite-strings -Wredundant-decls -Wmissing-prototypes -Wc++-compat  -I. -I./common -DXXH_NAMESPACE=ZSTD_ -I./legacy -DZSTD_LEGACY_SUPPORT=5  -c -o deprecated/zbuff_common.o deprecated/zbuff_common.c
cc -O3 -Wall -Wextra -Wcast-qual -Wcast-align -Wshadow -Wstrict-aliasing=1 -Wswitch-enum -Wdeclaration-after-statement -Wstrict-prototypes -Wundef -Wpointer-arith -Wformat-security -Wvla -Wformat=2 -Winit-self -Wfloat-equal -Wwrite-strings -Wredundant-decls -Wmissing-prototypes -Wc++-compat  -I. -I./common -DXXH_NAMESPACE=ZSTD_ -I./legacy -DZSTD_LEGACY_SUPPORT=5  -c -o deprecated/zbuff_compress.o deprecated/zbuff_compress.c
cc -O3 -Wall -Wextra -Wcast-qual -Wcast-align -Wshadow -Wstrict-aliasing=1 -Wswitch-enum -Wdeclaration-after-statement -Wstrict-prototypes -Wundef -Wpointer-arith -Wformat-security -Wvla -Wformat=2 -Winit-self -Wfloat-equal -Wwrite-strings -Wredundant-decls -Wmissing-prototypes -Wc++-compat  -I. -I./common -DXXH_NAMESPACE=ZSTD_ -I./legacy -DZSTD_LEGACY_SUPPORT=5  -c -o deprecated/zbuff_decompress.o deprecated/zbuff_decompress.c
cc -O3 -Wall -Wextra -Wcast-qual -Wcast-align -Wshadow -Wstrict-aliasing=1 -Wswitch-enum -Wdeclaration-after-statement -Wstrict-prototypes -Wundef -Wpointer-arith -Wformat-security -Wvla -Wformat=2 -Winit-self -Wfloat-equal -Wwrite-strings -Wredundant-decls -Wmissing-prototypes -Wc++-compat  -I. -I./common -DXXH_NAMESPACE=ZSTD_ -I./legacy -DZSTD_LEGACY_SUPPORT=5  -c -o dictBuilder/cover.o dictBuilder/cover.c
cc -O3 -Wall -Wextra -Wcast-qual -Wcast-align -Wshadow -Wstrict-aliasing=1 -Wswitch-enum -Wdeclaration-after-statement -Wstrict-prototypes -Wundef -Wpointer-arith -Wformat-security -Wvla -Wformat=2 -Winit-self -Wfloat-equal -Wwrite-strings -Wredundant-decls -Wmissing-prototypes -Wc++-compat  -I. -I./common -DXXH_NAMESPACE=ZSTD_ -I./legacy -DZSTD_LEGACY_SUPPORT=5  -c -o dictBuilder/divsufsort.o dictBuilder/divsufsort.c
cc -O3 -Wall -Wextra -Wcast-qual -Wcast-align -Wshadow -Wstrict-aliasing=1 -Wswitch-enum -Wdeclaration-after-statement -Wstrict-prototypes -Wundef -Wpointer-arith -Wformat-security -Wvla -Wformat=2 -Winit-self -Wfloat-equal -Wwrite-strings -Wredundant-decls -Wmissing-prototypes -Wc++-compat  -I. -I./common -DXXH_NAMESPACE=ZSTD_ -I./legacy -DZSTD_LEGACY_SUPPORT=5  -c -o dictBuilder/fastcover.o dictBuilder/fastcover.c
cc -O3 -Wall -Wextra -Wcast-qual -Wcast-align -Wshadow -Wstrict-aliasing=1 -Wswitch-enum -Wdeclaration-after-statement -Wstrict-prototypes -Wundef -Wpointer-arith -Wformat-security -Wvla -Wformat=2 -Winit-self -Wfloat-equal -Wwrite-strings -Wredundant-decls -Wmissing-prototypes -Wc++-compat  -I. -I./common -DXXH_NAMESPACE=ZSTD_ -I./legacy -DZSTD_LEGACY_SUPPORT=5  -c -o dictBuilder/zdict.o dictBuilder/zdict.c
cc -O3 -Wall -Wextra -Wcast-qual -Wcast-align -Wshadow -Wstrict-aliasing=1 -Wswitch-enum -Wdeclaration-after-statement -Wstrict-prototypes -Wundef -Wpointer-arith -Wformat-security -Wvla -Wformat=2 -Winit-self -Wfloat-equal -Wwrite-strings -Wredundant-decls -Wmissing-prototypes -Wc++-compat  -I. -I./common -DXXH_NAMESPACE=ZSTD_ -I./legacy -DZSTD_LEGACY_SUPPORT=5  -c -o legacy/zstd_v05.o legacy/zstd_v05.c
cc -O3 -Wall -Wextra -Wcast-qual -Wcast-align -Wshadow -Wstrict-aliasing=1 -Wswitch-enum -Wdeclaration-after-statement -Wstrict-prototypes -Wundef -Wpointer-arith -Wformat-security -Wvla -Wformat=2 -Winit-self -Wfloat-equal -Wwrite-strings -Wredundant-decls -Wmissing-prototypes -Wc++-compat  -I. -I./common -DXXH_NAMESPACE=ZSTD_ -I./legacy -DZSTD_LEGACY_SUPPORT=5  -c -o legacy/zstd_v06.o legacy/zstd_v06.c
cc -O3 -Wall -Wextra -Wcast-qual -Wcast-align -Wshadow -Wstrict-aliasing=1 -Wswitch-enum -Wdeclaration-after-statement -Wstrict-prototypes -Wundef -Wpointer-arith -Wformat-security -Wvla -Wformat=2 -Winit-self -Wfloat-equal -Wwrite-strings -Wredundant-decls -Wmissing-prototypes -Wc++-compat  -I. -I./common -DXXH_NAMESPACE=ZSTD_ -I./legacy -DZSTD_LEGACY_SUPPORT=5  -c -o legacy/zstd_v07.o legacy/zstd_v07.c
compiling static library
compiling dynamic library 1.3.8
creating versioned links
make[3]: Leaving directory '/dashing/bonsai/zstd/lib'
make[2]: Leaving directory '/dashing/bonsai/zstd'
make[1]: Leaving directory '/dashing/bonsai/bonsai'
cd bonsai/bonsai && make ../klib/kstring.o && cd ../.. && \
cd bonsai/bonsai && make ../klib/kthread.o && cd ../..
make[1]: Entering directory '/dashing/bonsai/bonsai'
gcc  -Iclhash/include -I. -I.. -I../libpopcnt -I.. -Iinclude -I../circularqueue -I../zstd/zlibWrapper -I../zstd/lib/common -I../zstd/lib  -I../hll/vec -I../hll -I../pdqsort -DNDEBUG -c ../klib/kstring.c -o ../klib/kstring.o -lz
make[1]: Leaving directory '/dashing/bonsai/bonsai'
make[1]: Entering directory '/dashing/bonsai/bonsai'
gcc  -Iclhash/include -I. -I.. -I../libpopcnt -I.. -Iinclude -I../circularqueue -I../zstd/zlibWrapper -I../zstd/lib/common -I../zstd/lib  -I../hll/vec -I../hll -I../pdqsort -DNDEBUG -c ../klib/kthread.c -o ../klib/kthread.o -lz
make[1]: Leaving directory '/dashing/bonsai/bonsai'
cd bonsai/bonsai && make clhash.o && cd ../..
make[1]: Entering directory '/dashing/bonsai/bonsai'
ls clhash.o 2>/dev/null || mv ../clhash/clhash.o . 2>/dev/null || (cd ../clhash "&& git checkout master" && make && cd ../bonsai && ln -s ../clhash/clhash.o .)
make[2]: Entering directory '/dashing/bonsai/clhash'
cc -fPIC -std=c99 -O3 -msse4.2 -mpclmul -march=native -funroll-loops -Wstrict-overflow -Wstrict-aliasing -Wall -Wextra -pedantic -Wshadow -c ./src/clhash.c -Iinclude
cc -fPIC -std=c99 -O3 -msse4.2 -mpclmul -march=native -funroll-loops -Wstrict-overflow -Wstrict-aliasing -Wall -Wextra -pedantic -Wshadow -o unit ./tests/unit.c -Iinclude  clhash.o
g++ -fPIC -std=c++11 -O3 -msse4.2 -mpclmul -march=native -funroll-loops -Wstrict-overflow -Wstrict-aliasing -Wall -Wextra -pedantic -Wshadow -o cppunit ./tests/cppunit.cpp -Iinclude  clhash.o
cc -fPIC -std=c99 -O3 -msse4.2 -mpclmul -march=native -funroll-loops -Wstrict-overflow -Wstrict-aliasing -Wall -Wextra -pedantic -Wshadow -o benchmark ./benchmarks/benchmark.c -Iinclude  clhash.o
cc -fPIC -std=c99 -O3 -msse4.2 -mpclmul -march=native -funroll-loops -Wstrict-overflow -Wstrict-aliasing -Wall -Wextra -pedantic -Wshadow -o example example.c -Iinclude  clhash.o
g++ -fPIC -std=c++11 -O3 -msse4.2 -mpclmul -march=native -funroll-loops -Wstrict-overflow -Wstrict-aliasing -Wall -Wextra -pedantic -Wshadow -o cppexample cppexample.cpp -Iinclude  clhash.o
make[2]: Leaving directory '/dashing/bonsai/clhash'
make[1]: Leaving directory '/dashing/bonsai/bonsai'
g++ -O3 -funroll-loops -pipe -fno-strict-aliasing -march=native -mpclmul -DUSE_PDQSORT -DNOT_THREADSAFE -DENABLE_COMPUTED_GOTO   -fopenmp -fno-rtti -std=c++14 -Wall -Wextra -Wno-char-subscripts -Wpointer-arith -Wwrite-strings -Wdisabled-optimization -Wformat -Wcast-align -Wno-unused-function -Wno-unused-parameter -pedantic -Wunused-variable -Wno-attributes -Wno-pedantic   -Ibonsai/clhash/include -I.  -Ibonsai/zlib -Ibonsai/libpopcnt -Iinclude -Ibonsai/circularqueue -Ibonsai/zstd/zlibWrapper -Ibonsai/zstd/lib/common -Ibonsai/zstd/lib  -Ibonsai/hll -Ibonsai/hll/vec -Ibonsai -Ibonsai/bonsai/include/ -L.  -Lbonsai/zlib bonsai/klib/kstring.o bonsai/klib/kthread.o bonsai/bonsai/clhash.o -DNDEBUG src/dashing.cpp -o dashing -lz
In file included from bonsai/hll/cbf.h:5:0,
                 from bonsai/hll/filterhll.h:5,
                 from ./bonsai/bonsai/include/encoder.h:11,
                 from ./bonsai/bonsai/include/database.h:4,
                 from src/dashing.cpp:5:
bonsai/hll/aesctr/aesctr.h:42:37: warning: ignoring attributes on template argument '__m128i {aka __vector(2) long long int}' [-Wignored-attributes]
     template<>struct is_simd<__m128i>: std::true_type {};
                                     ^
bonsai/hll/aesctr/aesctr.h:43:36: warning: ignoring attributes on template argument '__m128 {aka __vector(4) float}' [-Wignored-attributes]
     template<>struct is_simd<__m128>:  std::true_type {};
                                    ^
bonsai/hll/aesctr/aesctr.h:44:41: warning: ignoring attributes on template argument '__m128i {aka __vector(2) long long int}' [-Wignored-attributes]
     template<>struct is_simd_int<__m128i>: std::true_type {};
                                         ^
bonsai/hll/aesctr/aesctr.h:45:42: warning: ignoring attributes on template argument '__m128 {aka __vector(4) float}' [-Wignored-attributes]
     template<>struct is_simd_float<__m128>: std::true_type {};
                                          ^
bonsai/hll/aesctr/aesctr.h:48:37: warning: ignoring attributes on template argument '__m256i {aka __vector(4) long long int}' [-Wignored-attributes]
     template<>struct is_simd<__m256i>: std::true_type {};
                                     ^
bonsai/hll/aesctr/aesctr.h:49:36: warning: ignoring attributes on template argument '__m256 {aka __vector(8) float}' [-Wignored-attributes]
     template<>struct is_simd<__m256>:  std::true_type {};
                                    ^
bonsai/hll/aesctr/aesctr.h:50:41: warning: ignoring attributes on template argument '__m256i {aka __vector(4) long long int}' [-Wignored-attributes]
     template<>struct is_simd_int<__m256i>: std::true_type {};
                                         ^
bonsai/hll/aesctr/aesctr.h:51:42: warning: ignoring attributes on template argument '__m256 {aka __vector(8) float}' [-Wignored-attributes]
     template<>struct is_simd_float<__m256>: std::true_type {};
                                          ^
In file included from ./bonsai/bonsai/include/entropy.h:2:0,
                 from ./bonsai/bonsai/include/encoder.h:12,
                 from ./bonsai/bonsai/include/database.h:4,
                 from src/dashing.cpp:5:
bonsai/circularqueue/circular_buffer.h: In instantiation of 'T circ::roundup(T) [with T = unsigned int]':
bonsai/circularqueue/circular_buffer.h:147:26:   required from 'circ::FastCircularQueue<T, SizeType>::FastCircularQueue(SizeType) [with T = bns::ElScore<long unsigned int, long unsigned int>; SizeType = unsigned int]'
./bonsai/bonsai/include/qmap.h:46:47:   required from 'bns::QueueMap<T, ScoreType>::QueueMap(std::size_t) [with T = long unsigned int; ScoreType = long unsigned int; std::size_t = long unsigned int]'
./bonsai/bonsai/include/encoder.h:154:33:   required from 'bns::Encoder<ScoreType>::Encoder(char*, bns::u64, const bns::Spacer&, void*, bool, uint64_t) [with ScoreType = bns::score::Entropy; bns::u64 = long unsigned int; uint64_t = long unsigned int]'
src/dashing.cpp:295:9:   required from here
bonsai/circularqueue/circular_buffer.h:30:37: warning: right shift count >= width of type [-Wshift-count-overflow]
     CIRC_CONSTIF(sizeof(T) > 4) x|=x>>32; // Throws a warning on shift count. This is avoided in C++17, but is unavoidable in C++14 because of the lack of `if constexpr`.
                                    ~^~~~
In file included from ./bonsai/bonsai/include/popcnt.h:8:0,
                 from ./bonsai/bonsai/include/util.h:35,
                 from src/dashing.cpp:4:
bonsai/hll/hll.h: In member function 'void sketch::hll::hllbase_t<HashStruct>::write(int) const [with HashStruct = sketch::common::WangHash]':
bonsai/hll/hll.h:1045:9: warning: ignoring return value of 'ssize_t write(int, const void*, size_t)', declared with attribute warn_unused_result [-Wunused-result]
         ::write(fileno, bf, sizeof(bf));
         ^~
bonsai/hll/hll.h:1046:9: warning: ignoring return value of 'ssize_t write(int, const void*, size_t)', declared with attribute warn_unused_result [-Wunused-result]
         ::write(fileno, &np_, sizeof(np_));
         ^~
bonsai/hll/hll.h:1047:9: warning: ignoring return value of 'ssize_t write(int, const void*, size_t)', declared with attribute warn_unused_result [-Wunused-result]
         ::write(fileno, &value_, sizeof(value_));
         ^~
bonsai/hll/hll.h:1048:9: warning: ignoring return value of 'ssize_t write(int, const void*, size_t)', declared with attribute warn_unused_result [-Wunused-result]
         ::write(fileno, core_.data(), core_.size() * sizeof(core_[0]));
         ^~
In file included from bonsai/hll/common.h:20:0,
                 from bonsai/hll/hll.h:3,
                 from ./bonsai/bonsai/include/popcnt.h:8,
                 from ./bonsai/bonsai/include/util.h:35,
                 from src/dashing.cpp:4:
bonsai/hll/sseutil.h: In function 'void* sse::detail::allocate_aligned_memory(size_t, size_t)':
bonsai/hll/sseutil.h:40:42: warning: ignoring return value of 'int posix_memalign(void**, size_t, size_t)', declared with attribute warn_unused_result [-Wunused-result]
         posix_memalign(&ret, align, size);
                                          ^
In file included from src/dashing.cpp:10:0:
./distmat/distmat.h: In member function 'void dm::DistanceMatrix<ArithType, DefaultValue, <template-parameter-1-3> >::read(const char*) [with ArithType = float; long unsigned int DefaultValue = 0ul; <template-parameter-1-3> = void]':
./distmat/distmat.h:148:9: warning: ignoring return value of 'size_t fread(void*, size_t, size_t, FILE*)', declared with attribute warn_unused_result [-Wunused-result]
         std::fread(&nelem_, sizeof(nelem_), 1, fp);
         ^~~
./distmat/distmat.h:154:9: warning: ignoring return value of 'size_t fread(void*, size_t, size_t, FILE*)', declared with attribute warn_unused_result [-Wunused-result]
         std::fread(data_.data(), sizeof(ArithType), data_.size(), fp);
         ^~~
./distmat/distmat.h: In member function 'void dm::DistanceMatrix<ArithType, DefaultValue, <template-parameter-1-3> >::read(const char*) [with ArithType = double; long unsigned int DefaultValue = 0ul; <template-parameter-1-3> = void]':
./distmat/distmat.h:148:9: warning: ignoring return value of 'size_t fread(void*, size_t, size_t, FILE*)', declared with attribute warn_unused_result [-Wunused-result]
         std::fread(&nelem_, sizeof(nelem_), 1, fp);
         ^~~
./distmat/distmat.h:154:9: warning: ignoring return value of 'size_t fread(void*, size_t, size_t, FILE*)', declared with attribute warn_unused_result [-Wunused-result]
         std::fread(data_.data(), sizeof(ArithType), data_.size(), fp);
         ^~~
Removing intermediate container 1688b3fcf6aa
 ---> aab7aa8662c4
Step 19/19 : WORKDIR /
 ---> Running in 9d0433ffc9ce
Removing intermediate container 9d0433ffc9ce
 ---> 6274b0ab62fe
Successfully built 6274b0ab62fe
```


</details>

It's also possible to [link GitHub Dockerfiles to DockerHub](https://docs.docker.com/docker-hub/builds/link-source/) so one could `docker pull dnbaker/dashing` and the latest commit to the Dockerfile will be used for that image.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6a0b33153946`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
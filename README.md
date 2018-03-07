# gcc-6.4.0-boost-1.66
Bash script and Makefile to install gcc 6.4.0 and boost 1.66 on CentOS and Mac OS X.

To use it:
```bash
$ mkdir -p work/gcc
$ cd work/gcc
$ git clone https://github.com/jlinoff/gcc-6.4.0-boost-1.66.git 6.4.0
$ cd 6.4.0
$ chmod a+x bld.sh
$ make
```
To build and run the example do this:
```bash
#!/bin/bash
# Setup the environment.
MY_GXX_HOME="~/work/gcc/6.4.0/rtf"
export PATH="${MY_GXX_HOME}/bin:${PATH}"
export LD_LIBRARY_PATH="${MY_GXX_HOME}/lib:${MY_GXX_HOME}/lib64:${LD_LIBRARY_PATH}"
export LD_RUN_PATH="${MY_GXX_HOME}/lib:${MY_GXX_HOME}/lib64:${LD_LIBRARY_PATH}"
 
# Compile and link.
g++ -O3 -std=c++11 -Wall -o example.exe example.cc
 
# Run.
./example.exe
```

To specify alternate installation locations, build with the following variables set.
```bash
# If you want to change the default directory locations, override
# these variables.
#
#    ROOTDIR   The root directory.
#              Default: current directory.
#
#    ARDIR     The archive directory.
#              Default: $ROOTDIR/archives.
#
#    RTFDIR    The release directory.
#              Default: $ROOTDIR/rtf.
#              This is where the bin and lib  directories are
#              located.
#
#    SRCDIR    The source directory.
#              Default: $ROTDIR/src.
#
#    BLDDIR    The build directory.
#              Default: $ROOTDIR/bld.
$ MR=/opt/gcc/6.4.0
$ ROOTDIR=$MR RTFDIR=$MR ARDIR=$MR/cache SRCDIR=$MR/pkg/src BLDDIR=$MR/pkg/bld make
```

For more detailed information see http://joelinoff.com/blog/?p=1678.

Added a new test file in this version called src/LOCAL-TEST/test4.cc that has even more C++-11 constructs. It implements a simple randomized quicksort.

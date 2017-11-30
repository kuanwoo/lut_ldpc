# Introduction

LUT LDPC is a collection of software tools to design and test LDPC decoders based on discrete message passing decoding
using lookup tables (LUTs), referred to as LUT decoders, cf. [[1]](#Literature). It is mainly written in C++ and relies heavily on the [IT++](http://itpp.sourceforge.net/) for abstracting basic linear algebra and signal processing operations.
Consequently, the LUT decoders can easily be integrated into more complex communication systems including concatenated coding and/or modulation.

# Installation

## Requirements
The program has been tested on MacOSX and Linux, but with minor modification, will most likely also run on Windows. To compile you need static versions of the following libraries:
* IT++ and its dependencies
* boost
We favoured static over dynamic linking for portability, as we ran the compiled binaries on an inhomogeneous cluster of Linux hosts.
Dynamically linked versions could be obtained by changing the [Makefile](Makefile) appropriately.

To download and install the software open a terminal and enter
```
git clone --recursive https://github.com/mmeidlinger/lut_ldpc.git
cd lut_ldpc
make
```
This will compile and link the program as well as the patched IT++ library.
Note that all binaries and headers  are installed locally within the project directory.
Furthermore, you can pass the following options to `make`
* `BUILD_TYPE=Debug` (default: `Release`)


# Usage

LUT LDPC consists of several programs and scripts, whose usage we will discuss in what follows. In general, we want to emphasize that LUT LDPC is a research driven toolset. As such, its functionality should be used more like a library than via the included programs. Hence,
the ways to interact with the programs are limited and applying the software to specific and complex scenarios requires the user to write and compile their own programs. To assist users with that, LUT LDPC features [Doxygen](www.doxygen.org/) inline source code documentation.

## Designing LUT Decoders and testing Bit Error rate performance
### Running the simulation
`prog/ber_sim` is capable of designing decoders and conducting bit error rate (BER) Monte Carlo simulations.
```
PARAMS_BER_INI
```


### Evaluating the results

## Density evolution

## Generating codes



# Repository overview

### bin
Binary executables  corresponding to the sources in `prog`. Generated by `make` if need be; not under version control.

### build
Location of compiled object files  corresponding to the sources in `src`. Generated by `make` if need be; not under version control.

### codes
This is where we save LDPC parity check matrices, generator matrices and binary decoder objects, where only the parity check matrices (`.alist` files) should be under version control.

### doc
This is where the Doxygen documentation is generated

### ensembles
This is where LDPC ensembles (text files containing degree distributions are saved, cf. [ensembles/README.md](ensembles/README.md)

### include
Header directory

### itpp 
Location of the it++ library source, handled by a Git submodule, c.f. [IT++ Submodule](#it-submodule)

### lib
Directory for third party libraries (mainly itpp). Generated by `make` if need be; not under version control.

### params
Contains example parameter files for the program(s)

### prog
Contains the source code for executables with a `main()` function

### scripts
Various scripts, e.g. for evaluating and plotting BER simulation results or running simulations on an HTCondor cluster

### src
Contains the source code of the application modules, excluding executables with a `main()` function

### trees
This is where we save tree structures for the LUT based decoders



# Installation





# Contributing

## Changing the IT++ Submodul
Navigate into `cpp/itpp` ans issue `git status`. You can see that git complains about being in a detached head state. 
The reason for this is the way submodules work: The parent repository only saves a reference (commit-id) to the current commit of the
submodule. If you checkout the submodule, its head is set to this very commit. In order to create a local branch, type
``` git checkout -b ldpc-lut --track origin/ldpc-lut ```
This creates the local branch `ldpc-lut`, makes it point to the commit-id of the submodule and tells git that the
local branch `ldpc-lut` is supposed to track the remote branch `origin/ldpc-lut`.
You can now make changes to the submodule and push them upstream, given that you have write access to the submodule repo.
To get write access to the submodule containing the altered version of IT++ contact [Michael Meidlinger](mailto:michael@meidlinger.info).

# Referencing
If you use this software for your academic research, please consider referencing [our original contributions](#Literature)
# Literature
[[1] M. Meidlinger, A. Balatsoukas-Stimming, A. Burg, and G. Matz, “Quantized message passing for LDPC codes,” in Proc. 49th Asilomar Conf. Signals, Systems and Computers, Pacific Grove, CA, USA, Nov. 2015.](http://ieeexplore.ieee.org/document/7421419/)




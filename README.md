# Shared Library for Base64 Encoding and Decoding

This repository provides a shared library that can be used for high performance Base64 encoding and decoding.

The related kdb library that uses this shared object can be found here - [https://github.com/jasraj/kdb-base64](https://github.com/jasraj/kdb-base64).

## Pre-requisites

To compile this project, you must ensure the standard build tools for your OS are available.

If you require the 32-bit version of the shared library (to use with 32-bit kdb+), it can be cross-compiled if you have the 32-bit build tools available:

* Ubuntu: `apt install libsystemd-dev:i386 gcc-multilib g++-multilib`
* CentOS: `yum install glibc-devel.i686 libgcc.i686 libstdc++-devel.i686 ncurses-devel.i686 systemd-devel.i686`

Ubuntu may also need to explicitly enable 32-bit library installation:

```
dpkg --add-architecture i386
apt-get update
```

## Compilation

To compile, use `cmake`:

```
# Create build in a local 'build' folder within the repo
mkdir build
cd build
cmake ..
cmake --build .
```

To cross-compile the 32-bit version of the shared library:

```
mkdir build-32
cd build-32
cmake .. -DCMAKE_CXX_FLAGS=-m32
cmake --build .
```

## Installation

To install the shared library on the current server:

```
sudo cmake --install .
```

To build a TAR GZ, RPM or DEB containing the shared library, use `cpack`:

```
# Build all package types
cpack .

# Only build one of the package types
cpack -G TGZ .
cpack -G RPM .
cpack -G DEB .
```

Note that the packages generated do not differentiate between 32-bit and 64-bit builds; they should be manually renamed to account for this

# Shared Library for Base64 Encoding and Decoding

This repository provides a shared library that can be used for high performance Base64 encoding and decoding.

The related kdb library that uses this shared object can be found here - [https://github.com/jasraj/kdb-base64](https://github.com/jasraj/kdb-base64).

## Compiling

### Pre-requisites

To compile this project, you must ensure the standard build tools for your OS are available.

If you want to build the shared object for 32-bit kdb as well as 64-bit kdb processes, ensure the following packages are available:

* gcc-multilib
* g++-multilib

If you are using Ubuntu, you'll need to explicitly enable 32-bit library installation:

```
> dpkg --add-architecture i386
> apt-get update
```

### Compilation

To compile, use `make`:

```
# Compile the 32 and 64-bit versions of the shared library
make all

# Only compile the 64-bit version
make build_init build_lib_64
```

The build output folder can be customised by specifying a target folder in the environment variable `KBL_OUT`.

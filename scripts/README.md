# Spider Linux Build Scripts

This is the scripts that builds the system from source. We'll use these for now
until we have a package manager that can just install the packages. You
probably shouldn't run any of these unless you're familiar with bash as there
are some things which are still hardcoded which makes using them tedious if you
don't have the same system as me :).

## Nomenclature

- **sources**: tarballs with source code in them.
- **build-critical variables**: variables such as PATH, TARGET_TRIPLET etc.

Here's what a full build roughly looks like:

```
get_sources --> create_filesystem --> build_toolchain --> cross_compile_programs --> spider-chroot --> finalise_toolchain
```

## Sources Directory

The `sources/` directory holds all of the source code needed to be compiled to
create the system. There are a few scripts that manage this directory for you,
namely `clean_sources` and `get_sources`, which clean up the program-specific
directories and get the sources from their repositories respectively. For now
it is a good idea to create this directory within the `scripts/` directory as
we do not have an automated way to do that yet. I could add it in but I haven't
got around to it.

## Helper Scripts

### env_funcs

The `env_funcs` script contains various build-critical variables and functions
to make the experience a lot easier to write and perform. It gets sourced at
the start of every script. Variables defined here are things such as, but not
limited to:

- CFLAGS/CXXFLAGS
- JOBS (make -jN)
- path to base directory
- path to sources directory

### varcheck

The `varcheck` script checks to see if system variables have been set. It is
somewhat obsolete now because we use `env_funcs` which sets the build-critical
variables for us.

### get_sources

The `get_sources` script grabs all of the needed sources to build the system
from their respective code repositories. It also decompresses them into the
`sources/` directory once it has downloaded them.

### clean_sources

The `clean_sources` script will go through the `sources/` directory, remove all
the program-specific directories, then untar the existing tarballs thus
emulating a clean build.

### hard_clean

The `hard_clean` script will clean both the `sources/` directory and will
remove the `toolchain/` directory.

## Build Scripts

### create_filesystem

The `create_filesystem` script goes into the `base/` directory and creates a
filesystem which will eventually become the root (`/`) filesystem of the
distro. It creates various directories such as `/usr`, `/root` and `/dev` to
name a few,

### build_toolchain

The `build_toolchain` script will build the GCC toolchain using binutils,
gcc/libstdc++, glibc and kernel headers. This is the first important step in
building programs for the system.

### cross_compile_programs

The `cross_compile_programs` script will cross-compile programs for the system.
These programs will then be used to finalise the system.

### spider-chroot

The `spider-chroot` script will mount the required virtual filesystems in
`/sys`, `/dev` and `/proc` then `chroot` into the root filesystem in `base/`.

### finalise_toolchain

The `finalise_toolchain` script builds the final programs for the system.

# How to Build

Revision 2 (2022-04-20)

This will be a rough guide on how to build the system from the ground up with
the build scripts. It is mainly meant for people developing the system and the
package manager but anyone can really use it for now. Since the whole system is
basically one repo at this stage, some directories will need to be created
within the repo.

## Prerequisites for your system

* coreutils
* make
* automake
* autoconf
* findutils
* bash
* Python (one of the configure tests fails if your system doesn't have this installed)

If you find there is more then send a PR.

## 1. Setup

### 1.1 Creating the necessary directories

First you want to create the `base/` directory in the git root.

```
spiderlinux/
├── base/ <---------
├── documentation/
├── scripts/
├── FAQ.md
├── LICENSE.md
└── README.md
```

This is where the eventual root filesystem will go.

Next you want to go into `scripts/` and create a `sources/` directory.

### 1.2 Modifying the environment variables

If you go into `env_vars_etc` you will find all of the variables and functions
that the build scripts use to make life a lot easier. Change `BASE_DIR` to
the path to the git repository.

```bash
BASE_DIR=/home/sean/files/docs/projects/spiderlinux
```

Optionally you can change the `JOBS` variable to `-jX` with `X` being the
number of jobs you want. By default this is set to the value of `nproc` which
is number of processors.

```bash
JOBS="-j$(nproc)" # total number of cores
```

### 1.3 Getting the build sources

Now what you're gonna want to do is run the `get_sources` script. This will
download and untar all of the source code into the `sources/` directory you
just made.

```
$ ./get_sources
```

At this stage there should be tarballs and their untarred contents in the
`sources/` directory.

**Pro Tip:** if you need to kill the build process at any point and start over
from one of the stages then it is a good idea to run the `clean_sources` script
before you run the current stage to get rid of any lingering build files from
the previous builds.

```
$ ./clean_sources
```

### 1.4 Creating the root filesystem

To create the root filesystem we use the `create_filesystem` script. This goes
into `base/` and creates all the necessary directories for a working system. To
run the script you must use `sudo` as the root user will own the contents of
the directory.

```
$ sudo ./create_filesystem
```

## 2. Building

### 2.1 Starting the toolchain build

The first part to building the distro is getting the compiler toolchain up and
running. We start this with the `start_toolchain_build` script. This will build
the cross compiler, the files the cross compiler needs to build binaries, and
the C/C++ library. It finishes off with building GCC for the system.

On first run this may take a while (around 9 minutes or so on my machine) but
if you use ccache repeated builds will go faster.

```
$ ./start_toolchain_build
```

### 2.2 Cross Compiling the base system

Now the system needs some utilities so it can be used to finish off the
toolchain and the rest of the system, to do this we use the
`cross_compile_programs` script. For simplicity sake we cross compile all of
these. Anything that cannot be cross compiled gets built in the
`finalise_toolchain_build` script

```
$ ./cross_compile_programs
```

### 2.3 Entering the system via `chroot`

Before we finalise the toolchain we must enter the system. Some programs like
perl and libraries like libstdc++ require you to be on the actual system for
compiling because they like to make your life difficult. To enter the system run:

```
$ sudo ./spider-chroot ../base
```

### 2.4 Finalising the toolchain build

The final step is to complete the GCC toolchain by building libstdc++ (again)
then perl. As a reminder **This should ONLY be ran INSIDE THE CHROOT!!**.

First run `cd` on its own to get into `/root`.

Then we finish the process off by running:

```
$ ./finalise_toolchain_build
```

This shouldn't take very long and when it's done you should end up with a
nearly fully working system! The build process is nearly done and soon we'll be
able to be self-hosting but for now it's just a hosted system accessible within
a chroot.

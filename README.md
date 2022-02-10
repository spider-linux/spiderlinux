# Spider Linux

Spider Linux is a work-in-progress, modern, independent, free and open-source
GNU/Linux distribution.

**As of Feb 2022**: The system is in, by no means, a usable state even for an
advanced user. I am working on changing that and so can you :^)

Join the Discord: [https://discord.gg/erUaQVcsyw](https://discord.gg/erUaQVcsyw)

Watch development on Twitch! I try to stream everyday and start sometime between 11am and 4pm UK time: [https://www.twitch.tv/redshiftttt](https://www.twitch.tv/redshiftttt)

## Philosophy/Motivations

Spider Linux is developed with the following goals in mind: simplicity,
efficiency and functionality. The goal is to have a minimal base system unto
which the user can turn into whatever they desire using a powerful yet simple
package manager/management system. I started the project because I wanted the
best of both worlds when it came to package management, binary/source-based,
but in a more convenient manner.

I had used many distributions before now and I came to the realisation that
they all have 1 flaw (probably purposefully done) which is that they're either
a binary-based distribution or a source-based distribution. Sure they have ways
to install packages of the other paradigm if binaries, or what have you, don't
exist but there isn't a native 1:1 solution or a middle ground.

Let me ask you this, what if you had a server that needed a package urgently,
but there was only a source version of it available? And what if that
source-based package was out-of-date while there was an upstream version
available? And what if you wanted to edit the build file but it was a confusing
and tedious process? This is just one of many processes that Spider Linux aims
to make a lot better.

## Package Management System

The package management system uses our package manager, `arachnid`. As
previously mentioned, the goal is to have 1:1 compatibility for installing the
source/binary version of a package. Reasons for possibly wanting to do this
could be that you want to have a specific system with specific features, or you
want to do that and not have to bother with compiling some programs, or you
want to use a binary system but still have low level (i.e. core utilities,
kernel, maybe even init in the future) control over how your system runs.

The build file will be instructions in a custom but nearly pseudocode-like
format that tells the package manager how to build the package. The actual
package that gets installed whether it has been compiled locally or not will be
a tarball most likely with either ZSTD or XZ compression.

In order to accomplish this we need to have a system that can hold a build file
and a tarball containing what was built from the build file (the point of doing
this is to maximise compatibility). The package repository will likely be a Git
repository separated into directories with the package name and version as
their title. Inside the directory will be a build file, a tarball and a JSON
file describing the package. Users or myself are free to submit packages in the
form of a pull request if the package has already been built, tested and is in
the tarball format. At somewhat regular intervals, a server will create a
snapshot of the Git repository and that will be where the package manager will
retrieve the packages from whether that is source or binary format.

See my rough notes in [documentation/arachnid.md](documentation/arachnid.md).

## Inspiration

Projects from which I drew inspiration from in no particular order:

- Arch Linux
- Gentoo Linux
- Void Linux
- OpenBSD
- SerenityOS
- glaucus linux
- NixOS

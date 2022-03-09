# Spider Linux

Spider Linux is a work-in-progress, modern, independent, free and open-source
Linux distribution.

**As of Feb 2022**: The system is in, by no means, a usable state even for an
advanced user. It is mainly due to hardcoded variables that are useful for
testing on my machine but not for running on others'. I am working on changing
that and so can you :^)

Join the Discord (we don't bite):
[https://discord.gg/erUaQVcsyw](https://discord.gg/erUaQVcsyw)

Watch development on Twitch! I try to stream everyday and start sometime
between 11am and 4pm UK time:
[https://www.twitch.tv/redshiftttt](https://www.twitch.tv/redshiftttt)

You can see the FAQ [here](FAQ.md).

## Philosophy

Spider Linux is developed with the following goals in mind: simplicity,
efficiency and functionality. The goal is to have a minimal base system unto
which the user can turn into whatever they desire using a powerful yet simple
package manager/management system. I started the project because I wanted the
best of both worlds when it came to package management, pre-compiled
binary/source-based, but in a more convenient manner.

## Roadmap

- [x] Toolchain (done, but not simple enough)
    - [x] Basic Utilities (shell etc)
- [ ] Pick an Init System
- [ ] Kernel Config
- [ ] Create image for booting
- [ ] Make a start on Arachnid
- [ ] Move away from build scripts and use arachnid

## Documentation

I try my best to document as much of the process as possible. Rough notes from
before the project began can be found in the [documentation/](documentation/)
directory of the Git repo.

Documentation for the build scripts is provided
[here](https://github.com/redshifttt/spiderlinux/blob/master/scripts/README.md).

## Inspiration

Projects from which I drew inspiration from in no particular order:

- Arch Linux
- Gentoo Linux
- Void Linux
- OpenBSD
- SerenityOS
- glaucus linux
- NixOS

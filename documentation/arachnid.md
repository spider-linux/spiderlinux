# Package Manager

arachnid
- install - installs a package
- uninstall - removes a package
- search - searches for packages
    - local - searches locally for packages and displays their info
        - verbose - verbose local search output
    - verbose - verbose search output
    - tag - packages will use a tag system for more refined searches and organisation
    - last - get a list of the recently installed packages, their install reason and time
- update - updates the system
    - download - downloads updates (packages) and that's it
- garbage - cleans config files

---

- be able to build and install packages efficiently
- maybe have commands in plain english. e.g. arachnid search local bash
    - second word is overall operation
    - third word is optional suboperation but cannot be a specific list of words such as local etc

- be able to look up a list of last installed packages and their install times
- be able to optionally (prompt?, in the cfg?) clean config files - both in $HOME and / - on package removal
    - maybe need to have some sort of file tracking, maybe not

- cannot have both the binary and source version of a package on the system at the same time
- have a way to convert from other packing formats such as rpm, deb, pkgbuild or even nix
- use something nearly equivelent to plain english for the user to be able to quickly write a build file if need be
- use a tag system to be able to filter out packages
    - tags should be broad and not include the program name in them
- have verbosity that visually makes sense on first glance
    - colours

- have 2 repositories: one for source and one for compiled binaries, make them as identical as possible
    - give the user the option to compile from source for greater control over the software or to use a precompiled binary for speed.
    - source would be meant more for people who either want control or have the power to compile and binaries would be made for people with slower hardware but the choice is there for the user anyway
    - have a git repo for the bleeding edge packages
        - every now and then the main cached package repo - that the package manager would normally get the packages from - will update to the latest commit that day. think of it like a nightly release of the git repo.


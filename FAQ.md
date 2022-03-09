# Frequently Asked Questions

**1. What is the [USP](https://en.wikipedia.org/wiki/Unique_selling_proposition)
   of Spider Linux in comparison to every other distro?**

Spider Linux's unique selling point is that it can do whatever you like but
without all the cruft of something like, say, Gentoo and Portage. In fact the
whole distro is based around this idea of doing everything at the simplest
level. That's why we're using C and shell scripts and trying our best to make
the simplest implementations of things.

**2. Who is Spider Linux targeted towards?**

Anyone can use Spider Linux. We have plans to support a variety of installation
methods based on preference and hopefully have a variety of init systems as
well. This is supposed to be a flexible distro anyone can use.

**3. How does Spider Linux differ from X or Y?**

Lots of choice but without tons of drawbacks. You could go GNUless if you
really wanted to.

**4. How does the packaging system work?**

I am glad you asked. Our package management system uses our package manager
arachnid - you could think of it like pacman mixed with emerge/portage but 10x
cooler - for installing packages either from source or from a pre-compiled
binary tarball. Arachnid will be developed in C99 because every modern standard
after that just seems to be maintenance releases.

If you need/want to build a package from source the format will be in Lua. This
allows us to be functional while reproducible which, in the modern era, is a
pretty important thing. It also lets the build instructions be a format which
is well known and standardised and is quite simple to learn instead of having a
custom formatted build file or one which uses a shell-like format.

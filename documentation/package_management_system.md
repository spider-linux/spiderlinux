## Package Management System

The package management system uses our package manager, `arachnid`. As
previously mentioned, the goal is to have 1:1 compatibility for installing the
source/pre-compiled binary version of a package. Reasons for possibly wanting
to do this could be that you want to have a specific system with specific
features, or you want to do that and not have to bother with compiling some
programs, or you want to use a pre-compiled binary system but still have low
level (i.e. core utilities, kernel, maybe even init in the future) control over
how your system runs.

The build file will be a Python file - which will use `libarachnid` in the
future - that tells the package manager how to build the package. The actual
package that gets installed, whether it has been compiled locally or not, will
be a tarball most likely with either ZSTD or XZ compression.

In order to accomplish this we need to have a system that can hold a build file
and a tarball containing what was built from the build file (the point of doing
this is to maximise compatibility). The package repository will likely be a Git
repository separated into directories with the package name and version as
their title. Inside the directory will be a Python file with the build
instructions as mentioned above, a tarball and potentially a JSON file
describing the package. Users are free to submit packages in the form of a pull
request if the package has already been built, tested and is in the tarball
format. At somewhat regular intervals, a server will create a cached snapshot
of the Git repository and that will be where the package manager will retrieve
the packages from whether that is source or pre-compiled binary format.

See my rough notes for arachnid, from a while ago, in
[documentation/arachnid.md](documentation/arachnid.md).

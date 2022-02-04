# Run the following as ROOT

1. set-up disk
2. grab sources. we do this for now since we don't have a package repository. if we did we would just use the package manager to retrieve our sources.
3. generate root filesystem structure
4. create spider user for building the rest of the system
5. make spider user own the root filesystem

# Run the following as SPIDER USER

6. create bash profile and bashrc
7. build the cross toolchain and cross compiling temporary tools
8. exit spider user

# Run the following as ROOT

9. make root own the `/` filesystem
10. use chroot script to prepare virtual filesystems and enter the chroot env
11. create the essential directories, files and symlinks in `/`. this includes files such as /etc/hosts, /etc/passwd, /etc/group and others
12. do a second pass building the toolchain except this time it is inside the actual system
13. set a root password (or leave blank for the user to do it when they eventually install the system)
14. leave the chroot and re-enter it with the updated configuration
15. configure and install the rest of the base system
16. after it is all done, leave the chroot and tar up the `/` filesystem

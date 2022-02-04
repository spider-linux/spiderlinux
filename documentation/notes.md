# Spider Linux

### General Idea

- choice of what you want to run
- binary+source system
- fast
- minimal and light install
- not minimal as in the meme, minimal as in the unix philosophy in a way (programs should do one/a couple thing(s) and do it/them really well)

### Init System

- have an option to select the init system in the install file so that changing it over afterwards isn't too difficult
    - letting the user change init after install could also done
- be able to use any that the user desires

### Kernel

- be able to use any linux kernel
- give the user the option to compile their own kernel if they wish or use a stock kernel

### Install System

- configure drives, file-systems and networking then download the base system from a tar.xz (most likely) which will contain basic
    system tools to get the user off the ground such as a basic init system with the basic coreutils etc.
- from here the user would create an install file which will look something like a build file for packages and configure the system to-be from within that file

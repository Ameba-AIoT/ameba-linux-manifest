Ameba Linux Repo Manifest README
=================================

This repo is used to download manifests for Ameba Linux BSP releases.

Install the `repo` utility:
---------------------------

To use this manifest repo, the `repo` tool must be installed first.

Many Linux distros include `repo`, so you might be able to install from there.
```
# Debian/Ubuntu.
$ sudo apt-get install repo

# Gentoo.
$ sudo emerge dev-vcs/repo
```

You can also install it manually as well as it's a single script.
```
$ mkdir -p ~/.bin
$ PATH="${HOME}/.bin:${PATH}"
$ curl https://storage.googleapis.com/git-repo-downloads/repo > ~/.bin/repo
$ chmod a+rx ~/.bin/repo
```

Download Ameba Yocto Project SDK
---------------------------------

```
$ mkdir <release>
$ cd <release>
$ repo init -u https://github.com/Ameba-AIoT/ameba-linux-manifest -b <branch name> [ -m <release manifest>]
$ repo sync
```

Each branch will have detailed READMEs describing exact syntax.

Examples
--------

To download the ameba-3.1_r1 release
```
$ repo init -u https://github.com/Ameba-AIoT/ameba-linux-manifest -b ameba-3.1 -m ameba-3.1_r1.xml
```

Setup build environment for a release
-----------------------------------------

From within your working directory, source the envsetup.sh script to setup build environment.
The script can also take several command options. To get all the option list, use following command:

```
$ source envsetup.sh -h

SYNOPSIS
    source envsetup.sh [OPTION]...

DESCRIPTION
    The script will setup the build enviroment for yocto bitbake.

OPTIONS
    -h
        print this help and exit.

    -m machine
        the target machine to be built.

    -d distro
        the target distro to be built.

    -j jobs
        number of jobs for make to spawn during the compilation stage.

    -t tasks
        number of BitBake tasks that can be issued in parallel.

    -b path
        non-default path of project build folder.

    -p path
        non-default path of DL_DIR (downloaded source)

    -c path
        non-default path of SSTATE_DIR (shared state Cache)
```

Examples:
- Setup build for RTL8730ELH-VA8.
```
$ source envsetup.sh -m rtl8730elh-va8 -d ameba-generic
```

- Setup build from a lunch menu.
```
$ source envsetup.sh

You're building on Linux

Lunch menu... pick a combo:
     1. rtl8730elh-recovery
     2. rtl8730elh-va7-full
     3. rtl8730elh-va7-generic
     4. rtl8730elh-va8-full
     5. rtl8730elh-va8-generic

Which would you like?
```

Input the number of selection to setup the specific build environment.


Build an image:
---------------

The envsetup.sh script imports several commands that let you work with Ameba Linux SDK.
To build the SDK, you can use the commands in envsetup.sh.

Example:
- Build the whole SDK
```
$ m
```

You can also use Yocto's bitbake to build a image.

```
$ bitbake <image recipe>
```

Some image recipes:

Image Name           | Description
---------------------|---------------------------------------------------
ameba-image-core     | core image with basic functions
ameba-image-recovery | recovery image


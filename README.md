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
$ repo init -u https://github.com/Ameba-AIoT/ameba-linux-manifest -b <branch name> [ -m <manifest name>]
$ repo sync
```

Each branch will have detailed README describing exact syntax.

# RetroArch for Raspberry Pi 3B+

## Prerequisites

Make sure you run this inside a Raspberry Pi 3B+ with Raspbian! Otherwise it won't work! This script prepares a build of RetroArch for Raspberry Pi 3B+.

Install the following dependencies first:

```sh
$ sudo apt install -y devscripts build-essential lintian
```

## Create a release

Clone RetroArch (and select an appropriate version if you want, current tested version is `1.9.4`):

```sh
$ git clone https://github.com/libretro/RetroArch/
```

Copy this `pkg/debian` folder inside RetroArch (it should look like the following):

```sh
retroarch
    ├── [...] # RetroArch sources
    └── debian
        ├── changelog
        ├── compat
        ├── control
        ├── copyright
        ├── dirs
        ├── docs
        ├── retroarch.lintian-overrides
        └── rules
```

```sh
$ cd retroarch
```

We are using debuild to help us to create a debian package. More information on how to use [the tool can be found here](https://blog.packagecloud.io/debian/debuild/packaging/2015/06/08/buildling-deb-packages-with-debuild/).

```sh
$ debuild -b
```

The process should start compiling RetroArch. After the build finishes, relevant `*deb` file can be found in parent directory of RetroArch.

If you want to customize flags to modify settings for RetroArch, modify `rules` file.

## Acknowledgements 

This repository has been inspired by the work done on [RetroArch](https://github.com/libretro/RetroArch/tree/master/pkg/debian).
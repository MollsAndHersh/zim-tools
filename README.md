ZIM tools
=============

Various ZIM command line tools. More information about the ZIM format
and the [openZIM project](https://openzim.org):
* zimbench: Performance measurement of a ZIM file reading
* zimcheck: Check quality of ZIM file content
* zimdiff: Compute a diff ZIM file between two ZIM files
* zimdump: Dump content of a ZIM file
* zimpatch: Apply a ZIM diff file to a ZIM file
* zimrecreate: Recreate a ZIM file from the same "old" ZIM file
* zimsearch: (Fulltext) Search in a ZIM file
* zimsplit: Split smartly a ZIM file (without breaking clusters)

[![Build Status](https://travis-ci.org/openzim/zim-tools.svg?branch=master)](https://travis-ci.org/openzim/zim-tools)
[![CodeFactor](https://www.codefactor.io/repository/github/openzim/zim-tools/badge)](https://www.codefactor.io/repository/github/openzim/zim-tools)
[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)

Disclaimer
----------

This document assumes you have a little knowledge about software
compilation. If you experience difficulties with the dependencies or
with the ZIM libary compilation itself, we recommend to have a look to
[kiwix-build](https://github.com/kiwix/kiwix-build).

Dependencies
------------

The Kiwix library relies on the libzim.

* [ZIM](https://openzim.org) (package `libzim-dev` on Debian/Ubuntu)

These dependencies may or may not be packaged by your operating
system. They may also be packaged but only in an older version. The
compilation script will tell you if one of them is missing or too old.
In the worse case, you will have to download and compile a more recent
version by hand.

If you want to install these dependencies locally, then ensure that
meson (through pkg-config) will properly find them.

Environment
-------------

The ZIM tools build using [Meson](https://mesonbuild.com/) version
0.43 or higher. Meson relies itself on Ninja, pkg-config and few other
compilation tools.

Install first the few common compilation tools:
* Meson
* Ninja
* Pkg-config

These tools should be packaged if you use a cutting edge operating
system. If not, have a look to the [Troubleshooting](#Troubleshooting)
section.

Compilation
-----------

Once all dependencies are installed, you can compile ZIM tools with:
```bash
meson . build
ninja -C build
```

By default, it will compile dynamic linked libraries. All binary files
will be created in the "build" directory created automatically by
Meson. If you want statically linked libraries, you can add
`-Dstatic-linkage=true` option to the Meson command.

Depending of you system, `ninja` may be called `ninja-build`.

Installation
------------

If you want to install the ZIM tools you just have compiled on your
system, here we go:
```bash
ninja -C build install
```

You might need to run the command as root (or using 'sudo'), depending
where you want to install the libraries. After the installation
succeeded, you may need to run ldconfig (as root).

Uninstallation
------------

If you want to uninstall the ZIM tools:
```bash
ninja -C build uninstall
```

Like for the installation, you might need to run the command as user
`root` (or using `sudo`).

Troubleshooting
---------------

If you need to install Meson "manually":
```bash
virtualenv -p python3 ./ # Create virtualenv
source bin/activate      # Activate the virtualenv
pip3 install meson       # Install Meson
hash -r                  # Refresh bash paths
```

If you need to install Ninja "manually":
```bash
git clone git://github.com/ninja-build/ninja.git
cd ninja
git checkout release
./configure.py --bootstrap
mkdir ../bin
cp ninja ../bin
cd ..
```

If the compilation still fails, you might need to get a more recent
version of a dependency than the one packaged by your Linux
distribution. Try then with a source tarball distributed by the
problematic upstream project or even directly from the source code
repository.

License
-------

[GPLv3](https://www.gnu.org/licenses/gpl-3.0) or later, see
[LICENSE](LICENSE) for more details.

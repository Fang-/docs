---
navhome: /docs
next: true
sort: 1
title: Install
---

# Install

Urbit is designed to run on any Unix box with an internet connection.  Debian
(jessie), OS X, FreeBSD and Fedora all work well.

Urbit is alpha software.  It’s not yet completely stable, its crypto hasn’t
been audited, and there are plenty of rough edges.  Urbit is lots of fun to play
with, but not quite ready for your important or sensitive data.

### Setting up swap

Urbit wants to map 2GB of memory when it boots up.  We won’t
necessarily use all this memory, we just want to see it.  On a
normal modern PC or Mac, this is not an issue.  On some small
cloud virtual machines (Amazon or Digital Ocean), the default
memory configuration is smaller than this, and you need to
manually configure a swapfile.

Digital Ocean has a post on adding swap [here](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-ubuntu-14-04).  For Amazon there’s a StackOverflow thread [here](http://stackoverflow.com/questions/17173972/how-do-you-add-swap-to-an-ec2-instance).

Don’t spend a lot of time tweaking these settings; the simplest
thing is fine.

## Install a package

Urbit may be in your system's package repository - check there first. If not, we host packages for some platforms:

[FreeBSD](https://media.urbit.org/dist/freebsd/urbit-0.4.txz): install with `pkg install urbit-0.4.txz`.
[Debian](https://media.urbit.org/dist/debian/urbit_0.4-1_amd64.deb): install with `dpkg -i urbit_0.4-1_amd64.deb`, followed by `apt-get install -f` to install any missing dependencies.

## Build from source

First, fetch the source tarball from [here](https://media.urbit.org/dist/src/urbit-0.4.tar.gz).

### Dependencies

Urbit depends on:

    C compiler (gcc or clang)
    automake
    autoconf
    libtool
    cmake
    ragel
    re2c
    libcurl
    curses
    gmp
    libsigsegv
    openssl

Which can usually be installed with the following one-liners:

    # Mac OS X [Homebrew]
    $ brew install git gmp libsigsegv openssl libtool autoconf automake cmake

    # Mac OS X [Macports]
    $ sudo port install git gmp libsigsegv openssl autoconf automake cmake

    # Ubuntu or Debian
    $ sudo apt-get install libgmp3-dev libsigsegv-dev openssl libssl-dev libncurses5-dev git make exuberant-ctags automake autoconf libtool g++ ragel cmake re2c libcurl4-gnutls-dev

    # Fedora
    $ sudo dnf install gcc gcc-c++ git gmp-devel openssl-devel openssl ncurses-devel libsigsegv-devel ctags automake autoconf libtool ragel cmake re2c libcurl-devel

    # FreeBSD
    $ pkg install git gmake gmp libsigsegv curl python automake autoconf ragel cmake re2c libtool curl

    # Arch
    $ pacman -S gcc gmp libsigsegv openssl automake autoconf ragel cmake re2c libtool ncurses curl

    # AWS
    $ sudo yum —enablerepo epel install gcc gcc-c++ git gmp-devel openssl-devel ncurses-devel libsigsegv-devel ctags automake autoconf libtool cmake re2c libcurl-devel

### Clone and make

Once your dependencies are installed the rest is easy:

    $ tar xfvz urbit-0.4.tar.gz
    $ cd urbit-0.4
    $ make # gmake on FreeBSD

After running `make`, your Urbit executable is in `bin/urbit`. Install it wherever you'd like.

    # sudo install -m 0755 bin/urbit /usr/local/bin

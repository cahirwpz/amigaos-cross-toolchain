AmigaOS cross compiler for Linux / MacOSX / Windows
===

**Author:** [Krystian Bacławski](mailto:krystian.baclawski@gmail.com)

**Short description:** Cross toolchain build script for AmigaOS m68k and ppc targets. Supported host platforms are Linux, MacOSX and Windows (Cygwin).

### Overview

**amigaos-cross-toolchain** project provides an easy way to build AmigaOS 3.x (m68k) and ppc AmigaOS 4.x (ppc) target toolchain in a Unix-like environment.

Build process should produce following set of tools for **m68k-amigaos** target:

 * gcc 2.95.3
 * g++ 2.95.3
 * libstdc++ 2.10
 * binutils 2.9.1 (assembler, linker, etc.)
 * libnix 2.2 (standard ANSI/C library replacement for AmigaOS)
 * libm 5.4 (provides math library implementation for non-FPU Amigas)
 * AmigaOS headers & libraries & autodocs (for AmigaOS 3.9)
 * vbcc toolchain (most recent release) including vasm, vlink and C standard library
 * IRA: a 68k disassembler/reassembler

... and following set of tools for **ppc-amigaos** target:

 * gcc 4.2.4
 * g++ 4.2.4
 * binutils 2.18 (assembler, linker, etc.)
 * newlib
 * clib 2.2
 * AmigaOS headers & libraries & autodocs (for AmigaOS 4.1)

**Note:** *Patches are welcome!*

### Downloads

There are no binary downloads provided for the time being. I do as much as possible to make the toolchain portable among Unix-like environments. Following platforms were tested and the toolchain is known to work for them:

 * Cygwin 1.7.18 (gcc 4.5.3)
 * Ubuntu 14.04 LTS 32-bit (gcc 4.8.2)
 * Ubuntu 14.04 LTS 64-bit (gcc 4.8.2) *Requires gcc-multilib package, and i386 libraries!*
 * MacOS X 10.9.3 (MacPorts - Apple's clang-503.0.40)
 
### Documentation

Documentation from Free Software Fundation:

 * [gcc 2.95.3](http://gcc.gnu.org/onlinedocs/gcc-2.95.3/gcc.html)
 * [binutils](http://sourceware.org/binutils/docs/)

Texinfo documents from GeekGadgets converted into HTML:

 * [libnix - a static library for GCC on the amiga](http://cahirwpz.users.sourceforge.net/libnix/index.html)
 * [AmigaOS-only features of GCC](http://cahirwpz.users.sourceforge.net/gcc-amigaos/index.html)

AmigaOS specific documents:

 * [Amiga Developer Docs](http://amigadev.elowar.com)

### Compiling

*Firstly… you should have basic understanding of Unix console environment, really* ;-)

#### Prerequisites

You have to have following packages installed in your system:

 * GNU gcc 4.x **32-bit version!** or Clang
 * libncurses6-dev **32-bit version!**
 * GNU make
 * python-dev
 * perl
 * git
 * subversion
 * patch
 * yacc

*For MacOSX users*: you'll likely need to have [MacPorts](http://www.macports.org) or [Homebrew](http://brew.sh) installed in order to build the toolchain.

#### How to build?

**Warning:** *Building with `sudo` is not recommended. I'm not responsible for any damage to your system.*

Follow steps listed below:

1. Fetch *amigaos-cross-toolchain* project to your local drive:  

    ```
# git clone git://github.com/cahirwpz/amigaos-cross-toolchain.git
# cd amigaos-cross-toolchain
```

2. Run `toolchain-m68k` or `toolchain-ppc` script (with `--prefix` option to specify where to install the toolchain). Note, that the destination directory must be writable by the user. 

    ```
# ./toolchain-m68k --prefix=/opt/m68k-amigaos build
```

3. Wait for the result :-)

4. *(optional)* Install additional SDKs (e.g. AHI, CyberGraphX, Magic User Interface, etc.):

    ```
# ./toolchain-m68k --prefix=/opt/m68k-amigaos install-sdk ahi cgx mui
```

**Note:** *If the build process fails, please write me an e-mail.  I'll try to help out. Don't forget to put into e-mail as much data about your environment as possible!*


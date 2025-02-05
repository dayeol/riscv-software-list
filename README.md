# RISC-V Software Ecosystem Overview

This document captures the status of the RISC-V Software Ecosystem. Please add
to the list and fix inaccuracies.

* [Simulators](#simulators)
* [Object toolchain](#object-toolchain)
* [Debugging](#debugging)
* [C compilers and libraries](#c-compilers-and-libraries)
* [Boot loaders and monitors](#boot-loaders-and-monitors)
* [OS and OS kernels](#os-and-os-kernels)
* [Compilers and runtimes for other languages](#compilers-and-runtimes-for-other-languages)
* [IDEs](#ides)
* [Security](#security)

**We would like to enlist community help for the software ports in the [Help Wanted](#help-wanted) section.**

# Simulators

Name | Links | License | Maintainers
---- | ----- | ------- | -----------
DBT-RISE-RISCV | [github](https://github.com/Minres/DBT-RISE-RISCV) | BSD-3-Clause | [MINRES Technologies](www.minres.com)
FireSim | [website](https://fires.im), [mailing list](https://groups.google.com/forum/#!forum/firesim), [github](https://github.com/firesim/firesim), [ISCA 2018 Paper](https://sagark.org/assets/pubs/firesim-isca2018.pdf) | BSD | Sagar Karandikar, Howard Mao, Donggyu Kim, David Biancolin, Alon Amid, [Berkeley Architecture Research](https://bar.eecs.berkeley.edu)
gem5 | [SW-dev thread](https://groups.google.com/a/groups.riscv.org/forum/#!topic/sw-dev/se0TVeaA_JI), [repository](https://gem5.googlesource.com/public/gem5/) | BSD-style | Alec Roelke (University of Virginia)
Imperas | [website](http://www.imperas.com/riscv) | Proprietary, models available under Apache 2.0 | [Imperas](http://www.imperas.com/)
riscvOVPsim | [github](https://github.com/riscv/riscv-ovpsim) | [license](https://github.com/riscv/riscv-ovpsim/blob/master/LICENSE.pdf) | [Imperas](http://www.imperas.com/)
OVPsim | [website](http://www.ovpworld.org/riscv) | Free for non commercial use, models available under Apache 2.0 | [Imperas](http://www.imperas.com/)
jor1k | [website](http://s-macke.github.io/jor1k/demos/riscv.html), [github](https://github.com/s-macke/jor1k/) | BSD 2-Clause | Sebastian Macke
Jupiter | [github](https://github.com/andrescv/Jupiter) | GPL-3.0 | Andrés Castellanos
QEMU | [upstream](http://git.qemu.org/qemu.git) | GPL | Sagar Karandikar (University of California, Berkeley), Bastian Koppelmann (University of Paderborn), Alex Suykov, Stefan O'Rear and Michael Clark (SiFive)
RARS | [github](https://github.com/thethirdone/rars) | MIT | Benjamin Landers
Renode | [website](https://renode.io), [github](https://github.com/renode/renode) | MIT | [Antmicro](https://antmicro.com)
Ripes | [github](https://github.com/mortbopet/Ripes)| MIT | Morten Borup Petersen
RISC-V Virtual Prototype | [website](http://www.systemc-verification.org/riscv-vp), [github](https://github.com/agra-uni-bremen/riscv-vp) | MIT | Vladimir Herdt (University of Bremen, [AGRA](http://www.informatik.uni-bremen.de/agra/eng/index.php))
TinyEMU | [website](http://bellard.org/riscvemu/) | MIT | Fabrice Bellard
Spike | [github](https://github.com/riscv/riscv-isa-sim) | BSD 3-clause | Andrew Waterman & Yunsup Lee (SiFive)
Swerv-ISS  | [github](https://github.com/westerndigitalcorporation/swerv-ISS) | GPL - 3 | Joseph Rahmeh (Western Digital) 

# Object toolchain

## Binutils

* Maintainer(s): Andrew Waterman (SiFive), Palmer Dabbelt (SiFive), Jim Wilson (SiFive)
* Version: 2.28
* Upstreaming status: Upstream, RISC-V support available starting in 2.28
* Future work:
* RISC-V repository: https://github.com/riscv/riscv-binutils-gdb
* Upstream repository: https://sourceware.org/git/gitweb.cgi?p=binutils-gdb.git
* Privileged Spec: 1.9.1
* User Spec: 2.0
* ABI:
* Links:
https://groups.google.com/a/groups.riscv.org/forum/#!searchin/sw-dev/binutils/sw-dev/RS_wN0-wpCI/X923RdnDBQAJ

## LLVM

* Maintainer(s): Alex Bradbury (lowRISC)
* Version: HEAD
* Upstreaming status: MC changes are upstream, assembler and initial codegen patches submitted
* Future work:
  * Resolve remaining issues with GCC torture suite test cases (mostly calling convention related)
  * Expand support for different ISA variants, PIC/PIE code models etc
  * Scheduling model, peephole optimisations, and performance comparison vs GCC-generated code
* Upstream repository:
  * http://llvm.org/viewvc/llvm-project/llvm/trunk
  * https://github.com/llvm-mirror/llvm (Git mirror)
  * https://github.com/lowrisc/riscv-llvm (patch series)
* Privileged Spec:
* User Spec: 2.0
* ABI:
* Links: http://llvm.org/viewvc/llvm-project/llvm/trunk/lib/Target/RISCV/

## Cranelift

* Version: HEAD
* Repository: https://github.com/CraneStation/cranelift

# Debugging

## Gdb

* Maintainer(s): Andrew Burgess (Embecosm), Palmer Dabbelt (SiFive)
* Version: HEAD
* Upstreaming status: Bare metal support committed upstream 6 March 2018, was in 8.2 release.  XML target description support, non DWARF stack unwinding, basic Linux application support, and basic BSD application support will be in the next (8.3) release.
* Future work: Linux GDBServer support.
* RISC-V repository: https://github.com/riscv/riscv-binutils-gdb
* Upstream repository: https://sourceware.org/git/gitweb.cgi?p=binutils-gdb.git
* Privileged Spec: 1.9.1
* User Spec: 2.0
* ABI:
* Links:
  * https://sourceware.org/ml/gdb-patches/2018-03/msg00070.html
  * https://sourceware.org/ml/gdb-patches/2018-03/msg00071.html
  * https://sourceware.org/ml/gdb-patches/2018-03/msg00072.html

## OpenOCD

* Maintainer(s): Tim Newsome, Megan Wachs, Palmer Dabbelt (SiFive)
* Version: 0.10.0-dev
* Upstreaming status: Not started
* Future work: 
  * Implementing System Bus Access
  * Implementing semihosting and/or proxied syscalls
* RISC-V repository: https://github.com/riscv/riscv-openocd
* Upstream repository: https://sourceforge.net/p/openocd/code/ci/master/tree/
* Debug Spec Working Directory: https://github.com/riscv/riscv-debug-spec
* Debug Spec: https://github.com/riscv/riscv-debug-spec/blob/0.13/riscv-debug-spec.pdf
* Supported Debug Spec version(s): 0.11, 0.13

## GNU MCU Eclipse OpenOCD

A binary distribution of OpenOCD with support for RISC-V.

* Maintainer(s): Liviu Ionescu
* Web: https://gnu-mcu-eclipse.github.io/openocd/
* Repository: https://github.com/gnu-mcu-eclipse/openocd
* Build: https://github.com/gnu-mcu-eclipse/openocd-build
* Binary package installer: https://www.npmjs.com/package/@gnu-mcu-eclipse/openocd 

## Imperas Multi Processor Debugger

 * Status: commercially supported solution
 * Website: http://www.imperas.com/riscv#debug
 * Single core: simulator provides gdbServer for single core debug with GDB/Eclipse
 * Multi-Core debug available in Eclipse to debug SMP and AMP heterogeneous multi-core systems including all processor instances and peripheral behavioral components
 * Links: http://www.imperas.com/msdk-advanced-multicore-software-development-kit#Debug

## TCF Debugger

* Maintainer(s): Sanimir Agovic
* Website: https://projects.eclipse.org/projects/tools.cdt.tcf
* Version: HEAD
* Upstreaming status: Linux native debugging support commit
* Future work: 
  * Bare metal debugging based on RISC-V External Debug Support 
  * FPU support for native Linux debugging
* Upstream repository: https://github.com/eclipse/tcf.agent
* User Spec: 2.2
* Links:
  * https://git.eclipse.org/r/#/c/134914/

# C compilers and libraries


Name | Links | License | Maintainers
---- | ----- | ------- | -----------
GCC	| [Upstream](https://gcc.gnu.org/viewcvs/gcc/trunk/), [RISC-V repository](https://github.com/riscv/riscv-gcc) | GPL	| Andrew Waterman (SiFive), Palmer Dabbelt (SiFive), Jim Wilson (SiFive), Kito Cheng (Andes)
GNU MCU Eclipse RISC-V Embedded GCC (riscv-non-embed-gcc)	| [Web](https://gnu-mcu-eclipse.github.io/toolchain/riscv/), [Repository](https://github.com/gnu-mcu-eclipse/riscv-none-gcc), [Build](https://github.com/gnu-mcu-eclipse/riscv-none-gcc-build), [Binary package installer](https://www.npmjs.com/package/@gnu-mcu-eclipse/riscv-none-gcc)	| Eclipse Public License |	Liviu lonescu
clang	| -	| -	| -
CompCert	| [Upstream](https://github.com/AbsInt/CompCert.git)	| INRIA Non-Commercial License Agreement	| Xavier Leroy
Glibc	| [Upstream](https://sourceware.org/git/?p=glibc.git), [RISC-V repository](https://github.com/riscv/riscv-glibc) |	GPL |	Palmer Dabbelt (SiFive), Andrew Waterman (SiFive), DJ Delorie (Red Hat), Darius Rad(Bluespec)
Newlib	| [Upstream](http://cygwin.com/git/gitweb.cgi?p=newlib-cygwin.git), [RISC-V repository](https://github.com/riscv/riscv-newlib)	| GPL	| Kito Cheng (Andes)
Musl	| -	| - | -

# Boot loaders and monitors

## coreboot ##

* Maintainer(s): Ron Minnich (Google), Jonathan Neuschäfer
* Version: master
* Status: runs on spike, lowRISC/Nexys4DDR. Linux doesn't quite work yet.
* Upstreaming status: upstream
* Future work:
* RISC-V repository:
* Upstream repository: https://review.coreboot.org/cgit/coreboot.git/
* Privileged Spec: 1.9
* User Spec: 2.0
* ABI:

More information:
* https://riscv.org/wp-content/uploads/2016/01/Tues1345-riscvcoreboot.pdf
* https://www.youtube.com/watch?v=-KnwZzbvp1c (coreboot on RISC-V, Ron Minnich, RISC-V workshop)
* https://www.youtube.com/watch?v=CDNIWuf1jAk (coreboot on RISC-V, Ron Minnich, coreboot conference 2016)

## UEFI ##

* Maintainer(s): Abner Chang, Dong Wei (HP Enterprise)
* Version:
* Status:
* Upstreaming status:
* Future work:
* RISC-V repository:
* Upstream repository:
* Privileged Spec:
* User Spec: 2.0
* ABI:

https://riscv.org/wp-content/uploads/2016/01/Tues1415-RISC-V-and-UEFI.pdf

## Proxy Kernel/BBL ##

* Maintainer(s):
* Version:
* Status:
* Upstreaming status:
* Future work:
* Upstream repository: https://github.com/riscv/riscv-pk
* Privileged Spec: 1.9.1
* User Spec: 2.0
* ABI:

## OpenSBI
* Maintainer(s): Anup Patel
* Version: 0.3
* Status: 
* Upstreaming status:
* Future work:
* Upstream repository: https://github.com/riscv/opensbi
* Privileged Spec: 1.9.1
* User Spec:
* ABI:

# OS and OS kernels

## Linux Kernel

* Maintainer(s): Andrew Waterman (SiFive), Albert Ou (SiFive), Palmer Dabbelt (SiFive)
* Version: 4.15
* Upstreaming status: Merged
* Future work:
* RISC-V repository: https://github.com/riscv/riscv-linux
* Upstream repository: https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git
* Privileged Spec: 1.10
* User Spec: 2.0
* ABI:

## seL4

* Maintainer(s): Hesham Almatary and Data61/CSIRO
* Version: 9.0.1
* Status: Merged upstream.
* Upstreaming status: Done.
* Future work: Benchmarking.
* RISC-V repository: https://github.com/heshamelmatary/sel4riscv-manifest/blob/master/sel4test-06032018.xml
* Upstream repository: https://github.com/seL4/seL4
* Privileged Spec: 1.10
* User Spec: 2.1
* ABI:
* Links: http://heshamelmatary.blogspot.com.au/2017/06/update-sel4risc-v-smp-support-sel4.html

## RTEMS

* Maintainer(s): Hesham Almatary
* Version: 5
* Status: Merged upstream. Tier-1 RTEMS Target that runs on both simulators (Spike, QEMU, etc) and hardware with SMP, POSIX and Tests support.
* Upstream repository: https://git.rtems.org/rtems/
* Privileged Spec:
* User Spec:
* ABI:
* Links: https://docs.rtems.org/branches/master/user/bsps/bsps-riscv.html#riscv

## FreeRTOS

* Maintainer(s): AWS
* Version: 10.2.0
* Status: See https://www.freertos.org/Using-FreeRTOS-on-RISC-V.html#RISC_V_QUICK_START 
* Upstreaming status: Done
* Future work:
* Upstream repository: https://www.sourceforge.net/projects/freertos/  
* Privileged Spec:
* User Spec: 2.0
* ABI:
* Link(s): https://www.freertos.org/Using-FreeRTOS-on-RISC-V.html 

## NuttX

* Maintainer(s): 
* Version: 7.27
* Status: http://nuttx.org/Documentation/NuttX.html#riscv
* Upstreaming status: Done
* Future work:
* Upstream repository: https://bitbucket.org/nuttx/nuttx/src/master/
* Privileged Spec:
* User Spec: 
* ABI:
* Link(s): http://nuttx.org/Documentation/NuttX.html#riscv

## Apache Mynewt

* Maintainer(s): James Pace, Runtime
* Version:
* Status:
* Upstreaming status:
* Future work:
* RISC-V repository:
* Upstream repository:
* Privileged Spec:
* User Spec: 2.0
* ABI:
* Links: https://riscv.org/wp-content/uploads/2016/07/Wed930_riscv_apachemynewt_v1.2.pdf

## Zephyr

* Maintainer(s): Karol Gugala (Antmicro), Peter Gielda (Antmicro), Nathaniel Graff (SiFive)
* Version: 1.13.0
* Status: Support for RV32 QEMU Emulation, Zedboard Pulpino, SiFive HiFive1, MicroSemi M2GL025 Mi-V
* Upstreaming status: Done
* Future work:
* Upstream repository: https://github.com/zephyrproject-rtos/zephyr/
* Privileged Spec: 1.9.1
* User Spec: 2.1
* ABI:
* Links: http://docs.zephyrproject.org/boards/riscv32/index.html

## Fedora

* Maintainer(s): Richard WM Jones, Stefan O’Rear, David Abdurachmanov
* Version: 25
* Status: Packages from @Core group (except dracut and plymouth) built against an old ABI; on hold until the bootstrap can be repeated and automated
* Upstreaming status: Some changes upstreamed
* Future work: Redo bootstrap with gcc-7, upstream all patches
* RISC-V repository:
* Upstream repository:
* Privileged Spec: (depends on kernel used)
* User Spec: 2.0
* ABI: ~ September 2016 (not gcc-7)
* Links: http://fedoraproject.org/wiki/Architectures/RISC-V

## Debian

* Maintainer(s): Manuel A. Fernandez Montecelo
* Version: unstable (sid)
* Status: GCC and binutils for RISC-V are available in Unstable
* Upstreaming status: Out of tree
* Future work: -
* RISC-V repository: -
* Upstream repository: -
* Privileged Spec: Only important for the kernel, the userland is not affected
* User Spec: 2.0
* ABI:
* Links:
    * https://wiki.debian.org/RISC-V
    * http://riscv.mit.edu/
    * https://content.riscv.org/wp-content/uploads/2016/07/Wed1115_Working_Towards_a_Debian_RISC-V_Port.pdf
    * https://people.debian.org/~mafm/posts/2017/20170422_debian-gnulinux-port-for-risc-v-64-bit-riscv64/

## openSUSE

* Maintainer(s): Andreas Schwab (SUSE)
* Version: Tumbleweed
* Status:
* Upstreaming status: 
* Future work:
* RISC-V repository:
* Upstream repository: https://build.opensuse.org/project/show/openSUSE:Factory:RISCV
* Privileged Spec:
* User Spec: 2.2
* ABI:
* Links: https://en.opensuse.org/openSUSE:RISC-V

## OpenMandriva

* Maintainer(s): Bernhard "Bero" Rosenkränzer (bero at lindev dot ch)
* Version: cooker (AKA master)
* Status: Core packages built, RISC-V added to build server for all new packages. Currently building with gcc and ld.bfd (where OpenMandriva on other architectures defaults to clang and ld.gold). Package set not yet complete.
* Upstreaming status: upstream
* Future work: Toolchain changes, port remaining packages
* RISC-V repository: no separate repository, all merged into upstream
* Upstream repository: https://github.com/OpenMandrivaAssociation
* Privileged Spec: 2.0
* User Spec: 2.0
* ABI: lp64d, building with -march=rv64imafdc (ports to other subarches may happen in the future)
* Links: http://openmandriva.org/ http://abf-downloads.openmandriva.org/cooker/repository/riscv64/

## Yocto Project/OpenEmbedded

* Maintainer(s): Khem Raj
* Version: master
* Status: Support console images
* Upstreaming status: upstream
* Future work: Graphical packages, PIE, SSP
* RISC-V repository: https://github.com/riscv/meta-riscv
* Upstream repository: http://git.yoctoproject.org/
* Privileged Spec: 1.9.1
* User Spec: 2.0
* ABI:

## Poky

* Maintainer(s): Martin Maas (University of California, Berkeley)
* Version: master branch as of Oct 13, 2016.
* Status: Support for many packages, supports riscvemu and spike
* Upstreaming status: Out of tree
* Future work:
* RISC-V repository: https://github.com/riscv/riscv-poky
* Upstream repository: http://git.yoctoproject.org/cgit/cgit.cgi/poky/tree/
* Privileged Spec: 1.9.1
* User Spec: 2.0
* ABI:

## Gentoo

* Maintainer(s): Palmer Dabbelt (University of California, Berkeley)
* Version:
* Status:
* Upstreaming status: Out of tree
* Future work:
* RISC-V repository: https://github.com/palmer-dabbelt/riscv-gentoo
* Upstream repository: https://github.com/gentoo/gentoo
* Privileged Spec:
* User Spec: 2.0
* ABI:

## Parabola GNU/Linux-libre

* Maintainer(s): Andreas Grapentin (University of Potsdam, HPI)
* Version: rolling
* Status: complete base-devel cross-makepkg chroot
* Upstreaming status: 
* Future work: pacstrap bootable base VM 
* RISC-V repository: https://github.com/oaken-source/parabola-riscv64-bootstrap
* Upstream repository: https://git.parabola.nu/abslibre.git
* Privileged Spec:
* User Spec: 2.0
* ABI: stable
* Links:
    * https://parabola.nu

## OpenWrt

* Maintainer(s): Zoltan Herpai 
* Version: snapshots/trunk
* Status: Target and patches sit on top of trunk, builds with glibc. 99% of non-core (openwrt/packages) packages are built and availabe for download.
* Upstreaming status: Out of tree until 4.19 is integrated into trunk
* Future work: musl 1.21 integration
* RISC-V repository: https://git.openwrt.org/?p=openwrt/staging/wigyori.git;a=shortlog;h=refs/heads/kitchensink-201810
* Upstream repository: -
* Privileged Spec: 
* User Spec: 2.0
* ABI:
* Links: http://openwrt.uid0.hu (binary repository)

## januslinux

* Maintainer(s): nee-san
* Version: master
* Status: works 64-bit version only in QEMU. 32-bit has problems with Michael Forney's risc-v musl
* Upstreaming status: 
* Future work:
* RISC-V repository:
* Upstream repository: https://github.com/JanusLinux/janus
* Privileged Spec:
* User Spec: 2.2
* ABI:
* Links:

## Buildroot

* Maintainer(s): Mark Corbin (Embecosm)
* Version:
  * master branch as of Sept 25, 2018 (64 bit)
  * master branch as of Jan 10, 2019 (32 bit)
* Status: Basic RISC-V 32-bit and 64-bit support for QEMU virtual target
* Upstreaming status: upstream
* Future work: -
* Upstream repository: https://git.busybox.net/buildroot/
* Privileged Spec: 
* User Spec: 
* ABI:

## FreeBSD

* Maintainer(s): Ruslan Bukin (FreeBSD)
* Version: 11.0
* Status: Base system, no ports yet
* Upstreaming status: RISC-V support in FreeBSD 11.0
* Future work: FreeBSD ports system
* Upstream repository: https://github.com/freebsd/freebsd (Mirror)
* Privileged Spec: 1.10
* User Spec: 2.0
* ABI:
* Links: https://wiki.freebsd.org/riscv

https://riscv.org/wp-content/uploads/2016/01/Tues1445-freebsd-riscv-1.pdf

## NetBSD

* Maintainer(s): Matt Thomas (NetBSD), Reinoud Zandijk (NetBSD)
* Version:
* Status:
* Upstreaming status:
* Future work:
* Upstream repository:
http://cvsweb.netbsd.org/bsdweb.cgi/src/?only_with_tag=MAIN
https://github.com/jsonn/src (Git Mirror)
* Privileged Spec: 1.9
* User Spec: 2.0
* ABI:

# Compilers and runtimes for other languages

Name | Links | License | Maintainers
---- | ----- | ------- | -----------
Go	| [Upstream](https://github.com/golang/go), [RISC-V repository](https://github.com/riscv/riscv-go), [Stef's fork](https://github.com/sorear/golang-go) | BSD 3-clause	| Benjamin Barenblat (Google), Michael Pratt (Google), Stef O'Rear
Ocaml	| [Upstream](https://github.com/ocaml/ocaml), [RISC-V repository](https://github.com/nojb/riscv-ocaml)	| LGPL	| Nicolás Ojeda Bär
Maxine VM (Java Virtual Machine)	| [Upstream](https://github.com/beehive-lab/Maxine-VM)	| GPL	| Maxine team
Jikes RVM (Java Virtual Machine)	| [Upstream](https://github.com/JikesRVM/JikesRVM)	| Eclipse Public License (EPL)	| Martin Maas (University of California, Berkeley)
OpenJDK/HotSpot (Java Virtual Machine)	| ?	| ?	| Alexey Baturo, Michael Knysnek, Martin Maas
Free Pascal	| [Upstream](https://svn.freepascal.org/cgi-bin/viewvc.cgi/trunk/)	| ?	| Jeppe Johansen and others
Nim	| [Upstream](https://nim-lang.org/)	| MIT	| Andreas Rumpf and others
Ada (GNAT)	| [Upstream](https://gcc.gnu.org/viewcvs/gcc/trunk/)	| Proprietary	| [AdaCore](http://adacore.com)
Rust	| [Upstream](https://github.com/rust-lang/rust/)	| Apache and MIT	| [Rust Project](https://www.rust-lang.org/)
muForth	| [Upstream](https://github.com/nimblemachines/muforth)	| ?	| David Frech
ibForth	| [Upstream](https://github.com/larsbrinkhoff/lbForth)	| GPL	| Lars Brinkhoff
Mecrisp-Quintis Forth kernel	| [Upstream](http://mecrisp.sourceforge.net/)	| ?	| Matthias Koch

# IDEs

Name | Links | License | Maintainers
---- | ----- | ------- | -----------
GNU MCU Eclipse | [Website](https://gnu-mcu-eclipse.github.io), [Repositories](https://github.com/gnu-mcu-eclipse), [Binary distribution](https://github.com/gnu-mcu-eclipse/org.eclipse.epp.packages/releases/) |	EPL-1.0 / various	| Liviu Ionescu


# Security

Name | Links | License | Maintainers
---- | ----- | ------- | -----------
Hex Five Security | [SDK](https://github.com/hex-five/multizone-sdk) |	Proprietary	| [Hex Five Security Inc.](www.hex-five.com)

# Help Wanted

* V8
* Node.js
* Dart


---
- #### Download [Busybox](https://busybox.net)
> - **Sources**
> > ```bash
> > --> Linux:
> >      - Built & Compiled from source : 'https://git.busybox.net/busybox/'
> >        - GCC (Natively using Cross Toolchains)
> >        - MUSL
> >           - 'https://hub.docker.com/r/abcfy2/muslcc-toolchain-ubuntu'
> >           - 'https://hub.docker.com/r/blackdex/musl-toolchain'
> >
> > ```
```bash
!# Get CPU Arch (Android)
[ADB]
adb shell getprop ro.product.cpu.abi
[Termux]
getprop ro.product.cpu.abi

!# Get CPU Arch (Linux)
 uname -m || dpkg --print-architecture

!# Get CPU Arch (Windows)
[cmd prompt]
echo %PROCESSOR_ARCHITECTURE%
[Powershell]
$env:PROCESSOR_ARCHITECTURE

!# Index (ARCH || ALT_ARCH)
!# Linux
--> aarch64 || arm64 [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/busybox/busybox_aarch64_arm64_gcc_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/busybox/busybox_aarch64_arm64_musl_Linux"
--> Amd x86_64 || x86_64 [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/busybox/busybox_amd_x86_64_gcc_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/busybox/busybox_amd_x86_64_musl_Linux"
--> ARM_abi [32-bit]
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/busybox/busybox_arm_abi_gcc_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/busybox/busybox_arm_abi_musl_Linux"
--> ARM_abihf [32-bit]
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/busybox/busybox_arm_abihf_gcc_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/busybox/busybox_arm_abihf_musl_Linux"
--> ARMv7_abi [32-bit]
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/busybox/busybox_armv7_abi_gcc_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/busybox/busybox_armv7_abi_musl_Linux"
--> ARMv7l_abihf [32-bit]
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/busybox/busybox_armv7_abihf_musl_Linux"
--> i586 || Intel 80386 [32-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/busybox/busybox_i586_gcc_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/busybox/busybox_i586_musl_Linux"
--> i686 || x86 [32-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/busybox/busybox_amd_x86_i686_gcc_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/busybox/busybox_amd_x86_i686_musl_Linux"
--> MIPS (Big-Endian) [32-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/busybox/busybox_mips_gcc_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/busybox/busybox_mips_musl_Linux"
--> MIPSel || MIPSle (Little-Endian) [32-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/busybox/busybox_mipsel_gcc_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/busybox/busybox_mipsel_musl_Linux"
--> MIPS64 (Big-Endian) [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/busybox/busybox_mips64_gcc_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/busybox/busybox_mips64_musl_Linux"
--> MIPS64el || MIPS64le (Little-Endian) [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/busybox/busybox_mips64el_gcc_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/busybox/busybox_mips64el_musl_Linux"
--> powerpc || ppc || cisco 4500 [32-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/busybox/busybox_powerpc_gcc_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/busybox/busybox/busybox_powerpc_musl_Linux"
--> powerpc64|| ppc64 || cisco 7500 [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/busybox/busybox_powerpc64_gcc_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/busybox/busybox/busybox_powerpc64_musl_Linux"
--> powerpc64le || ppc64le || cisco 7500 || OpenPOWER ELF V2 ABI (Little-Endian) [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/busybox/busybox_powerpc64le_gcc_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/busybox/busybox_powerpc64le_musl_Linux"
--> riscv32 || CB RISC-V || RVC [32-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/busybox/busybox_riscv32_gcc_Linux"
--> riscv64 || CB RISC-V || RVC [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/busybox/busybox_riscv64_gcc_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/busybox/busybox_riscv64_musl_Linux"
--> s390x || IBM S/390 [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/busybox/busybox_s390x_gcc_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/busybox/busybox_s390x_musl_Linux"
```
---
- #### Install busybox
```bash
!# Create a $USER Writeable DIR & export to PATH
 mkdir -p "$HOME/bin" && export PATH="$HOME/bin:$PATH"

!# Move Downloaded Busybox binary to that DIR
 mv "$Path_To_Busybox_Binary" "$HOME/bin/busybox"

!# Give Writeable Perms
 chmod +xwr "$HOME/bin/busybox" && chmod +xwr $HOME/bin/*

#! Install & Symlink Everything
 cd "$HOME/bin" && "$HOME/bin/busybox" --install -s .
```

---
```console

--> METADATA
./busybox/busybox_aarch64_arm64_gcc_Linux:  ELF 64-bit LSB executable, ARM aarch64, version 1 (GNU/Linux), statically linked, BuildID[sha1]=c75df99a0b31bd412a6dfcc71dd6e29aee7088dd, for GNU/Linux 3.7.0, stripped
./busybox/busybox_aarch64_arm64_musl_Linux: ELF 64-bit LSB pie executable, ARM aarch64, version 1 (SYSV), static-pie linked, stripped
./busybox/busybox_amd_x86_64_gcc_Linux:     ELF 64-bit LSB executable, x86-64, version 1 (GNU/Linux), statically linked, BuildID[sha1]=1a52ba5644656e0dc19f60d596e11b35f253ef8a, for GNU/Linux 3.2.0, stripped
./busybox/busybox_amd_x86_64_musl_Linux:    ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), static-pie linked, stripped
./busybox/busybox_arm_abi_gcc_Linux:        ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, BuildID[sha1]=6bc6aa15a5174803d384fb5c56e898a55fdaba77, for GNU/Linux 3.2.0, stripped
./busybox/busybox_arm_abi_musl_Linux:       ELF 32-bit LSB pie executable, ARM, EABI5 version 1 (SYSV), static-pie linked, stripped
./busybox/busybox_arm_abihf_gcc_Linux:      ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), statically linked, BuildID[sha1]=bf8602733ca66c049fa969594fe2cc7080c15f07, for GNU/Linux 3.2.0, stripped
./busybox/busybox_arm_abihf_musl_Linux:     ELF 32-bit LSB pie executable, ARM, EABI5 version 1 (SYSV), static-pie linked, stripped
./busybox/busybox_armv7l_abihf_musl_Linux:  ELF 32-bit LSB pie executable, ARM, EABI5 version 1 (SYSV), static-pie linked, stripped
./busybox/busybox_i686_x86_gcc_Linux:       ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), statically linked, BuildID[sha1]=b5ef99375fad540f1962dafccf6d7ebb50957b09, for GNU/Linux 3.2.0, stripped
./busybox/busybox_m68k_gcc_Linux:           ELF 32-bit MSB executable, Motorola m68k, 68020, version 1 (SYSV), statically linked, BuildID[sha1]=2568e14ce3cb1ed866f749f6255a2ce30e6230f7, for GNU/Linux 3.2.0, stripped
./busybox/busybox_m68k_linux_musl_Linux:    ELF 32-bit MSB pie executable, Motorola m68k, 68020, version 1 (SYSV), static-pie linked, stripped
./busybox/busybox_mips64_gcc_Linux:         ELF 64-bit MSB executable, MIPS, MIPS64 rel2 version 1 (SYSV), statically linked, BuildID[sha1]=6483b79fd77ab6e522d02481426e4490daf3cf43, for GNU/Linux 3.2.0, stripped
./busybox/busybox_mips64_musl_Linux:        ELF 64-bit MSB pie executable, MIPS, MIPS-III version 1 (SYSV), static-pie linked, stripped
./busybox/busybox_mips64el_gcc_Linux:       ELF 64-bit LSB executable, MIPS, MIPS64 rel2 version 1 (SYSV), statically linked, BuildID[sha1]=32b29b1af2d725021e2d0f32f3929352825fc67d, for GNU/Linux 3.2.0, stripped
./busybox/busybox_mips64el_musl_Linux:      ELF 64-bit LSB pie executable, MIPS, MIPS-III version 1 (SYSV), static-pie linked, stripped
./busybox/busybox_mips_gcc_Linux:           ELF 32-bit MSB executable, MIPS, MIPS32 rel2 version 1 (SYSV), statically linked, BuildID[sha1]=df74f99a051802ebb9757030aab758add5f1faeb, for GNU/Linux 3.2.0, stripped
./busybox/busybox_mips_musl_Linux:          ELF 32-bit MSB pie executable, MIPS, MIPS-I version 1 (SYSV), static-pie linked, stripped
./busybox/busybox_mipsel_gcc_Linux:         ELF 32-bit LSB executable, MIPS, MIPS32 rel2 version 1 (SYSV), statically linked, BuildID[sha1]=7133022e36b20ccd9f5a1619bf4b0d8df06cd19c, for GNU/Linux 3.2.0, stripped
./busybox/busybox_mipsel_musl_Linux:        ELF 32-bit LSB pie executable, MIPS, MIPS-I version 1 (SYSV), static-pie linked, stripped
./busybox/busybox_powerpc64_gcc_Linux:      ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (GNU/Linux), statically linked, BuildID[sha1]=4dfecb0adc6815b3702b05eb6ad56fef476987d1, for GNU/Linux 3.2.0, stripped
./busybox/busybox_powerpc64_musl_Linux:     ELF 64-bit MSB pie executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), static-pie linked, stripped
./busybox/busybox_powerpc64le_gcc_Linux:    ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (GNU/Linux), statically linked, BuildID[sha1]=2f7b454650469bb610edefb152067c1d1a2493c3, for GNU/Linux 3.10.0, stripped
./busybox/busybox_powerpc64le_musl_Linux:   ELF 64-bit LSB pie executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), static-pie linked, stripped
./busybox/busybox_powerpc_gcc_Linux:        ELF 32-bit MSB executable, PowerPC or cisco 4500, version 1 (SYSV), statically linked, BuildID[sha1]=8d00571ed69ada70df702055582ac847bcef4253, for GNU/Linux 3.2.0, stripped
./busybox/busybox_powerpc_musl_Linux:       ELF 32-bit MSB pie executable, PowerPC or cisco 4500, version 1 (SYSV), static-pie linked, stripped
./busybox/busybox_riscv32_gcc_Linux:        ELF 32-bit LSB executable, UCB RISC-V, RVC, double-float ABI, version 1 (SYSV), statically linked, for GNU/Linux 5.4.0, stripped
./busybox/busybox_riscv64_gcc_Linux:        ELF 64-bit LSB executable, UCB RISC-V, RVC, double-float ABI, version 1 (SYSV), statically linked, BuildID[sha1]=247bc90ba94dd172e907aa015321dd1d097cd6b6, for GNU/Linux 4.15.0, stripped
./busybox/busybox_riscv64_musl_Linux:       ELF 64-bit LSB pie executable, UCB RISC-V, RVC, double-float ABI, version 1 (SYSV), static-pie linked, stripped
./busybox/busybox_s390x_gcc_Linux:          ELF 64-bit MSB executable, IBM S/390, version 1 (GNU/Linux), statically linked, BuildID[sha1]=a2ebd8e3fd9cff74a78df14b0395a122f10c9ff1, for GNU/Linux 3.2.0, stripped
./busybox/busybox_s390x_musl_Linux:         ELF 64-bit MSB pie executable, IBM S/390, version 1 (SYSV), static-pie linked, stripped

--> SHA256SUM
cc149d6d0b7044a3e64f2dd2b68bb27604d9de6ed2beb8bc276923bd81c91fff  ./busybox/busybox_aarch64_arm64_gcc_Linux
89e8e12b6933d966fab05b3935223f085b4de055e35f775aacc4b795e0445865  ./busybox/busybox_aarch64_arm64_musl_Linux
7a84f3b02c8c4b93b1fb5939b54b880c4f4c1999c4251dabca217ca0b42e0185  ./busybox/busybox_amd_x86_64_gcc_Linux
72b59cfbcbce34f7480354c9209c8e852b34d0c8863cb9ea290e1a23a80153d4  ./busybox/busybox_amd_x86_64_musl_Linux
fbc5858ee5ea03e9180c4bfce6b2b5c939a807c78b685cbe82d5009127925ad3  ./busybox/busybox_arm_abi_gcc_Linux
4605a149bc47d0ac99851471abe7045bd19f50d66f1b0c2c6680ccd1d4494538  ./busybox/busybox_arm_abi_musl_Linux
55c4bb3a99fc11c0cfc16619386662211a86e71910907bcfce896943749ca118  ./busybox/busybox_arm_abihf_gcc_Linux
1054c5105e9eb00b80198e9180dfe21377ff39575ff655d7ed32b05ab7f58343  ./busybox/busybox_arm_abihf_musl_Linux
e8fd62962d6612161320713623a238d333710f9d9ee35f7964abf9a791f0379d  ./busybox/busybox_armv7l_abihf_musl_Linux
426a652862a1c367e5f10f8a7346e2836a01a46fbc24a16eec24f834567f1bac  ./busybox/busybox_i686_x86_gcc_Linux
ac9672bce80190605ce53f01303d1f8c0a4433db1a2dbcf0a3eefb37ed4608d7  ./busybox/busybox_m68k_gcc_Linux
32bfb1391a2e01c8483db5d3f368dbf22eb18d4a20040178cab16bbfd5070024  ./busybox/busybox_m68k_linux_musl_Linux
f8887e4cfb31da6e4b834a5e1817dffb454ee5b8b89f36aa73835cf435ee0f65  ./busybox/busybox_mips64_gcc_Linux
38aed7384c5fe192b9ee878b815e06bf6d515351316e6d1763de9bb393e33d6f  ./busybox/busybox_mips64_musl_Linux
ba3c3fafb85bdccc05f989f96bb17dca6772c8c49b0703a32ea4704b65112078  ./busybox/busybox_mips64el_gcc_Linux
9e5f6cbdefe2d49c4aae6b649d3e2730c9c80544b64a1676f3b161259f4d0952  ./busybox/busybox_mips64el_musl_Linux
51eaf3fd8deb5c560dc9de3c385118570805d820dd20b7712b7244874126e404  ./busybox/busybox_mips_gcc_Linux
b5e0e563365ae93f2db908742bbec6471b34a88e07d895dd71e3a6a2b68ef791  ./busybox/busybox_mips_musl_Linux
c0ac6e49fa0ee60c081f76789ee79f1067b858f5bda17dd640889be229b6c936  ./busybox/busybox_mipsel_gcc_Linux
a35e9a727b3fe340be78b0c6b217e3dfcb5a7b8d1d7c64c97667edc3b4b609e3  ./busybox/busybox_mipsel_musl_Linux
087ee233c829eed53003571ec21bf870f0384ee9bb6e45e228e5e6568953e39c  ./busybox/busybox_powerpc64_gcc_Linux
4482dc6803381a6f23b07e832d9ff7d2730d7ffa0d06a5dc677290247e0d5881  ./busybox/busybox_powerpc64_musl_Linux
39f436a7148115e135c886d64722d4120670c2d354baa05264870bf970077b78  ./busybox/busybox_powerpc64le_gcc_Linux
e9cfd2bd591add8b46b59b6ecf4cd4394d0e859dfd8b338c96b76c5b8055602b  ./busybox/busybox_powerpc64le_musl_Linux
e6aad66dd298647ef4986813918c0d0434ca3d047b8170ebe9519bc170d5b7b0  ./busybox/busybox_powerpc_gcc_Linux
73088f1145671381d1187789e7738aeb8c57ae70a2ccbde5b8ef9bb500bede1a  ./busybox/busybox_powerpc_musl_Linux
37d6bb612fbb16bf0c9bc91fd6beefd0f22c4fece4ae24edf9bf9355965a2725  ./busybox/busybox_riscv32_gcc_Linux
bef507b172302238785c18c0e0359be018cd61b3a8368a2d5bb5af9842a5f0ee  ./busybox/busybox_riscv64_gcc_Linux
819b826133249b63a9d2f8102bcce7ab2be8d47a300e0be68099ea0d33fad729  ./busybox/busybox_riscv64_musl_Linux
38055f4803c8c4988345d662e1904b15e7f644769622d4dd0bdbb5054b60046c  ./busybox/busybox_s390x_gcc_Linux
c2020629df39e385cd564ce75d4f5dec1a9b70a9fe13281ba3a578a1b7b76c78  ./busybox/busybox_s390x_musl_Linux
```


---

- #### Sizes

```console
2.1M  ./busybox/busybox_aarch64_arm64_gcc_Linux
1.2M  ./busybox/busybox_aarch64_arm64_musl_Linux
2.5M  ./busybox/busybox_amd_x86_64_gcc_Linux
1.2M  ./busybox/busybox_amd_x86_64_musl_Linux
2.1M  ./busybox/busybox_arm_abi_gcc_Linux
1.3M  ./busybox/busybox_arm_abi_musl_Linux
1.5M  ./busybox/busybox_arm_abihf_gcc_Linux
1.3M  ./busybox/busybox_arm_abihf_musl_Linux
898K  ./busybox/busybox_armv7l_abihf_musl_Linux
2.3M  ./busybox/busybox_i686_x86_gcc_Linux
1.8M  ./busybox/busybox_m68k_gcc_Linux
1.3M  ./busybox/busybox_m68k_linux_musl_Linux
2.8M  ./busybox/busybox_mips64_gcc_Linux
1.7M  ./busybox/busybox_mips64_musl_Linux
2.8M  ./busybox/busybox_mips64el_gcc_Linux
1.7M  ./busybox/busybox_mips64el_musl_Linux
2.6M  ./busybox/busybox_mips_gcc_Linux
1.8M  ./busybox/busybox_mips_musl_Linux
2.6M  ./busybox/busybox_mipsel_gcc_Linux
1.8M  ./busybox/busybox_mipsel_musl_Linux
2.9M  ./busybox/busybox_powerpc64_gcc_Linux
1.5M  ./busybox/busybox_powerpc64_musl_Linux
2.9M  ./busybox/busybox_powerpc64le_gcc_Linux
1.6M  ./busybox/busybox_powerpc64le_musl_Linux
2.4M  ./busybox/busybox_powerpc_gcc_Linux
1.5M  ./busybox/busybox_powerpc_musl_Linux
1.7M  ./busybox/busybox_riscv32_gcc_Linux
1.7M  ./busybox/busybox_riscv64_gcc_Linux
1.1M  ./busybox/busybox_riscv64_musl_Linux
2.3M  ./busybox/busybox_s390x_gcc_Linux
1.5M  ./busybox/busybox_s390x_musl_Linux
```

---

- #### Bundled Commands
```console

$ ./busybox/busybox_amd_x86_64_gcc_Linux
BusyBox v1.36.1 (2024-07-24 20:39:04 UTC) multi-call binary.
BusyBox is copyrighted by many authors between 1998-2015.
Licensed under GPLv2. See source distribution for detailed
copyright notices.

Usage: busybox [function [arguments]...]
   or: busybox --list[-full]
   or: busybox --show SCRIPT
   or: busybox --install [-s] [DIR]
   or: function [arguments]...

	BusyBox is a multi-call binary that combines many common Unix
	utilities into a single executable.  Most people will create a
	link to busybox for each function they wish to use and BusyBox
	will act like whatever it was invoked as.

Currently defined functions:
	[, [[, acpid, add-shell, addgroup, adduser, adjtimex, arch, arp,
	arping, ascii, ash, awk, base32, base64, basename, bc, beep,
	blkdiscard, blkid, blockdev, bootchartd, brctl, bunzip2, bzcat, bzip2,
	cal, cat, chat, chattr, chgrp, chmod, chown, chpasswd, chpst, chroot,
	chrt, chvt, cksum, clear, cmp, comm, conspy, cp, cpio, crc32, crond,
	crontab, cryptpw, cttyhack, cut, date, dc, dd, deallocvt, delgroup,
	deluser, depmod, devmem, df, dhcprelay, diff, dirname, dmesg, dnsd,
	dnsdomainname, dos2unix, dpkg, dpkg-deb, du, dumpkmap, dumpleases,
	echo, ed, egrep, eject, env, envdir, envuidgid, ether-wake, expand,
	expr, factor, fakeidentd, fallocate, false, fatattr, fbset, fbsplash,
	fdflush, fdformat, fdisk, fgconsole, fgrep, find, findfs, flock, fold,
	free, freeramdisk, fsck, fsck.minix, fsfreeze, fstrim, fsync, ftpd,
	ftpget, ftpput, fuser, getopt, getty, grep, groups, gunzip, gzip, halt,
	hd, hdparm, head, hexdump, hexedit, hostid, hostname, httpd, hush,
	hwclock, i2cdetect, i2cdump, i2cget, i2cset, i2ctransfer, id, ifconfig,
	ifdown, ifenslave, ifplugd, ifup, inetd, init, insmod, install, ionice,
	iostat, ip, ipaddr, ipcalc, ipcrm, ipcs, iplink, ipneigh, iproute,
	iprule, iptunnel, kbd_mode, kill, killall, killall5, klogd, last, less,
	link, linux32, linux64, linuxrc, ln, loadfont, loadkmap, logger, login,
	logname, logread, losetup, lpd, lpq, lpr, ls, lsattr, lsmod, lsof,
	lspci, lsscsi, lsusb, lzcat, lzma, lzop, makedevs, makemime, man,
	md5sum, mdev, mesg, microcom, mim, mkdir, mkdosfs, mke2fs, mkfifo,
	mkfs.ext2, mkfs.minix, mkfs.vfat, mknod, mkpasswd, mkswap, mktemp,
	modinfo, modprobe, more, mount, mountpoint, mpstat, mt, mv, nameif,
	nanddump, nandwrite, nbd-client, nc, netstat, nice, nl, nmeter, nohup,
	nologin, nproc, nsenter, nslookup, ntpd, od, openvt, partprobe, passwd,
	paste, patch, pgrep, pidof, ping, ping6, pipe_progress, pivot_root,
	pkill, pmap, popmaildir, poweroff, powertop, printenv, printf, ps,
	pscan, pstree, pwd, pwdx, raidautorun, rdate, rdev, readahead,
	readlink, readprofile, realpath, reboot, reformime, remove-shell,
	renice, reset, resize, resume, rev, rm, rmdir, rmmod, route, rpm,
	rpm2cpio, rtcwake, run-init, run-parts, runlevel, runsv, runsvdir, rx,
	script, scriptreplay, sed, seedrng, sendmail, seq, setarch, setconsole,
	setfattr, setfont, setkeycodes, setlogcons, setpriv, setserial, setsid,
	setuidgid, sh, sha1sum, sha256sum, sha3sum, sha512sum, showkey, shred,
	shuf, slattach, sleep, smemcap, softlimit, sort, split, ssl_client,
	start-stop-daemon, stat, strings, stty, su, sulogin, sum, sv, svc,
	svlogd, svok, swapoff, swapon, switch_root, sync, sysctl, syslogd, tac,
	tail, tar, taskset, tc, tcpsvd, tee, telnet, telnetd, test, tftp,
	tftpd, time, timeout, top, touch, tr, traceroute, traceroute6, tree,
	true, truncate, ts, tsort, tty, ttysize, tunctl, ubiattach, ubidetach,
	ubimkvol, ubirename, ubirmvol, ubirsvol, ubiupdatevol, udhcpc, udhcpc6,
	udhcpd, udpsvd, uevent, umount, uname, unexpand, uniq, unix2dos,
	unlink, unlzma, unshare, unxz, unzip, uptime, users, usleep, uudecode,
	uuencode, vconfig, vi, vlock, volname, w, wall, watch, watchdog, wc,
	wget, which, who, whoami, whois, xargs, xxd, xz, xzcat, yes, zcat,
	zcip


```

---


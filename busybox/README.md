
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
./busybox/busybox_aarch64_arm64_gcc_Linux:  ELF 64-bit LSB executable, ARM aarch64, version 1 (GNU/Linux), statically linked, BuildID[sha1]=a8a4014916bacad7da45e82ede9052642d9a93c5, for GNU/Linux 3.7.0, stripped
./busybox/busybox_aarch64_arm64_musl_Linux: ELF 64-bit LSB pie executable, ARM aarch64, version 1 (SYSV), static-pie linked, stripped
./busybox/busybox_amd_x86_64_gcc_Linux:     ELF 64-bit LSB executable, x86-64, version 1 (GNU/Linux), statically linked, BuildID[sha1]=818cdf6053c3b3fe2b61387c91ec2637feaaa395, for GNU/Linux 3.2.0, stripped
./busybox/busybox_amd_x86_64_musl_Linux:    ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), static-pie linked, stripped
./busybox/busybox_arm_abi_gcc_Linux:        ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, BuildID[sha1]=a5c2e73df718ba267f553e7a12f0115a8c3d0418, for GNU/Linux 3.2.0, stripped
./busybox/busybox_arm_abi_musl_Linux:       ELF 32-bit LSB pie executable, ARM, EABI5 version 1 (SYSV), static-pie linked, stripped
./busybox/busybox_arm_abihf_gcc_Linux:      ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), statically linked, BuildID[sha1]=5056e2d7b5b5b29ec67853546e7e2903f2a40ae4, for GNU/Linux 3.2.0, stripped
./busybox/busybox_arm_abihf_musl_Linux:     ELF 32-bit LSB pie executable, ARM, EABI5 version 1 (SYSV), static-pie linked, stripped
./busybox/busybox_armv7l_abihf_musl_Linux:  ELF 32-bit LSB pie executable, ARM, EABI5 version 1 (SYSV), static-pie linked, stripped
./busybox/busybox_i686_x86_gcc_Linux:       ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), statically linked, BuildID[sha1]=dbb3dfd7721220a5c4a14d7ca9357543dc25b45c, for GNU/Linux 3.2.0, stripped
./busybox/busybox_m68k_gcc_Linux:           ELF 32-bit MSB executable, Motorola m68k, 68020, version 1 (SYSV), statically linked, BuildID[sha1]=2bcd931a3573fbfb3408e8b24b44072b9c03580b, for GNU/Linux 3.2.0, stripped
./busybox/busybox_m68k_linux_musl_Linux:    ELF 32-bit MSB pie executable, Motorola m68k, 68020, version 1 (SYSV), static-pie linked, stripped
./busybox/busybox_mips64_gcc_Linux:         ELF 64-bit MSB executable, MIPS, MIPS64 rel2 version 1 (SYSV), statically linked, BuildID[sha1]=e3c74ac6365d3a395554a5a03e8b6785906e7206, for GNU/Linux 3.2.0, stripped
./busybox/busybox_mips64_musl_Linux:        ELF 64-bit MSB pie executable, MIPS, MIPS-III version 1 (SYSV), static-pie linked, stripped
./busybox/busybox_mips64el_gcc_Linux:       ELF 64-bit LSB executable, MIPS, MIPS64 rel2 version 1 (SYSV), statically linked, BuildID[sha1]=ab514f1c5e2e325f9de4ebb96d5dd1c022498919, for GNU/Linux 3.2.0, stripped
./busybox/busybox_mips64el_musl_Linux:      ELF 64-bit LSB pie executable, MIPS, MIPS-III version 1 (SYSV), static-pie linked, stripped
./busybox/busybox_mips_gcc_Linux:           ELF 32-bit MSB executable, MIPS, MIPS32 rel2 version 1 (SYSV), statically linked, BuildID[sha1]=2cb1b31660df68d2516b141b4270e5ac04c605ac, for GNU/Linux 3.2.0, stripped
./busybox/busybox_mips_musl_Linux:          ELF 32-bit MSB pie executable, MIPS, MIPS-I version 1 (SYSV), static-pie linked, stripped
./busybox/busybox_mipsel_gcc_Linux:         ELF 32-bit LSB executable, MIPS, MIPS32 rel2 version 1 (SYSV), statically linked, BuildID[sha1]=d175d5997e5836f51bd32386244b784a30cad7ca, for GNU/Linux 3.2.0, stripped
./busybox/busybox_mipsel_musl_Linux:        ELF 32-bit LSB pie executable, MIPS, MIPS-I version 1 (SYSV), static-pie linked, stripped
./busybox/busybox_powerpc64_gcc_Linux:      ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (GNU/Linux), statically linked, BuildID[sha1]=3a32201d6118b7b31267b379540c8aa2b1aaecd0, for GNU/Linux 3.2.0, stripped
./busybox/busybox_powerpc64_musl_Linux:     ELF 64-bit MSB pie executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), static-pie linked, stripped
./busybox/busybox_powerpc64le_gcc_Linux:    ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (GNU/Linux), statically linked, BuildID[sha1]=46819d9a94de5e8bafcf2cb5921da8fade017287, for GNU/Linux 3.10.0, stripped
./busybox/busybox_powerpc64le_musl_Linux:   ELF 64-bit LSB pie executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), static-pie linked, stripped
./busybox/busybox_powerpc_gcc_Linux:        ELF 32-bit MSB executable, PowerPC or cisco 4500, version 1 (SYSV), statically linked, BuildID[sha1]=8b8dbd0155596fd797df1f4f3dc9a9ba79165948, for GNU/Linux 3.2.0, stripped
./busybox/busybox_powerpc_musl_Linux:       ELF 32-bit MSB pie executable, PowerPC or cisco 4500, version 1 (SYSV), static-pie linked, stripped
./busybox/busybox_riscv32_gcc_Linux:        ELF 32-bit LSB executable, UCB RISC-V, RVC, double-float ABI, version 1 (SYSV), statically linked, for GNU/Linux 5.4.0, stripped
./busybox/busybox_riscv64_gcc_Linux:        ELF 64-bit LSB executable, UCB RISC-V, RVC, double-float ABI, version 1 (SYSV), statically linked, BuildID[sha1]=093c955dbb8925ba5bcdfb9c6bd587815a63fe11, for GNU/Linux 4.15.0, stripped
./busybox/busybox_riscv64_musl_Linux:       ELF 64-bit LSB pie executable, UCB RISC-V, RVC, double-float ABI, version 1 (SYSV), static-pie linked, stripped
./busybox/busybox_s390x_gcc_Linux:          ELF 64-bit MSB executable, IBM S/390, version 1 (GNU/Linux), statically linked, BuildID[sha1]=4c369d7dde1959c0bd1a2671db0bab10c73a9f67, for GNU/Linux 3.2.0, stripped
./busybox/busybox_s390x_musl_Linux:         ELF 64-bit MSB pie executable, IBM S/390, version 1 (SYSV), static-pie linked, stripped

--> SHA256SUM
95ecdbbae5797b18f91048078a4d71960099a27d2534213da963b97d12634b83  ./busybox/busybox_aarch64_arm64_gcc_Linux
89e8e12b6933d966fab05b3935223f085b4de055e35f775aacc4b795e0445865  ./busybox/busybox_aarch64_arm64_musl_Linux
4a32f43115bac88da8f9f850e34938c9eb9bbc49bd74202c10383bcf4a8b289a  ./busybox/busybox_amd_x86_64_gcc_Linux
72b59cfbcbce34f7480354c9209c8e852b34d0c8863cb9ea290e1a23a80153d4  ./busybox/busybox_amd_x86_64_musl_Linux
9517ff35e576d5b189d5c99100fe98b2a525d6474a387820dff9e59725c723aa  ./busybox/busybox_arm_abi_gcc_Linux
4605a149bc47d0ac99851471abe7045bd19f50d66f1b0c2c6680ccd1d4494538  ./busybox/busybox_arm_abi_musl_Linux
08876a8d0dd8dd7932566fb6e492e4ab10f6cc490a903f2ac9f0158802fe71b9  ./busybox/busybox_arm_abihf_gcc_Linux
4260118d29a95826adbf570a73910ed899813d42b7fde1ef44612c807a06ead9  ./busybox/busybox_arm_abihf_musl_Linux
e8fd62962d6612161320713623a238d333710f9d9ee35f7964abf9a791f0379d  ./busybox/busybox_armv7l_abihf_musl_Linux
df9c68994742f42e9fd10e8787731ea76ebaffbdd7d9f14652b7fcc1ecc0240e  ./busybox/busybox_i686_x86_gcc_Linux
fad7cf77b8cb4343121deecac5c59d51e79036791bf425fbcbc70f01b25c66b4  ./busybox/busybox_m68k_gcc_Linux
32bfb1391a2e01c8483db5d3f368dbf22eb18d4a20040178cab16bbfd5070024  ./busybox/busybox_m68k_linux_musl_Linux
75157d9d1f8d06643095864a5efb0df8e0ea54876f0fb083d158319a0abcc8c0  ./busybox/busybox_mips64_gcc_Linux
38aed7384c5fe192b9ee878b815e06bf6d515351316e6d1763de9bb393e33d6f  ./busybox/busybox_mips64_musl_Linux
488bf2a5ac3456654b5cc45504df6fb35291fe81566d162d39210329c7c80233  ./busybox/busybox_mips64el_gcc_Linux
9e5f6cbdefe2d49c4aae6b649d3e2730c9c80544b64a1676f3b161259f4d0952  ./busybox/busybox_mips64el_musl_Linux
fc0a5356feb251469d7fd1968286f153d9d499fba755bed05de567511e9f83d9  ./busybox/busybox_mips_gcc_Linux
b5e0e563365ae93f2db908742bbec6471b34a88e07d895dd71e3a6a2b68ef791  ./busybox/busybox_mips_musl_Linux
84017c4b3d09d8470c90819e561e2ee8e3a4b096f32c1928544fb0c20ef68ea1  ./busybox/busybox_mipsel_gcc_Linux
a35e9a727b3fe340be78b0c6b217e3dfcb5a7b8d1d7c64c97667edc3b4b609e3  ./busybox/busybox_mipsel_musl_Linux
a4c2845e26e1eb42b870d052db06165eaeb8e24ae8207a12a7088eeedff4898b  ./busybox/busybox_powerpc64_gcc_Linux
4482dc6803381a6f23b07e832d9ff7d2730d7ffa0d06a5dc677290247e0d5881  ./busybox/busybox_powerpc64_musl_Linux
f1a13479ea92d37a7bb4049067b08c65c2cbf2a02de643456de3a5b2e9cac1b4  ./busybox/busybox_powerpc64le_gcc_Linux
e9cfd2bd591add8b46b59b6ecf4cd4394d0e859dfd8b338c96b76c5b8055602b  ./busybox/busybox_powerpc64le_musl_Linux
305c4953df7b72b43ae46cd20c080c5a97c50cccec63c1cec60c95760328b9b4  ./busybox/busybox_powerpc_gcc_Linux
73088f1145671381d1187789e7738aeb8c57ae70a2ccbde5b8ef9bb500bede1a  ./busybox/busybox_powerpc_musl_Linux
b4fa8ee7f0b116f2f745b605f114648af89ef07c9e8ff5a48b745bbc76d3331e  ./busybox/busybox_riscv32_gcc_Linux
fd9f70d2db50f999794e8b7a0edce0410f77736dc614dd060b0b966a4d48c6f7  ./busybox/busybox_riscv64_gcc_Linux
819b826133249b63a9d2f8102bcce7ab2be8d47a300e0be68099ea0d33fad729  ./busybox/busybox_riscv64_musl_Linux
2da5329c917f8e98f0fd24acfdcd7dcc30aa442c32e16e2ac13f522d6a752038  ./busybox/busybox_s390x_gcc_Linux
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
BusyBox v1.36.1 (2024-08-09 20:37:39 UTC) multi-call binary.
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



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
./busybox/busybox_aarch64_arm64_gcc_Linux:  ELF 64-bit LSB executable, ARM aarch64, version 1 (GNU/Linux), statically linked, BuildID[sha1]=7a0af7cd9cf98d512099d1249e7ec346bdeafb0c, for GNU/Linux 3.7.0, stripped
./busybox/busybox_aarch64_arm64_musl_Linux: ELF 64-bit LSB pie executable, ARM aarch64, version 1 (SYSV), static-pie linked, stripped
./busybox/busybox_amd_x86_64_gcc_Linux:     ELF 64-bit LSB executable, x86-64, version 1 (GNU/Linux), statically linked, BuildID[sha1]=530ab75e35a51c9e7ec7509fee0a4974e600445e, for GNU/Linux 3.2.0, stripped
./busybox/busybox_amd_x86_64_musl_Linux:    ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), static-pie linked, stripped
./busybox/busybox_arm_abi_gcc_Linux:        ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, BuildID[sha1]=709bf7cb20d4af2576f6804aea8080a0e2bd25c1, for GNU/Linux 3.2.0, stripped
./busybox/busybox_arm_abi_musl_Linux:       ELF 32-bit LSB pie executable, ARM, EABI5 version 1 (SYSV), static-pie linked, stripped
./busybox/busybox_arm_abihf_gcc_Linux:      ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), statically linked, BuildID[sha1]=879eaf907ab4e9e81b4e636554752f89796da160, for GNU/Linux 3.2.0, stripped
./busybox/busybox_arm_abihf_musl_Linux:     ELF 32-bit LSB pie executable, ARM, EABI5 version 1 (SYSV), static-pie linked, stripped
./busybox/busybox_armv7l_abihf_musl_Linux:  ELF 32-bit LSB pie executable, ARM, EABI5 version 1 (SYSV), static-pie linked, stripped
./busybox/busybox_i686_x86_gcc_Linux:       ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), statically linked, BuildID[sha1]=b246cb3a533c3e7d95d573a9461c7d86fe625611, for GNU/Linux 3.2.0, stripped
./busybox/busybox_m68k_gcc_Linux:           ELF 32-bit MSB executable, Motorola m68k, 68020, version 1 (SYSV), statically linked, BuildID[sha1]=eec40963a773aedcda93388d7c454669fb5c2cc0, for GNU/Linux 3.2.0, stripped
./busybox/busybox_m68k_linux_musl_Linux:    ELF 32-bit MSB pie executable, Motorola m68k, 68020, version 1 (SYSV), static-pie linked, stripped
./busybox/busybox_mips64_gcc_Linux:         ELF 64-bit MSB executable, MIPS, MIPS64 rel2 version 1 (SYSV), statically linked, BuildID[sha1]=b70a0e8a89469116be3b6dd9f4cf8c41ec6ca8d3, for GNU/Linux 3.2.0, stripped
./busybox/busybox_mips64_musl_Linux:        ELF 64-bit MSB pie executable, MIPS, MIPS-III version 1 (SYSV), static-pie linked, stripped
./busybox/busybox_mips64el_gcc_Linux:       ELF 64-bit LSB executable, MIPS, MIPS64 rel2 version 1 (SYSV), statically linked, BuildID[sha1]=477f14db030700a6da42bd7c5a6d36bf00fec4dc, for GNU/Linux 3.2.0, stripped
./busybox/busybox_mips64el_musl_Linux:      ELF 64-bit LSB pie executable, MIPS, MIPS-III version 1 (SYSV), static-pie linked, stripped
./busybox/busybox_mips_gcc_Linux:           ELF 32-bit MSB executable, MIPS, MIPS32 rel2 version 1 (SYSV), statically linked, BuildID[sha1]=237dea9d33e43e605eacafc7207cffbc1622612f, for GNU/Linux 3.2.0, stripped
./busybox/busybox_mips_musl_Linux:          ELF 32-bit MSB pie executable, MIPS, MIPS-I version 1 (SYSV), static-pie linked, stripped
./busybox/busybox_mipsel_gcc_Linux:         ELF 32-bit LSB executable, MIPS, MIPS32 rel2 version 1 (SYSV), statically linked, BuildID[sha1]=ba320a1824b3c826fa4cd01b03f7d71f65c27581, for GNU/Linux 3.2.0, stripped
./busybox/busybox_mipsel_musl_Linux:        ELF 32-bit LSB pie executable, MIPS, MIPS-I version 1 (SYSV), static-pie linked, stripped
./busybox/busybox_powerpc64_gcc_Linux:      ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (GNU/Linux), statically linked, BuildID[sha1]=3fadc1b5f0fc32ad4a1fef85313d8e21f61e3c24, for GNU/Linux 3.2.0, stripped
./busybox/busybox_powerpc64_musl_Linux:     ELF 64-bit MSB pie executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), static-pie linked, stripped
./busybox/busybox_powerpc64le_gcc_Linux:    ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (GNU/Linux), statically linked, BuildID[sha1]=a759ef1975140e6d0fd3be93882b29d3fee62d50, for GNU/Linux 3.10.0, stripped
./busybox/busybox_powerpc64le_musl_Linux:   ELF 64-bit LSB pie executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), static-pie linked, stripped
./busybox/busybox_powerpc_gcc_Linux:        ELF 32-bit MSB executable, PowerPC or cisco 4500, version 1 (SYSV), statically linked, BuildID[sha1]=6f1140db80a022e803dac30ab4a1b7d99a2a57d7, for GNU/Linux 3.2.0, stripped
./busybox/busybox_powerpc_musl_Linux:       ELF 32-bit MSB pie executable, PowerPC or cisco 4500, version 1 (SYSV), static-pie linked, stripped
./busybox/busybox_riscv32_gcc_Linux:        ELF 32-bit LSB executable, UCB RISC-V, RVC, double-float ABI, version 1 (SYSV), statically linked, for GNU/Linux 5.4.0, stripped
./busybox/busybox_riscv64_gcc_Linux:        ELF 64-bit LSB executable, UCB RISC-V, RVC, double-float ABI, version 1 (SYSV), statically linked, BuildID[sha1]=aa48fa1daa408cd7014c75f2ec2bc5290444245e, for GNU/Linux 4.15.0, stripped
./busybox/busybox_riscv64_musl_Linux:       ELF 64-bit LSB pie executable, UCB RISC-V, RVC, double-float ABI, version 1 (SYSV), static-pie linked, stripped
./busybox/busybox_s390x_gcc_Linux:          ELF 64-bit MSB executable, IBM S/390, version 1 (GNU/Linux), statically linked, BuildID[sha1]=c059bdce3eda499f885dbe91280b17b690ca90d2, for GNU/Linux 3.2.0, stripped
./busybox/busybox_s390x_musl_Linux:         ELF 64-bit MSB pie executable, IBM S/390, version 1 (SYSV), static-pie linked, stripped

--> SHA256SUM
65f6fcdfe6628d9b7cc3038c181625d994a60c7f71565eb173df60219d6fd21e  ./busybox/busybox_aarch64_arm64_gcc_Linux
89e8e12b6933d966fab05b3935223f085b4de055e35f775aacc4b795e0445865  ./busybox/busybox_aarch64_arm64_musl_Linux
7d39996a4cd7dcd2fb87b75a5944a70ee73c3211aeb54479e1b8131e76fc9a4d  ./busybox/busybox_amd_x86_64_gcc_Linux
72b59cfbcbce34f7480354c9209c8e852b34d0c8863cb9ea290e1a23a80153d4  ./busybox/busybox_amd_x86_64_musl_Linux
6e70731faa402fb124c1b823a81171d63675dcad2a1fea3de2de5d9dc11a3ec3  ./busybox/busybox_arm_abi_gcc_Linux
4605a149bc47d0ac99851471abe7045bd19f50d66f1b0c2c6680ccd1d4494538  ./busybox/busybox_arm_abi_musl_Linux
78f1dc39801c596ad3bcc215fa3f8a700dba07aea356e21ac45a43f795b3d1f6  ./busybox/busybox_arm_abihf_gcc_Linux
86c56b8aacd8a6927745882e20655fb9696606021d017b9941727af5055da0b3  ./busybox/busybox_arm_abihf_musl_Linux
e8fd62962d6612161320713623a238d333710f9d9ee35f7964abf9a791f0379d  ./busybox/busybox_armv7l_abihf_musl_Linux
34c83b7e28cc0b1dcaef4eb1a3c429abe3b9db464ef3116bad7c9ea74c4b96fd  ./busybox/busybox_i686_x86_gcc_Linux
daeab3904dad92b8c657ecde3800881927499c6050621e946595306e7a76d831  ./busybox/busybox_m68k_gcc_Linux
32bfb1391a2e01c8483db5d3f368dbf22eb18d4a20040178cab16bbfd5070024  ./busybox/busybox_m68k_linux_musl_Linux
0f6621c9e6fe966620df3531da863db4d31586f32ff4dcc0aa12a586b957d60b  ./busybox/busybox_mips64_gcc_Linux
38aed7384c5fe192b9ee878b815e06bf6d515351316e6d1763de9bb393e33d6f  ./busybox/busybox_mips64_musl_Linux
29330b45bff6c17c008f81eebcd8ea0dd1065af546a79b721c402e646d0339ca  ./busybox/busybox_mips64el_gcc_Linux
9e5f6cbdefe2d49c4aae6b649d3e2730c9c80544b64a1676f3b161259f4d0952  ./busybox/busybox_mips64el_musl_Linux
0f54df642b483e29f0ac816ae88804e7c12e5d7e5392d124d61bec365748eb0d  ./busybox/busybox_mips_gcc_Linux
b5e0e563365ae93f2db908742bbec6471b34a88e07d895dd71e3a6a2b68ef791  ./busybox/busybox_mips_musl_Linux
248e6891a6a1e00fec6c2f7d6a7d7c8c2864c2a5973f40e28e99fe177a10794c  ./busybox/busybox_mipsel_gcc_Linux
a35e9a727b3fe340be78b0c6b217e3dfcb5a7b8d1d7c64c97667edc3b4b609e3  ./busybox/busybox_mipsel_musl_Linux
b589b18b27b684552bfa4cf21077db6a577ad93b4bc86596464bb15daeb4a0cc  ./busybox/busybox_powerpc64_gcc_Linux
4482dc6803381a6f23b07e832d9ff7d2730d7ffa0d06a5dc677290247e0d5881  ./busybox/busybox_powerpc64_musl_Linux
925b69526e8b5720b2440453116c39dd4a7dcef32d34f5d2ea3e2bed44a31289  ./busybox/busybox_powerpc64le_gcc_Linux
e9cfd2bd591add8b46b59b6ecf4cd4394d0e859dfd8b338c96b76c5b8055602b  ./busybox/busybox_powerpc64le_musl_Linux
d6b0302dd87266599fc12752c90aed6d4da025c395f21024220072608ac46e35  ./busybox/busybox_powerpc_gcc_Linux
73088f1145671381d1187789e7738aeb8c57ae70a2ccbde5b8ef9bb500bede1a  ./busybox/busybox_powerpc_musl_Linux
b2e8cb4c69b17f91a8527e10949802ee8f83c512301114a19c027e69f7210c86  ./busybox/busybox_riscv32_gcc_Linux
528d2201a2dc9fd3bb5644560028bf8acc12974026870d8fc9682a07cd8a328f  ./busybox/busybox_riscv64_gcc_Linux
819b826133249b63a9d2f8102bcce7ab2be8d47a300e0be68099ea0d33fad729  ./busybox/busybox_riscv64_musl_Linux
64c786988e44cfb25f1efe0383a7a8f4a120e95154f26dff62ecdc0ef7591cb1  ./busybox/busybox_s390x_gcc_Linux
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
BusyBox v1.36.1 (2024-07-03 20:36:54 UTC) multi-call binary.
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


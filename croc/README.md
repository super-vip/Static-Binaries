
---
- #### Download [croc](https://github.com/schollz/croc#install)
> - **Sources**
> > ```bash
> > --> Android:
> >      - Built using dockercross (Dynamic Only)
> >      - Currently this fails with: loadinternal: cannot find runtime/cgo
> >
> > --> DragonFlyBSD:
> >      - https://github.com/schollz/croc/releases
> > 
> > --> FreeBSD:
> >      - https://github.com/schollz/croc/releases
> > 
> > --> Linux:
> >      - https://github.com/schollz/croc/releases
> >      - Binaries for '386' | 'loong64' | 'mips' | 'mipsle' | 'mips64' | 'mips64le' |'ppc64' | 'ppc64le' | 'riscv64' | 's390x' are crosscompiled
> > 
> > --> NetBSD:
> >      - https://github.com/schollz/croc/releases
> > 
> > --> macOS:
> >      - https://github.com/schollz/croc/releases
> > 
> > --> OpenBSD:
> >      - https://github.com/schollz/croc/releases
> > 
> > --> Windows:
> >      - https://github.com/schollz/croc/releases
> > ```
> > 
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

!# DragonFlyBSD
--> Amd x86_64 || x86_64 [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/croc/croc_amd_x86_64_DragonFlyBSD"

!# FreeBSD
--> aarch64 || arm64 [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/croc/croc_aarch64_arm64_FreeBSD"
--> Amd x86|| x86 [32-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/croc/croc_amd_x86_FreeBSD"
--> Amd x86_64 || x86_64 [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/croc/croc_amd_x86_64_FreeBSD"

!# Linux
--> aarch64 || arm64 [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/croc/croc_aarch64_arm64_Linux"
--> Amd x86 || x86 [32-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/croc/croc_amd_x86_Linux"
--> Amd x86_64 || x86_64 [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/croc/croc_amd_x86_64_Linux"
--> ARM_abi|| ARMv4 || ARMv5 || ARMv7 (?) [32-bit]
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/croc/croc_arm_abi_Linux"
--> i386 || Intel 80386 [32-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/croc/croc_i386_Linux"
--> MIPS (Big-Endian) [32-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/croc/croc_mips_Linux"
--> MIPSel || MIPSle (Little-Endian) [32-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/croc/croc_mipsle_Linux"
--> MIPS64 (Big-Endian) [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/croc/croc_mips64_Linux"
--> MIPS64le (Little-Endian) [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/croc/croc_mips64le_Linux"
--> powerpc64|| ppc64 || cisco 7500 [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/croc/croc_powerpc64_ppc64_Linux"
--> powerpc64le || ppc64le || cisco 7500 || OpenPOWER ELF V2 ABI (Little-Endian) [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/croc/croc_powerpc64le_ppc64le_Linux"
--> risc64 || CB RISC-V || RVC [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/croc/croc_riscv64_Linux"
--> s390x || IBM S/390 [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/croc/croc_s390x_Linux"

!# macOS
--> aarch64 || arm64
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/croc/croc_aarch64_arm64_macOS"
--> Amd x86_64 || x86_64
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/croc/croc_x86_64_macOS"

!# NetBSD
--> Amd x86 || x86 [32-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/croc/croc_amd_x86_NetBSD"
--> Amd x86_64 || x86_64 [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/croc/croc_amd_x86_64_NetBSD"
--> ARM_abi|| ARMv4 || ARMv5 || ARMv7 (?) [32-bit]
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/croc/croc_arm_abi_NetBSD"

!# OpenBSD
--> aarch64 || arm64 [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/croc/croc_aarch64_arm64_OpenBSD"
--> Amd x86 || x86 [32-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/croc/croc_amd_x86_OpenBSD"
--> Amd x86_64 || x86_64 [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/croc/croc_amd_x86_64_OpenBSD"
--> ARM_abi|| ARMv4 || ARMv5 || ARMv7 (?) [32-bit]
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/croc/croc_arm_abi_OpenBSD"

#Windows
--> aarch64 || arm64 [64-bit]
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/croc/croc_aarch64_arm64_Windows.exe"
--> Amd_x86 || x86 [32-bit]
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/croc/croc_amd_x86_Windows.exe"
--> Amd x86_64 || x86_64 [64-bit]
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/croc/croc_amd_x86_64_Windows.exe"
--> ARM_abi|| ARMv4 || ARMv5 || ARMv7 (?) 
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/croc/croc_arm_Windows.exe"

```
---
- #### Install croc
```bash
!# Recommended way to install croc is:
 curl https://getcroc.schollz.com | bash
!# Compile Dynamically using go
  go install github.com/schollz/croc/v9@latest

!# Copy downloaded croc binaries to /usr/bin || /usr/local/bin
!# For $HOME/bin
 mkdir -p "$HOME/bin" && export PATH="$HOME/bin:$PATH"

!# Move Downloaded croc binaries to that DIR
 mv "$Path_To_croc_Binary" "/usr/bin/croc"

!# Give Writeable Perms
 chmod +xwr /usr/bin/croc*
```

---
```console

--> METADATA
./croc/croc_386_Linux:                 ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, stripped
./croc/croc_aarch64_arm64_FreeBSD:     ELF 64-bit LSB executable, ARM aarch64, version 1 (FreeBSD), statically linked, Go BuildID=KX168B8m7YSW7rPW6zmO/j5FngEH3tPVDCQp5TOHx/0LsQ8lW2k6cffr8T6-Mx/VMkYw5Lo9CZVi7gFgfIq, BuildID[sha1]=2c92c760ed95dce2b8b53b2b026946965b75f130, for FreeBSD 12.3, FreeBSD-style, with debug_info, not stripped
./croc/croc_aarch64_arm64_Linux:       ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=L733uzJWHDDxwG8b5bD2/XWoxnM6xwAOcGpKLzojg/svMAKY2FwEG2FHoUINmv/-NyYy8fXGXFEZiOuT0_b, BuildID[sha1]=70dfbdf50a03e5084180338da6ca3066769e99d8, with debug_info, not stripped
./croc/croc_aarch64_arm64_OpenBSD:     ELF 64-bit LSB executable, ARM aarch64, version 1 (OpenBSD), dynamically linked, interpreter /usr/libexec/ld.so, Go BuildID=csdh040RIybe798K7yqb/MxUEFFy2dvilP91pV5kA/P3Q3plyImcc00YoWRwX_/BKAPIvlHdQAF6YmhFXue, BuildID[sha1]=6b091e2a83f9f19b635b25591cb0bbd3c6580480, for OpenBSD, with debug_info, not stripped
./croc/croc_aarch64_arm64_Windows.exe: PE32+ executable (console) Aarch64, for MS Windows, 14 sections
./croc/croc_aarch64_arm64_macOS:       Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./croc/croc_amd_x86_64_DragonFlyBSD:   ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=3Z4dSaUbiQTnhQ8WbqT0/dLSOziIcguqWaKiyMPY1/0XNNDFJ49gFHjrlxvP3r/ropnH_dcTHfXwPEtiuUF, BuildID[sha1]=1131ba474f7f02662ac64147657bb8cfc1ef1f8d, stripped
./croc/croc_amd_x86_64_FreeBSD:        ELF 64-bit LSB executable, x86-64, version 1 (FreeBSD), statically linked, Go BuildID=t3mEOXp9akfHT4j3Zc3t/MM79fA19QIbStg8btqS1/50mwWwwlga6d7vyTmTfK/sqHMs54Ll9nA7HUS13DJ, BuildID[sha1]=e3d062c8de264417b30a84e7a39e13616130ad97, for FreeBSD 12.3, FreeBSD-style, stripped
./croc/croc_amd_x86_64_Linux:          ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=ijzQDIoRO9fjThpybGZQ/iOQ_MV9N9WSrkp6F6G1X/yX45TUSPBrQv0YHeEu8N/20pFAG3mCmjAFZ5FuFC-, BuildID[sha1]=2bc218ad1a042ccf05a22131311e6e3e77c077e9, stripped
./croc/croc_amd_x86_64_NetBSD:         ELF 64-bit LSB executable, x86-64, version 1 (NetBSD), statically linked, Go BuildID=x61Gzh0uvxizGYrHrbHl/0oTWD2KlUB7kUHKdEhPV/CV-SDZVWeBH4-Cdn0nGL/KXw6uVQU30G-0os72iAR, BuildID[sha1]=e37858c268d05e46cad045e9ad75bda77c8a52b6, for NetBSD 7.0, stripped
./croc/croc_amd_x86_64_OpenBSD:        ELF 64-bit LSB executable, x86-64, version 1 (OpenBSD), dynamically linked, interpreter /usr/libexec/ld.so, Go BuildID=rzG55yHOuhwrBkptuu9n/YO5NmIEEgq7UoTbIIkt1/pd3rKBhtLaHu0zUWdT1O/IP35CDSjtY-KQ1xSZicN, BuildID[sha1]=a22035c182cff74f299e6716d92e84fcf5f34035, for OpenBSD, stripped
./croc/croc_amd_x86_64_Windows.exe:    PE32+ executable (console) x86-64 (stripped to external PDB), for MS Windows, 8 sections
./croc/croc_amd_x86_FreeBSD:           ELF 32-bit LSB executable, Intel 80386, version 1 (FreeBSD), statically linked, for FreeBSD 12.3, FreeBSD-style, Go BuildID=pzNrEUJBJW2rS8WbBo1i/efB3Y9OPU_FNUsEveobp/eHFP7W8to9BzwgUQ0dYW/9Bo7qlkEzoieE5kfcHL3, stripped
./croc/croc_amd_x86_Linux:             ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=zHs5n-Zq4zYR6KYb0BBk/dIcWrjOnTX-JinVEf1XH/R2IkN4CavhgpobBWZOI3/XUZ3kY986EQA5uLPKywE, BuildID[sha1]=1af3f33434f35e6b43aa8af48effd27b80f78b09, stripped
./croc/croc_amd_x86_NetBSD:            ELF 32-bit LSB executable, Intel 80386, version 1 (NetBSD), statically linked, Go BuildID=7SKuaWgh_iGUiEJT_WzA/6f8kwheEf2mDi91fKB6Q/fTGWDaWy04GPh0rEjpPb/lQOtnuMQ_c-Q7XfoCCwu, BuildID[sha1]=5d8a3afc302a5ac4f5735e83ccd05df4cd260fea, for NetBSD 7.0, stripped
./croc/croc_amd_x86_OpenBSD:           ELF 32-bit LSB executable, Intel 80386, version 1 (OpenBSD), dynamically linked, interpreter /usr/libexec/ld.so, for OpenBSD, Go BuildID=QJxeN-dGsKofnMKOHiqI/-nycADcw5xsi0Hxak8HL/DuUbViwnVIXgJHYxTg-F/NnSTXqNJaWdfOy8QkASY, stripped
./croc/croc_amd_x86_Windows.exe:       PE32 executable (console) Intel 80386 (stripped to external PDB), for MS Windows, 6 sections
./croc/croc_arm_Windows.exe:           PE32 executable (console) ARMv7 Thumb, for MS Windows, 14 sections
./croc/croc_arm_abi_NetBSD:            ELF 32-bit LSB executable, ARM, EABI5 version 1 (NetBSD), statically linked, for NetBSD 7.0, Go BuildID=8uSMKwcUg1iN7BfQ7wYN/hwB71Wn3g4HL1_ZEyTkC/u3lfuo7obGubolbbz-Zc/SWAXosYtZD8AfdJ-u9b_, stripped
./croc/croc_arm_abi_OpenBSD:           ELF 32-bit LSB executable, ARM, version 1 (OpenBSD), dynamically linked, interpreter /usr/libexec/ld.so, for OpenBSD, Go BuildID=KEk2TdQLPEAlnn114S38/p1hVwSb4OB8mvl4t8V8s/I7pHswwhjFgaHMUbyvpF/sfMTszszjzGjmte8nIul, stripped
./croc/croc_loong64_Linux:             ELF 64-bit LSB executable, LoongArch, version 1 (SYSV), statically linked, stripped
./croc/croc_mips64_Linux:              ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, stripped
./croc/croc_mips64le_Linux:            ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, stripped
./croc/croc_mips_Linux:                ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, stripped
./croc/croc_mipsle_Linux:              ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, stripped
./croc/croc_powerpc64_ppc64_Linux:     ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./croc/croc_powerpc64le_ppc64le_Linux: ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./croc/croc_riscv64_Linux:             ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, stripped
./croc/croc_s390x_Linux:               ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped
./croc/croc_x86_64_macOS:              Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>

--> SHA256SUM
504e76e5e841da8624328375f94ea656bd9f56898e11b7550e5ed0d5c2a09617  ./croc/croc_386_Linux
8d7595b496092307e0964732b5ec233121b1284cf191547281295fb285c91fab  ./croc/croc_aarch64_arm64_FreeBSD
1f9451b8621dcbf5b06705c0a08d9ad77ac9d094abd3611abd7551145c6ea782  ./croc/croc_aarch64_arm64_Linux
6f2795b6091a88256deab55f2a345f0605f7d699eb315c70980fd7b82b5ed818  ./croc/croc_aarch64_arm64_OpenBSD
43360abfabf7473e863765a6a2e28c76d5e96b6e790c0cd62fbe3d9a51b1ec26  ./croc/croc_aarch64_arm64_Windows.exe
74f5ac184e6200bf66bd14779672ee70b6c2da3a5d8a171f1caef2eef92d12aa  ./croc/croc_aarch64_arm64_macOS
8c5d544ec7c046b1babec736c3eb1cd7de6181336c8d3fb2c009a3d7f8ebe860  ./croc/croc_amd_x86_64_DragonFlyBSD
e397b73a2ca8a82f9128b787633611a47b00cd16627836d81fb28c6f0f5760c3  ./croc/croc_amd_x86_64_FreeBSD
f01b0b23a3a392624a910f81ecc2ab499755ebd95277f0704540daf010412d6d  ./croc/croc_amd_x86_64_Linux
b237a93b7a8164013679990fe936c8f2ab461b714a6935c7f4cc7e62f93bf595  ./croc/croc_amd_x86_64_NetBSD
3790148d78494af1ef51f5b1bdee0791d89be8b26be7977bffe20f3f649bbbae  ./croc/croc_amd_x86_64_OpenBSD
d2f2ef08a7e704750a6eebb410a7db734301c3d0ab7886ef7a16d944bb74132c  ./croc/croc_amd_x86_64_Windows.exe
7ff1b6c223ed59e440118debc349e65254d507e82865377f3e2904184258b08e  ./croc/croc_amd_x86_FreeBSD
08b42116a6ab9e522674ead87afcc01d61f749e9e4ce356f1a956e0e06bb3d44  ./croc/croc_amd_x86_Linux
811aeceddea409185d171e5ea66bd42a6e57bcc8c6b4a9a4e9f40b4209b2773a  ./croc/croc_amd_x86_NetBSD
9964c8ee5e7abcce36d282ccadeae66e1f2244bcff4befdb2b2bf9f974da957d  ./croc/croc_amd_x86_OpenBSD
4c195aa49bf02d53580e1870c264ba9f4c649924c8adf4ae949c139f00e8b317  ./croc/croc_amd_x86_Windows.exe
ed657a7f38152378e377ac7b7df5720e550362cf5d411203aab105e3ad389e5f  ./croc/croc_arm_Windows.exe
2419b6a55fc015b0548bc9ce29c849bb9baf346889d459f463ac0dbe8575a48f  ./croc/croc_arm_abi_NetBSD
b6f4ae2184afec08f332e4bae80293eac0f9004b25e0bac46639e66a713b3cb2  ./croc/croc_arm_abi_OpenBSD
2cef65c2b0b890973ca182948ca81b9aec3498b0e503094f88cdf4937f98a98d  ./croc/croc_loong64_Linux
23e002ffd40b4b9e9156523d88f848eb6605d88ac160ccce211feb50e7098662  ./croc/croc_mips64_Linux
4924bc6ce774e681ca3f2cba0c24fb293591f39b3babc29e4d70260d69876adc  ./croc/croc_mips64le_Linux
d8b64070740d106ba16adff5a58618f206627cde2a9875f29fdc5c570842cc1d  ./croc/croc_mips_Linux
d2774f86ee1ea01e01a43cdd4e31649d8c03ccf211497f1aa852dae89f8e7933  ./croc/croc_mipsle_Linux
7ef86010f894ee17abf60aaa273d8c691118bda775dca7dedb85662375f5b83e  ./croc/croc_powerpc64_ppc64_Linux
3efae3d640c010242c01c5521ec5e1edee69be6c5525496912068103badd6166  ./croc/croc_powerpc64le_ppc64le_Linux
775d8eae8244d65f0826e1a8a307d10b4aea6be6667ded57d6ea2d14006a3948  ./croc/croc_riscv64_Linux
97a881bd3f2e60384756160ae479eb1609be03322aa520e2ad197c775f7be94b  ./croc/croc_s390x_Linux
344500336c1e046f6e97e8b117521888a45f05a04729a8a9938e33998611ae7d  ./croc/croc_x86_64_macOS
```


---

- #### Sizes

```console
16M   ./croc/croc_386_Linux
20M   ./croc/croc_aarch64_arm64_FreeBSD
20M   ./croc/croc_aarch64_arm64_Linux
20M   ./croc/croc_aarch64_arm64_OpenBSD
20M   ./croc/croc_aarch64_arm64_Windows.exe
16M   ./croc/croc_aarch64_arm64_macOS
16M   ./croc/croc_amd_x86_64_DragonFlyBSD
16M   ./croc/croc_amd_x86_64_FreeBSD
17M   ./croc/croc_amd_x86_64_Linux
16M   ./croc/croc_amd_x86_64_NetBSD
16M   ./croc/croc_amd_x86_64_OpenBSD
18M   ./croc/croc_amd_x86_64_Windows.exe
7.1M  ./croc/croc_amd_x86_FreeBSD
16M   ./croc/croc_amd_x86_Linux
16M   ./croc/croc_amd_x86_NetBSD
7.1M  ./croc/croc_amd_x86_OpenBSD
17M   ./croc/croc_amd_x86_Windows.exe
15M   ./croc/croc_arm_Windows.exe
7.2M  ./croc/croc_arm_abi_NetBSD
7.2M  ./croc/croc_arm_abi_OpenBSD
16M   ./croc/croc_loong64_Linux
17M   ./croc/croc_mips64_Linux
17M   ./croc/croc_mips64le_Linux
17M   ./croc/croc_mips_Linux
17M   ./croc/croc_mipsle_Linux
16M   ./croc/croc_powerpc64_ppc64_Linux
16M   ./croc/croc_powerpc64le_ppc64le_Linux
16M   ./croc/croc_riscv64_Linux
17M   ./croc/croc_s390x_Linux
17M   ./croc/croc_x86_64_macOS
```

---

- #### Version
```console

$ ./croc/croc_amd_x86_64_Linux --version
croc version 10.6.0

$ ./croc/croc_amd_x86_64_Linux -h
NAME:
   croc - easily and securely transfer stuff from one computer to another

USAGE:
   croc [GLOBAL OPTIONS] [COMMAND] [COMMAND OPTIONS] [filename(s) or folder]

   USAGE EXAMPLES:
   Send a file:
      croc send file.txt

      -git to respect your .gitignore
   Send multiple files:
      croc send file1.txt file2.txt file3.txt
    or
      croc send *.jpg

   Send everything in a folder:
      croc send example-folder-name

   Send a file with a custom code:
      croc send --code secret-code file.txt

   Receive a file using code:
      croc secret-code

VERSION:
   10.6.0

COMMANDS:
   send     send file(s), or folder (see options with croc send -h)
   relay    start your own relay (optional)
   serve    serve the embedded web client and browser relay
   help, h  Shows a list of commands or help for one command

GLOBAL OPTIONS:
   --internal-dns          use a built-in DNS stub resolver rather than the host operating system (default: false)
   --classic               toggle between the classic mode (insecure due to local attack vector) and new mode (secure) (default: false)
   --remember              save these settings to reuse next time (default: false)
   --debug                 toggle debug mode (default: false)
   --yes                   automatically agree to all prompts (default: false)
   --stdout                redirect file to stdout (default: false)
   --no-compress           disable compression (default: false)
   --ask                   make sure sender and recipient are prompted (default: false)
   --local                 force to use only local connections (default: false)
   --ignore-stdin          ignore piped stdin (default: false)
   --overwrite             do not prompt to overwrite or resume (default: false)
   --rename                receive files that already exist under a new name instead of prompting (default: false)
   --testing               flag for testing purposes (default: false)
   --quiet                 disable all output (default: false)
   --disable-clipboard     disable copy to clipboard (default: false)
   --extended-clipboard    copy full command with secret as env variable to clipboard (default: false)
   --multicast value       multicast address to use for local discovery (default: "239.255.255.250")
   --curve value           choose an encryption curve (p521, p256, p384, siec, ed25519) (default: "p256")
   --ip value              set sender ip if known e.g. 10.0.0.1:9009, [::1]:9009
   --relay value           address of the relay (default: "62.238.29.226:9009") [$CROC_RELAY]
   --relay6 value          ipv6 address of the relay (default: "[2a01:4f9:c013:7b04::1]:9009") [$CROC_RELAY6]
   --out value             specify an output folder to receive the file (default: ".")
   --pass value            password for the relay (default: "pass123") [$CROC_PASS]
   --socks5 value          add a socks5 proxy [$SOCKS5_PROXY]
   --connect value         add a http proxy [$HTTP_PROXY]
   --throttleUpload value  throttle the upload speed e.g. 500k
   --help, -h              show help (default: false)
   --version, -v           print the version (default: false)


```

---


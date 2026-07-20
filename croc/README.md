
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
./croc/croc_aarch64_arm64_FreeBSD:     ELF 64-bit LSB executable, ARM aarch64, version 1 (FreeBSD), statically linked, Go BuildID=V3KpZ-374zwOA_bldaSD/me-NAXtGApWb8-bCxsps/ArdFdP1967yq6lXhi8U2/kZi-AWUlf7Vtawpu1t03, BuildID[sha1]=6bac0731e0720ed4d8abdcf2e1462c39678ade3c, for FreeBSD 12.3, FreeBSD-style, with debug_info, not stripped
./croc/croc_aarch64_arm64_Linux:       ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=fv8cjDXwSJ4dgpmTAyAl/Jd3ASLY0ROK9gpF_XHx8/a3Rvz4Y5Cgx6LgjbgHRu/G1gmBjFIZ73Z9JBEQsL2, BuildID[sha1]=5355f40286487c29af0ccffadb6e1b431d9ccb9e, with debug_info, not stripped
./croc/croc_aarch64_arm64_OpenBSD:     ELF 64-bit LSB executable, ARM aarch64, version 1 (OpenBSD), dynamically linked, interpreter /usr/libexec/ld.so, Go BuildID=MF7xi2oxJYPNxZH2xHpl/hPBvIphOPRg6ncamk-qa/flkdfjpkZ3oy9fFEMuJJ/b2LVQkedox7kibqWN6mT, BuildID[sha1]=6e9f67c67943c30c32f7d6b39252c1ad4cd5f368, for OpenBSD, with debug_info, not stripped
./croc/croc_aarch64_arm64_Windows.exe: PE32+ executable (console) Aarch64, for MS Windows, 14 sections
./croc/croc_aarch64_arm64_macOS:       Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./croc/croc_amd_x86_64_DragonFlyBSD:   ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=CQGPKL9O2TevzZsBCmrQ/dp7jClC1VH4RwUA_OZdG/jYTXh0DFwZES86-4w2yZ/GIKSXaKed5Y2DBRe6FYa, BuildID[sha1]=3718ebd40027ad5e6ccd6e69bf74756022f2db8d, stripped
./croc/croc_amd_x86_64_FreeBSD:        ELF 64-bit LSB executable, x86-64, version 1 (FreeBSD), statically linked, Go BuildID=iQ1ZzCGCjoMa1AeMZdBN/ZpKYi_vVGPxr0uazRnLo/dGloFySVQAgzQbtm80nE/YzOM_SPjhSXBx1Im40lJ, BuildID[sha1]=ddb3e7de1b770dab61ee041f58bdf431253a52d6, for FreeBSD 12.3, FreeBSD-style, stripped
./croc/croc_amd_x86_64_Linux:          ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=Qxv1N7iZpQDwdqd1d3kv/vX9CyN4iye4gYi7z-1--/WNBcgfkMF6hXW6At5hvV/kNsaD6ERmBSTFscm_jHx, BuildID[sha1]=15af16900bb1ee5e093408eaca78d2a232c4539b, stripped
./croc/croc_amd_x86_64_NetBSD:         ELF 64-bit LSB executable, x86-64, version 1 (NetBSD), statically linked, Go BuildID=vjSfx_r985WYoIjuu0uL/7ult5ZuKE8lGLKyfiDGI/Z0RUxTG4L-WjlxvDs_nR/AYMzVbA3_kNEoHhlmslU, BuildID[sha1]=5ad402606090780ea1e6e0e9eb893faa6b2471d1, for NetBSD 7.0, stripped
./croc/croc_amd_x86_64_OpenBSD:        ELF 64-bit LSB executable, x86-64, version 1 (OpenBSD), dynamically linked, interpreter /usr/libexec/ld.so, Go BuildID=AzDaB9s6_FCpH2jkHgVI/rEzel6FvpZ7k1B3VgZw6/GPXPo__tFU1WtPLe96X6/u1qeST3ZrscCTMFw-HwB, BuildID[sha1]=11701ba9e48399eca62fdab10db1815fa5453d1e, for OpenBSD, stripped
./croc/croc_amd_x86_64_Windows.exe:    PE32+ executable (console) x86-64 (stripped to external PDB), for MS Windows, 8 sections
./croc/croc_amd_x86_FreeBSD:           ELF 32-bit LSB executable, Intel 80386, version 1 (FreeBSD), statically linked, for FreeBSD 12.3, FreeBSD-style, Go BuildID=pzNrEUJBJW2rS8WbBo1i/efB3Y9OPU_FNUsEveobp/eHFP7W8to9BzwgUQ0dYW/9Bo7qlkEzoieE5kfcHL3, stripped
./croc/croc_amd_x86_Linux:             ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=dS8UTvr2g5Wju4rUXax-/yUREnQVGNt-neJ8VBmht/LRyEItl86Wrv598iSTbg/EhEOz5CNskecRp_3I0Sa, BuildID[sha1]=90fc22420f0fa2e473f46eb6ae66f278d764578e, stripped
./croc/croc_amd_x86_NetBSD:            ELF 32-bit LSB executable, Intel 80386, version 1 (NetBSD), statically linked, Go BuildID=AuT9C_25B6Aq7j3GSncc/ou-K_luUI-2n4JB2-695/Z29KGNabMDlUG8Jd5Wbe/fsXz_7PFEmN43qTTAHnA, BuildID[sha1]=7928b0d9faf35132b2663d921dfac184370ee621, for NetBSD 7.0, stripped
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
dd495a2380d76f421a5cce8f79cab059f5c22d204e84e81cf0288e0a321ec598  ./croc/croc_386_Linux
2b0255907d49b08caff63dcf936f9fea3b7a4745fea6d4c65b8848dea7c4879a  ./croc/croc_aarch64_arm64_FreeBSD
294856e999af610b2125675eb29f768a847afdebdf9604fe8f26d49f6efb1595  ./croc/croc_aarch64_arm64_Linux
e4cb1f35869c47b13a5815d6168fdee767865065dd6a854a55df3c6d739d1b77  ./croc/croc_aarch64_arm64_OpenBSD
ea1bafbffb1a8423b5572084a447b2fef0e214ee7786430b7abcf71e5958e50e  ./croc/croc_aarch64_arm64_Windows.exe
579e24dda40c88fb3c12acfdfb21726c796df18129dd784184d7c3b1005906cb  ./croc/croc_aarch64_arm64_macOS
0db1bad959865f29ffc17ef2b2bf7a9a8026deaf988a0b46e276e97e783df198  ./croc/croc_amd_x86_64_DragonFlyBSD
cdf318d61cdd92c77739ed1205acb21755ed7241f9e68539115a46b369c96eb6  ./croc/croc_amd_x86_64_FreeBSD
863fa74c6dd6e51bd07607f70db2b87ddac0a5de98d019ead8f84b0c7c1ff83b  ./croc/croc_amd_x86_64_Linux
ba440d15372ba9ffc4fc80103250d040edcd9f9414edd296567fa904cd31d2c3  ./croc/croc_amd_x86_64_NetBSD
e0bd63334e3fd3710852ea9feba349ce4ff76261ef4b2a148a2322027cc2d9c6  ./croc/croc_amd_x86_64_OpenBSD
6c48aae366b70c76bba9d060da3ab7060597f5bb6bb10b7b01960b59bc3ee495  ./croc/croc_amd_x86_64_Windows.exe
7ff1b6c223ed59e440118debc349e65254d507e82865377f3e2904184258b08e  ./croc/croc_amd_x86_FreeBSD
d980c33f2cfcdb6f835c3404f9e2f6b9757cad1c03a1a1376d7a4fe6e2f67d75  ./croc/croc_amd_x86_Linux
b404b8ff6706ebd2cbff0f5532ccd840dade24905c585aa64f81f536b981a581  ./croc/croc_amd_x86_NetBSD
9964c8ee5e7abcce36d282ccadeae66e1f2244bcff4befdb2b2bf9f974da957d  ./croc/croc_amd_x86_OpenBSD
6a6fcbc172bd6004dcbce1f801fae60dc8332ec2a00f88d06885896491d9a56e  ./croc/croc_amd_x86_Windows.exe
ed657a7f38152378e377ac7b7df5720e550362cf5d411203aab105e3ad389e5f  ./croc/croc_arm_Windows.exe
2419b6a55fc015b0548bc9ce29c849bb9baf346889d459f463ac0dbe8575a48f  ./croc/croc_arm_abi_NetBSD
b6f4ae2184afec08f332e4bae80293eac0f9004b25e0bac46639e66a713b3cb2  ./croc/croc_arm_abi_OpenBSD
dc8754bb02c4f04916eed5643fc2b20aac3f072391103be817970f21be21dcc1  ./croc/croc_loong64_Linux
ee6af7302233861d819b97f14388ca5940a7977804d3673a553734cecb05c07a  ./croc/croc_mips64_Linux
7bf1c99e1794e10ab5e3989a9a32541764a062683cac3c828d5ad036c6bb58de  ./croc/croc_mips64le_Linux
e8062ac83f558abd24e3e73d68fc32f0f3a983c08a2c7d07170fd92a018c53c0  ./croc/croc_mips_Linux
73c195d7ef87a09a6ebcb12d470282b530d38576d661eebc1a53a8e166a1089b  ./croc/croc_mipsle_Linux
06595c68ff2e9194051c4e95aa42d7cded287608035d63b8c03526e7fd12df8c  ./croc/croc_powerpc64_ppc64_Linux
e50f0bb5f69491097bd47cc87ddc761249fb6ee6ef2ab05c660a136434c26ecc  ./croc/croc_powerpc64le_ppc64le_Linux
879f2168998f37c74a9b646f9a59b6657c14468d00b5aa62850b403e5b406686  ./croc/croc_riscv64_Linux
46eb15e4af17cfd88d70ab23af31bb87db7f2530cdae07673b8f62cd991e4dc6  ./croc/croc_s390x_Linux
d29fb90b203bf51d936c7e4dc6c8df279d449fef0ac72502972fbdc1de6a7690  ./croc/croc_x86_64_macOS
```


---

- #### Sizes

```console
10M   ./croc/croc_386_Linux
15M   ./croc/croc_aarch64_arm64_FreeBSD
15M   ./croc/croc_aarch64_arm64_Linux
15M   ./croc/croc_aarch64_arm64_OpenBSD
15M   ./croc/croc_aarch64_arm64_Windows.exe
11M   ./croc/croc_aarch64_arm64_macOS
11M   ./croc/croc_amd_x86_64_DragonFlyBSD
11M   ./croc/croc_amd_x86_64_FreeBSD
11M   ./croc/croc_amd_x86_64_Linux
11M   ./croc/croc_amd_x86_64_NetBSD
11M   ./croc/croc_amd_x86_64_OpenBSD
12M   ./croc/croc_amd_x86_64_Windows.exe
7.1M  ./croc/croc_amd_x86_FreeBSD
11M   ./croc/croc_amd_x86_Linux
10M   ./croc/croc_amd_x86_NetBSD
7.1M  ./croc/croc_amd_x86_OpenBSD
12M   ./croc/croc_amd_x86_Windows.exe
15M   ./croc/croc_arm_Windows.exe
7.2M  ./croc/croc_arm_abi_NetBSD
7.2M  ./croc/croc_arm_abi_OpenBSD
11M   ./croc/croc_loong64_Linux
12M   ./croc/croc_mips64_Linux
12M   ./croc/croc_mips64le_Linux
12M   ./croc/croc_mips_Linux
12M   ./croc/croc_mipsle_Linux
11M   ./croc/croc_powerpc64_ppc64_Linux
11M   ./croc/croc_powerpc64le_ppc64le_Linux
11M   ./croc/croc_riscv64_Linux
12M   ./croc/croc_s390x_Linux
11M   ./croc/croc_x86_64_macOS
```

---

- #### Version
```console

$ ./croc/croc_amd_x86_64_Linux --version
croc version v10.4.14

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
   v10.4.14

COMMANDS:
   send     send file(s), or folder (see options with croc send -h)
   relay    start your own relay (optional)
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
   --testing               flag for testing purposes (default: false)
   --quiet                 disable all output (default: false)
   --disable-clipboard     disable copy to clipboard (default: false)
   --extended-clipboard    copy full command with secret as env variable to clipboard (default: false)
   --multicast value       multicast address to use for local discovery (default: "239.255.255.250")
   --curve value           choose an encryption curve (p521, p256, p384, siec, ed25519) (default: "p256")
   --ip value              set sender ip if known e.g. 10.0.0.1:9009, [::1]:9009
   --relay value           address of the relay (default: "167.233.99.128:9009") [$CROC_RELAY]
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


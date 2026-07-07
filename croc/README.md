
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
./croc/croc_aarch64_arm64_FreeBSD:     ELF 64-bit LSB executable, ARM aarch64, version 1 (FreeBSD), statically linked, Go BuildID=LhjRNNdUpg-fxGkxkarZ/MSRDnGhApgshYF8unIsR/rDO2S5wBkE9E0z-rrgXP/7u7k9TuBuXMvzheo7L1W, BuildID[sha1]=95292ff55d9b630cdec481c79d4a9bb59e27cca3, for FreeBSD 12.3, FreeBSD-style, with debug_info, not stripped
./croc/croc_aarch64_arm64_Linux:       ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=kIen8CZqx3YtUDEWJLd_/ciXTfUUCN4bKNVLcIFdL/rGG07uyJzSvE2rIpFrX_/vkB2vdcr09g63kWs8J7z, BuildID[sha1]=836a100264a9734b57f28b0358daa0a405cf20fc, with debug_info, not stripped
./croc/croc_aarch64_arm64_OpenBSD:     ELF 64-bit LSB executable, ARM aarch64, version 1 (OpenBSD), dynamically linked, interpreter /usr/libexec/ld.so, Go BuildID=oa42PbKbjGUPksvAWCNo/L-kNuLuLFpYnQUNkd9AR/-ypPvQlQbFCbMp47eBKg/Iu-3XoBOc8exaOQWhX_3, BuildID[sha1]=093d24dd4ba785761fcc4e378e860375bdd3365d, for OpenBSD, with debug_info, not stripped
./croc/croc_aarch64_arm64_Windows.exe: PE32+ executable (console) Aarch64, for MS Windows, 14 sections
./croc/croc_aarch64_arm64_macOS:       Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./croc/croc_amd_x86_64_DragonFlyBSD:   ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=YcsbvAHSSlBMk3EXEGPs/WDNaPZSTdBumsoxIh7rP/3eyZe9niv4ep0TJ6fOA3/ypldQ_HR6IcWslqkEDP_, BuildID[sha1]=75ea0334db8ed35a3615cd15d08c462e046ab761, stripped
./croc/croc_amd_x86_64_FreeBSD:        ELF 64-bit LSB executable, x86-64, version 1 (FreeBSD), statically linked, Go BuildID=7bjxqIBwkTdYv3SSCd0S/I-u9Iz1xmp5sllOOZJOI/arfHOoVcbCttqhPVYiUe/jtma6trkEDBSrIwoCseb, BuildID[sha1]=a5f345e7260ab595479195bbbb962d546233336b, for FreeBSD 12.3, FreeBSD-style, stripped
./croc/croc_amd_x86_64_Linux:          ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=lyYdYNO6lIiZaUqhLTQ3/WyYF-IYtlVrMuNzUCGny/tuytUQhfpUJIm_LvIygU/H7gZH6WqWvPC5hlWC0eq, BuildID[sha1]=f70b7b6ba7c5bc516bb1edb8be8b87863a0758b7, stripped
./croc/croc_amd_x86_64_NetBSD:         ELF 64-bit LSB executable, x86-64, version 1 (NetBSD), statically linked, Go BuildID=nR2qVsN3IkJRBGNr6SwZ/TAV2bEZjtUPhhPPaIw40/b-gnQ7NHHIM41-lQiXCY/xUevVbO3tc_3EBT9H9wI, BuildID[sha1]=d1e7267050445571dd3cae66f9f16f50720a25a3, for NetBSD 7.0, stripped
./croc/croc_amd_x86_64_OpenBSD:        ELF 64-bit LSB executable, x86-64, version 1 (OpenBSD), dynamically linked, interpreter /usr/libexec/ld.so, Go BuildID=ipNOthgr9XZHxj_pFuC_/r0M3MdVBhzz22EjhrSej/DdZSSwI17UJBdoSqEWuH/l6HIgGrcMbccAI36X60K, BuildID[sha1]=c4be43b8fc7b64808990ecf5cb127b06c0b16f90, for OpenBSD, stripped
./croc/croc_amd_x86_64_Windows.exe:    PE32+ executable (console) x86-64 (stripped to external PDB), for MS Windows, 8 sections
./croc/croc_amd_x86_FreeBSD:           ELF 32-bit LSB executable, Intel 80386, version 1 (FreeBSD), statically linked, for FreeBSD 12.3, FreeBSD-style, Go BuildID=pzNrEUJBJW2rS8WbBo1i/efB3Y9OPU_FNUsEveobp/eHFP7W8to9BzwgUQ0dYW/9Bo7qlkEzoieE5kfcHL3, stripped
./croc/croc_amd_x86_Linux:             ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=vRs-Y020IJ-uwjvF6QX0/ONI9iJ4N7a7gQeujxJcc/DFbDptlJAyy-rmFF2xze/wyfNtkvPGvUJDKChjMwx, BuildID[sha1]=c8d586cd1b0a7d20986ac2da675043db376a27ff, stripped
./croc/croc_amd_x86_NetBSD:            ELF 32-bit LSB executable, Intel 80386, version 1 (NetBSD), statically linked, Go BuildID=byQ6IcJlijwBsu20wJZi/c7-qwF-hr68ugYI0ZPQ_/Xj6rER_ac2kjxlDYnuuS/S4Od_pR4B1RvuVfnVqC8, BuildID[sha1]=46005f4e3da1ca5546928bac233e7e570f898764, for NetBSD 7.0, stripped
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
a0154fd20eaf4e45570152568e3d7fd8a6e8a02569099a5d3761f943c85febcb  ./croc/croc_386_Linux
be33aba7360b99f30f8d056fb9007afc81afaa96b4e3d537f130aff296d5e9e9  ./croc/croc_aarch64_arm64_FreeBSD
da59a3c6cf648af37721d4c5693e81758c120d8a795f3b0242d0deb33a4fcca5  ./croc/croc_aarch64_arm64_Linux
e23bc2fafa426d306c65fa11ca8e38295a8dce11fceba0921b3a882cd376254a  ./croc/croc_aarch64_arm64_OpenBSD
aad6ebc7b343e555d8bf6aea82ecda42647d149ceb815239c0c05ae61bdf9c69  ./croc/croc_aarch64_arm64_Windows.exe
b83034b7f10388a6d320579f65cc3831f4cf4b3483ea81a6c5ef67066c3e8f9c  ./croc/croc_aarch64_arm64_macOS
40e23841ea48da47af9a608ba9c2c9a8b97aa9f69c868e8e792ac249e3408298  ./croc/croc_amd_x86_64_DragonFlyBSD
8cb21b7d662b01d9c1ea64e4dd7f4948cbb42c9a7ea4f10508dcc03039d6a305  ./croc/croc_amd_x86_64_FreeBSD
c1af60d57a36968d3f5431e8a75c9d4a0dac793873c125d79201721b58a8545a  ./croc/croc_amd_x86_64_Linux
1be5f752817fcea9fd7e9b5597138b02c2719f0cc10db29c9e51defa6f5fcc3d  ./croc/croc_amd_x86_64_NetBSD
f5bd5ec603a466765c4c344296cf64ddb94dbac19dc7dd348c43e07d4b641d7d  ./croc/croc_amd_x86_64_OpenBSD
e6c12bb6013c1578f233dc749d6b121d1df998c51c73f43c8088638fab21d060  ./croc/croc_amd_x86_64_Windows.exe
7ff1b6c223ed59e440118debc349e65254d507e82865377f3e2904184258b08e  ./croc/croc_amd_x86_FreeBSD
ef2c9e3b8c2fdcba5934ee3705866ae4e30032da8003ce6bca8b19d194037e69  ./croc/croc_amd_x86_Linux
ee0718ef2c5569914c97e506bdf13dade61b5c64b5adbe23df889ccb49f28e1a  ./croc/croc_amd_x86_NetBSD
9964c8ee5e7abcce36d282ccadeae66e1f2244bcff4befdb2b2bf9f974da957d  ./croc/croc_amd_x86_OpenBSD
d32a01e44131fa7fd8b7e70ebf31593f1b7c34ded29cde5f8489e7d939221e39  ./croc/croc_amd_x86_Windows.exe
ed657a7f38152378e377ac7b7df5720e550362cf5d411203aab105e3ad389e5f  ./croc/croc_arm_Windows.exe
2419b6a55fc015b0548bc9ce29c849bb9baf346889d459f463ac0dbe8575a48f  ./croc/croc_arm_abi_NetBSD
b6f4ae2184afec08f332e4bae80293eac0f9004b25e0bac46639e66a713b3cb2  ./croc/croc_arm_abi_OpenBSD
935f37a71fe871d3bc17213eb13bb722bf1ad7265200296b4cffa6bfe533f2e2  ./croc/croc_loong64_Linux
2a421c2cc44147814d8c1e54b656286d502ebcdcf9369a470bed0aadc612ecb8  ./croc/croc_mips64_Linux
2fa90c8c089d6b1e5f595194aa13192ce56a0a8004574be08b13d92ab4d1288c  ./croc/croc_mips64le_Linux
6cd8a0d183b722a90d802cfdd155ba0b69cde487c069b4fcad26aa4a7e6a8f7c  ./croc/croc_mips_Linux
ed11a075efc3603c4440f40a40cea57a0ea93fcfdc8f9831044a412530055435  ./croc/croc_mipsle_Linux
f3e163aead1fd43a8cae92572fd6a34b47be36d84c73f91403b2e8bbe38a9ed5  ./croc/croc_powerpc64_ppc64_Linux
8c806e21edaedbb38eb8a6341398fba44127b9d360b4c1c6a58e2ddb560f9852  ./croc/croc_powerpc64le_ppc64le_Linux
7ba2bce738b3aa08062ea6c9307c7d4e4b732fa4469ad6ab9c368cb2a4d63e83  ./croc/croc_riscv64_Linux
3177d3cd364088db77e73e3bb2cc7a7a7f998081f09c368c617be79071cb4b9a  ./croc/croc_s390x_Linux
65b0d1a8ed0325bf0a8319aaa2b3f825b6499d52bc5b5942bae4155e9cc6204f  ./croc/croc_x86_64_macOS
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
10M   ./croc/croc_riscv64_Linux
12M   ./croc/croc_s390x_Linux
11M   ./croc/croc_x86_64_macOS
```

---

- #### Version
```console

$ ./croc/croc_amd_x86_64_Linux --version
croc version v10.4.11

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
   v10.4.11

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
   --relay value           address of the relay (default: "178.105.79.46:9009") [$CROC_RELAY]
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


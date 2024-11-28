
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
./croc/croc_aarch64_arm64_FreeBSD:     ELF 64-bit LSB executable, ARM aarch64, version 1 (FreeBSD), statically linked, for FreeBSD 12.3, FreeBSD-style, Go BuildID=D6bNOgElGVjwSRCOM1KG/YmEBqdC-2Yaqyvv39lys/O38_ckkk8yBqjMzIe3Wk/VnUXzyKcm4SNPxwdY0OO, with debug_info, not stripped
./croc/croc_aarch64_arm64_Linux:       ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=LGEkG0iCHfXzkuze3k6u/mk5U0DTYS1Bh4RESdxZ9/fgHNOZqDYV1kg6ilxB_K/4Huzn75vRqgvbqUjF-sm, with debug_info, not stripped
./croc/croc_aarch64_arm64_OpenBSD:     ELF 64-bit LSB executable, ARM aarch64, version 1 (OpenBSD), dynamically linked, interpreter /usr/libexec/ld.so, for OpenBSD, Go BuildID=SZqV5ZU8y9D0ICfwOUa2/a9th2ECX5S99_CtbQvBW/X1UiW5qdiL6V7mjMq1qw/ChuSe7-UbKs0rqOcKyTb, with debug_info, not stripped
./croc/croc_aarch64_arm64_Windows.exe: PE32+ executable (console) Aarch64, for MS Windows
./croc/croc_aarch64_arm64_macOS:       Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./croc/croc_amd_x86_64_DragonFlyBSD:   ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=72TizQMOVM3TGl5MfyQZ/6MOdlNivg5jI4ghetlFy/2P_zq5trhqTO_BIU6s3p/JlN0VlBpF5amfw_-2Te7, stripped
./croc/croc_amd_x86_64_FreeBSD:        ELF 64-bit LSB executable, x86-64, version 1 (FreeBSD), statically linked, for FreeBSD 12.3, FreeBSD-style, Go BuildID=jjYuQDuDN4nWP_exGuUa/Djd6BCYP-q_-3nfsxTrj/ZXB4zj-gQavVaTNS8mSe/PQpqinRiAhUKKUhDT0LA, stripped
./croc/croc_amd_x86_64_Linux:          ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=oksYQn8kRJQHKEvD6WJC/XHpBo8fcmQdOWT4lPOU7/WdhLzo2Ssp1MYQUPJPzO/-2LTCXOhus3-QxjYY47B, stripped
./croc/croc_amd_x86_64_NetBSD:         ELF 64-bit LSB executable, x86-64, version 1 (NetBSD), statically linked, for NetBSD 7.0, Go BuildID=3WSyx-fz1CdvGoZ0AhVp/b24KPrxJfwDkyKkRoyee/JorOG2Yu_JHIiat2sLQG/qo_KmherOfHEeBOiK2rw, stripped
./croc/croc_amd_x86_64_OpenBSD:        ELF 64-bit LSB executable, x86-64, version 1 (OpenBSD), dynamically linked, interpreter /usr/libexec/ld.so, for OpenBSD, Go BuildID=JxFFLblbx1MROH_45vNP/2_eky31bQveZEOcpnYma/oolH6Q1Wahah1tbUDrCE/sNDsQRejqQirYEfrUndu, stripped
./croc/croc_amd_x86_64_Windows.exe:    PE32+ executable (console) x86-64 (stripped to external PDB), for MS Windows
./croc/croc_amd_x86_FreeBSD:           ELF 32-bit LSB executable, Intel 80386, version 1 (FreeBSD), statically linked, for FreeBSD 12.3, FreeBSD-style, Go BuildID=pzNrEUJBJW2rS8WbBo1i/efB3Y9OPU_FNUsEveobp/eHFP7W8to9BzwgUQ0dYW/9Bo7qlkEzoieE5kfcHL3, stripped
./croc/croc_amd_x86_Linux:             ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=VqnLP7T8ew42xDvcUcmv/UavcCIzA64XhEy2Ln_b-/SWnFhohO2zDh4NNzzvs0/Ct1fCnYF4hsBjOVrm8KV, stripped
./croc/croc_amd_x86_NetBSD:            ELF 32-bit LSB executable, Intel 80386, version 1 (NetBSD), statically linked, for NetBSD 7.0, Go BuildID=aYLH38iIxM14-PJVrZKo/4yxRngYGVf9OTbSs6Ovj/m7NrCy30QNNJx0dNNcOZ/SDEwscZI3CHMmxpogBWk, stripped
./croc/croc_amd_x86_OpenBSD:           ELF 32-bit LSB executable, Intel 80386, version 1 (OpenBSD), dynamically linked, interpreter /usr/libexec/ld.so, for OpenBSD, Go BuildID=QJxeN-dGsKofnMKOHiqI/-nycADcw5xsi0Hxak8HL/DuUbViwnVIXgJHYxTg-F/NnSTXqNJaWdfOy8QkASY, stripped
./croc/croc_amd_x86_Windows.exe:       PE32 executable (console) Intel 80386 (stripped to external PDB), for MS Windows
./croc/croc_arm_Windows.exe:           PE32 executable (console) ARMv7 Thumb, for MS Windows
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
6779cc799bcbb232df501a6063542fee8df2ac6a699158099fa004b95487b4ef  ./croc/croc_386_Linux
572b1e75f00a17ef92de6cb427b9cd33e699335e509003d7c7f3fa64fae7aa71  ./croc/croc_aarch64_arm64_FreeBSD
6eaa541b3f2cece3ca73c4c68b610938e352c20bc7c2e146212408ed6544bebd  ./croc/croc_aarch64_arm64_Linux
0a6c9cdbd571d38ffbbb4c083fefe50e982b8524aaa7487e65dad2112fda93aa  ./croc/croc_aarch64_arm64_OpenBSD
bba4ca4fc7b7f1f3fe475386bbafad75b15d27757b6e0796e906a165d337c445  ./croc/croc_aarch64_arm64_Windows.exe
733519d805f17aaef16e2d686877f900d5bcbe3d983c2dfbf09ebfd0aa94ad83  ./croc/croc_aarch64_arm64_macOS
5efd85d8e789dd0a891fcf16025d2aced93309bc4d3ab5e7a8da8d32e3003b92  ./croc/croc_amd_x86_64_DragonFlyBSD
0aff49e2c8de0395dc094a8a82342d20d824f723722090921a38671925be4d03  ./croc/croc_amd_x86_64_FreeBSD
4de3bd27bde7e3ec59b21c5011aa9fd18b33a6504eea2283c509f202f805b595  ./croc/croc_amd_x86_64_Linux
7411ee64c91a8a1a1058b42d74bca5bfae27e502f70f55c6f50e5b1f5cb3e4a4  ./croc/croc_amd_x86_64_NetBSD
01341dcd8c3c46a0dafdb27b8bef74c53ce28593c50dabe97eae45ea9f4e146c  ./croc/croc_amd_x86_64_OpenBSD
f9b56d493fcaf93e143dd0178d1e35fe70800c9c3bbd2fb959464062674493a1  ./croc/croc_amd_x86_64_Windows.exe
7ff1b6c223ed59e440118debc349e65254d507e82865377f3e2904184258b08e  ./croc/croc_amd_x86_FreeBSD
dfd2d7ee3d445e911bcc758f783a138ec6ed8f08c181b4244ac2acd4583a1d12  ./croc/croc_amd_x86_Linux
ec49e7395d28a1174abe6c2032425f53e23504b158f596d81b4b9c3b1949b704  ./croc/croc_amd_x86_NetBSD
9964c8ee5e7abcce36d282ccadeae66e1f2244bcff4befdb2b2bf9f974da957d  ./croc/croc_amd_x86_OpenBSD
66b6c04fa4bdaef24463cb6a2b365e2f1dbc947cf7e224c2e3b4a001ebddf36d  ./croc/croc_amd_x86_Windows.exe
c15c6312c89db3454da768b4a402d786d007b3e6a9a70e28c92cdd4787b1e8f0  ./croc/croc_arm_Windows.exe
2419b6a55fc015b0548bc9ce29c849bb9baf346889d459f463ac0dbe8575a48f  ./croc/croc_arm_abi_NetBSD
b6f4ae2184afec08f332e4bae80293eac0f9004b25e0bac46639e66a713b3cb2  ./croc/croc_arm_abi_OpenBSD
3221a722c51495c973f95a844d1229797a42566e08003b838a26945db8eb56a7  ./croc/croc_loong64_Linux
5e04fb23c6e1b47f1237dbfe869ea0f72edf609c11d17dbaf240b18faef610e9  ./croc/croc_mips64_Linux
694b7d529f8ff5fedf7dad38d3d3c795fca4a0cf29edfe78c52913ce928ed90a  ./croc/croc_mips64le_Linux
6b4373564f35756a5a57f7cdd61e24c304477ded395bdb74876d0790211ff8c3  ./croc/croc_mips_Linux
39c47998b3114d992af17a741c454ce1cbe10507c4b0d64ae44c49523556b6a1  ./croc/croc_mipsle_Linux
4ff4e73d1797f577b36b94adbc049edfc5f90216618b09615ef482a9f2db26d3  ./croc/croc_powerpc64_ppc64_Linux
969e3b73a67c8f1c7968cf36f4b2ebb455648486588a40873d07345f74b1d343  ./croc/croc_powerpc64le_ppc64le_Linux
632d7c03216ba4fa704e3b8690723701e94c4a62a7d08e29fcbec4a1b8297ccf  ./croc/croc_riscv64_Linux
4a7270a8204ebcb790bb5e9085690cca49d718bd0e5e2040580dba2d5bff8948  ./croc/croc_s390x_Linux
95418ddc3004fa77ee4c7b54d03ef544c337b7eaef52d1c4bdb3b26ab5502b31  ./croc/croc_x86_64_macOS
```


---

- #### Sizes

```console
8.5M  ./croc/croc_386_Linux
13M   ./croc/croc_aarch64_arm64_FreeBSD
13M   ./croc/croc_aarch64_arm64_Linux
13M   ./croc/croc_aarch64_arm64_OpenBSD
13M   ./croc/croc_aarch64_arm64_Windows.exe
8.9M  ./croc/croc_aarch64_arm64_macOS
8.9M  ./croc/croc_amd_x86_64_DragonFlyBSD
9.0M  ./croc/croc_amd_x86_64_FreeBSD
9.0M  ./croc/croc_amd_x86_64_Linux
8.9M  ./croc/croc_amd_x86_64_NetBSD
9.0M  ./croc/croc_amd_x86_64_OpenBSD
10M   ./croc/croc_amd_x86_64_Windows.exe
7.1M  ./croc/croc_amd_x86_FreeBSD
8.5M  ./croc/croc_amd_x86_Linux
8.3M  ./croc/croc_amd_x86_NetBSD
7.1M  ./croc/croc_amd_x86_OpenBSD
9.4M  ./croc/croc_amd_x86_Windows.exe
13M   ./croc/croc_arm_Windows.exe
7.2M  ./croc/croc_arm_abi_NetBSD
7.2M  ./croc/croc_arm_abi_OpenBSD
8.9M  ./croc/croc_loong64_Linux
9.9M  ./croc/croc_mips64_Linux
9.9M  ./croc/croc_mips64le_Linux
9.7M  ./croc/croc_mips_Linux
9.7M  ./croc/croc_mipsle_Linux
8.7M  ./croc/croc_powerpc64_ppc64_Linux
8.9M  ./croc/croc_powerpc64le_ppc64le_Linux
8.5M  ./croc/croc_riscv64_Linux
9.5M  ./croc/croc_s390x_Linux
9.2M  ./croc/croc_x86_64_macOS
```

---

- #### Version
```console

$ ./croc/croc_amd_x86_64_Linux --version
croc version v10.1.0

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
   v10.1.0

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
   --multicast value       multicast address to use for local discovery (default: "239.255.255.250")
   --curve value           choose an encryption curve (p521, p256, p384, siec) (default: "p256")
   --ip value              set sender ip if known e.g. 10.0.0.1:9009, [::1]:9009
   --relay value           address of the relay (default: "5.78.91.237:9009") [$CROC_RELAY]
   --relay6 value          ipv6 address of the relay (default: "[2a01:4ff:1f0:c10b::1]:9009") [$CROC_RELAY6]
   --out value             specify an output folder to receive the file (default: ".")
   --pass value            password for the relay (default: "pass123") [$CROC_PASS]
   --socks5 value          add a socks5 proxy [$SOCKS5_PROXY]
   --connect value         add a http proxy [$HTTP_PROXY]
   --throttleUpload value  Throttle the upload speed e.g. 500k
   --help, -h              show help (default: false)
   --version, -v           print the version (default: false)


```

---


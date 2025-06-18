
---
- #### Download aria2
> - **Sources**
> > ```bash
> > --> Android:
> >      - https://github.com/Zackptg5/Cross-Compiled-Binaries-Android/tree/master/aria2
> > --> Linux:
> >      - https://github.com/abcfy2/aria2-static-build [ Stable Releases + Latest Preleases ]
> >      - Binaries for s390x are compiled using dockercross
> > --> Windows:
> >      - https://github.com/abcfy2/aria2-static-build
> >      - https://github.com/repos/minnyres/aria2-windows-arm64
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

!# For Android
--> aria2c_aarch_arm_Android
--> aria2c_aarch64_arm64_Android
--> aria2c_x86_64_Android
--> aria2c_x86_Android

!#For Linux
--> aria2c_aarch64_arm64_musl_Linux || aarch64 || arm64 [64-bit] (GNU/Linux)
--> aria2c_aarch64_arm64_musl_latest_Linux
--> aria2c_aarch64_arm64_libressl_musl_Linux
--> aria2c_aarch64_arm64_libressl_musl_latest_Linux
--> aria2c_amd_x86_64_musl_Linux || amd x86_64 || x86_64 [64-bit] (GNU/Linux)
--> aria2c_amd_x86_64_musl_latest_Linux
--> aria2c_amd_x86_64_libressl_musl_Linux
--> aria2c_amd_x86_64_libressl_musl_latest_Linux
--> aria2c_arm_abi_musl_Linux || ARMv4 || ARMv5 || ARMv7 (?) [32-bit] {Hardware Floating-Point Unit (FPU) support : NO}
--> aria2c_arm_abi_musl_latest_Linux
--> aria2c_arm_abi_libressl_musl_Linux
--> aria2c_arm_abi_libressl_musl_latest_Linux
--> //_gnueabihf_Linux || ARMv7 [32-bit] {Hardware Floating-Point Unit (FPU) support : YES}
--> // || x86_64 [32-bit] (GNU/Linux)
--> //_m68k_Linux || Motorola_NXP [32-bit] (SYSV)
--> aria2c_mips_musl_Linux || MIPS (Big-Endian) [32-bit] (SYSV)
--> aria2c_mips_musl_latest_Linux
--> aria2c_mips_libressl_musl_Linux
--> aria2c_mips_libressl_musl_latest_Linux
--> aria2c_mips64_musl_Linux || MIPS (Big-Endian) [64-bit] (SYSV)
--> aria2c_mips64_musl_latest_Linux
--> aria2c_mips64_libressl_musl_Linux
--> aria2c_mips64_libressl_musl_latest_Linux
--> //_mips64el_Linux || MIPSel (Little-Endian) [64-bit] (SYSV)
--> aria2c_mipsel_musl_Linux || MIPSel (Little-Endian) [32-bit] (SYSV)
--> aria2c_mipsel_musl_latest_Linux
--> aria2c_mipsel_libressl_musl_Linux
--> aria2c_mipsel_libressl_musl_latest_Linux
--> //powerpc_Linux || ppc || cisco 4500 [32-bit] (SYSV)
--> //powerpc64_Linux || ppc || cisco 4500 [32-bit] (SYSV)
--> //powerpc64le_Linux || ppc64le || cisco 7500 || OpenPOWER ELF V2 ABI (Little-Endian) [64-bit] (GNU/Linux)
--> //riscv32_Linux || UCB RISC-V || RVC [32-bit] (SYSV)
--> //riscv64_Linux || UCB RISC-V || RVC [64-bit] (SYSV)
--> //s390x_Linux || IBM S/390 [64-bit] (GNU/Linux)

!# For Windows
--> aria2c_aarch64_arm64_Windows.exe || [64-bit] (PE32+) 
--> aria2c_amd_x86_x64_Windows.exe || [64-bit] (PE32+) 
--> aria2c_i686_Windows.exe || [32-bit] (PE32)
--> aria2c_i686_latest_Windows.exe


!# Export
export aria2_ARCH="$YOUR_CPU_ARCH_FROM_LIST_ABOVE"
!# For Linux : append `musl` before `_Linux` if you want the musl compiled binaries
!# Example: aria2_busybox_aarch_arm64_Linux --> aria2_busybox_aarch_arm64_musl_Linux
!# export aria2_ARCH="aria2_busybox_aarch_arm64_musl_Linux"

!# Download Def
 curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/aria2/$aria2_ARCH"

!# Or for .base64
 curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/aria2/$aria2_ARCH.base64"

```
---
- #### Install aria2
```bash
!# Copy downloaded aria2c binary to /usr/bin || /usr/local/bin

!# For $HOME/bin
 mkdir -p "$HOME/bin" && export PATH="$HOME/bin:$PATH"

!# Move Downloaded aria2 binary to that DIR
 mv "$Path_To_aria2c_Binary" "/usr/bin/aria2c"

!# Give Writeable Perms
 chmod +xwr "/usr/bin/aria2c"
```




---
```console
$ file ./aria2/aria2c_aarch64_arm64_Android ./aria2/aria2c_aarch64_arm64_Windows.exe ./aria2/aria2c_aarch64_arm64_libressl_musl_Linux ./aria2/aria2c_aarch64_arm64_libressl_musl_latest_Linux ./aria2/aria2c_aarch64_arm64_musl_Linux ./aria2/aria2c_aarch64_arm64_musl_latest_Linux ./aria2/aria2c_aarch_arm_Android ./aria2/aria2c_amd_x86_64_libressl_musl_Linux ./aria2/aria2c_amd_x86_64_libressl_musl_latest_Linux ./aria2/aria2c_amd_x86_64_musl_Linux ./aria2/aria2c_amd_x86_64_musl_latest_Linux ./aria2/aria2c_amd_x86_x64_Windows.exe ./aria2/aria2c_amd_x86_x64_latest_Windows.exe ./aria2/aria2c_arm_abi_libressl_musl_Linux ./aria2/aria2c_arm_abi_libressl_musl_latest_Linux ./aria2/aria2c_arm_abi_musl_Linux ./aria2/aria2c_arm_abi_musl_latest_Linux ./aria2/aria2c_i686_Windows.exe ./aria2/aria2c_i686_latest_Windows.exe ./aria2/aria2c_mips64_libressl_musl_Linux ./aria2/aria2c_mips64_libressl_musl_latest_Linux ./aria2/aria2c_mips64_musl_Linux ./aria2/aria2c_mips64_musl_latest_Linux ./aria2/aria2c_mips_libressl_musl_Linux ./aria2/aria2c_mips_libressl_musl_latest_Linux ./aria2/aria2c_mips_musl_Linux ./aria2/aria2c_mips_musl_latest_Linux ./aria2/aria2c_mipsel_libressl_musl_Linux ./aria2/aria2c_mipsel_libressl_musl_latest_Linux ./aria2/aria2c_mipsel_musl_Linux ./aria2/aria2c_mipsel_musl_latest_Linux ./aria2/aria2c_x86_64_Android ./aria2/aria2c_x86_Android
./aria2/aria2c_aarch64_arm64_Android:                    ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, stripped
./aria2/aria2c_aarch64_arm64_Windows.exe:                PE32+ executable (console) Aarch64, for MS Windows, 7 sections
./aria2/aria2c_aarch64_arm64_libressl_musl_Linux:        ELF 64-bit LSB pie executable, ARM aarch64, version 1 (SYSV), static-pie linked, stripped
./aria2/aria2c_aarch64_arm64_libressl_musl_latest_Linux: ELF 64-bit LSB pie executable, ARM aarch64, version 1 (SYSV), static-pie linked, stripped
./aria2/aria2c_aarch64_arm64_musl_Linux:                 ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, stripped
./aria2/aria2c_aarch64_arm64_musl_latest_Linux:          ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, stripped
./aria2/aria2c_aarch_arm_Android:                        ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, stripped
./aria2/aria2c_amd_x86_64_libressl_musl_Linux:           ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), static-pie linked, stripped
./aria2/aria2c_amd_x86_64_libressl_musl_latest_Linux:    ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), static-pie linked, stripped
./aria2/aria2c_amd_x86_64_musl_Linux:                    ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), static-pie linked, stripped
./aria2/aria2c_amd_x86_64_musl_latest_Linux:             ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), static-pie linked, stripped
./aria2/aria2c_amd_x86_x64_Windows.exe:                  PE32+ executable (console) x86-64 (stripped to external PDB), for MS Windows, 10 sections
./aria2/aria2c_amd_x86_x64_latest_Windows.exe:           PE32+ executable (console) x86-64 (stripped to external PDB), for MS Windows, 10 sections
./aria2/aria2c_arm_abi_libressl_musl_Linux:              ELF 32-bit LSB pie executable, ARM, EABI5 version 1 (SYSV), static-pie linked, stripped
./aria2/aria2c_arm_abi_libressl_musl_latest_Linux:       ELF 32-bit LSB pie executable, ARM, EABI5 version 1 (SYSV), static-pie linked, stripped
./aria2/aria2c_arm_abi_musl_Linux:                       ELF 32-bit LSB pie executable, ARM, EABI5 version 1 (SYSV), static-pie linked, stripped
./aria2/aria2c_arm_abi_musl_latest_Linux:                ELF 32-bit LSB pie executable, ARM, EABI5 version 1 (SYSV), static-pie linked, stripped
./aria2/aria2c_i686_Windows.exe:                         PE32 executable (console) Intel 80386 (stripped to external PDB), for MS Windows, 8 sections
./aria2/aria2c_i686_latest_Windows.exe:                  PE32 executable (console) Intel 80386 (stripped to external PDB), for MS Windows, 9 sections
./aria2/aria2c_mips64_libressl_musl_Linux:               ELF 64-bit MSB pie executable, MIPS, MIPS-III version 1 (SYSV), static-pie linked, stripped
./aria2/aria2c_mips64_libressl_musl_latest_Linux:        ELF 64-bit MSB pie executable, MIPS, MIPS-III version 1 (SYSV), static-pie linked, stripped
./aria2/aria2c_mips64_musl_Linux:                        ELF 64-bit MSB pie executable, MIPS, MIPS-III version 1 (SYSV), static-pie linked, stripped
./aria2/aria2c_mips64_musl_latest_Linux:                 ELF 64-bit MSB pie executable, MIPS, MIPS-III version 1 (SYSV), static-pie linked, stripped
./aria2/aria2c_mips_libressl_musl_Linux:                 ELF 32-bit MSB pie executable, MIPS, MIPS-I version 1 (SYSV), static-pie linked, stripped
./aria2/aria2c_mips_libressl_musl_latest_Linux:          ELF 32-bit MSB pie executable, MIPS, MIPS-I version 1 (SYSV), static-pie linked, stripped
./aria2/aria2c_mips_musl_Linux:                          ELF 32-bit MSB pie executable, MIPS, MIPS-II version 1 (SYSV), static-pie linked, stripped
./aria2/aria2c_mips_musl_latest_Linux:                   ELF 32-bit MSB pie executable, MIPS, MIPS-II version 1 (SYSV), static-pie linked, stripped
./aria2/aria2c_mipsel_libressl_musl_Linux:               ELF 32-bit LSB pie executable, MIPS, MIPS-I version 1 (SYSV), static-pie linked, stripped
./aria2/aria2c_mipsel_libressl_musl_latest_Linux:        ELF 32-bit LSB pie executable, MIPS, MIPS-I version 1 (SYSV), static-pie linked, stripped
./aria2/aria2c_mipsel_musl_Linux:                        ELF 32-bit LSB pie executable, MIPS, MIPS-II version 1 (SYSV), static-pie linked, stripped
./aria2/aria2c_mipsel_musl_latest_Linux:                 ELF 32-bit LSB pie executable, MIPS, MIPS-II version 1 (SYSV), static-pie linked, stripped
./aria2/aria2c_x86_64_Android:                           ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, stripped
./aria2/aria2c_x86_Android:                              ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, stripped

--> SHA256SUM
$ sha256sum ./aria2/aria2c_aarch64_arm64_Android ./aria2/aria2c_aarch64_arm64_Windows.exe ./aria2/aria2c_aarch64_arm64_libressl_musl_Linux ./aria2/aria2c_aarch64_arm64_libressl_musl_latest_Linux ./aria2/aria2c_aarch64_arm64_musl_Linux ./aria2/aria2c_aarch64_arm64_musl_latest_Linux ./aria2/aria2c_aarch_arm_Android ./aria2/aria2c_amd_x86_64_libressl_musl_Linux ./aria2/aria2c_amd_x86_64_libressl_musl_latest_Linux ./aria2/aria2c_amd_x86_64_musl_Linux ./aria2/aria2c_amd_x86_64_musl_latest_Linux ./aria2/aria2c_amd_x86_x64_Windows.exe ./aria2/aria2c_amd_x86_x64_latest_Windows.exe ./aria2/aria2c_arm_abi_libressl_musl_Linux ./aria2/aria2c_arm_abi_libressl_musl_latest_Linux ./aria2/aria2c_arm_abi_musl_Linux ./aria2/aria2c_arm_abi_musl_latest_Linux ./aria2/aria2c_i686_Windows.exe ./aria2/aria2c_i686_latest_Windows.exe ./aria2/aria2c_mips64_libressl_musl_Linux ./aria2/aria2c_mips64_libressl_musl_latest_Linux ./aria2/aria2c_mips64_musl_Linux ./aria2/aria2c_mips64_musl_latest_Linux ./aria2/aria2c_mips_libressl_musl_Linux ./aria2/aria2c_mips_libressl_musl_latest_Linux ./aria2/aria2c_mips_musl_Linux ./aria2/aria2c_mips_musl_latest_Linux ./aria2/aria2c_mipsel_libressl_musl_Linux ./aria2/aria2c_mipsel_libressl_musl_latest_Linux ./aria2/aria2c_mipsel_musl_Linux ./aria2/aria2c_mipsel_musl_latest_Linux ./aria2/aria2c_x86_64_Android ./aria2/aria2c_x86_Android
6705bac56e0752b26b22d4aa98cf5caa0f4672904e6cbf0ac2f516cc5f05797d  ./aria2/aria2c_aarch64_arm64_Android
8aeaf6bcf7f4e897acbfc5dde154e1894403aa89722bddc45468d4e6a734d50f  ./aria2/aria2c_aarch64_arm64_Windows.exe
84c4598d25d0150fd0ca4793eb967fa7a7ee9980c02d9e1028132f82d9ac8681  ./aria2/aria2c_aarch64_arm64_libressl_musl_Linux
106f8bda4748f41e41ac6c9d7940916eade60c2456add3c596a2d90996a9db85  ./aria2/aria2c_aarch64_arm64_libressl_musl_latest_Linux
9acc2c6e7dc97d4302bd197cc9ef4c2e54cc79e449ba90e252c10f53f9e74cc3  ./aria2/aria2c_aarch64_arm64_musl_Linux
3f16465e24700263bb011be741e24706403acf1aab240a4d6efe09a85d86e207  ./aria2/aria2c_aarch64_arm64_musl_latest_Linux
b06494c59df4c3536ad68dfc1ce5b33d3e638cd1e845ae5452709b35ed1270bb  ./aria2/aria2c_aarch_arm_Android
1d17b0371e82a51be97f787a9b80d2ff70fbf57e0373b081562992eb8e05cbf3  ./aria2/aria2c_amd_x86_64_libressl_musl_Linux
eba651b3d28f41f41d3c9d7e69c821947338374401b951e244c26b1633120537  ./aria2/aria2c_amd_x86_64_libressl_musl_latest_Linux
b0f94bc56521ce52c8cc344381779a1f693746ef3c2083fdae776e49a51291b3  ./aria2/aria2c_amd_x86_64_musl_Linux
add2d5e80e09bae997a545a083a80bfc45f33d9c8144332de4a867025f40deaf  ./aria2/aria2c_amd_x86_64_musl_latest_Linux
fb58da27a9dda5b6a7137283770a5a041158f1676c4bdd33762987b5e6cad179  ./aria2/aria2c_amd_x86_x64_Windows.exe
d138cfc718e4b38c8c6aa868d4ba6662ac6635b2135138e8179a5d23cb7df4b8  ./aria2/aria2c_amd_x86_x64_latest_Windows.exe
9f764d16e33516b774199ab43083c2e7c87b87b33725010d69c482438b22f41c  ./aria2/aria2c_arm_abi_libressl_musl_Linux
fb36ad4c9470f5a91c07a58887e1414b6646cd43dc44cbe106bd9f1b7d8202f9  ./aria2/aria2c_arm_abi_libressl_musl_latest_Linux
058ba484a6956141b7f5dab67fd884a0fb1891f6ede3f5dcdeaab335084ecea6  ./aria2/aria2c_arm_abi_musl_Linux
0bf27b94a4006a0fcea15888e30c514deebfa069726da0407a5e8b5af9e4ce3d  ./aria2/aria2c_arm_abi_musl_latest_Linux
0b51fc224b746751c5145137b917af324d7fc7dc5618441aa68cf224488a4f2f  ./aria2/aria2c_i686_Windows.exe
c702b0ba503c702abbb44d2e1d1eca7c35e1d9aeb739541cef7d3a1ad343ad8c  ./aria2/aria2c_i686_latest_Windows.exe
f14161c6cd93e34dca987e5153f0f8b36d6f301abc671970883ffefd4fa77284  ./aria2/aria2c_mips64_libressl_musl_Linux
cc8fc0a29cb98fd3153b7225d26695111475911e53394779496e3eedcb419d49  ./aria2/aria2c_mips64_libressl_musl_latest_Linux
59e3f2eaffd71ce7ce84d67c230f073d77b80f5354dd53e8e463e0f624c68563  ./aria2/aria2c_mips64_musl_Linux
5ba13dd394b86d97be4e8d8a639bd7af4c33105e6c3074c3e0a88ca981537fb0  ./aria2/aria2c_mips64_musl_latest_Linux
b6ca9b4b88aa79e21f41d511b8e4a362055501f11d8ff9302f17774d274ea302  ./aria2/aria2c_mips_libressl_musl_Linux
b13b5f97e0c01dd1848f669ec8bf0f0a895faff6f2bf2962b91b41935c204801  ./aria2/aria2c_mips_libressl_musl_latest_Linux
9a8c30e26eca2b4a823ccbb96640f4e48a8fccae5c8804756b2d5d8be78867c1  ./aria2/aria2c_mips_musl_Linux
2a7dec21cb9633dfcbe5a76bf9ac384d3d0ca08a5b86701fa8daeecd939327a9  ./aria2/aria2c_mips_musl_latest_Linux
d7efbbff6e5e6ffcc5c1cd8a89edc65e71b9d7945381b09ce38a25bf59b4eb36  ./aria2/aria2c_mipsel_libressl_musl_Linux
3adbbb5ee6e4cbeab17276cc5a6517a980dc3ce9127b9645ed9c86084d422115  ./aria2/aria2c_mipsel_libressl_musl_latest_Linux
fc88358393c8f5d5a00f2f3a7550dbc5393109cbcb0b2210ae046974a5f62d58  ./aria2/aria2c_mipsel_musl_Linux
4f9652ad1252f7db906ad1487856c929f0f6985af773f0775060c921d16c4fbe  ./aria2/aria2c_mipsel_musl_latest_Linux
43be89da4d7eef4f3d0d789f8fbffc404c6cbd6cf9606cb53cc7fe3e9bf6d59c  ./aria2/aria2c_x86_64_Android
4df82676bef78c241efe873914d3af5312c62eab2e4719c22f619c231650ba53  ./aria2/aria2c_x86_Android
```


---

- #### Sizes

```console
3.8K  INFO.md
15K   README.md
9.7M  aria2c_aarch64_arm64_Android
4.4M  aria2c_aarch64_arm64_Windows.exe
8.1M  aria2c_aarch64_arm64_libressl_musl_Linux
8.0M  aria2c_aarch64_arm64_libressl_musl_latest_Linux
11M   aria2c_aarch64_arm64_musl_Linux
13M   aria2c_aarch64_arm64_musl_latest_Linux
8.0M  aria2c_aarch_arm_Android
8.3M  aria2c_amd_x86_64_libressl_musl_Linux
8.2M  aria2c_amd_x86_64_libressl_musl_latest_Linux
13M   aria2c_amd_x86_64_musl_Linux
13M   aria2c_amd_x86_64_musl_latest_Linux
5.9M  aria2c_amd_x86_x64_Windows.exe
5.9M  aria2c_amd_x86_x64_latest_Windows.exe
6.8M  aria2c_arm_abi_libressl_musl_Linux
6.7M  aria2c_arm_abi_libressl_musl_latest_Linux
8.9M  aria2c_arm_abi_musl_Linux
9.1M  aria2c_arm_abi_musl_latest_Linux
5.9M  aria2c_i686_Windows.exe
6.4M  aria2c_i686_latest_Windows.exe
12M   aria2c_mips64_libressl_musl_Linux
11M   aria2c_mips64_libressl_musl_latest_Linux
15M   aria2c_mips64_musl_Linux
15M   aria2c_mips64_musl_latest_Linux
11M   aria2c_mips_libressl_musl_Linux
11M   aria2c_mips_libressl_musl_latest_Linux
14M   aria2c_mips_musl_Linux
14M   aria2c_mips_musl_latest_Linux
11M   aria2c_mipsel_libressl_musl_Linux
11M   aria2c_mipsel_libressl_musl_latest_Linux
14M   aria2c_mipsel_musl_Linux
14M   aria2c_mipsel_musl_latest_Linux
11M   aria2c_x86_64_Android
12M   aria2c_x86_Android
7     version.txt
```

---

- #### Flags
```console
$ qemu-aarch64-static ./aria2/aria2c_aarch64_arm64_libressl_musl_latest_Linux --version
aria2 version 1.37.0
Copyright (C) 2006, 2019 Tatsuhiro Tsujikawa

This program is free software; you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation; either version 2 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

** Configuration **
Enabled Features: Async DNS, BitTorrent, Firefox3 Cookie, GZip, HTTPS, Message Digest, Metalink, XML-RPC, SFTP
Hash Algorithms: sha-1, sha-224, sha-256, sha-384, sha-512, md5, adler32
Libraries: zlib/1.3.1.zlib-ng libxml2/2.13.4 sqlite3/3.47.0 OpenSSL/2.0.0 c-ares/1.34.2 libssh2/1.11.1
Compiler: gcc 11.2.1 20211120
  built by  x86_64-pc-linux-gnu
  targeting aarch64-unknown-linux-musl
  on        Nov  2 2024 01:27:54
System: Linux 6.11.0-1015-azure #15~24.04.1-Ubuntu SMP Thu May  1 02:52:08 UTC 2025 aarch64

Report bugs to https://github.com/aria2/aria2/issues
Visit https://aria2.github.io/

```

---


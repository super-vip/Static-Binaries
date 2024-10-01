
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
./croc/croc_aarch64_arm64_FreeBSD:     ELF 64-bit LSB executable, ARM aarch64, version 1 (FreeBSD), statically linked, for FreeBSD 12.3, FreeBSD-style, Go BuildID=_77wuB9QgFAA5tqyaJvg/_Xn-xfv8QaGw4Ushq1TB/mUr9akJNWaaac33k5E-0/Z3Y6wiKB5NgX9qMExk81, with debug_info, not stripped
./croc/croc_aarch64_arm64_Linux:       ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=qxqDMcUXjybxcGTz2dWS/0MPNDBvr-Gvh6YBTDnEc/oTreLUHGXOV6piakNfsI/Lx1kIhnqKOmUuRcPPR6I, with debug_info, not stripped
./croc/croc_aarch64_arm64_OpenBSD:     ELF 64-bit LSB executable, ARM aarch64, version 1 (OpenBSD), dynamically linked, interpreter /usr/libexec/ld.so, for OpenBSD, Go BuildID=8rE4edH4EyiXv667PSI9/jv7TrOs-sytkGZKTFNb1/mRIa68nrqQ9iWgXu5nwN/ZKb_kXgIinJkilU1bLF6, with debug_info, not stripped
./croc/croc_aarch64_arm64_Windows.exe: PE32+ executable (console) Aarch64, for MS Windows
./croc/croc_aarch64_arm64_macOS:       Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./croc/croc_amd_x86_64_DragonFlyBSD:   ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=5LsUrY3-Ex2t45ht8zU1/zs5djGKeQk3gbmFugxpG/9jQRR3JAHwWRywVc9SRd/GNwcvMxI_dmhrGa4VGJ9, stripped
./croc/croc_amd_x86_64_FreeBSD:        ELF 64-bit LSB executable, x86-64, version 1 (FreeBSD), statically linked, for FreeBSD 12.3, FreeBSD-style, Go BuildID=_psTlqPTnUZSuo40M32r/uuPqMRQfMuTPz7jE4eof/ncbkZcR1gBPD2KdMtCgy/OFEyL9adJfqQkJQqJxSq, stripped
./croc/croc_amd_x86_64_Linux:          ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=eWELxZ7YXOhmwRBIbGHI/6F0UqsJla71SUTHE_Exo/UfDC7p3B1Hk4weTVEKuC/nmudBPvHjzen6Ulrbz8G, stripped
./croc/croc_amd_x86_64_NetBSD:         ELF 64-bit LSB executable, x86-64, version 1 (NetBSD), statically linked, for NetBSD 7.0, Go BuildID=XvmgzO9n6KiruiGyFES7/8dzc49i8CYmJnSVlRvn9/KvYPv2v9J7GB2KWntKyk/u3-kS9GTI0YXqisjQTvh, stripped
./croc/croc_amd_x86_64_OpenBSD:        ELF 64-bit LSB executable, x86-64, version 1 (OpenBSD), dynamically linked, interpreter /usr/libexec/ld.so, for OpenBSD, Go BuildID=yAk8ggOHJITQYW1utjVr/DM7syqkV2iD_7D8VGy2C/pExBFwcKRS2EONv2Hd_B/vflgl6G84EgAXTnaNjVT, stripped
./croc/croc_amd_x86_64_Windows.exe:    PE32+ executable (console) x86-64 (stripped to external PDB), for MS Windows
./croc/croc_amd_x86_FreeBSD:           ELF 32-bit LSB executable, Intel 80386, version 1 (FreeBSD), statically linked, for FreeBSD 12.3, FreeBSD-style, Go BuildID=pzNrEUJBJW2rS8WbBo1i/efB3Y9OPU_FNUsEveobp/eHFP7W8to9BzwgUQ0dYW/9Bo7qlkEzoieE5kfcHL3, stripped
./croc/croc_amd_x86_Linux:             ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=jTXTo0fXVredKOXGRMwD/tGqRK7_vI4N5B1gSKmUb/0cHg3m6HKZK8uiYjOmyH/JcvtSoPkSc0gr-_4Y3Hb, stripped
./croc/croc_amd_x86_NetBSD:            ELF 32-bit LSB executable, Intel 80386, version 1 (NetBSD), statically linked, for NetBSD 7.0, Go BuildID=juS9krl3UZVkQNDbr7ji/nduG1uXRvzMfOVMS11hZ/a79zWrCdrG0lc324UHYL/u_9zKtFpT8gnWPBXsEh1, stripped
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
7d4ff68db8810cb2ef728d1e0db2b50ef2f93dfe7412d296a1a88870517b2b60  ./croc/croc_386_Linux
ada89347cdd64ae1eebc9cf13f50f9e09d22e55c3b3b8ddd39f6482ef1ada586  ./croc/croc_aarch64_arm64_FreeBSD
662407f078aa2a234e5e45bb6e660f72eac96bfbf05d23210ac34706c21ee6dc  ./croc/croc_aarch64_arm64_Linux
c28d7b63c5f5003f560437102f08e22b05ffb60e403ae2cefed0a0a387edbed3  ./croc/croc_aarch64_arm64_OpenBSD
f1a912848c7ae0297d445eb7489631116e661993e93ac20569aca4616c1b127a  ./croc/croc_aarch64_arm64_Windows.exe
a9bfcb23881e4ce4d699123615a448273dba610d85abc16e74c8d5351e32e701  ./croc/croc_aarch64_arm64_macOS
a98fbc4140cfe0c32a1a0874fde4d5994c67c5b71d3f961f618f58b167933f07  ./croc/croc_amd_x86_64_DragonFlyBSD
4bd315f652e804a4aa6f66bd64fae60e6b3f5e8883fc23c60d77f876214ea5eb  ./croc/croc_amd_x86_64_FreeBSD
1bf6c38b7623ef660c3aa11115eef9776adb0a8c609f661f2934370285f42fba  ./croc/croc_amd_x86_64_Linux
053546a7a646f5e52918d9c0a094cff2729fc2004e7da8f1939d2afec7d1b72f  ./croc/croc_amd_x86_64_NetBSD
2649a91d346e1af5731dc9d63c7b7ecc57c194d50450d3e7683208690b973d24  ./croc/croc_amd_x86_64_OpenBSD
c6ce7f1950008e2e978a3f794bf03b6f4c917cf0c4c797d851e099830ffd5b5a  ./croc/croc_amd_x86_64_Windows.exe
7ff1b6c223ed59e440118debc349e65254d507e82865377f3e2904184258b08e  ./croc/croc_amd_x86_FreeBSD
a3bed4614a1f330db1cdbf1d808b268653db51874c642bd7f7c35e9c0319f0fd  ./croc/croc_amd_x86_Linux
d5042a6474fb84728840971f3469bdce11f8dbb8ca46b858326177632ccec0a9  ./croc/croc_amd_x86_NetBSD
9964c8ee5e7abcce36d282ccadeae66e1f2244bcff4befdb2b2bf9f974da957d  ./croc/croc_amd_x86_OpenBSD
befa24324d1207994c43a0aba5158fcfefcfb65fc5b62491aee39b2e08401cdc  ./croc/croc_amd_x86_Windows.exe
0150885c8a89dca6d19ac307f787059053fffd35cd4adbe27609443ea7a72782  ./croc/croc_arm_Windows.exe
2419b6a55fc015b0548bc9ce29c849bb9baf346889d459f463ac0dbe8575a48f  ./croc/croc_arm_abi_NetBSD
b6f4ae2184afec08f332e4bae80293eac0f9004b25e0bac46639e66a713b3cb2  ./croc/croc_arm_abi_OpenBSD
41b14e010d1a8ca19db4cd4ccaf71b1dd83c4872f96da251edb036e1ae323a88  ./croc/croc_loong64_Linux
75437e0d0076077adda70530a74c6ea8d15c070d65ff817a4714a1888e00b0ed  ./croc/croc_mips64_Linux
659d8c14c9f1834175e2dd88ba383d61d8a148c8968d4d9005b730eccdc33a4e  ./croc/croc_mips64le_Linux
5ebd558a8fea40869c1a71d126ae1d37177d021db845ee7b78eed94c02dcd8e7  ./croc/croc_mips_Linux
6c5f4039eca5a7bbd65fe0f81c7d7553c1a1f3e8a7d1a2c7ababbaf4195cbc28  ./croc/croc_mipsle_Linux
e53b843c00659f810e39d52db84b69709b2d6e59b7aec4450f096d3ae65dd7dd  ./croc/croc_powerpc64_ppc64_Linux
945e4118dbcc91733b36e4b43754ec367522ee0b572e98a3195884b39507c179  ./croc/croc_powerpc64le_ppc64le_Linux
0cac8ce4221d84fa9687658f0eea9e80e834cadfae0a5acfd8c2a59aeebd57b8  ./croc/croc_riscv64_Linux
9906b5c9b9094c2d12b999ab00898254056c6769b780f90492bc0d48d37f14dd  ./croc/croc_s390x_Linux
f86f2bf8fa22b0e98485c67e19c2c01d682ebfa748727a35e4c4040982f8b9f2  ./croc/croc_x86_64_macOS
```


---

- #### Sizes

```console
7.8M  ./croc/croc_386_Linux
12M   ./croc/croc_aarch64_arm64_FreeBSD
12M   ./croc/croc_aarch64_arm64_Linux
12M   ./croc/croc_aarch64_arm64_OpenBSD
12M   ./croc/croc_aarch64_arm64_Windows.exe
8.2M  ./croc/croc_aarch64_arm64_macOS
8.3M  ./croc/croc_amd_x86_64_DragonFlyBSD
8.3M  ./croc/croc_amd_x86_64_FreeBSD
8.3M  ./croc/croc_amd_x86_64_Linux
8.3M  ./croc/croc_amd_x86_64_NetBSD
8.3M  ./croc/croc_amd_x86_64_OpenBSD
9.2M  ./croc/croc_amd_x86_64_Windows.exe
7.1M  ./croc/croc_amd_x86_FreeBSD
7.8M  ./croc/croc_amd_x86_Linux
7.7M  ./croc/croc_amd_x86_NetBSD
7.1M  ./croc/croc_amd_x86_OpenBSD
8.7M  ./croc/croc_amd_x86_Windows.exe
12M   ./croc/croc_arm_Windows.exe
7.2M  ./croc/croc_arm_abi_NetBSD
7.2M  ./croc/croc_arm_abi_OpenBSD
8.1M  ./croc/croc_loong64_Linux
9.1M  ./croc/croc_mips64_Linux
9.1M  ./croc/croc_mips64le_Linux
8.9M  ./croc/croc_mips_Linux
8.9M  ./croc/croc_mipsle_Linux
8.1M  ./croc/croc_powerpc64_ppc64_Linux
8.2M  ./croc/croc_powerpc64le_ppc64le_Linux
7.8M  ./croc/croc_riscv64_Linux
8.8M  ./croc/croc_s390x_Linux
8.6M  ./croc/croc_x86_64_macOS
```

---

- #### Version
```console

$ ./croc/croc_amd_x86_64_Linux --version
croc version v10.0.13

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
   v10.0.13

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


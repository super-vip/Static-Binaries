
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
./croc/croc_aarch64_arm64_FreeBSD:     ELF 64-bit LSB executable, ARM aarch64, version 1 (FreeBSD), statically linked, Go BuildID=6xqxfEQh8TGNWzVQhFFY/L-taDCqzAUJ-Bi8htU_w/Bi9pTsRH8Zz1CVsCIYwl/2X86z36uErMLnl3dkSpg, BuildID[sha1]=85ae7954caa44729462b2762f3110f679b4ceb34, for FreeBSD 12.3, FreeBSD-style, with debug_info, not stripped
./croc/croc_aarch64_arm64_Linux:       ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=4B75REQZ-u486zmJxHy-/V4lw0AoqFzqjdx3bCtjZ/VbEtGl-D6OlaKDGZ-ZFp/ZBMRReIMYW2zrdQqi9dW, BuildID[sha1]=af751f65b5fd7c4af93c41e8abf6eabcc74e78b0, with debug_info, not stripped
./croc/croc_aarch64_arm64_OpenBSD:     ELF 64-bit LSB executable, ARM aarch64, version 1 (OpenBSD), dynamically linked, interpreter /usr/libexec/ld.so, Go BuildID=LTWdCzmPOITtKwr7TFfQ/JE7Vg4W_L2__HC5Lb48Z/zdw1SHjM4qv2m8P-MHXw/rEB2WhkC9oBj3Uox2Igv, BuildID[sha1]=1b7f43cb7d40b4951964653c642cba256542d3e6, for OpenBSD, with debug_info, not stripped
./croc/croc_aarch64_arm64_Windows.exe: PE32+ executable (console) Aarch64, for MS Windows, 14 sections
./croc/croc_aarch64_arm64_macOS:       Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./croc/croc_amd_x86_64_DragonFlyBSD:   ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=awVWaSJKnXbW8O-byryG/DIfz1s9wp7QKsFlAOcCU/BjiRS3YQ9uNop4tYD0q-/E020g-3SJTE4tHzR6Ko4, BuildID[sha1]=c61df90450bcf224c16774f57ac0561488e86950, stripped
./croc/croc_amd_x86_64_FreeBSD:        ELF 64-bit LSB executable, x86-64, version 1 (FreeBSD), statically linked, Go BuildID=eAuJBMuAYAzC9XZFMZcj/AvbWl14h7Xubh9MEOMl6/GQgU0Rkei0accMULo9K1/-GxPeRQoAqjXWUBZmls8, BuildID[sha1]=3937acf3746e99d51f327a45167dee6426013ba1, for FreeBSD 12.3, FreeBSD-style, stripped
./croc/croc_amd_x86_64_Linux:          ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=RvWb1p677rie5nIvJda4/ff6GnJ-db_vP9uAk2KIF/gRw9JQTZ2qAorJ51A80C/XVnt3mbm3b_j0W5QHv5j, BuildID[sha1]=442addc010356383dcf5e59943256e49af930d26, stripped
./croc/croc_amd_x86_64_NetBSD:         ELF 64-bit LSB executable, x86-64, version 1 (NetBSD), statically linked, Go BuildID=ZB1AwrBDxzkuekaLF958/viv7FkIY1UmYTPbxz9Ri/YPj7l8LOuJaWzC_psy0E/IkNWg0ilVWk8R0YJYMID, BuildID[sha1]=bd3a12ac756cce7e75c0971ff834d97625dbe862, for NetBSD 7.0, stripped
./croc/croc_amd_x86_64_Windows.exe:    PE32+ executable (console) x86-64 (stripped to external PDB), for MS Windows, 8 sections
./croc/croc_amd_x86_FreeBSD:           ELF 32-bit LSB executable, Intel 80386, version 1 (FreeBSD), statically linked, for FreeBSD 12.3, FreeBSD-style, Go BuildID=pzNrEUJBJW2rS8WbBo1i/efB3Y9OPU_FNUsEveobp/eHFP7W8to9BzwgUQ0dYW/9Bo7qlkEzoieE5kfcHL3, stripped
./croc/croc_amd_x86_Linux:             ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=8FDbhQgV5NuKkvXuufHf/HQgTxXASajmufvsc1jOK/4wOFxF0nPI0Q5PsFboS1/E9-HxRNTgMvdlUtN3vZW, BuildID[sha1]=bcd9004a34d1635661cbb03df0308a43afd3308a, stripped
./croc/croc_amd_x86_NetBSD:            ELF 32-bit LSB executable, Intel 80386, version 1 (NetBSD), statically linked, Go BuildID=UBXiOwa0PdCB3QnBD8uR/xxzZBi9ajHI8VFk1DOhL/zs9ASIsDlRw1hPHX1QNU/rXCn7Vgb4ObMvQRvYTzl, BuildID[sha1]=7ab54d7186e704430d879a421953fc8d64fc326b, for NetBSD 7.0, stripped
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
dd0db260045cf6901432628e63d03c075296af0d640bbaf7d1c4d4679b909203  ./croc/croc_386_Linux
138d2bfb53036dd5d4b2fadd09f45469c26b215aeda1bfbeb80b511b6fbc6e9b  ./croc/croc_aarch64_arm64_FreeBSD
b7509d4bf69395bef09fdf3f491dd974a9d2135df3ea4091392bd9b2f0421709  ./croc/croc_aarch64_arm64_Linux
c65c71d378b2d77e96924ec3b7ace33fb75b776c15e331353edf217f18a9aacd  ./croc/croc_aarch64_arm64_OpenBSD
c030605373f728ee89df976169a5e668d23b3cebd3edb3390253c594ce5ef381  ./croc/croc_aarch64_arm64_Windows.exe
e188a23c4d21e00d2b772028cfeeb94a63f9de75e748d47370507038f13edcd8  ./croc/croc_aarch64_arm64_macOS
fb0d7f446fd182dd2ce723d16ee4796cb73729ea91b4d444e66bf79277ac4251  ./croc/croc_amd_x86_64_DragonFlyBSD
91aabbdd95b379b7d35239cf6b07f95021008af8b6b31c9a3ea337a6ee1971c5  ./croc/croc_amd_x86_64_FreeBSD
69de6dd6dccb2573d0d3391277b20e09814cfce566817565117cfb8c086f434e  ./croc/croc_amd_x86_64_Linux
e0b5a35b9b5a8ee1c933394aa7405a685088cb8e861358fdb88c2755d910e434  ./croc/croc_amd_x86_64_NetBSD
af4568f14ef9e467261e2298f1bdeb4ca0c22c9ca267cdcdd041a1bc96353f39  ./croc/croc_amd_x86_64_OpenBSD
2d532888ef717ecb983ee39d21bcd70319656362b54b1dc4f934bfef7278c743  ./croc/croc_amd_x86_64_Windows.exe
7ff1b6c223ed59e440118debc349e65254d507e82865377f3e2904184258b08e  ./croc/croc_amd_x86_FreeBSD
e936ea0c2bc552f3d4aefbc55fd701b32df232062d185fb1899f8fd57fc1b706  ./croc/croc_amd_x86_Linux
0667699d928214b6bd1cdc16f2532a07427f8a3f19237da6dbc7ed400467d921  ./croc/croc_amd_x86_NetBSD
9964c8ee5e7abcce36d282ccadeae66e1f2244bcff4befdb2b2bf9f974da957d  ./croc/croc_amd_x86_OpenBSD
2b2de5988c4905eabd999f8a98cb5612728860eeeb15910d6236c044cfd550b2  ./croc/croc_amd_x86_Windows.exe
ed657a7f38152378e377ac7b7df5720e550362cf5d411203aab105e3ad389e5f  ./croc/croc_arm_Windows.exe
2419b6a55fc015b0548bc9ce29c849bb9baf346889d459f463ac0dbe8575a48f  ./croc/croc_arm_abi_NetBSD
b6f4ae2184afec08f332e4bae80293eac0f9004b25e0bac46639e66a713b3cb2  ./croc/croc_arm_abi_OpenBSD
8efd2572940ab772d8918fddb3991d2c3aa30f0fc866f0bf823a741a68daa120  ./croc/croc_loong64_Linux
68ce8b4b9e63b600b4e152b93d5104f419548df49933f8892e50347072279e1a  ./croc/croc_mips64_Linux
b3f890ceb9f3748737402c942d4537c2d0e41cd4acfa4f6897469b8c09fd005a  ./croc/croc_mips64le_Linux
3b15fe271f1814b9656de6f56bba04349dfc428cc7ce5fe8c94022023cd2b951  ./croc/croc_mips_Linux
a5eb48d5fbc6a78d7728689bd10c8f1dea880198f8782e174227c3923a2eb9a5  ./croc/croc_mipsle_Linux
f9ed1168cfcee93a14d0ce599f2efb437d7c780b46ba86679fbfa50109712896  ./croc/croc_powerpc64_ppc64_Linux
7d10c284e44049f0f2b5d885791ecf25df7003025f72cee8d9818ed4162bdf9a  ./croc/croc_powerpc64le_ppc64le_Linux
fb280fc0e779f6562f32d2f065a30ab6a1cfd11ede9dff7c68b0105fb1dfd2b8  ./croc/croc_riscv64_Linux
a0a38ef4828b506e859b69b209cc3fc79720b23c7ab62145fabb569538e2b118  ./croc/croc_s390x_Linux
f6154cdf640d4857371186a6e2ebf5121b4c36a96f38be02f66f344070d06163  ./croc/croc_x86_64_macOS
```


---

- #### Sizes

```console
18M   ./croc/croc_386_Linux
22M   ./croc/croc_aarch64_arm64_FreeBSD
22M   ./croc/croc_aarch64_arm64_Linux
22M   ./croc/croc_aarch64_arm64_OpenBSD
23M   ./croc/croc_aarch64_arm64_Windows.exe
18M   ./croc/croc_aarch64_arm64_macOS
19M   ./croc/croc_amd_x86_64_DragonFlyBSD
19M   ./croc/croc_amd_x86_64_FreeBSD
19M   ./croc/croc_amd_x86_64_Linux
19M   ./croc/croc_amd_x86_64_NetBSD
19M   ./croc/croc_amd_x86_64_OpenBSD
20M   ./croc/croc_amd_x86_64_Windows.exe
7.1M  ./croc/croc_amd_x86_FreeBSD
18M   ./croc/croc_amd_x86_Linux
18M   ./croc/croc_amd_x86_NetBSD
7.1M  ./croc/croc_amd_x86_OpenBSD
19M   ./croc/croc_amd_x86_Windows.exe
15M   ./croc/croc_arm_Windows.exe
7.2M  ./croc/croc_arm_abi_NetBSD
7.2M  ./croc/croc_arm_abi_OpenBSD
18M   ./croc/croc_loong64_Linux
19M   ./croc/croc_mips64_Linux
19M   ./croc/croc_mips64le_Linux
19M   ./croc/croc_mips_Linux
19M   ./croc/croc_mipsle_Linux
18M   ./croc/croc_powerpc64_ppc64_Linux
18M   ./croc/croc_powerpc64le_ppc64le_Linux
18M   ./croc/croc_riscv64_Linux
19M   ./croc/croc_s390x_Linux
19M   ./croc/croc_x86_64_macOS
```

---

- #### Version
```console

$ ./croc/croc_amd_x86_64_Linux --version
croc version 11.0.1

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
   11.0.1

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
   --revoke value          revoke a stored transfer using its local sender receipt
   --multicast value       multicast address to use for local discovery (default: "239.255.255.250")
   --curve value           choose an encryption curve (p521, p256, p384, siec, ed25519) (default: "p256")
   --ip value              set sender ip if known e.g. 10.0.0.1:9009, [::1]:9009
   --relay value           address of the relay (default: "142.132.189.179:9009") [$CROC_RELAY]
   --relay6 value          ipv6 address of the relay (default: "[3a01:5f8:d015:6a55::1]:9009") [$CROC_RELAY6]
   --out value             specify an output folder to receive the file (default: ".")
   --pass value            password for the relay (default: "pass123") [$CROC_PASS]
   --socks5 value          add a socks5 proxy [$SOCKS5_PROXY]
   --connect value         add a http proxy [$HTTP_PROXY]
   --throttleUpload value  throttle the upload speed e.g. 500k
   --help, -h              show help (default: false)
   --version, -v           print the version (default: false)


```

---


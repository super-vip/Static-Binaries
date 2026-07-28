
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
./croc/croc_aarch64_arm64_FreeBSD:     ELF 64-bit LSB executable, ARM aarch64, version 1 (FreeBSD), statically linked, Go BuildID=Q3TCxe-3quv6Vep57OkO/BJKYPOjAjcNK_5ZpQ5jZ/JSLA2U7QeSiwX2823iLm/49nZs0ATcTV8B3zunSZx, BuildID[sha1]=305e04394c68e2dfbd883731b98bd188d36375e4, for FreeBSD 12.3, FreeBSD-style, with debug_info, not stripped
./croc/croc_aarch64_arm64_Linux:       ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=aMWs3gIFrOSkfhhdOlss/uMvErIpQRQA97nhVJv6x/yhpDhsxg1_Y_cVBop8bz/RgMsR6YQsWdeFecFA7BB, BuildID[sha1]=af323fd82c77e94ff0439110a4ffbf506def0510, with debug_info, not stripped
./croc/croc_aarch64_arm64_OpenBSD:     ELF 64-bit LSB executable, ARM aarch64, version 1 (OpenBSD), dynamically linked, interpreter /usr/libexec/ld.so, Go BuildID=Ju7azjpmGhd5pYm_up-k/ML3gqvXzf2Doj4f1rc8e/_v0tF292160-vv40fLuH/wRvcdIPoSyaI8ymh3DBP, BuildID[sha1]=6a0fec34ec56cf2ac53f34fb6103c5e1943880a4, for OpenBSD, with debug_info, not stripped
./croc/croc_aarch64_arm64_Windows.exe: PE32+ executable (console) Aarch64, for MS Windows, 14 sections
./croc/croc_aarch64_arm64_macOS:       Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./croc/croc_amd_x86_64_DragonFlyBSD:   ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=C0a2pFA0QiZnXAA8De-T/_d642ynrR3dWfiAp_JHv/A09x4CBJU2Laamxeca7i/b3TdD6hMk_wYaKDW6BnM, BuildID[sha1]=44c736fd77175cb18f0b9132290b12b8f1114dba, stripped
./croc/croc_amd_x86_64_FreeBSD:        ELF 64-bit LSB executable, x86-64, version 1 (FreeBSD), statically linked, Go BuildID=g7KvDre-XxIEgOnu9GQr/d9yR0FcUV1SKHoS8kH3n/fJgr8H8XANyXn6Oxjb8I/z-sGMzAlMcVgUGaeOuxp, BuildID[sha1]=3ffc1aec270b06f5531c5ffde32f49076e26ea45, for FreeBSD 12.3, FreeBSD-style, stripped
./croc/croc_amd_x86_64_Linux:          ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=l1S2d_b20d_ix2YXu5f9/PVy1iEAGMV01zWKx3e1h/NBDf4v8VhNTzm9BL_9Ae/1I31_4WWZZcKKFo2RNq4, BuildID[sha1]=7cd8085bc0a33913c0f96a94e42e32a5f00c7c6c, stripped
./croc/croc_amd_x86_64_NetBSD:         ELF 64-bit LSB executable, x86-64, version 1 (NetBSD), statically linked, Go BuildID=hNEdhwJTze3PkmqoBZjj/NkCJnbcbow3lV1s1-WAv/0rdJJFW1UhtepiR8GkbP/C55On-sApx4E7oe9xJON, BuildID[sha1]=fd8ced81c7b20498f8c88f62402f8edbad962362, for NetBSD 7.0, stripped
./croc/croc_amd_x86_64_OpenBSD:        ELF 64-bit LSB executable, x86-64, version 1 (OpenBSD), dynamically linked, interpreter /usr/libexec/ld.so, Go BuildID=SsUNIMT0GiIvnAD3ExZy/yh7W_PpmTFKyIbjvQ8dF/Ev3tHyOR-YvdL1znuZiK/g7EzqfqKsXf5qh9QMZeR, BuildID[sha1]=6be00b13a6e59ea1ba76e9bc085bb18b1e978c5a, for OpenBSD, stripped
./croc/croc_amd_x86_64_Windows.exe:    PE32+ executable (console) x86-64 (stripped to external PDB), for MS Windows, 8 sections
./croc/croc_amd_x86_FreeBSD:           ELF 32-bit LSB executable, Intel 80386, version 1 (FreeBSD), statically linked, for FreeBSD 12.3, FreeBSD-style, Go BuildID=pzNrEUJBJW2rS8WbBo1i/efB3Y9OPU_FNUsEveobp/eHFP7W8to9BzwgUQ0dYW/9Bo7qlkEzoieE5kfcHL3, stripped
./croc/croc_amd_x86_Linux:             ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=zB5wEn0guI4GnsKqcj3r/Hg9CV0hKM55982vdL1yw/ae1AZAI7JjJqs9s7qSFv/nRNWajNRBMifKH3E06dD, BuildID[sha1]=0cbcd4627cb5d9aef705477023648406e8e4a7f0, stripped
./croc/croc_amd_x86_NetBSD:            ELF 32-bit LSB executable, Intel 80386, version 1 (NetBSD), statically linked, Go BuildID=hXlVeZTbmDIBEqP_ycW3/P34rgqxoy67zQplGhdrl/Y9gh1aivEc8o0YrLav-B/TRe-86cU848eP-7WDt5E, BuildID[sha1]=396ae5adfd28612da79a933db277a3b3cafa1517, for NetBSD 7.0, stripped
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
f06b824c88ce42ed0134c8aec7702fd79eba718983a34c2c913c2c55ffffb2c9  ./croc/croc_386_Linux
afbc7aacc9dc519e3d03be9509ef665b6ece644f1a76dc9ac8b36aab70f5c127  ./croc/croc_aarch64_arm64_FreeBSD
478df04261bf243465f64c4f541d8d92b577e2af254a72048ec38641d5073a96  ./croc/croc_aarch64_arm64_Linux
5b279aa06987d3e8924b53f8cee560093751cadf2d3f8c91872749c02887a10b  ./croc/croc_aarch64_arm64_OpenBSD
40452b9930aca3eaea610e18ecb2f8ada336ca9798665fb275684e0254f84c0a  ./croc/croc_aarch64_arm64_Windows.exe
5063bc6f029cb38936067e69d0851606c98705441aed6b2eb3406a337ea280eb  ./croc/croc_aarch64_arm64_macOS
8758ab0748567d8b444546e3aba6397d3e12821b35f33b07e4d85a0dc52563a0  ./croc/croc_amd_x86_64_DragonFlyBSD
862a2c5c5c8dbeaf16477cabe48a6dac4bae53494d38e046c690469d08293136  ./croc/croc_amd_x86_64_FreeBSD
a12e655832b7a8ac96aece1e4afc29ab78f9e371351660cab63182294e834347  ./croc/croc_amd_x86_64_Linux
8d0da540d7e4cb55627c1379bc10e8c6437f2b3cbfafe2c3bab35769c96a18b7  ./croc/croc_amd_x86_64_NetBSD
20f2ef1be756c4e2591bf4b4ceff06b8cb7c0de4ec025b10b98c84a291f8161f  ./croc/croc_amd_x86_64_OpenBSD
1a182510a3c239b45032f56de1b5ba5338cdb97798e168079edeebb8ca10c26b  ./croc/croc_amd_x86_64_Windows.exe
7ff1b6c223ed59e440118debc349e65254d507e82865377f3e2904184258b08e  ./croc/croc_amd_x86_FreeBSD
6f8446e943ace5e0345c53a2492f32f6812458c1dda2df8ef342574e0a45bab7  ./croc/croc_amd_x86_Linux
2aeabcd5e3fbd8beb12f740d4ef174c732d24394c74ab1d5320d8c01da192840  ./croc/croc_amd_x86_NetBSD
9964c8ee5e7abcce36d282ccadeae66e1f2244bcff4befdb2b2bf9f974da957d  ./croc/croc_amd_x86_OpenBSD
0e1942c914f2b938ea29099ad58d8f1a57615d0ae70d3240bf2b019d016610e2  ./croc/croc_amd_x86_Windows.exe
ed657a7f38152378e377ac7b7df5720e550362cf5d411203aab105e3ad389e5f  ./croc/croc_arm_Windows.exe
2419b6a55fc015b0548bc9ce29c849bb9baf346889d459f463ac0dbe8575a48f  ./croc/croc_arm_abi_NetBSD
b6f4ae2184afec08f332e4bae80293eac0f9004b25e0bac46639e66a713b3cb2  ./croc/croc_arm_abi_OpenBSD
1a2642a1e73aa88679a8c2e2584ffdc7e184ec04d4502c1ae60c550f5b713a31  ./croc/croc_loong64_Linux
8c4d73ea3f08e618ded847da4c73fd3861cf6c9562a319febdba216cff6d6ba6  ./croc/croc_mips64_Linux
e7c7953d86e1d6d10d5832aed2d8835271e11e82b794feb50e1ff9534a3a79c3  ./croc/croc_mips64le_Linux
cb2f9a14b432269aed25a86f13346655e2ab77a8af4ebc3e930ad2e345248146  ./croc/croc_mips_Linux
613b64849d8935eda5e602ed215a0d75dd048bacdba0f235719cd828e4f264fd  ./croc/croc_mipsle_Linux
fac923e5637155ca8c7c0cb401e8c46b5df97687b8b5c9a16ee40135b3923869  ./croc/croc_powerpc64_ppc64_Linux
b6d7b8023db7dae5f7906f2cc08e29188ddb7065523d23a5c46f7766ecacb05b  ./croc/croc_powerpc64le_ppc64le_Linux
545ee9d464177cb88d08945dba084f89f9d2f0ff1e49eebeca7b9cd0e3429533  ./croc/croc_riscv64_Linux
8dc0f37c75defe92649c239f4c4ab8b44cbf625b536fa66eff07c02909bac1c7  ./croc/croc_s390x_Linux
2d4165149aff8d9cbe5ab20014575f4924cb2ca715c1e7b73503b73f22313ea0  ./croc/croc_x86_64_macOS
```


---

- #### Sizes

```console
16M   ./croc/croc_386_Linux
21M   ./croc/croc_aarch64_arm64_FreeBSD
21M   ./croc/croc_aarch64_arm64_Linux
21M   ./croc/croc_aarch64_arm64_OpenBSD
21M   ./croc/croc_aarch64_arm64_Windows.exe
17M   ./croc/croc_aarch64_arm64_macOS
17M   ./croc/croc_amd_x86_64_DragonFlyBSD
17M   ./croc/croc_amd_x86_64_FreeBSD
17M   ./croc/croc_amd_x86_64_Linux
17M   ./croc/croc_amd_x86_64_NetBSD
17M   ./croc/croc_amd_x86_64_OpenBSD
18M   ./croc/croc_amd_x86_64_Windows.exe
7.1M  ./croc/croc_amd_x86_FreeBSD
17M   ./croc/croc_amd_x86_Linux
16M   ./croc/croc_amd_x86_NetBSD
7.1M  ./croc/croc_amd_x86_OpenBSD
18M   ./croc/croc_amd_x86_Windows.exe
15M   ./croc/croc_arm_Windows.exe
7.2M  ./croc/croc_arm_abi_NetBSD
7.2M  ./croc/croc_arm_abi_OpenBSD
16M   ./croc/croc_loong64_Linux
18M   ./croc/croc_mips64_Linux
18M   ./croc/croc_mips64le_Linux
18M   ./croc/croc_mips_Linux
18M   ./croc/croc_mipsle_Linux
17M   ./croc/croc_powerpc64_ppc64_Linux
17M   ./croc/croc_powerpc64le_ppc64le_Linux
16M   ./croc/croc_riscv64_Linux
17M   ./croc/croc_s390x_Linux
17M   ./croc/croc_x86_64_macOS
```

---

- #### Version
```console

$ ./croc/croc_amd_x86_64_Linux --version
croc version 10.7.0

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
   10.7.0

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


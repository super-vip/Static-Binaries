
---
- #### Download [bore](https://github.com/ekzhang/bore)
> - **Sources**
> > ```bash
> > --> Android:
> >      - Built using cross (https://github.com/cross-rs/cross)
> > 
> > --> macOS:
> >      - https://github.com/ekzhang/bore/releases
> > 
> > --> Windows:
> >      - https://github.com/ekzhang/bore/releases
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

!# Android
--> aarch64 || arm64 || v8a [64-bit]
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/bore/bore_aarch64_arm64_Android"
--> ARM_abi || ARMv5 [32-bit]
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/bore/bore_armv_abi_Android"
--> ARM_abi || ARMv7 [32-bit]
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/bore/bore_armv7_abi_Android"
--> i686 || Intel 80386 [32-bit]
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/bore/bore_i686_Android"

!# Linux
--> aarch64 || arm64 [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/bore/bore_aarch64_arm64_gcc_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/bore/bore_aarch64_arm64_musl_Linux"
--> Amd x86_64 || x86_64 [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/bore/bore_amd_x86_64_gcc_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/bore/bore_amd_x86_64_musl_Linux"
--> ARM_abi [32-bit]
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/bore/bore_arm_abi_gcc_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/bore/bore_arm_abi_musl_Linux"
--> ARM_abihf [32-bit]
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/bore/bore_arm_abihf_gcc_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/bore/bore_arm_abihf_musl_Linux"
--> ARMv7_abi [32-bit]
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/bore/bore_armv7_abi_gcc_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/bore/bore_armv7_abi_musl_Linux"
--> ARMv7_abihf [32-bit]
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/bore/bore_armv7_abihf_gcc_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/bore/bore_armv7_abihf_musl_Linux"
--> i586 || Intel 80386 [32-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/bore/bore_i586_gcc_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/bore/bore_i586_musl_Linux"
--> i686 || x86 [32-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/bore/bore_amd_x86_i686_gcc_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/bore/bore_amd_x86_i686_musl_Linux"
--> MIPS (Big-Endian) [32-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/bore/bore_mips_gcc_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/bore/bore_mips_musl_Linux"
--> MIPSel || MIPSle (Little-Endian) [32-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/bore/bore_mipsel_gcc_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/bore/bore_mipsel_musl_Linux"
--> MIPS64 (Big-Endian) [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/bore/bore_mips64_gcc_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/bore/bore_mips64_musl_Linux"
--> MIPS64el || MIPS64le (Little-Endian) [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/bore/bore_mips64el_gcc_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/bore/bore_mips64el_musl_Linux"
--> powerpc || ppc || cisco 4500 [32-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/bore/bore_powerpc_ppc_gcc_Linux"
--> powerpc64|| ppc64 || cisco 7500 [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/bore/bore_powerpc64_ppc64_gcc_Linux"
--> powerpc64le || ppc64le || cisco 7500 || OpenPOWER ELF V2 ABI (Little-Endian) [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/bore/bore_powerpc64le_ppc64le_gcc_Linux"
--> risc64 || CB RISC-V || RVC [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/bore/bore_riscv64_gcc_Linux"
--> s390x || IBM S/390 [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/bore/bore_s390x_gcc_Linux"
--> SPARC V9 || Sun UltraSPARC1 [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/bore/bore_sparc64_gcc_Linux"

!# macOS
--> aarch64 || arm64
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/bore/bore_aarch64_arm64_macOS"
--> Amd x86_64 || x86_64
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/bore/bore_x86_64_macOS"

#Windows
--> Amd_x86 || x86 [32-bit]
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/bore/bore_amd_x86_Windows.exe"
--> Amd x86_64 || x86_64 [64-bit]
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/bore/bore_amd_x86_64_Windows.exe"

```
---
- #### Install bore
```bash
!# Recommended way to install bore is:
  cargo install bore-cli
!# Compile Dynamically from source 
  cargo install --git "https://github.com/ekzhang/bore"

!# Copy downloaded bore binaries to /usr/bin || /usr/local/bin
!# For $HOME/bin
 mkdir -p "$HOME/bin" && export PATH="$HOME/bin:$PATH"

!# Move Downloaded bore binaries to that DIR
 mv "$Path_To_bore_Binary" "/usr/bin/bore"

!# Give Writeable Perms
 chmod +xwr /usr/bin/bore*
```

---
```console

--> METADATA
./bore/bore_aarch64_arm64_Android:         ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, stripped
./bore/bore_aarch64_arm64_gcc_Linux:       ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, BuildID[sha1]=496077c8eee8cad1d532f64a2ff960bd5202286f, for GNU/Linux 3.7.0, stripped
./bore/bore_aarch64_arm64_macOS:           Mach-O 64-bit arm64 executable, flags:<NOUNDEFS|DYLDLINK|TWOLEVEL|PIE|HAS_TLV_DESCRIPTORS>
./bore/bore_aarch64_arm64_musl_Linux:      ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, stripped
./bore/bore_amd_x86_64_Windows.exe:        PE32+ executable (console) x86-64 (stripped to external PDB), for MS Windows, 5 sections
./bore/bore_amd_x86_64_gcc_Linux:          ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), static-pie linked, BuildID[sha1]=ce8b0a0a1135a9325c6cd641f39ac22e8af6577f, for GNU/Linux 3.2.0, stripped
./bore/bore_amd_x86_64_musl_Linux:         ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), static-pie linked, stripped
./bore/bore_amd_x86_Windows.exe:           PE32 executable (console) Intel 80386 (stripped to external PDB), for MS Windows, 4 sections
./bore/bore_amd_x86_i686_gcc_Linux:        ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, BuildID[sha1]=b8f90cc6174aa85b7fa2c5ac5475fc6631751564, for GNU/Linux 3.2.0, stripped
./bore/bore_amd_x86_i686_musl_Linux:       ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, stripped
./bore/bore_arm_abi_gcc_Linux:             ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, BuildID[sha1]=f109ca322714e4a360a8cf726083a132d6f6ec32, for GNU/Linux 3.2.0, stripped
./bore/bore_arm_abi_musl_Linux:            ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, stripped
./bore/bore_arm_abihf_gcc_Linux:           ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, for GNU/Linux 4.19.255, stripped
./bore/bore_arm_abihf_musl_Linux:          ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, stripped
./bore/bore_armv7_abi_Android:             ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, stripped
./bore/bore_armv7_abi_gcc_Linux:           ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, BuildID[sha1]=18ba34e191d9af684684a0e646c93442fe1ee354, for GNU/Linux 3.2.0, stripped
./bore/bore_armv7_abi_musl_Linux:          ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, stripped
./bore/bore_armv7_abihf_gcc_Linux:         ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, BuildID[sha1]=d2999df8810b13457b05976a8fa701dce946e86b, for GNU/Linux 3.2.0, stripped
./bore/bore_armv7_abihf_musl_Linux:        ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, stripped
./bore/bore_armv_abi_Android:              ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, stripped
./bore/bore_i586_gcc_Linux:                ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, BuildID[sha1]=65ec5acb7b9ad75eab35ca198efb310f8e725a38, for GNU/Linux 3.2.0, stripped
./bore/bore_i586_musl_Linux:               ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, stripped
./bore/bore_i686_Android:                  ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, stripped
./bore/bore_mips64_gcc_Linux:              ELF 64-bit MSB executable, MIPS, MIPS64 rel2 version 1 (SYSV), statically linked, BuildID[sha1]=3dc8ddc1663bbf5bd2156c3c52fc4a4e13664f8d, for GNU/Linux 3.2.0, stripped
./bore/bore_mips64_musl_Linux:             ELF 64-bit MSB executable, MIPS, MIPS64 rel2 version 1 (SYSV), statically linked, stripped
./bore/bore_mips64el_gcc_Linux:            ELF 64-bit LSB executable, MIPS, MIPS64 rel2 version 1 (SYSV), statically linked, BuildID[sha1]=baff583c8467e3d3f3eb2352e73b6f2db4828085, for GNU/Linux 3.2.0, stripped
./bore/bore_mips64el_musl_Linux:           ELF 64-bit LSB executable, MIPS, MIPS64 rel2 version 1 (SYSV), statically linked, stripped
./bore/bore_mips_gcc_Linux:                ELF 32-bit MSB executable, MIPS, MIPS32 rel2 version 1 (SYSV), statically linked, BuildID[sha1]=6b8197a890c465790da3bad2428544d44383f686, for GNU/Linux 3.2.0, stripped
./bore/bore_mips_musl_Linux:               ELF 32-bit MSB executable, MIPS, MIPS32 rel2 version 1 (SYSV), statically linked, stripped
./bore/bore_mipsel_gcc_Linux:              ELF 32-bit LSB executable, MIPS, MIPS32 rel2 version 1 (SYSV), statically linked, BuildID[sha1]=5573a0a24b5e75c5091a2e26d5f131314e566022, for GNU/Linux 3.2.0, stripped
./bore/bore_mipsel_musl_Linux:             ELF 32-bit LSB executable, MIPS, MIPS32 rel2 version 1 (SYSV), statically linked, stripped
./bore/bore_powerpc64_ppc64_gcc_Linux:     ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, BuildID[sha1]=1c052db08af5c03c52f9293adc17da68e6a77318, for GNU/Linux 3.2.0, stripped
./bore/bore_powerpc64le_ppc64le_gcc_Linux: ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, BuildID[sha1]=e20b528aae14aa6947dc8ca7a2a40251256c96b4, for GNU/Linux 3.10.0, stripped
./bore/bore_powerpc_ppc_gcc_Linux:         ELF 32-bit MSB executable, PowerPC or cisco 4500, version 1 (SYSV), statically linked, BuildID[sha1]=56a8bb20fba9c4385576137e44ee9dfd3912d1e1, for GNU/Linux 3.2.0, stripped
./bore/bore_riscv64_gcc_Linux:             ELF 64-bit LSB executable, UCB RISC-V, RVC, double-float ABI, version 1 (SYSV), statically linked, BuildID[sha1]=a94ce26ca48a98bb46727ff3b81410607c9f2aa6, for GNU/Linux 4.15.0, stripped
./bore/bore_s390x_gcc_Linux:               ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, BuildID[sha1]=4fae4790f7f89a4b34ec5967d0b7d44767fb2722, for GNU/Linux 3.2.0, stripped
./bore/bore_sparc64_gcc_Linux:             ELF 64-bit MSB executable, SPARC V9, Sun UltraSPARC1 Extensions Required, total store ordering, version 1 (SYSV), statically linked, BuildID[sha1]=8876cead22ba65e2bb7406a205ec871afa0f42fb, for GNU/Linux 3.2.0, stripped
./bore/bore_x86_64_macOS:                  Mach-O 64-bit x86_64 executable, flags:<NOUNDEFS|DYLDLINK|TWOLEVEL|PIE|HAS_TLV_DESCRIPTORS>

--> SHA256SUM
03a9c76dd8e00b7159533ebc317b97fbbbc6cd83e5431ee849137447a08c67b4  ./bore/bore_aarch64_arm64_Android
aea1886c13daa87325304c3c48ef55bd1874c874a76ace99d565aaee695942f6  ./bore/bore_aarch64_arm64_gcc_Linux
aab3e0f13c6cf35a4203d74cf9a229b935ea4d39a98b25ee8222a3311b4d52f1  ./bore/bore_aarch64_arm64_macOS
7fcd23e90ff1c5c53364572325dca98bbb9a846b8b0072fd65e3131ff597e202  ./bore/bore_aarch64_arm64_musl_Linux
2706a022b1a945efa65af83524ab7611784b21c6c44f5d9285b108523a493c72  ./bore/bore_amd_x86_64_Windows.exe
bbf55a32afe7ec070f6b2c6dd6b1e912b974bd46da5d0fdf217f16dfcfd649f2  ./bore/bore_amd_x86_64_gcc_Linux
efe51a5366b474b0f14479063e282146b44ae1b90e0b8066ebaffdd5a43f40d7  ./bore/bore_amd_x86_64_musl_Linux
41ae5b57f2c18676300fd8623c16979778e700d77bf271e937214ebe1aea90d7  ./bore/bore_amd_x86_Windows.exe
051316fa76302766548c1efcf686bef7b3e6fbc225095dceaedc5f5d868aa26d  ./bore/bore_amd_x86_i686_gcc_Linux
b11de0e3b24aaaf4cffdf6a1e28bd1e4482cd24d256131775753fdeb308f44d7  ./bore/bore_amd_x86_i686_musl_Linux
e36c3a611ff7077539c4e8ccfc7454ba238681bd9796b0bd47f9059d006d2c49  ./bore/bore_arm_abi_gcc_Linux
987178ff8f2751803c73aecd34effb5b0c5a1bb792881e3ff65e2d12ec47dc36  ./bore/bore_arm_abi_musl_Linux
928eb9ef78bbccba3af209331fa6515f79090b190e0d5005f928d28cd9c9ed3b  ./bore/bore_arm_abihf_gcc_Linux
65f016012a05c200790952648fdb4c70833c2dcf28101a5d8477ae4db9f93beb  ./bore/bore_arm_abihf_musl_Linux
547ff47ddffb53ae44481a70bdddff7474d3f250101fc83591cd56f196e29a7a  ./bore/bore_armv7_abi_Android
cf0e3cf9950a863864704a6c92ff11a0ad6bdbebfbb1b724c439f2c1f6864728  ./bore/bore_armv7_abi_gcc_Linux
59ef50a9fc78ca0928af487f287828747bee9daaa757e892dc00f69e019f9323  ./bore/bore_armv7_abi_musl_Linux
3a695ab918bfdb9555282440d0fac6e68b62cc9d62cd90d32b8240dee83a8965  ./bore/bore_armv7_abihf_gcc_Linux
fbf0f720e1e1fec971eeddf9920b091775613bd65a3d5391b5e8676b8822bed6  ./bore/bore_armv7_abihf_musl_Linux
8d660364026465d43ec77f4a741e2d756f4b94ee8722c315dda9cc9f7c563875  ./bore/bore_armv_abi_Android
c0617e8083d852fe70b9ffe57969c0a191452c31d9daab70688d9c0280620b12  ./bore/bore_i586_gcc_Linux
07272920e55b63cdfab656c5f07ae4e89d4fcc054dc5d999b069dbd64be38746  ./bore/bore_i586_musl_Linux
c812ac196b60f0d48c97abe4fd20ce282ed4b5a17371eb4c997cfa5bd0e720cc  ./bore/bore_i686_Android
4be810533490b43e0fc59bab2132c2485dd4285f6a68f533dfcded726ecbf104  ./bore/bore_mips64_gcc_Linux
07ea5e96766e2b1f35feb1ef823af53adfad22d0e0ad129e94d5db8307b98012  ./bore/bore_mips64_musl_Linux
1b413a2f4186c1c8f48b27ab15cad549c76ef2f4d40084f1936e7cae0fa44407  ./bore/bore_mips64el_gcc_Linux
f1da60bb75107d4ef527c2343a566079f7d8da8559fb409bb4e3393954c8649b  ./bore/bore_mips64el_musl_Linux
8d0a62156bdcf50a0acb4cb5de04e46724ad31b93a2f043b29631b90907e0323  ./bore/bore_mips_gcc_Linux
15f540a27495d8e9afd6ff422e8f6962cb56c6833a32213017ac88efbcbb7ab6  ./bore/bore_mips_musl_Linux
9c6d0da32751dda461276975bce5c11cf373b54a47240f7958e585a66684147b  ./bore/bore_mipsel_gcc_Linux
01b50222959e138d5acffc8ca2c98c450011b82d4630c3767bac4aac4476103c  ./bore/bore_mipsel_musl_Linux
b05e9d625052504bc34f8bb8bec9e287ce2a143805dc481c6855f18e23fd5c70  ./bore/bore_powerpc64_ppc64_gcc_Linux
038f31525a60094536dbc74f04cf255ee511e7269f00097219ab177279a1dc50  ./bore/bore_powerpc64le_ppc64le_gcc_Linux
3ca163463cd760f1a8bcc60a98064caf76b9a0a477c388151673bcc94fc8d5c1  ./bore/bore_powerpc_ppc_gcc_Linux
4df840d7ec14fb62e4bd54861c6ca75226cef0d8e35387d873b2e44da12b51d9  ./bore/bore_riscv64_gcc_Linux
a421969009ebd83d37ae45e9fa65542d71d73e86a4cbb150a421597efb47784d  ./bore/bore_s390x_gcc_Linux
f43313991b10cc2a133f0420198b2d17d76e2804026897eca01028562df2b164  ./bore/bore_sparc64_gcc_Linux
204f89169dbb89a6da0cb21a1ba5da645d14d22508888cfc46ad27353fd6c674  ./bore/bore_x86_64_macOS
```


---

- #### Sizes

```console
1.7M  ./bore/bore_aarch64_arm64_Android
1.8M  ./bore/bore_aarch64_arm64_gcc_Linux
2.3M  ./bore/bore_aarch64_arm64_macOS
1.3M  ./bore/bore_aarch64_arm64_musl_Linux
1.8M  ./bore/bore_amd_x86_64_Windows.exe
2.4M  ./bore/bore_amd_x86_64_gcc_Linux
1.5M  ./bore/bore_amd_x86_64_musl_Linux
1.4M  ./bore/bore_amd_x86_Windows.exe
2.2M  ./bore/bore_amd_x86_i686_gcc_Linux
1.4M  ./bore/bore_amd_x86_i686_musl_Linux
1.7M  ./bore/bore_arm_abi_gcc_Linux
1.3M  ./bore/bore_arm_abi_musl_Linux
1.7M  ./bore/bore_arm_abihf_gcc_Linux
1.3M  ./bore/bore_arm_abihf_musl_Linux
1.2M  ./bore/bore_armv7_abi_Android
1.7M  ./bore/bore_armv7_abi_gcc_Linux
1.2M  ./bore/bore_armv7_abi_musl_Linux
1.6M  ./bore/bore_armv7_abihf_gcc_Linux
1.2M  ./bore/bore_armv7_abihf_musl_Linux
1.5M  ./bore/bore_armv_abi_Android
2.2M  ./bore/bore_i586_gcc_Linux
1.4M  ./bore/bore_i586_musl_Linux
1.9M  ./bore/bore_i686_Android
2.3M  ./bore/bore_mips64_gcc_Linux
1.8M  ./bore/bore_mips64_musl_Linux
2.3M  ./bore/bore_mips64el_gcc_Linux
1.8M  ./bore/bore_mips64el_musl_Linux
2.3M  ./bore/bore_mips_gcc_Linux
1.9M  ./bore/bore_mips_musl_Linux
2.3M  ./bore/bore_mipsel_gcc_Linux
1.8M  ./bore/bore_mipsel_musl_Linux
2.5M  ./bore/bore_powerpc64_ppc64_gcc_Linux
2.4M  ./bore/bore_powerpc64le_ppc64le_gcc_Linux
2.2M  ./bore/bore_powerpc_ppc_gcc_Linux
1.8M  ./bore/bore_riscv64_gcc_Linux
2.0M  ./bore/bore_s390x_gcc_Linux
2.0M  ./bore/bore_sparc64_gcc_Linux
2.4M  ./bore/bore_x86_64_macOS
```

---

- #### Version
```console

$ ./bore/bore_amd_x86_64_musl_Linux --version
bore-cli 0.6.0

$ ./bore/bore_amd_x86_64_musl_Linux -h
A modern, simple TCP tunnel in Rust that exposes local ports to a remote server, bypassing standard NAT connection firewalls.

Usage: bore_amd_x86_64_musl_Linux <COMMAND>

Commands:
  local   Starts a local proxy to the remote server
  server  Runs the remote proxy server
  help    Print this message or the help of the given subcommand(s)

Options:
  -h, --help     Print help
  -V, --version  Print version


```

---


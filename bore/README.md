
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
./bore/bore_aarch64_arm64_gcc_Linux:       ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, BuildID[sha1]=ddc8e61a7ccb03ae4f95b433ced8e4d4645220bb, for GNU/Linux 3.7.0, stripped
./bore/bore_aarch64_arm64_macOS:           Mach-O 64-bit arm64 executable, flags:<NOUNDEFS|DYLDLINK|TWOLEVEL|PIE|HAS_TLV_DESCRIPTORS>
./bore/bore_aarch64_arm64_musl_Linux:      ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, stripped
./bore/bore_amd_x86_64_Windows.exe:        PE32+ executable (console) x86-64 (stripped to external PDB), for MS Windows, 5 sections
./bore/bore_amd_x86_64_gcc_Linux:          ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), static-pie linked, BuildID[sha1]=ac5349bb82b71be8eee41b36d94f22da3bca8aeb, for GNU/Linux 3.2.0, stripped
./bore/bore_amd_x86_64_musl_Linux:         ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), static-pie linked, stripped
./bore/bore_amd_x86_Windows.exe:           PE32 executable (console) Intel 80386 (stripped to external PDB), for MS Windows, 4 sections
./bore/bore_amd_x86_i686_gcc_Linux:        ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, BuildID[sha1]=712359ea8c66d7f0fa64dee54313ed7dc2198491, for GNU/Linux 3.2.0, stripped
./bore/bore_amd_x86_i686_musl_Linux:       ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, stripped
./bore/bore_arm_abi_gcc_Linux:             ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, BuildID[sha1]=c920139d9be1b5466083900b7d0c5d35f9beba9c, for GNU/Linux 3.2.0, stripped
./bore/bore_arm_abi_musl_Linux:            ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, stripped
./bore/bore_arm_abihf_gcc_Linux:           ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, for GNU/Linux 4.19.255, stripped
./bore/bore_arm_abihf_musl_Linux:          ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, stripped
./bore/bore_armv7_abi_Android:             ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, stripped
./bore/bore_armv7_abi_gcc_Linux:           ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, BuildID[sha1]=06178b0c4a440d8385f25bd6616bb8bf4332a078, for GNU/Linux 3.2.0, stripped
./bore/bore_armv7_abi_musl_Linux:          ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, stripped
./bore/bore_armv7_abihf_gcc_Linux:         ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, BuildID[sha1]=33a0661beeab57d37917c281fdbedeb3fa149e14, for GNU/Linux 3.2.0, stripped
./bore/bore_armv7_abihf_musl_Linux:        ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, stripped
./bore/bore_armv_abi_Android:              ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, stripped
./bore/bore_i586_gcc_Linux:                ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, BuildID[sha1]=e52c32439e6b365bc2aa203877292ce30b6582af, for GNU/Linux 3.2.0, stripped
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
./bore/bore_powerpc64_ppc64_gcc_Linux:     ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, BuildID[sha1]=32d6ab1d211259b82af51ae27d0de3c3c8ecf39d, for GNU/Linux 3.2.0, stripped
./bore/bore_powerpc64le_ppc64le_gcc_Linux: ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, BuildID[sha1]=deb55ddb59fa0b7e9c150a5dcba6714d50bca873, for GNU/Linux 3.10.0, stripped
./bore/bore_powerpc_ppc_gcc_Linux:         ELF 32-bit MSB executable, PowerPC or cisco 4500, version 1 (SYSV), statically linked, BuildID[sha1]=730ca0bd1ce2518e5801b4885445d2a256b5757f, for GNU/Linux 3.2.0, stripped
./bore/bore_riscv64_gcc_Linux:             ELF 64-bit LSB executable, UCB RISC-V, RVC, double-float ABI, version 1 (SYSV), statically linked, BuildID[sha1]=858aa425ba2ebec9631e3a40fc9301006170146b, for GNU/Linux 4.15.0, stripped
./bore/bore_s390x_gcc_Linux:               ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, BuildID[sha1]=0aa40d257a1cd995fc526cbeb05ea6b7b23831b7, for GNU/Linux 3.2.0, stripped
./bore/bore_sparc64_gcc_Linux:             ELF 64-bit MSB executable, SPARC V9, Sun UltraSPARC1 Extensions Required, total store ordering, version 1 (SYSV), statically linked, BuildID[sha1]=015aaf43a502d786d589a573b3f19b4a4f513c8e, for GNU/Linux 3.2.0, stripped
./bore/bore_x86_64_macOS:                  Mach-O 64-bit x86_64 executable, flags:<NOUNDEFS|DYLDLINK|TWOLEVEL|PIE|HAS_TLV_DESCRIPTORS>

--> SHA256SUM
29e15237dab59619a9f91a0505daa20d0a2cbfacafcc4767d39ab9c4144008f0  ./bore/bore_aarch64_arm64_Android
78fe1290f43a0eaffe644feb47aec993d3bd395495a63da5cf6a18dc5f33d614  ./bore/bore_aarch64_arm64_gcc_Linux
93b6777935984502c8a10b61ebf79bc4680254764d1d450083d8b6b2661be099  ./bore/bore_aarch64_arm64_macOS
044136f53c921361c57d67f657ff083fdf8fa80fe2121a1658937455cfe0ad32  ./bore/bore_aarch64_arm64_musl_Linux
00e3c3de987c0962fa634a0f7a256a59a2c0b419ddc402785649a3223244bad5  ./bore/bore_amd_x86_64_Windows.exe
f5e9c68054d585b5393af4d5ce53938ed579b9c59b9a7d66b046766ac213b636  ./bore/bore_amd_x86_64_gcc_Linux
f3dc90c864fbd7b87af0efcd545b18f780ff89f58f26b6b2bd9d694c8983c147  ./bore/bore_amd_x86_64_musl_Linux
49a07c5f64ee8c99b8f4bcc1b9eee897df121ff589a2c8e6a4845bf9d941b8d1  ./bore/bore_amd_x86_Windows.exe
37b5c42ccb2cda3a8b7c511cb45c560f052e7493a3b14b2efdb6806afafb2081  ./bore/bore_amd_x86_i686_gcc_Linux
31970767c06a3b2c064802596716218fc7d09b1ccddd9930b666c6614c5dcb19  ./bore/bore_amd_x86_i686_musl_Linux
6996095f6bea35d9e60b4d14ee429fc856819e01436d64e4a87d9a04324bd664  ./bore/bore_arm_abi_gcc_Linux
dc6dcd5e715c08385ed88c7a39515062cc1a4f692e158cbb56d8a7c1139fe713  ./bore/bore_arm_abi_musl_Linux
4db22e02da21f1e98f87dfff339915fb249d7d27cdbc124d6493c25b99dceae8  ./bore/bore_arm_abihf_gcc_Linux
d1ba840dc657192d8fa00f74872525ff361104c6510a8d7e0c25860994bdf2c2  ./bore/bore_arm_abihf_musl_Linux
a4fdae3ef6c4fd80e3d1ea8e7fe6b2fc4ac534c1926ae35d4fea8f8596a81ab5  ./bore/bore_armv7_abi_Android
dc14b38c79802370437b41546ad0e09a1f329036cdf4419d01428f1eaf5c26ea  ./bore/bore_armv7_abi_gcc_Linux
b327a743dddcb35df4c28c085e33ea1d84b05071bbf38a4f1bdad45dd6daf61c  ./bore/bore_armv7_abi_musl_Linux
08b6485d7eb3b67bd8ec6bf014a1829822c430638b1eb4454debe2a73251c45a  ./bore/bore_armv7_abihf_gcc_Linux
1b1dfa260672a0f14cc15f92a11bd9200b49a37745ea3c0bdd3206e43267e241  ./bore/bore_armv7_abihf_musl_Linux
678822677e9353093b734d5d963ff1eb6e2df35a9a835de699ce765ed54b1abf  ./bore/bore_armv_abi_Android
4f75c984dad2cee327d767b037cfaf64ed9d48362132334c3703dcfdfc047b89  ./bore/bore_i586_gcc_Linux
f7afa3397c5179df56b8e77e9575d28a57e313f3a0196c5ab56094c55d285814  ./bore/bore_i586_musl_Linux
468f263f3896283748b88b39b1e98e792117791c378e10261f9fdb605959fa30  ./bore/bore_i686_Android
4be810533490b43e0fc59bab2132c2485dd4285f6a68f533dfcded726ecbf104  ./bore/bore_mips64_gcc_Linux
07ea5e96766e2b1f35feb1ef823af53adfad22d0e0ad129e94d5db8307b98012  ./bore/bore_mips64_musl_Linux
1b413a2f4186c1c8f48b27ab15cad549c76ef2f4d40084f1936e7cae0fa44407  ./bore/bore_mips64el_gcc_Linux
f1da60bb75107d4ef527c2343a566079f7d8da8559fb409bb4e3393954c8649b  ./bore/bore_mips64el_musl_Linux
8d0a62156bdcf50a0acb4cb5de04e46724ad31b93a2f043b29631b90907e0323  ./bore/bore_mips_gcc_Linux
15f540a27495d8e9afd6ff422e8f6962cb56c6833a32213017ac88efbcbb7ab6  ./bore/bore_mips_musl_Linux
9c6d0da32751dda461276975bce5c11cf373b54a47240f7958e585a66684147b  ./bore/bore_mipsel_gcc_Linux
01b50222959e138d5acffc8ca2c98c450011b82d4630c3767bac4aac4476103c  ./bore/bore_mipsel_musl_Linux
65ad4b03d695708413132fc5d0b8c0a45a4708f059dd5bbc12adbf0e08adb72a  ./bore/bore_powerpc64_ppc64_gcc_Linux
a75d1f9cd2b41dcf863a88c83bb7a7eca4bfa18f904638b10b5cfc72ff6d3524  ./bore/bore_powerpc64le_ppc64le_gcc_Linux
84e1cb313ebc8799f8e225deaf5b857811a4afdaf75c137beb41da136c3b5e7d  ./bore/bore_powerpc_ppc_gcc_Linux
f800ff287ba8d9b02dd0d06b5d2823decfc628cc67084a27cc8630a8e908992f  ./bore/bore_riscv64_gcc_Linux
8ce6dcffcd4062d39754318c6bd85c4c0d548fc1700a0eb7d63c09e1100788f5  ./bore/bore_s390x_gcc_Linux
bd25be5ccffbf6fe0b120623e2648fa32cf7e2b3128516713af99764e708866f  ./bore/bore_sparc64_gcc_Linux
7b40690709b4a458945c9a263bc94e96e7521cd6a854e90b35c0ae8de395fffa  ./bore/bore_x86_64_macOS
```


---

- #### Sizes

```console
1.7M  ./bore/bore_aarch64_arm64_Android
1.8M  ./bore/bore_aarch64_arm64_gcc_Linux
2.4M  ./bore/bore_aarch64_arm64_macOS
1.3M  ./bore/bore_aarch64_arm64_musl_Linux
1.8M  ./bore/bore_amd_x86_64_Windows.exe
2.4M  ./bore/bore_amd_x86_64_gcc_Linux
1.5M  ./bore/bore_amd_x86_64_musl_Linux
1.5M  ./bore/bore_amd_x86_Windows.exe
2.2M  ./bore/bore_amd_x86_i686_gcc_Linux
1.4M  ./bore/bore_amd_x86_i686_musl_Linux
1.7M  ./bore/bore_arm_abi_gcc_Linux
1.3M  ./bore/bore_arm_abi_musl_Linux
1.7M  ./bore/bore_arm_abihf_gcc_Linux
1.3M  ./bore/bore_arm_abihf_musl_Linux
1.2M  ./bore/bore_armv7_abi_Android
1.7M  ./bore/bore_armv7_abi_gcc_Linux
1.3M  ./bore/bore_armv7_abi_musl_Linux
1.6M  ./bore/bore_armv7_abihf_gcc_Linux
1.2M  ./bore/bore_armv7_abihf_musl_Linux
1.6M  ./bore/bore_armv_abi_Android
2.2M  ./bore/bore_i586_gcc_Linux
1.4M  ./bore/bore_i586_musl_Linux
2.0M  ./bore/bore_i686_Android
2.3M  ./bore/bore_mips64_gcc_Linux
1.8M  ./bore/bore_mips64_musl_Linux
2.3M  ./bore/bore_mips64el_gcc_Linux
1.8M  ./bore/bore_mips64el_musl_Linux
2.3M  ./bore/bore_mips_gcc_Linux
1.9M  ./bore/bore_mips_musl_Linux
2.3M  ./bore/bore_mipsel_gcc_Linux
1.8M  ./bore/bore_mipsel_musl_Linux
2.5M  ./bore/bore_powerpc64_ppc64_gcc_Linux
2.5M  ./bore/bore_powerpc64le_ppc64le_gcc_Linux
2.2M  ./bore/bore_powerpc_ppc_gcc_Linux
1.7M  ./bore/bore_riscv64_gcc_Linux
2.1M  ./bore/bore_s390x_gcc_Linux
2.0M  ./bore/bore_sparc64_gcc_Linux
2.4M  ./bore/bore_x86_64_macOS
```

---

- #### Version
```console

$ ./bore/bore_amd_x86_64_musl_Linux --version
bore-cli 0.5.3

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


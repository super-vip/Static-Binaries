
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
./bore/bore_aarch64_arm64_gcc_Linux:       ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, BuildID[sha1]=140dda75a686576a71966401f5c2c79a6d793e8f, for GNU/Linux 3.7.0, stripped
./bore/bore_aarch64_arm64_macOS:           Mach-O 64-bit arm64 executable, flags:<NOUNDEFS|DYLDLINK|TWOLEVEL|PIE|HAS_TLV_DESCRIPTORS>
./bore/bore_aarch64_arm64_musl_Linux:      ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, stripped
./bore/bore_amd_x86_64_Windows.exe:        PE32+ executable (console) x86-64 (stripped to external PDB), for MS Windows
./bore/bore_amd_x86_64_gcc_Linux:          ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), static-pie linked, BuildID[sha1]=1fef38d4c9c25248ff9a0da06617f758a34e16c8, for GNU/Linux 3.2.0, stripped
./bore/bore_amd_x86_64_musl_Linux:         ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), static-pie linked, stripped
./bore/bore_amd_x86_Windows.exe:           PE32 executable (console) Intel 80386 (stripped to external PDB), for MS Windows
./bore/bore_amd_x86_i686_gcc_Linux:        ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, BuildID[sha1]=411dfb74a76e2e528d3cdb563995ec2f7cdfdbd8, for GNU/Linux 3.2.0, stripped
./bore/bore_amd_x86_i686_musl_Linux:       ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, stripped
./bore/bore_arm_abi_gcc_Linux:             ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, BuildID[sha1]=d3d57a1b3632fc686772d673e871074ca3b0068b, for GNU/Linux 3.2.0, stripped
./bore/bore_arm_abi_musl_Linux:            ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, stripped
./bore/bore_arm_abihf_gcc_Linux:           ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, for GNU/Linux 4.19.255, stripped
./bore/bore_arm_abihf_musl_Linux:          ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, stripped
./bore/bore_armv7_abi_Android:             ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, stripped
./bore/bore_armv7_abi_gcc_Linux:           ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, BuildID[sha1]=0664e9ae092ad2fbbb49ba8d3e3946f9c838e382, for GNU/Linux 3.2.0, stripped
./bore/bore_armv7_abi_musl_Linux:          ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, stripped
./bore/bore_armv7_abihf_gcc_Linux:         ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, BuildID[sha1]=dadccc6080b9a63c2e85f7c452a076ee1b4d020f, for GNU/Linux 3.2.0, stripped
./bore/bore_armv7_abihf_musl_Linux:        ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, stripped
./bore/bore_armv_abi_Android:              ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, stripped
./bore/bore_i586_gcc_Linux:                ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, BuildID[sha1]=36c2e04d689f0597dd2c6caa886a917d63517627, for GNU/Linux 3.2.0, stripped
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
./bore/bore_powerpc64_ppc64_gcc_Linux:     ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, BuildID[sha1]=5bb637a5c2d9171210f4efa7fd9763de9942b77c, for GNU/Linux 3.2.0, stripped
./bore/bore_powerpc64le_ppc64le_gcc_Linux: ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, BuildID[sha1]=6dd323b0278b7626546ae273c74f234d97727434, for GNU/Linux 3.10.0, stripped
./bore/bore_powerpc_ppc_gcc_Linux:         ELF 32-bit MSB executable, PowerPC or cisco 4500, version 1 (SYSV), statically linked, BuildID[sha1]=27ef503fea284a5143862cdc43fb592411398b73, for GNU/Linux 3.2.0, stripped
./bore/bore_riscv64_gcc_Linux:             ELF 64-bit LSB executable, UCB RISC-V, RVC, double-float ABI, version 1 (SYSV), statically linked, BuildID[sha1]=051d68d9eee58e9a4877f9e5852d408a3b3c565f, for GNU/Linux 4.15.0, stripped
./bore/bore_s390x_gcc_Linux:               ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, BuildID[sha1]=8850bd4ecfbf9076db595f3910a0354cae680993, for GNU/Linux 3.2.0, stripped
./bore/bore_sparc64_gcc_Linux:             ELF 64-bit MSB executable, SPARC V9, Sun UltraSPARC1 Extensions Required, total store ordering, version 1 (SYSV), statically linked, BuildID[sha1]=04d6de5434f0466daf46ebfb7030aa5959a1408a, for GNU/Linux 3.2.0, stripped
./bore/bore_x86_64_macOS:                  Mach-O 64-bit x86_64 executable, flags:<NOUNDEFS|DYLDLINK|TWOLEVEL|PIE|HAS_TLV_DESCRIPTORS>

--> SHA256SUM
b515bb8604e13d1aac380e9dd9ad240618aa6ae081dc19170754b24184024482  ./bore/bore_aarch64_arm64_Android
08071fc85223da6e2a24ec29ae279f9c8049f07a4aca0622c772e301bfb4a9f1  ./bore/bore_aarch64_arm64_gcc_Linux
6b6d909d31f362f21b2c5d604b54937c6fcfbb8e4ba13a04d1586e393444bc8a  ./bore/bore_aarch64_arm64_macOS
3371dc3873283e40a281e2ea762ee43007144b3ec54eab2b4e9454f421a7d5a9  ./bore/bore_aarch64_arm64_musl_Linux
d906433f66ff4ac55c55db3ffa24ca41975e46582bddb46765b0678b67c1ef89  ./bore/bore_amd_x86_64_Windows.exe
4b6847aef7ce70f9b2cbb232a4b997d76b00ec6c6013c87816a2e88ba2cda50f  ./bore/bore_amd_x86_64_gcc_Linux
d51656fc73940e8c1c6be7660187115ce682296ea00f97ebeabc500361b65984  ./bore/bore_amd_x86_64_musl_Linux
c23c06d121434fcd68d571c93c5e1874707f93057e9c63958d7918a785eed882  ./bore/bore_amd_x86_Windows.exe
ce24005bcc6969db1d6bd15c4b0c062b0677e13b3a58326d5944c991b6c3a1b9  ./bore/bore_amd_x86_i686_gcc_Linux
caa1673108b7ebd2941c89b339433b9692a7cf63f6935b33d2feb5a7318944a6  ./bore/bore_amd_x86_i686_musl_Linux
3acb1026ebeca6831ce0a2d25a80dca2cd440df3d51bc97f048ec6d9a22692bd  ./bore/bore_arm_abi_gcc_Linux
ef389ea54c7f152c9825e9c32f8eb6cf2a199a5202dec382dd94e9441bd9a38f  ./bore/bore_arm_abi_musl_Linux
fff35e348c85579ac779955dadd1287a4070f24ce3b9aba02c67e38294c8bb03  ./bore/bore_arm_abihf_gcc_Linux
c5543119115373144ea716442b881dbfa55b5e7ea2e3dae8c9a06db74849f413  ./bore/bore_arm_abihf_musl_Linux
9bc35e79338c15f4b8cd38896dec3158eb8a5889dab0a06d9f11eaa91585f368  ./bore/bore_armv7_abi_Android
bed50b3686dbb7840e08475d0b62cf9981feaa4f5dcd3d2379ade5b8e8d39b71  ./bore/bore_armv7_abi_gcc_Linux
9db99c3c4c60c3338ed290206ff2f0b35f62d1e0153654fdd569f1622461d366  ./bore/bore_armv7_abi_musl_Linux
cc490a3947c9b853a41f644b6eefef441c457801d15358ef44bba35336478bdd  ./bore/bore_armv7_abihf_gcc_Linux
afd43c1ee13e20a7b83c466dd7634e3dd35c584159706f071ea99192afc09c7a  ./bore/bore_armv7_abihf_musl_Linux
c4ba69dfc2f182119a658a7983af04a8c9eb875135ef3dabdae0fa366becf8c3  ./bore/bore_armv_abi_Android
13f2e6b4671d0e8627a907b482382f7219376e87fa1602d12449cc5279edb3ef  ./bore/bore_i586_gcc_Linux
8c8d5d4192f33669832aa22c98d69c91911af7936405fc5ff2468e0aa238b591  ./bore/bore_i586_musl_Linux
4c2b7846a22356ade1c3000583ea3af337a7223d70e833ff4e642e995ba0a74c  ./bore/bore_i686_Android
4be810533490b43e0fc59bab2132c2485dd4285f6a68f533dfcded726ecbf104  ./bore/bore_mips64_gcc_Linux
07ea5e96766e2b1f35feb1ef823af53adfad22d0e0ad129e94d5db8307b98012  ./bore/bore_mips64_musl_Linux
1b413a2f4186c1c8f48b27ab15cad549c76ef2f4d40084f1936e7cae0fa44407  ./bore/bore_mips64el_gcc_Linux
f1da60bb75107d4ef527c2343a566079f7d8da8559fb409bb4e3393954c8649b  ./bore/bore_mips64el_musl_Linux
8d0a62156bdcf50a0acb4cb5de04e46724ad31b93a2f043b29631b90907e0323  ./bore/bore_mips_gcc_Linux
15f540a27495d8e9afd6ff422e8f6962cb56c6833a32213017ac88efbcbb7ab6  ./bore/bore_mips_musl_Linux
9c6d0da32751dda461276975bce5c11cf373b54a47240f7958e585a66684147b  ./bore/bore_mipsel_gcc_Linux
01b50222959e138d5acffc8ca2c98c450011b82d4630c3767bac4aac4476103c  ./bore/bore_mipsel_musl_Linux
38371e8169bab65c725e5425e214ad247e06850b8b4f7e4a19e7e540bb11d4f0  ./bore/bore_powerpc64_ppc64_gcc_Linux
e5095a803418ab3e6ade2a476ade9422b38124ec57e766bd43309a6d8a93bdb0  ./bore/bore_powerpc64le_ppc64le_gcc_Linux
376e4f3e403d0b624695d1a8b593b5fd831019a79c0d793291bb2fc3fc4972b4  ./bore/bore_powerpc_ppc_gcc_Linux
1c7cad7c732e24ac7c0a4fed9364ac04c59d9c374e8a7ce5b4bc08a8233f64f4  ./bore/bore_riscv64_gcc_Linux
f07323f79a0cfcfff2c2bb124e83f2b54716aaaad9e0050a51a3cb9b183059e2  ./bore/bore_s390x_gcc_Linux
066818828bb672c6ccff3bbac392d196b9616df47642aeb5290c9551df0ac97a  ./bore/bore_sparc64_gcc_Linux
2be7379207f6c4823866657b69a325a3f094fa703de81bbe9e246c6034fa67ed  ./bore/bore_x86_64_macOS
```


---

- #### Sizes

```console
1.6M  ./bore/bore_aarch64_arm64_Android
1.8M  ./bore/bore_aarch64_arm64_gcc_Linux
2.4M  ./bore/bore_aarch64_arm64_macOS
1.3M  ./bore/bore_aarch64_arm64_musl_Linux
1.7M  ./bore/bore_amd_x86_64_Windows.exe
2.4M  ./bore/bore_amd_x86_64_gcc_Linux
1.5M  ./bore/bore_amd_x86_64_musl_Linux
1.5M  ./bore/bore_amd_x86_Windows.exe
2.2M  ./bore/bore_amd_x86_i686_gcc_Linux
1.4M  ./bore/bore_amd_x86_i686_musl_Linux
1.7M  ./bore/bore_arm_abi_gcc_Linux
1.3M  ./bore/bore_arm_abi_musl_Linux
1.7M  ./bore/bore_arm_abihf_gcc_Linux
1.3M  ./bore/bore_arm_abihf_musl_Linux
1.1M  ./bore/bore_armv7_abi_Android
1.7M  ./bore/bore_armv7_abi_gcc_Linux
1.2M  ./bore/bore_armv7_abi_musl_Linux
1.6M  ./bore/bore_armv7_abihf_gcc_Linux
1.2M  ./bore/bore_armv7_abihf_musl_Linux
1.4M  ./bore/bore_armv_abi_Android
2.2M  ./bore/bore_i586_gcc_Linux
1.4M  ./bore/bore_i586_musl_Linux
1.8M  ./bore/bore_i686_Android
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
1.6M  ./bore/bore_riscv64_gcc_Linux
2.1M  ./bore/bore_s390x_gcc_Linux
2.1M  ./bore/bore_sparc64_gcc_Linux
2.4M  ./bore/bore_x86_64_macOS
```

---

- #### Version
```console

$ ./bore/bore_amd_x86_64_musl_Linux --version
bore-cli 0.5.1

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


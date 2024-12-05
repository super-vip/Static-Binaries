
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
./bore/bore_aarch64_arm64_gcc_Linux:       ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, BuildID[sha1]=ffdd38f5da1305b5f24d308eef0b255ae5cf96a2, for GNU/Linux 3.7.0, stripped
./bore/bore_aarch64_arm64_macOS:           Mach-O 64-bit arm64 executable, flags:<NOUNDEFS|DYLDLINK|TWOLEVEL|PIE|HAS_TLV_DESCRIPTORS>
./bore/bore_aarch64_arm64_musl_Linux:      ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, stripped
./bore/bore_amd_x86_64_Windows.exe:        PE32+ executable (console) x86-64 (stripped to external PDB), for MS Windows
./bore/bore_amd_x86_64_gcc_Linux:          ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), static-pie linked, BuildID[sha1]=cc062d09098eef51156fe4b2069aab8e957b4c8a, for GNU/Linux 3.2.0, stripped
./bore/bore_amd_x86_64_musl_Linux:         ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), static-pie linked, stripped
./bore/bore_amd_x86_Windows.exe:           PE32 executable (console) Intel 80386 (stripped to external PDB), for MS Windows
./bore/bore_amd_x86_i686_gcc_Linux:        ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, BuildID[sha1]=545f70d97a87441d5052ca003f516513570607ed, for GNU/Linux 3.2.0, stripped
./bore/bore_amd_x86_i686_musl_Linux:       ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, stripped
./bore/bore_arm_abi_gcc_Linux:             ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, BuildID[sha1]=b170aca0d7c0bc87923000b7e2221a7a0b8bf3a5, for GNU/Linux 3.2.0, stripped
./bore/bore_arm_abi_musl_Linux:            ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, stripped
./bore/bore_arm_abihf_gcc_Linux:           ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, for GNU/Linux 4.19.255, stripped
./bore/bore_arm_abihf_musl_Linux:          ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, stripped
./bore/bore_armv7_abi_Android:             ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, stripped
./bore/bore_armv7_abi_gcc_Linux:           ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, BuildID[sha1]=7b9cc9fefea0404fb7ff0397d956bee7ffb88dbf, for GNU/Linux 3.2.0, stripped
./bore/bore_armv7_abi_musl_Linux:          ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, stripped
./bore/bore_armv7_abihf_gcc_Linux:         ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, BuildID[sha1]=cfca79b4d16bd820788ac361c2bd8facdbbbb3fc, for GNU/Linux 3.2.0, stripped
./bore/bore_armv7_abihf_musl_Linux:        ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, stripped
./bore/bore_armv_abi_Android:              ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, stripped
./bore/bore_i586_gcc_Linux:                ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, BuildID[sha1]=c48bb75e3ac95e31a24a5706c7e20e281d868ca8, for GNU/Linux 3.2.0, stripped
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
./bore/bore_powerpc64_ppc64_gcc_Linux:     ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, BuildID[sha1]=522885d2c235a3213f37496b1549ab1703ec3771, for GNU/Linux 3.2.0, stripped
./bore/bore_powerpc64le_ppc64le_gcc_Linux: ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, BuildID[sha1]=a52a5cb87a2bc781d474c16d877bea55afc12977, for GNU/Linux 3.10.0, stripped
./bore/bore_powerpc_ppc_gcc_Linux:         ELF 32-bit MSB executable, PowerPC or cisco 4500, version 1 (SYSV), statically linked, BuildID[sha1]=8424e1c30017b7537f3a1b1dbe4f03f2c56fbad8, for GNU/Linux 3.2.0, stripped
./bore/bore_riscv64_gcc_Linux:             ELF 64-bit LSB executable, UCB RISC-V, RVC, double-float ABI, version 1 (SYSV), statically linked, BuildID[sha1]=026284dee7eaa9a1db34776129a71b1123199197, for GNU/Linux 4.15.0, stripped
./bore/bore_s390x_gcc_Linux:               ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, BuildID[sha1]=3dc0e5d6a6ac1bc4fa6627878c53af2b60d218e3, for GNU/Linux 3.2.0, stripped
./bore/bore_sparc64_gcc_Linux:             ELF 64-bit MSB executable, SPARC V9, Sun UltraSPARC1 Extensions Required, total store ordering, version 1 (SYSV), statically linked, BuildID[sha1]=263d65902ada333a41b5f69534bd7b4d48a26755, for GNU/Linux 3.2.0, stripped
./bore/bore_x86_64_macOS:                  Mach-O 64-bit x86_64 executable, flags:<NOUNDEFS|DYLDLINK|TWOLEVEL|PIE|HAS_TLV_DESCRIPTORS>

--> SHA256SUM
024113e40bb4f937dc57560492f30dcca64bc3e599c67f3ad945e860be1150a7  ./bore/bore_aarch64_arm64_Android
c8180d8837142c3c858d48bc8ad5ab5f83357326aac6c32d6a3f7452919d67c4  ./bore/bore_aarch64_arm64_gcc_Linux
93b6777935984502c8a10b61ebf79bc4680254764d1d450083d8b6b2661be099  ./bore/bore_aarch64_arm64_macOS
631e33d28939c68d775c11df5e65e396106f9413bb3c5fc30cc66b67cd687622  ./bore/bore_aarch64_arm64_musl_Linux
00e3c3de987c0962fa634a0f7a256a59a2c0b419ddc402785649a3223244bad5  ./bore/bore_amd_x86_64_Windows.exe
1addf8f6b713642d709f08b92d1c13edf55882a8fffba8ba048be1cf88c1978a  ./bore/bore_amd_x86_64_gcc_Linux
66ccb41fcfce7e9e3e5d776b44ad4ba1633917b065f725c9392082f82dd17d3f  ./bore/bore_amd_x86_64_musl_Linux
49a07c5f64ee8c99b8f4bcc1b9eee897df121ff589a2c8e6a4845bf9d941b8d1  ./bore/bore_amd_x86_Windows.exe
3f20a8e70a73b936dcb2eaa11035ac1021da1d9446656c9f33372cdd768af564  ./bore/bore_amd_x86_i686_gcc_Linux
7e025d5c738995ab3de4170fcc6ab551f1f076310b8f5feb69c20458f49dfdc6  ./bore/bore_amd_x86_i686_musl_Linux
fa4f1e0181e72a4811be376b3b6f267201b20531302df1e340eac4d26e5fd867  ./bore/bore_arm_abi_gcc_Linux
1d2797b9cc67ca1b831cb9215629e72e1abd04819f12b55e789ae589abf4aae2  ./bore/bore_arm_abi_musl_Linux
d3ada4f4ba4776bd78eec6734814929b2e37dfd23816e0cebe89b48715278afc  ./bore/bore_arm_abihf_gcc_Linux
91c1735b33e514eed57e4c0b778930f61448208c328c227e6243c59a84bfb24d  ./bore/bore_arm_abihf_musl_Linux
fb5513359567d8b96a3216cb2e742b0c8efe781c70c7d29a6a04bbdfbb320c54  ./bore/bore_armv7_abi_Android
91ac87e7e18cfe47604bca3b68c6ea79a53f887a07139c6455b618eb1d5fe82f  ./bore/bore_armv7_abi_gcc_Linux
e1d4374a37d2db4b92bb9d58ec1712dc002cf4b0d7ac86e5f237b39dc10fe1b9  ./bore/bore_armv7_abi_musl_Linux
cbbfebfb9ee31ca4f64f45793ef91afe2a4f607e8ae9c152ca685fc3bed484b1  ./bore/bore_armv7_abihf_gcc_Linux
d2e37b19c9dce9635aa959c9a648ae1f2554c5480e412f6787f58ad5fca0ed63  ./bore/bore_armv7_abihf_musl_Linux
3d7151f335d12283c2a5ed087b79bf1d2a327fde0e42f70c3bfb40569fe4d59a  ./bore/bore_armv_abi_Android
a21821ca08ded36af7ca1bd58404a84fc96dd2cf1c99f7dd57db56a570423211  ./bore/bore_i586_gcc_Linux
7c307197c6a1d2b6d7eaa623752cfc6544c582b893beaf57c7bc1604e7eb3aa7  ./bore/bore_i586_musl_Linux
68c3fc0dc99e9d6f8faeb359e03fe7bc577cf45a949036b7614e48c1b4ea9831  ./bore/bore_i686_Android
4be810533490b43e0fc59bab2132c2485dd4285f6a68f533dfcded726ecbf104  ./bore/bore_mips64_gcc_Linux
07ea5e96766e2b1f35feb1ef823af53adfad22d0e0ad129e94d5db8307b98012  ./bore/bore_mips64_musl_Linux
1b413a2f4186c1c8f48b27ab15cad549c76ef2f4d40084f1936e7cae0fa44407  ./bore/bore_mips64el_gcc_Linux
f1da60bb75107d4ef527c2343a566079f7d8da8559fb409bb4e3393954c8649b  ./bore/bore_mips64el_musl_Linux
8d0a62156bdcf50a0acb4cb5de04e46724ad31b93a2f043b29631b90907e0323  ./bore/bore_mips_gcc_Linux
15f540a27495d8e9afd6ff422e8f6962cb56c6833a32213017ac88efbcbb7ab6  ./bore/bore_mips_musl_Linux
9c6d0da32751dda461276975bce5c11cf373b54a47240f7958e585a66684147b  ./bore/bore_mipsel_gcc_Linux
01b50222959e138d5acffc8ca2c98c450011b82d4630c3767bac4aac4476103c  ./bore/bore_mipsel_musl_Linux
34b9183b41aee2cb1cb38b90c446ae326e1536f93247a59131a1a30254475f79  ./bore/bore_powerpc64_ppc64_gcc_Linux
55195d40afa2d0ff2f023c45898eb15ffaaa028092193f2871b19eef4515b9dc  ./bore/bore_powerpc64le_ppc64le_gcc_Linux
67afaa119e460b3164fc125b584bc2e3013c93ff7c31c4dcacfdf85d8689a710  ./bore/bore_powerpc_ppc_gcc_Linux
516bd2df4f7eeed7f1d550c2ad9eed54d92a976d15f4881f886ef8a5e41d408e  ./bore/bore_riscv64_gcc_Linux
871c3862e34f6b59996f9a8f4b514070fe471439576a5d1d1694fb5b9596d03b  ./bore/bore_s390x_gcc_Linux
4deceea0ebf53a3d720d8dc426c7131e915018582239910facba02e12ae4af67  ./bore/bore_sparc64_gcc_Linux
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
1.2M  ./bore/bore_arm_abihf_musl_Linux
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
2.4M  ./bore/bore_powerpc64_ppc64_gcc_Linux
2.4M  ./bore/bore_powerpc64le_ppc64le_gcc_Linux
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
bore-cli 0.5.2

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



---
- #### Download [ngrok](https://ngrok.com/download)
> - **Sources**
> > ```bash
> > --> FreeBSD || Linux || Solaris || Windows:
> >      - https://ngrok.com/download
> > ```
> >
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

!# FreeBSD
--> 386 || Amd x86|| x86 [32-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/ngrok/ngrok_386_FreeBSD"
--> Amd x86_64 || x86_64 [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/ngrok/ngrok_amd_x86_64_FreeBSD"

!# Linux
--> aarch64 || arm64 [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/ngrok/ngrok_aarch64_arm64_Linux"
--> Amd x86_64 || x86_64 [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/ngrok/ngrok_amd_x86_64_Linux"
--> ARM_abi || ARMv4 || ARMv5 || ARMv7 (?) [32-bit]
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/ngrok/ngrok_arm_Linux"
--> i386 || Intel 80386 [32-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/ngrok/ngrok_i386_Linux"
--> MIPS (Big-Endian) [32-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/ngrok/ngrok_mips_Linux"
--> MIPSel || MIPSle (Little-Endian) [32-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/ngrok/ngrok_mipsle_Linux"
--> MIPS64 (Big-Endian) [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/ngrok/ngrok_mips64_Linux"
--> MIPS64le (Little-Endian) [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/ngrok/ngrok_mips64le_Linux"
--> powerpc64|| ppc64 || cisco 7500 [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/ngrok/ngrok_powerpc64_Linux"
--> powerpc64le || ppc64le || cisco 7500 || OpenPOWER ELF V2 ABI (Little-Endian) [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/ngrok/ngrok_powerpc64le_Linux"
--> s390x || IBM S/390 [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/ngrok/ngrok_s390x_Linux"

!# macOS
--> aarch64 || arm64
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/ngrok/ngrok_aarch64_arm64_macOS"
--> Amd x86_64 || x86_64
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/ngrok/ngrok_x86_64_macOS"


!# Solaris
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/ngrok/ngrok_amd_x86_64_Solaris"

#Windows
--> Amd_x86 || x86 [32-bit]
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/ngrok/ngrok_amd_x86_Windows.exe"
--> Amd x86_64 || x86_64 [64-bit]
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/ngrok/ngrok_amd_x86_64_Windows.exe"

```
---
- #### Install ngrok
```bash
!# Recommended way to install ngrok is:
!# Download a binary from : https://ngrok.com/download
!# unzip it 
tar -xzvf "$Path_To_ngrok_Binary.tgz"

!# Copy downloaded ngrok binaries to /usr/bin || /usr/local/bin
!# For $HOME/bin
 mkdir -p "$HOME/bin" && export PATH="$HOME/bin:$PATH"

!# Move Downloaded ngrok binaries to that DIR
 mv "$Path_To_ngrok_Binary" "/usr/bin/ngrok"

!# Give Writeable Perms
 chmod +xwr /usr/bin/ngrok*
```

---
```console

--> METADATA
./ngrok/ngrok_386_FreeBSD:            ELF 32-bit LSB executable, Intel 80386, version 1 (FreeBSD), statically linked, for FreeBSD 12.3, FreeBSD-style, Go BuildID=mr99Vf4KoEx25a2TjBys/y3oW-D2b5xJMgR0k12nU/PJ7xIz6hp6Hazbukk3wi/pDLuAnmQ6S7wTLbrT3XB, stripped
./ngrok/ngrok_aarch64_arm64_Linux:    ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=mCM9GX231I48SlLqR2ro/R7YF4ThQqJeFTaylnRcP/zym8CJ6W4N7Q3PifWodN/5eCmOi2ANeCf82M3LxDW, stripped
./ngrok/ngrok_aarch64_arm64_macOS:    Mach-O 64-bit arm64 executable, flags:<NOUNDEFS|DYLDLINK|TWOLEVEL|PIE>
./ngrok/ngrok_amd_x86_64_FreeBSD:     ELF 64-bit LSB executable, x86-64, version 1 (FreeBSD), statically linked, for FreeBSD 12.3, FreeBSD-style, Go BuildID=rFDTAP4xNO0oAqgBniPv/-Eh5eRg4bGyWINchSZac/VG89ejHFXdud3U0nv4Lr/PwmuVQYuQN3CMYqZTzPK, stripped
./ngrok/ngrok_amd_x86_64_Linux:       ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=vcKSX2fCzUGt8QQJpQaQ/Ae-TGNrTdBitBJQyYXAP/opj42nxcJMU-sAMos3ag/nLLnrEgQCgtsYhK8yS4I, stripped
./ngrok/ngrok_amd_x86_64_Solaris:     ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib/amd64/ld.so.1, Go BuildID=o7hxUnFJXIyHVtL_Ectm/-GS9iv9PxSttrhv73Jii/ds2-RLExHX4zL-6OCAsw/KWLgeJo5i__z-ISEX_kO, stripped
./ngrok/ngrok_amd_x86_64_Windows.exe: PE32+ executable (console) x86-64 (stripped to external PDB), for MS Windows
./ngrok/ngrok_amd_x86_64_macOS:       Mach-O 64-bit x86_64 executable, flags:<NOUNDEFS|DYLDLINK|TWOLEVEL|PIE>
./ngrok/ngrok_amd_x86_Windows.exe:    PE32 executable (console) Intel 80386 (stripped to external PDB), for MS Windows
./ngrok/ngrok_arm_FreeBSD:            ELF 32-bit LSB executable, ARM, EABI5 version 1 (FreeBSD), statically linked, for FreeBSD 12.3, FreeBSD-style, Go BuildID=j5Ce9A45sa9ckIJ-oYBS/oWVMNHtf2RDLC4eGHmEP/FNNvzet3ECdAAWd18Ckc/_S29303ptT_ROmjMAAQo, stripped
./ngrok/ngrok_arm_Linux:              ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=h-WJywPp6Qr74_DRpjtz/LhjUav-sqGrX0QnGctMY/mF_QCQQFAqQW0X4c6z9v/Q8LYSj4rN1Qw8bae73Y1, stripped
./ngrok/ngrok_i386_Linux:             ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=a7Gb0aMwtWt0QdfpNfQW/rBhBPz3Tq9-9pqhKAadm/pxbhXV-66t8d6-HcKIVv/Vef1oJcW2oJrQSSPd408, stripped
./ngrok/ngrok_mips64_Linux:           ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=eawoGkbzrS-NFDQButVb/3aBXKLlgpASUtRnKw2-z/O6ZzggMplvorn2MXCHML/wA_aeF6ZUPD2THKp24Ag, stripped
./ngrok/ngrok_mips64le_Linux:         ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=X_7P8hP8Af8zhCWHSyCp/VFlO4RpwkGYRCvTZsOlZ/xYbTklyVpxkROJqKFXNo/3p8FQD-1ZuAGwV7sFdGa, stripped
./ngrok/ngrok_mips_Linux:             ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=FiEbmlXHP1cqf8C28VsV/qcZjKMeEOFuCuBN5MesM/DHAa4DM-Hs7uWQHpqxp4/IVRYsJsgUItWXlo0bqNH, stripped
./ngrok/ngrok_mipsle_Linux:           ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=yfmH4KN1NEBCuazh5Av3/V0CJbIIk9ZRzeYE3CA63/Td6q2Tmm5-B77gcqBQWm/_2pUGEV_StlREO23Zho7, stripped
./ngrok/ngrok_powerpc64_Linux:        ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, Go BuildID=pjIEbv-l3MZx7o-J1yHk/etTejGEx8__R4RnBQfzY/Ms69MGoEkdsbsnZF2dQW/CQFaaM4ZDkhITomejZAA, stripped
./ngrok/ngrok_powerpc64le_Linux:      ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, Go BuildID=L_3uEmf7G2zXE63YQl3l/YYBHl93q7w_Arb8rDzU3/_rlBC1mtd5iXge_y9NEB/K0eqsGALo7B789AVVLZ3, stripped
./ngrok/ngrok_s390x_Linux:            ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, Go BuildID=QQPn6FE0UW4FLVzaeIpo/AtYBMFxUWrSkFZUHF0MA/XOEcmtOOC1dnOZkoQSnM/t8Z9Jm8mnV0aWBtUEL8F, stripped

--> SHA256SUM
c6b61eb8b66dc23ec1cafde4a248458d5fa95f439789c0ef869e6255c716572e  ./ngrok/ngrok_386_FreeBSD
4c04662def82cef26e3a38e88001fcd13b6b33695fbd19fe4ac554aad5b82764  ./ngrok/ngrok_aarch64_arm64_Linux
033862d18743c1e168328b25ca0b224b1e12cc11625b49027b57448eb4bcb1e3  ./ngrok/ngrok_aarch64_arm64_macOS
02658a91e6a26c740626998621e7a6081e4b333ab7ce0a072d0d74a7175a7562  ./ngrok/ngrok_amd_x86_64_FreeBSD
f029ebcf23ff7a4c693c50819336f695119399683c25eb884967b04d1a27e4a5  ./ngrok/ngrok_amd_x86_64_Linux
7ed5c035e811314e5ed541c00ce8a9b95e83841b54d3d77c2a015a1a5970e10a  ./ngrok/ngrok_amd_x86_64_Solaris
400b283a4499d7181588247665974a64b9ae9e67c6fd9c3ab9129a3de8b5d66c  ./ngrok/ngrok_amd_x86_64_Windows.exe
06b7ac5597cf5c9ff2bba4ae09884e451a2c0fa2fcfd35d582704c30feca8726  ./ngrok/ngrok_amd_x86_64_macOS
0d4170ea9489e59effbdec4fa2712c40541c3881f5f07e7db47c7a48f12b8674  ./ngrok/ngrok_amd_x86_Windows.exe
fa4754faed0f77608004f93f5ffab1d856784022bf4e393c1a91b2a2b63ab422  ./ngrok/ngrok_arm_FreeBSD
745f35034b3739027a0119701828f9edd6fa162f0eccc4ce803db81a2c691bb1  ./ngrok/ngrok_arm_Linux
c9c251541dd074ef2e9b195e17f137c7599506266acafbf781d3e9f3bdd7dbbc  ./ngrok/ngrok_i386_Linux
8fb68962d57e6f302fd6d67f354b09f96ef5245535ed9fc17e19213bd0ab6ed3  ./ngrok/ngrok_mips64_Linux
95ddea90d59f92f7647cbcc6acfce0e33d9e68f4498aa2850be5fad2e5dcf816  ./ngrok/ngrok_mips64le_Linux
0fc72a8ada9801518ff02c2417b877b350540f8d9c29822bb26a410affe10abd  ./ngrok/ngrok_mips_Linux
57d9f961033181c4f753b2e02a7f61aeaae3d7658d6e17775004f0e6cc402400  ./ngrok/ngrok_mipsle_Linux
0330d9af20c89d96db0ab68b287a12d37a606c843927a5f313d4e6e8cbcd5ba1  ./ngrok/ngrok_powerpc64_Linux
c693fe6569a6870fd45d2f88d3057f414b5a05c9b5c5ed92b7a1338a93658a7a  ./ngrok/ngrok_powerpc64le_Linux
1760c0a4f794ce8bf462449b81ecc3b3eb40fddbad7aa0a52959ad19913cf14b  ./ngrok/ngrok_s390x_Linux
```


---

- #### Version
```console
ngrok version 3.16.1

NAME:
  ngrok - tunnel local ports to public URLs and inspect traffic

USAGE:
  ngrok [command] [flags]

DESCRIPTION: 
  ngrok exposes local networked services behinds NATs and firewalls to the
  public internet over a secure tunnel. Share local websites, build/test
  webhook consumers and self-host personal services.
  Detailed help for each command is available with 'ngrok help <command>'.
  Open https://dashboard.ngrok.com/obs/traffic-inspector to inspect traffic.

Author:
  ngrok - <support@ngrok.com>

TERMS OF SERVICE: https://ngrok.com/tos

EXAMPLES: 
  ngrok http 80                           # secure public URL for port 80 web server
  ngrok http --url baz.ngrok.dev 8080     # port 8080 available at baz.ngrok.dev
  ngrok http foo.dev:80                   # tunnel to host:port instead of localhost
  ngrok http https://localhost            # expose a local https server
  ngrok tcp 22                            # tunnel arbitrary TCP traffic to port 22
  ngrok tls --url=foo.com 443             # TLS traffic for foo.com to port 443
  ngrok start foo bar baz                 # start tunnels from the configuration file

COMMANDS:
  api                            use ngrok agent as an api client
  completion                     generates shell completion code for bash or zsh
  config                         update or migrate ngrok's configuration file
  credits                        prints author and licensing information
  diagnose                       diagnose connection issues
  help                           Help about any command
  http                           start an HTTP tunnel
  service                        run and control an ngrok service on a target operating system
  start                          start endpoints or tunnels by name from the configuration file
  tcp                            start a TCP tunnel
  tls                            start a TLS tunnel
  tunnel                         start a tunnel for use with a tunnel-group backend
  update                         update ngrok to the latest version
  version                        print the version string

OPTIONS:
      --config strings    path to config files; they are merged if multiple
  -h, --help              help for ngrok
      --metadata string   opaque user-defined metadata for the tunnel session
  -v, --version           version for ngrok
```

---

- #### Sizes

```console
24M  ./ngrok/ngrok_386_FreeBSD
26M  ./ngrok/ngrok_aarch64_arm64_Linux
26M  ./ngrok/ngrok_aarch64_arm64_macOS
26M  ./ngrok/ngrok_amd_x86_64_FreeBSD
26M  ./ngrok/ngrok_amd_x86_64_Linux
26M  ./ngrok/ngrok_amd_x86_64_Solaris
27M  ./ngrok/ngrok_amd_x86_64_Windows.exe
26M  ./ngrok/ngrok_amd_x86_64_macOS
25M  ./ngrok/ngrok_amd_x86_Windows.exe
25M  ./ngrok/ngrok_arm_FreeBSD
25M  ./ngrok/ngrok_arm_Linux
25M  ./ngrok/ngrok_i386_Linux
28M  ./ngrok/ngrok_mips64_Linux
28M  ./ngrok/ngrok_mips64le_Linux
28M  ./ngrok/ngrok_mips_Linux
28M  ./ngrok/ngrok_mipsle_Linux
26M  ./ngrok/ngrok_powerpc64_Linux
26M  ./ngrok/ngrok_powerpc64le_Linux
27M  ./ngrok/ngrok_s390x_Linux

```


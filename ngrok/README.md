
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
./ngrok/ngrok_386_FreeBSD:            ELF 32-bit LSB executable, Intel 80386, version 1 (FreeBSD), statically linked, for FreeBSD 12.3, FreeBSD-style, Go BuildID=pPukQ7uKf3weVCgGEkry/EIXPKRL0atXLBxqy_yvc/EylAeexeBXzOBVal0wkw/NTO-b-S9giPLAUwKElDi, stripped
./ngrok/ngrok_aarch64_arm64_Linux:    ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=QSwfisZibHhJLflMhONe/C7PjTq2Ll66gXGHSs5pc/BnjeqrA4khJv_UPU7cJh/LIMEK6pF8AcjohP-Y6nn, stripped
./ngrok/ngrok_aarch64_arm64_macOS:    Mach-O 64-bit arm64 executable, flags:<NOUNDEFS|DYLDLINK|TWOLEVEL|PIE>
./ngrok/ngrok_amd_x86_64_FreeBSD:     ELF 64-bit LSB executable, x86-64, version 1 (FreeBSD), statically linked, for FreeBSD 12.3, FreeBSD-style, Go BuildID=IdH-o7VkQL2AqeDPPyGT/0jpfH_cL8Lw8VTqf8kQP/R-ycv-yOUBfTpKFLRTqB/q7R9g541kTOgy7IxgsV6, stripped
./ngrok/ngrok_amd_x86_64_Linux:       ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=31kmzRp1sT-OZm5zrtyR/_H4FzuT5UJ4jlQtr1qbK/2NZMVPdcy8QujmoD5Wmq/-2YRS-0jyDCn0OfDR2vx, stripped
./ngrok/ngrok_amd_x86_64_Solaris:     ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib/amd64/ld.so.1, Go BuildID=xrthwh-AljThOLVc-3JH/4D0lk-Ar4VyTBBjcJyiu/6ZNQ-iSh1io6P9r3_gAW/9Z65lYKRXWXjlsAVd9Ql, stripped
./ngrok/ngrok_amd_x86_64_Windows.exe: PE32+ executable (console) x86-64 (stripped to external PDB), for MS Windows
./ngrok/ngrok_amd_x86_64_macOS:       Mach-O 64-bit x86_64 executable, flags:<NOUNDEFS|DYLDLINK|TWOLEVEL|PIE>
./ngrok/ngrok_amd_x86_Windows.exe:    PE32 executable (console) Intel 80386 (stripped to external PDB), for MS Windows
./ngrok/ngrok_arm_FreeBSD:            ELF 32-bit LSB executable, ARM, EABI5 version 1 (FreeBSD), statically linked, for FreeBSD 12.3, FreeBSD-style, Go BuildID=ksxY1_AYI5Wnii3aXQgi/LQlpPaUzouw8cHzPJ6nb/3YAbe62NVj2HNvpZuAoB/4XyX-EekyRDi_gZPg9VZ, stripped
./ngrok/ngrok_arm_Linux:              ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=u4FAjNpCD1ZDu-AOVcCS/ehcTP04u_DwPrYpiB4qN/gsCS4hhyHyHnmyk6ytIl/2uUy1agz4m1soYPV0Lpq, stripped
./ngrok/ngrok_i386_Linux:             ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=oJiLMOAjUy6bjxrvm8QV/-a99ItBW4zDPRnOU67yC/1LnfRmGs3-KPGhZKggO8/m7LjuSHuugDPwUHxAZZk, stripped
./ngrok/ngrok_mips64_Linux:           ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=ZMsIsvq_5Qwvm31lJQP7/VWBB14DijD8bdhcoMeYc/5LE0z9Hu1prJKI8a5L-N/5RCMJGbf2nrhooF373ET, stripped
./ngrok/ngrok_mips64le_Linux:         ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=ZCQKSriLrYln9AH2urZO/LV3OE3hGP-tVsaIHK5HX/3O3uLGGChU66HX7-gunC/vX1FkNrEvRtzL4xmaMBv, stripped
./ngrok/ngrok_mips_Linux:             ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=nkYkTFT1TKZUUl35Jla1/B0VGLqzVodz1bQgGFJBb/ZRIayvTp5bNYZYAaE9n_/crmvFNn1PlRLAzfd_Jbt, stripped
./ngrok/ngrok_mipsle_Linux:           ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=fYEhnujZWY4l3EbY32bA/rB-qf754Jw8tGgj1HnUU/i_qU4zI9_mfi5aMKEagI/sA488i4U0iGFoy84tchH, stripped
./ngrok/ngrok_powerpc64_Linux:        ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, Go BuildID=pLs70eqJHCEG0UmbKY3Z/iJdsr74IdO-ENyw9kOwg/UtUlrEslWbTERfYoL6TZ/k41zdBi9y9HD-mNKm3T3, stripped
./ngrok/ngrok_powerpc64le_Linux:      ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, Go BuildID=FN7bW8_FcMlYWXwKFvHa/V-djQCFu2mWtxghxJ4IE/Hu6K_ouNR1McDAfYvJ05/-mz5OHadgtfJAtISc_y2, stripped
./ngrok/ngrok_s390x_Linux:            ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, Go BuildID=apbXwEjC9xuvn9DvysNF/F9EM-uZC-1jrcH_X0DN-/drhrG2IzSLAvfO9ZoEmF/F6jYstQi-r_rBaHjEAel, stripped

--> SHA256SUM
34cb1b479daf048b93df22b7788ba36dd64c02a2b71e8f20631dc9a66eb3ab5d  ./ngrok/ngrok_386_FreeBSD
e9cb9a3e65f92fa095101884291f9e5ed0989633cff480353a65877cf710399e  ./ngrok/ngrok_aarch64_arm64_Linux
3fe7cc8f0d6b1978487c502cd6b832a1963287ad0f7c171904ac2c27d81bf9be  ./ngrok/ngrok_aarch64_arm64_macOS
478fcc691865c4f8f1510eaebf66800e439243672e7471d791ee93af5756a771  ./ngrok/ngrok_amd_x86_64_FreeBSD
7b360bf317b78a9dfefaf3571534390df0282a8920cc27da605142d9c364aa36  ./ngrok/ngrok_amd_x86_64_Linux
fcb3eec5fe58f0c84b7a4cf6ca9e2cb1deeb1df6eb0937310af83adcef75d0c9  ./ngrok/ngrok_amd_x86_64_Solaris
a74f6bc18eac29485892cfaf385f56d5eb37cb50f6b3df9a7e024657a439b475  ./ngrok/ngrok_amd_x86_64_Windows.exe
5c2fb13ab825876f183bcff82f98b0979f9f5250638a8cb88e5f987f2b109b6c  ./ngrok/ngrok_amd_x86_64_macOS
4be83d3f743d42733628fb7e645890e4efe3b11457d0b7f905de19d79dee2758  ./ngrok/ngrok_amd_x86_Windows.exe
cb4e7a1e7bdff813c160303ccc9e7ca2258e6f207dc5b53a5bdfaf079df51009  ./ngrok/ngrok_arm_FreeBSD
3cb21e33be918ad4e547db5f0401d0c6fea61876ae46c14daf39f1038f80a1af  ./ngrok/ngrok_arm_Linux
e8c28e4ba403dd75db33187557e47fb066ceab6d00ecb68d47d622af773a401a  ./ngrok/ngrok_i386_Linux
522cb1e383d8b033379351108dacaf6a94cf57333b91c01cb933a4c73e155479  ./ngrok/ngrok_mips64_Linux
f2491ac96d4c4760024cd80cfc7d321fa2e76f4d03abbe1ed3b1c819e9457ce6  ./ngrok/ngrok_mips64le_Linux
d656398417a37e24bc3d7d25d0a8a7bb8ea700b73cd65f459e344028bbd4c85a  ./ngrok/ngrok_mips_Linux
60e8b8d3e44539b6c9f21566a037cd6a73a6718510eac92f41c3f40fd527ab32  ./ngrok/ngrok_mipsle_Linux
e5415c19bbcd8eb40fa3a9020a816a32f313c83cf8ee1cbc16eb8e56de674e5e  ./ngrok/ngrok_powerpc64_Linux
3d9e5f8c7ce8b828f042c8b61d32451911ea9ac464f57a3310518fcc2aa1d71e  ./ngrok/ngrok_powerpc64le_Linux
78dea29930343b5bcd705cd4c4a9f7ba77ece434ebaea7fda863d60ca1525a1d  ./ngrok/ngrok_s390x_Linux
```


---

- #### Version
```console
ngrok version 3.16.0

NAME:
  ngrok - tunnel local ports to public URLs and inspect traffic

USAGE:
  ngrok [command] [flags]

DESCRIPTION: 
  ngrok exposes local networked services behinds NATs and firewalls to the
  public internet over a secure tunnel. Share local websites, build/test
  webhook consumers and self-host personal services.
  Detailed help for each command is available with 'ngrok help <command>'.
  Open http://localhost:4040 for ngrok's web interface to inspect traffic.

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


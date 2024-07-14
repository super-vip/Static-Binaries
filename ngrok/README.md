
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
./ngrok/ngrok_386_FreeBSD:            ELF 32-bit LSB executable, Intel 80386, version 1 (FreeBSD), statically linked, for FreeBSD 12.3, FreeBSD-style, Go BuildID=uZiQyI-S63WO-N2yRT_3/tk61PuAyWBr0b346IEmo/KBqjutCI-7IbFTIYiPqM/U5OV_aGazgMnHTX3NVDU, stripped
./ngrok/ngrok_aarch64_arm64_Linux:    ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=17VTWaGmMdR0NHWg3Sz1/3BmOmDpeg5zqPNKXq5U2/K9VQFEX9A7rQD9kL-Byv/54FAAGYvHrC8_jHO1XKk, stripped
./ngrok/ngrok_aarch64_arm64_macOS:    Mach-O 64-bit arm64 executable, flags:<NOUNDEFS|DYLDLINK|TWOLEVEL|PIE>
./ngrok/ngrok_amd_x86_64_FreeBSD:     ELF 64-bit LSB executable, x86-64, version 1 (FreeBSD), statically linked, for FreeBSD 12.3, FreeBSD-style, Go BuildID=IVwr2E2rhF_YfpsABXwI/eveqXyvwpQCjJ8SLL_r0/SKysk8kXgam-KQP5xLre/JMAuu1A1nyPdskat_dlG, stripped
./ngrok/ngrok_amd_x86_64_Linux:       ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=ZqNw52oPozbgayOhpZHU/j-qY_UqX0TK2kBmwfaT8/aH9E7eS69Cffp02RPMDJ/wqK1eB9y1hJCpkx-DbFg, stripped
./ngrok/ngrok_amd_x86_64_Solaris:     ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib/amd64/ld.so.1, Go BuildID=UB-6Yue35CvO1T8NaoL2/CzBXIw54RgZWBDFxZUe6/cBvrjBWyl_ko2zsW93vw/hfRBp223-2RL-87_zDRv, stripped
./ngrok/ngrok_amd_x86_64_Windows.exe: PE32+ executable (console) x86-64 (stripped to external PDB), for MS Windows
./ngrok/ngrok_amd_x86_64_macOS:       Mach-O 64-bit x86_64 executable, flags:<NOUNDEFS|DYLDLINK|TWOLEVEL|PIE>
./ngrok/ngrok_amd_x86_Windows.exe:    PE32 executable (console) Intel 80386 (stripped to external PDB), for MS Windows
./ngrok/ngrok_arm_FreeBSD:            ELF 32-bit LSB executable, ARM, EABI5 version 1 (FreeBSD), statically linked, for FreeBSD 12.3, FreeBSD-style, Go BuildID=2FCSX_5f4ALSrJ_SOevV/gMV0qwgK0aGWXl6DSYiQ/rYpl4AEY4mTs_dBD-xKa/ka3qWEt49KsVVUEbfWA5, stripped
./ngrok/ngrok_arm_Linux:              ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=dR1m3n95naVSBwUA5TtS/wVyHUZkDezX0KYeEvFzH/GG7GwuxnNWcVrauHUKck/liOvcwJ4Pc_UL1Q_cT5H, stripped
./ngrok/ngrok_i386_Linux:             ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=x0ycWHKPlYlmp54MF3SC/L6GK_ST4d7Ae5AEU5gFP/guzzz3EqemiInC0jyLnc/7xhqqJywvJ8gT0XnmDpY, stripped
./ngrok/ngrok_mips64_Linux:           ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=IVdqir-RrjjFU1G9Tonk/Wi7KrSARdTdP0qYJQ3Eo/gtWajBNAEyHOgLqx4ytE/OGVJpNoEVXAGDIcbhgTD, stripped
./ngrok/ngrok_mips64le_Linux:         ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=UeDg4WWpzdut_3TypAQu/nnhJ3pqjClv2PBn-Y3Ur/uo4TYUVrkKdP75iS_AxD/PuzWkOR0ggzoYdaxxJqk, stripped
./ngrok/ngrok_mips_Linux:             ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=JYbsyKkXhTdJk9mN4hQu/NsPCaEP8QY2bKJmVw5av/zYRecSjZHPXaFvhLVeTy/MckOyrYzJPyOxd2RowjD, stripped
./ngrok/ngrok_mipsle_Linux:           ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=fhnVh5aAttk9Vzoh6rMG/bYFKHpFpTTdDq6B6o_iU/wSp4Hmp5gBslq0IrOcHB/bstj34B6GfTK25VFamaJ, stripped
./ngrok/ngrok_powerpc64_Linux:        ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, Go BuildID=VBUAZWxvkA-A3iOG4CIr/e5pIcq0-gVSTUr0AJfp-/N9uSC6eNI11PFptUdOjK/v1ZeOiGDfd4Oiv4w9zkr, stripped
./ngrok/ngrok_powerpc64le_Linux:      ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, Go BuildID=knoS6TNKc2eqZ48rgUvv/TSV-i2T3h02LVqBQ7tcj/jfBEWIOtoBLhuWJnKXTc/gPcrTzOfv4UFkZBeszKF, stripped
./ngrok/ngrok_s390x_Linux:            ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, Go BuildID=bJ7Bw7AQIPA1RWOqFk6d/neKZOaP8KB8eLYM-pNqs/JLxwr8WE1ydrkVxYvjy7/kqpr1SJUyyMBDZeH4kiH, stripped

--> SHA256SUM
b023c50b19d20b6c856ccddac32f2e83b9e40c20e40582890d73c72eb78766b1  ./ngrok/ngrok_386_FreeBSD
2740f2aeaa8aff1c5a9a3d1c017b83813bba99b97d4f856fe0c479c897775728  ./ngrok/ngrok_aarch64_arm64_Linux
a9da4514327c67666a602cd08b53551b9009425ae5e8ee5e6277d054437c17d6  ./ngrok/ngrok_aarch64_arm64_macOS
3e83ac2b31fa106e96f6ac3378a3aa076e669ebdf3ff7e682c7a92b2ee754d97  ./ngrok/ngrok_amd_x86_64_FreeBSD
b85a173fe18636018892741cde6cb4557c86cadac3a3e4015e1187e6584d58a4  ./ngrok/ngrok_amd_x86_64_Linux
b5d68eab8fc78e142348816d483cf4591e9bbff96f2f5334517badb7b1ced065  ./ngrok/ngrok_amd_x86_64_Solaris
1842c06c0bd3240a4be91cfef2beabdd5f9820ab32dbb51cda1158dab205cab1  ./ngrok/ngrok_amd_x86_64_Windows.exe
ef53ae994e04e44da222024994d61c2f8fd682c70801629498a1c681dc3a06eb  ./ngrok/ngrok_amd_x86_64_macOS
c5bc9a0ddda1d43ebbe96b224ba629c9e6bc741d118b1566cbd5d538e8995435  ./ngrok/ngrok_amd_x86_Windows.exe
98c9425cf7bd444a4850d8e4496a09cbd0aea9a61fe0e32df0aa0af590310fb4  ./ngrok/ngrok_arm_FreeBSD
e383edc5d8459eda7d6a167252bbb512e0464aa0ee2a6a4423ce74d02f106eab  ./ngrok/ngrok_arm_Linux
596c11c9cf136a8d7edba92499c7f745cff7327eb89cf0bc8b1e717fd044b92c  ./ngrok/ngrok_i386_Linux
888acab5b64c7369e0f7c6004cb22bdd119d4675519891203d39b1543b1b6a42  ./ngrok/ngrok_mips64_Linux
fcf16a9d07cba14e9e9a6b3c0b70b7e8b212929bf7105ab780e8335d4c623b85  ./ngrok/ngrok_mips64le_Linux
5246f0d455e1e8a6b4cbf236ed35b804dfa8dd56956799df1c9c453db63975b5  ./ngrok/ngrok_mips_Linux
d1a243ba0f61454ffdb7be6fec798a04fdad6b038e2c5e9a1c448c34e4ebe3bf  ./ngrok/ngrok_mipsle_Linux
7b42f33938c5c3c5a4f0cd56c7bd489b3439615db3f233ffa6b273688e40d037  ./ngrok/ngrok_powerpc64_Linux
51ddc923a35ec7798843ced5e3faf1d40df67fe6a602d2532fa273525f42e592  ./ngrok/ngrok_powerpc64le_Linux
3759b6ca996f0c3dac936915478c9a3c0657a773a8c80c7518e88fb7657ee0fe  ./ngrok/ngrok_s390x_Linux
```


---

- #### Version
```console
ngrok version 3.12.1

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
  ngrok http --domain baz.ngrok.dev 8080  # port 8080 available at baz.ngrok.dev
  ngrok http foo.dev:80                   # tunnel to host:port instead of localhost
  ngrok http https://localhost            # expose a local https server
  ngrok tcp 22                            # tunnel arbitrary TCP traffic to port 22
  ngrok tls --domain=foo.com 443          # TLS traffic for foo.com to port 443
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
  start                          start tunnels by name from the configuration file
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
27M  ./ngrok/ngrok_386_FreeBSD
28M  ./ngrok/ngrok_aarch64_arm64_Linux
28M  ./ngrok/ngrok_aarch64_arm64_macOS
28M  ./ngrok/ngrok_amd_x86_64_FreeBSD
28M  ./ngrok/ngrok_amd_x86_64_Linux
28M  ./ngrok/ngrok_amd_x86_64_Solaris
29M  ./ngrok/ngrok_amd_x86_64_Windows.exe
28M  ./ngrok/ngrok_amd_x86_64_macOS
27M  ./ngrok/ngrok_amd_x86_Windows.exe
27M  ./ngrok/ngrok_arm_FreeBSD
27M  ./ngrok/ngrok_arm_Linux
27M  ./ngrok/ngrok_i386_Linux
30M  ./ngrok/ngrok_mips64_Linux
30M  ./ngrok/ngrok_mips64le_Linux
30M  ./ngrok/ngrok_mips_Linux
30M  ./ngrok/ngrok_mipsle_Linux
28M  ./ngrok/ngrok_powerpc64_Linux
28M  ./ngrok/ngrok_powerpc64le_Linux
29M  ./ngrok/ngrok_s390x_Linux

```


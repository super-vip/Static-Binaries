
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
./ngrok/ngrok_386_FreeBSD:            ELF 32-bit LSB executable, Intel 80386, version 1 (FreeBSD), statically linked, for FreeBSD 12.3, FreeBSD-style, Go BuildID=Z0OdJ1Wzwrhs3Eq4zJrA/BD0BreqUg_RJKtpfCG9-/Uvzsm26tT_-zT9hDSsju/f4z7BFZ-0WasAagxVicz, stripped
./ngrok/ngrok_aarch64_arm64_Linux:    ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=CLZgtACqK0P7VheM9OEo/SXQFrA3aSsmq3ByqYt2n/DPlLa-HL5bGD3NFGWTku/WLXpJ6LNDe96M5RS594W, stripped
./ngrok/ngrok_aarch64_arm64_macOS:    Mach-O 64-bit arm64 executable, flags:<NOUNDEFS|DYLDLINK|TWOLEVEL|PIE>
./ngrok/ngrok_amd_x86_64_FreeBSD:     ELF 64-bit LSB executable, x86-64, version 1 (FreeBSD), statically linked, for FreeBSD 12.3, FreeBSD-style, Go BuildID=CNg-MgHZBAQ9UwUta2po/kzsj3MFwYxxQP7QOSZXU/fklFPDbA6YZCh1UaRW0P/3c-UMGhNM42myRQn1rOU, stripped
./ngrok/ngrok_amd_x86_64_Linux:       ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=0Ripzt1wMdfK2BPY42wP/DZVLb6xE0kDlByLAbHr2/HtyIsgzMcRjSlWAuOllZ/b-1-Z0xxOgJj6LfrokJF, stripped
./ngrok/ngrok_amd_x86_64_Solaris:     ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib/amd64/ld.so.1, Go BuildID=BJ4ktDjAaZAywtjYUuDw/IdiWSrqg6m0x_u0K_8Wd/9bAZ7PedliUgtLfJOhyU/eWCWBM4XVVcdWmg6WEk8, stripped
./ngrok/ngrok_amd_x86_64_Windows.exe: PE32+ executable (console) x86-64 (stripped to external PDB), for MS Windows
./ngrok/ngrok_amd_x86_64_macOS:       Mach-O 64-bit x86_64 executable, flags:<NOUNDEFS|DYLDLINK|TWOLEVEL|PIE>
./ngrok/ngrok_amd_x86_Windows.exe:    PE32 executable (console) Intel 80386 (stripped to external PDB), for MS Windows
./ngrok/ngrok_arm_FreeBSD:            ELF 32-bit LSB executable, ARM, EABI5 version 1 (FreeBSD), statically linked, for FreeBSD 12.3, FreeBSD-style, Go BuildID=Dl-kIqJB_LczJYWGUdsf/DwqBHNmxHq-JprBYSrhI/U-u1oBgZpSBrauaegt57/8Vwz__5jscLVF8s6k6_8, stripped
./ngrok/ngrok_arm_Linux:              ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=np2vfLmTs5Y9Cf-5N_dr/Z0rbxLtl30eTOHJkTTWT/Cjvo_7ppNBeLd4O5qpQA/3FOdY5PQkVdud1wG5Irn, stripped
./ngrok/ngrok_i386_Linux:             ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=mHMd9bpMM6Jx_DaoYMoh/qniwKHfYBzic4h9oOEtw/gACE8wYYC__VfNskczcE/ScVcsNc3F7L_xFioVHcH, stripped
./ngrok/ngrok_mips64_Linux:           ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=sfAkhb8NhcznLcj1k3Dq/OI7aNxeRigF_E3ctszGM/Rzdw5JgFK6PAAAsuuW1y/88TpwHKWCVoCma_9_PFb, stripped
./ngrok/ngrok_mips64le_Linux:         ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=9QEiP3117Icqii3op65M/GQNr5Sf0ah80LLZRjM2z/7gN-zXMmoPqGbyUwpb0I/kX1DV7yuiUjVXX39rX-c, stripped
./ngrok/ngrok_mips_Linux:             ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=X6wGgDTba0GWGlGscLf2/38HVv-pfLICWmyQoN2-K/WzjBWush2ZyuggVz-5Zq/Bc4ohRHfahN-UweveSz3, stripped
./ngrok/ngrok_mipsle_Linux:           ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=eYh7Np1Re4_YkABT7Otn/QH8iCFrDZ8pky1aBPNZZ/dSNtOWcXl9-v1tmrbY_p/utdBKiBvUwyhUemtD4-1, stripped
./ngrok/ngrok_powerpc64_Linux:        ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, Go BuildID=VkDYPO4wDXGXbpYw60x_/Y2zLnPuBPGjy0u9B3IJp/MbcWkNsye7qjWe4z3X8Y/jJB-gdh2KRgqv9BbvXAG, stripped
./ngrok/ngrok_powerpc64le_Linux:      ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, Go BuildID=c4Q_tYpR8cdvQOp0cNVp/uaFy1iF2gCnhcJNhjs1I/bxCpM4Gyc8llaszNwRMy/3x4n2up7inUWJNvb9hbL, stripped
./ngrok/ngrok_s390x_Linux:            ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, Go BuildID=hPG1_aZ6qdMYxPrTWthQ/09zBVw6CkG4uMyLnSZX6/axc9l4TjQ30fz_jmTwzP/xhC-iv_zZgCCNyzvsYF8, stripped

--> SHA256SUM
53ea7e0998933775b23efd1a46a4a406e6d95b1b971eea0a6bafbc59008f76d4  ./ngrok/ngrok_386_FreeBSD
c707d000ef69f2a16ce520c807c6c5115839b9cd2b917e16f17d720f3e66508c  ./ngrok/ngrok_aarch64_arm64_Linux
a45c093622899debea83829b0996c725501c92680ca6b8c71801050cc03d9e33  ./ngrok/ngrok_aarch64_arm64_macOS
fc252bd28542c4b3cb869737dd51409105122588db0bd374664c0352019dab8f  ./ngrok/ngrok_amd_x86_64_FreeBSD
74cedaea7ec20446892d1289c82d54dffe092afb4805fc2bd693bb9c874fba7f  ./ngrok/ngrok_amd_x86_64_Linux
1ec58e576bca62328e45a8a63d0aa92ea68ec128b4898f19581b3401f961e174  ./ngrok/ngrok_amd_x86_64_Solaris
6109db64376baa8fee39d1fa14f787518100116a03070c994bb27dc11673ee11  ./ngrok/ngrok_amd_x86_64_Windows.exe
b238c8d59f80d2b9d35ea2fffd60330270b06cbf17b75a0e00c44bc775c4b44e  ./ngrok/ngrok_amd_x86_64_macOS
19869ce56f1e4b682e2475cb2420210bf02e44e455b07c43feb3289672fa7084  ./ngrok/ngrok_amd_x86_Windows.exe
3f1eca5175662ef8d8093e6e32a130dafea7d0f68d397677a1b81292f6998b88  ./ngrok/ngrok_arm_FreeBSD
8e9643d5f6310134d236edc8b3c8f0444bcaea7465efb43fe97a9af3f6e32ba9  ./ngrok/ngrok_arm_Linux
72a5beb8885d82d92bf119bc5bc33a0f17cac7e5bdaca9b1666a24724becc10b  ./ngrok/ngrok_i386_Linux
f33796cd9cdaeb89be1bbcb0efd2e4ae8792d36c232ee82dd71b44e8a0ef998b  ./ngrok/ngrok_mips64_Linux
a6c8f82b35024dc4d10a090814ed608fd2ca32d91005ee6061b342f84298f218  ./ngrok/ngrok_mips64le_Linux
c5f68771feff6ae1a78917d22967000011165930f38a60882e30e943df926939  ./ngrok/ngrok_mips_Linux
63baeb7f7e5016d741dc560f02843154a1e0f8c452408dc3d7e14147a566cf54  ./ngrok/ngrok_mipsle_Linux
d5b6a4ce02adc464ad08a8d7e5f0bd4f7ac34abaca34638172f356d03275fd8b  ./ngrok/ngrok_powerpc64_Linux
d8fd4bd5f037b1872fd58a428135c44e1e43b5dce6a30abf0894e4aa483781cf  ./ngrok/ngrok_powerpc64le_Linux
2cb0a698f37e1cebc9b62cdd83a9961d453ae687a33721d9115c1e1ea4b10698  ./ngrok/ngrok_s390x_Linux
```


---

- #### Version
```console
ngrok version 3.17.0

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


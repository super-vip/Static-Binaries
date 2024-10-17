
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
./ngrok/ngrok_386_FreeBSD:            ELF 32-bit LSB executable, Intel 80386, version 1 (FreeBSD), statically linked, for FreeBSD 12.3, FreeBSD-style, Go BuildID=Q10GHzh2jVqNBTg8L-r2/zhyZXjW49TVlc3uX0q9B/lWODm3zIq7_ECAqxDILP/85RQl6ILHwJC0OMfJ5qy, stripped
./ngrok/ngrok_aarch64_arm64_Linux:    ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=bSU04V1CIoe9FVwhLpoV/-3_rzID0HknM6Bvip-18/vtcGqHbde-PuZ3ddNWTc/3nvdkuS3e9jFwpU7si3Q, stripped
./ngrok/ngrok_aarch64_arm64_macOS:    Mach-O 64-bit arm64 executable, flags:<NOUNDEFS|DYLDLINK|TWOLEVEL|PIE>
./ngrok/ngrok_amd_x86_64_FreeBSD:     ELF 64-bit LSB executable, x86-64, version 1 (FreeBSD), statically linked, for FreeBSD 12.3, FreeBSD-style, Go BuildID=NHh0_JLzvy4ElH-SQVpv/VHQHHDlXqU1Uc4Ixfpzv/D6UI-sO0Dif841VJ3zsE/0fdrGFQ7kN5L1rcDS7B4, stripped
./ngrok/ngrok_amd_x86_64_Linux:       ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=O2G-dIPA0_AJjAIuyCYR/A1qVd9a9ur1qdBK_z72w/17u-uJvAqaeVXQta4_qC/hPLgv4wS0vvDjqCWhLkT, stripped
./ngrok/ngrok_amd_x86_64_Solaris:     ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib/amd64/ld.so.1, Go BuildID=-HLdh50jMTLIbHuESWo-/8zsr0bVrkg8p1wP13RdV/evcqQJTWXv6e9g5-5A5O/Knx_ibwZ5hJvx44JRtmR, stripped
./ngrok/ngrok_amd_x86_64_Windows.exe: PE32+ executable (console) x86-64 (stripped to external PDB), for MS Windows
./ngrok/ngrok_amd_x86_64_macOS:       Mach-O 64-bit x86_64 executable, flags:<NOUNDEFS|DYLDLINK|TWOLEVEL|PIE>
./ngrok/ngrok_amd_x86_Windows.exe:    PE32 executable (console) Intel 80386 (stripped to external PDB), for MS Windows
./ngrok/ngrok_arm_FreeBSD:            ELF 32-bit LSB executable, ARM, EABI5 version 1 (FreeBSD), statically linked, for FreeBSD 12.3, FreeBSD-style, Go BuildID=pptLC8svzWgmy4zZehFV/FsHpPvLAcc9HqHWduDEd/2mocM1T8GMgYkz_-6xkE/FHWfsdiir1gSJJtyQtZG, stripped
./ngrok/ngrok_arm_Linux:              ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=sApQqt6-NFXPgjg5jCAr/fY5k6DXQh51sgn5-CKd-/aDqrEd2zISRGLA0hrVWE/dnoDJ4CPkPz8NA8a4nph, stripped
./ngrok/ngrok_i386_Linux:             ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=DyFeQSbtO86kz_jNTFUZ/nFWS2bVPeIwFyngLMBvh/fLPHTlRo9-_XaxyrodkE/xOXis2xQnLVKJroCKLEV, stripped
./ngrok/ngrok_mips64_Linux:           ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=c6CRdJC-YUn1EebRDa1w/Sn9oQBI5aIHngYLOaiGI/piLa3ZSuR676gYL4NEko/BkNSsz9Gj7agkUY8yRMX, stripped
./ngrok/ngrok_mips64le_Linux:         ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=3mlGVmU9sbhy2eIUCVXf/QTCgGgT61QRiWEV2uOkk/3-faDQo9XfdffhQawitj/lLoVKegah7iEgiU9amq7, stripped
./ngrok/ngrok_mips_Linux:             ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=Cf7NiuZXWfovvVtJJLTE/geyqaaeAeGcJ0v_kpevg/oIm1rb8R3dx1V9_OZjNZ/hBYojFmD0iI1F9Ovbdtj, stripped
./ngrok/ngrok_mipsle_Linux:           ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=lrQfgObvW3sv1KYRXSz-/PdlQ0dovXs3fE5HTmlyq/1b4S3Ly-ylya5lW8q3Bt/sKD4v6LPg0MxzTUR3fV7, stripped
./ngrok/ngrok_powerpc64_Linux:        ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, Go BuildID=6SjFyCYs5tQX35C0LxIr/B5njdkbYGxoSHNd0iSGD/4KmpgRi7xeRNq3mq4Fc3/k5-k80M3UwXJENBnCpWy, stripped
./ngrok/ngrok_powerpc64le_Linux:      ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, Go BuildID=HKSjKpXxeDyaRaucrnQD/USqv5_McGtpts2q0qp5a/HTKOuTPbvoaPPSZXpwYt/VfnLtrY9rqFrkIh4Cb1C, stripped
./ngrok/ngrok_s390x_Linux:            ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, Go BuildID=VnqujN1Gs2e0wzQjZX-f/xKBYt0C2QLAZLJRtW0e5/HJXLKKzh3NdhN_5YtD7T/Qx4NAHgtCBcEYGyvLdEW, stripped

--> SHA256SUM
9107334dccec39f316468fae43475367a38609ffd7cc26f9b2342299c24dcf74  ./ngrok/ngrok_386_FreeBSD
730cc03c957d7e0b9aa7fc022604b2ef68cb4edf074dd3cb1206093a43b0294b  ./ngrok/ngrok_aarch64_arm64_Linux
bb189fa9c83a09385d60e7f7770bd38f7ff470d41c686b82a0adb2a9bc093bed  ./ngrok/ngrok_aarch64_arm64_macOS
d46b409ee8ea8f967eb772fae78ecf563c15d1949928423957f8f10f04f36028  ./ngrok/ngrok_amd_x86_64_FreeBSD
ba6923fed04fe04589ae3585c02ef5d92fb85dd5e922f70743a8e6d58aba72c3  ./ngrok/ngrok_amd_x86_64_Linux
b8210e1286977c9a7ee84591daaafea97ae0d817121ced9a9f66a71a572856b8  ./ngrok/ngrok_amd_x86_64_Solaris
b47ff661c757dfdcef83e89b52ba4a3d6d2708d55bf0943d0454877b0be1bc6f  ./ngrok/ngrok_amd_x86_64_Windows.exe
54e8d771dd3367b9157392a3b795ea2a7dce7ddb08f0e4dbfd040f5af4efea99  ./ngrok/ngrok_amd_x86_64_macOS
41aa7a6012875dce2bc2123a3e2cf063ddf176011d57ceaa0bb2386a6efe49c4  ./ngrok/ngrok_amd_x86_Windows.exe
e78a3b818e7b8d291e91ee86c32165aaf3e87cee35a9c075bf680572adaca51f  ./ngrok/ngrok_arm_FreeBSD
05e47138df976a3b085f425b4c9fa1aa9a14fa1468625aae02bb9ed381a12231  ./ngrok/ngrok_arm_Linux
2bcf5f64de7e6cdf430bdce7915050e7bb5b7d6e95da537beb354ec23f069b3e  ./ngrok/ngrok_i386_Linux
245c8ecbd7894dc3c7f8abcfca5f8e2d6db738b9d459b1e035bd69d17dfb5381  ./ngrok/ngrok_mips64_Linux
ef0740a44f620b0213d027fece477791a2f2a12d05ea5c455b77b4ae91465605  ./ngrok/ngrok_mips64le_Linux
f1bcce31b129ab2625c8ff6fde0f0a931b4e013f785861fd1f37b0e50d725832  ./ngrok/ngrok_mips_Linux
0e937297dbbe9fcdf9dd076dbbf075bec1850e1c805092374a3dd5b7a051264a  ./ngrok/ngrok_mipsle_Linux
62c631127d81ec86a203cb78f4e5cdc7e9e1f1afad31d98f0884d003975fdc1b  ./ngrok/ngrok_powerpc64_Linux
f5a49ae02c863d7b77946a12d649f27e32fc4a626a02299819a61dce5e4686e4  ./ngrok/ngrok_powerpc64le_Linux
b1952cc2595b43dc69801850630f3690d52c3543d54f1339f7150648bae22ba6  ./ngrok/ngrok_s390x_Linux
```


---

- #### Version
```console
ngrok version 3.18.0

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


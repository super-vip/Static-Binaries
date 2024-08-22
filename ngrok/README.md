
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
./ngrok/ngrok_386_FreeBSD:            ELF 32-bit LSB executable, Intel 80386, version 1 (FreeBSD), statically linked, for FreeBSD 12.3, FreeBSD-style, Go BuildID=j2rb4Ei24eC6NIt8_3DT/2pPYVugehprMpxRheXUW/PY8jIIVgOR0BE-ZfXYcZ/MH3AHhRK1fc7cVBEoTKo, stripped
./ngrok/ngrok_aarch64_arm64_Linux:    ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=Oli89Yt2DHvDu1tOcZSC/8ahnia6ht6zxduC4ZF2P/LMpnSFLGasVTvjGqZ5MZ/7eQoepJjMYyCBNPyJ8Hy, stripped
./ngrok/ngrok_aarch64_arm64_macOS:    Mach-O 64-bit arm64 executable, flags:<NOUNDEFS|DYLDLINK|TWOLEVEL|PIE>
./ngrok/ngrok_amd_x86_64_FreeBSD:     ELF 64-bit LSB executable, x86-64, version 1 (FreeBSD), statically linked, for FreeBSD 12.3, FreeBSD-style, Go BuildID=2EDkqpe7e6mcvPzXEO_T/ok4utQpIoirho7z33GVG/UC1-s_FYa-OPTJgK4WpA/gB3G7jhRU72dl0yepfsj, stripped
./ngrok/ngrok_amd_x86_64_Linux:       ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=3RBZIhip_s2nSMAngkvE/6WgkeIVZJPfB7TcIwCr8/2Lm-jOx_YkpiSqtRTBL1/7vNN8ggjF6hugNsOUtGB, stripped
./ngrok/ngrok_amd_x86_64_Solaris:     ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib/amd64/ld.so.1, Go BuildID=OeA4EtyIvaV08oNTgm1S/NbTFPSYE670xnt41znud/CRKJY5xwzBshfGOlCN_a/j7oOlIqfwuTys6Gv6Qej, stripped
./ngrok/ngrok_amd_x86_64_Windows.exe: PE32+ executable (console) x86-64 (stripped to external PDB), for MS Windows
./ngrok/ngrok_amd_x86_64_macOS:       Mach-O 64-bit x86_64 executable, flags:<NOUNDEFS|DYLDLINK|TWOLEVEL|PIE>
./ngrok/ngrok_amd_x86_Windows.exe:    PE32 executable (console) Intel 80386 (stripped to external PDB), for MS Windows
./ngrok/ngrok_arm_FreeBSD:            ELF 32-bit LSB executable, ARM, EABI5 version 1 (FreeBSD), statically linked, for FreeBSD 12.3, FreeBSD-style, Go BuildID=HBefusSdh4WfLxC5F51y/7qs3RYHh-tFHSzlB0FU5/4iy84cHV_ZHLwEByA3qK/Qn8R4JLR0v5LwmSAjw4o, stripped
./ngrok/ngrok_arm_Linux:              ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=K5TNNurMaEB9gCOBUtYV/PurKjklcT-3vr3uE_q_F/aKkjDt4npCJSjyGUPFNT/f9FSJPof10MlBnKddEe7, stripped
./ngrok/ngrok_i386_Linux:             ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=UMW69q2lO5HpFKmaEfM7/SP7QvIaHygv17F2By9si/ijqqE-vTypLefLi8kChi/ZepYam09hA3vWvAoLECW, stripped
./ngrok/ngrok_mips64_Linux:           ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=ZxM91ZEaUZL0veK1Glh5/dMdbQF6iuMuWI8Zbe2QX/NE_Ar7vM00oQjh95N1MT/AauGhW_RWkV_Jjt6SaQk, stripped
./ngrok/ngrok_mips64le_Linux:         ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=CVmjUHB2wUfSJtdcre9j/hO8jfUIxcuajYEYW1peK/h1kPPGhBTh34P0gVJBlu/D68maJaRrDGBm7cueFEz, stripped
./ngrok/ngrok_mips_Linux:             ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=RWf_uxutpELn9_ytYOYj/rfXtGK3-IJ7UOULVV5Of/hkG0paQipmG7Alf9zb7h/31DXs5oUQIOYPrw5CajI, stripped
./ngrok/ngrok_mipsle_Linux:           ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=dtm125w_3RqTq9AruNlZ/KDTaFMC2tJ62tw-oPx9w/ABzqSbTvbxvcnsCOFJ-T/hLWszyhm91KVdAMwlFz3, stripped
./ngrok/ngrok_powerpc64_Linux:        ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, Go BuildID=wK0A8-ajCYPjEmHbEBWB/r9eOGrhXcBFwuygnkEPp/SiJzLR3QlZ3aRVuT0P8L/BcTnvT_7hoUSQj2KJrYs, stripped
./ngrok/ngrok_powerpc64le_Linux:      ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, Go BuildID=1nDhPZJUb4TTuYkac_88/j5mJKaoL5RZfteWwAf41/LokDHbIoATxwLJP763ZA/rGN9sjCTW0l_Ix9Xre_C, stripped
./ngrok/ngrok_s390x_Linux:            ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, Go BuildID=S5Q_Nlj8yrNmuqkMXbgM/7Avqq0U8QEt40HpgxVfr/8QfiWRxbbtWUarA14xiu/DwbHnFQk6Ux6LfyVpv0V, stripped

--> SHA256SUM
548694b3ac789b27e3b638f59e6a660d8d8c03259353c19986a2b320804c3ed4  ./ngrok/ngrok_386_FreeBSD
f727e13feedc7c75fed95e212eaad8c72624c10762eb50ab2478998a7a4be3b1  ./ngrok/ngrok_aarch64_arm64_Linux
df03b299268baf9c91fa4cf7d9a591f4726da0680d8a30feb5708a57b99651ea  ./ngrok/ngrok_aarch64_arm64_macOS
21ce093ae1f7b8a72ba42c4d52ddb8ecf7ffbe04ded323c8b69e901c39c97108  ./ngrok/ngrok_amd_x86_64_FreeBSD
25ffc1a190538b9ae936b2206e36423b9254b628afef4888b991b43bd519435b  ./ngrok/ngrok_amd_x86_64_Linux
daf59dc42163817752277faca510a8a0889ed0b73d0a154f0b2e5c764dc604eb  ./ngrok/ngrok_amd_x86_64_Solaris
c979a5b225a73de735f7edfd4819ea26a4e6688c9325f581420eeabbee0ac8cb  ./ngrok/ngrok_amd_x86_64_Windows.exe
631168df60fea37d9e30ed94e9d8aae0b8fba52fdd8ca8dac65374b241d47ab3  ./ngrok/ngrok_amd_x86_64_macOS
567a63c137d6bf34b66f7f6af63d71089a0a7f7943e87c585ad3cda5722358f8  ./ngrok/ngrok_amd_x86_Windows.exe
cd2cf83f13580cb55f2f08bd6c83aa137433188dd4d48307ef16c07c9450f6f4  ./ngrok/ngrok_arm_FreeBSD
971626d53ef8275bee6b870a338b1a6e48cefaf23dc6c4f1f2ef5ada2b831759  ./ngrok/ngrok_arm_Linux
0043ccbe2c54aca5bf8534eadc81e38db01cccc798b9a298482d64587cce7f3b  ./ngrok/ngrok_i386_Linux
4ee5c0d97201d528fa30da4269b09c49a63550bd55dc16ae3414eb760d270c5c  ./ngrok/ngrok_mips64_Linux
d7c1b0e82bb61363ffa05388c7598da4a507bd61496afe4bf9c8b59c28bf4aed  ./ngrok/ngrok_mips64le_Linux
10ccdb617d0781e45bdc0b1e6d96ed87c9567c149b509a40e86535228741fdeb  ./ngrok/ngrok_mips_Linux
bf9e7e16fd137dcbad396a2bc0348534e5ca94ab2f90aad2b0cc2b6ea15a6c3c  ./ngrok/ngrok_mipsle_Linux
186904068cc2785aa72e26eeab360e5661c21d4cece5527e4d3fdfc4d7d4bcff  ./ngrok/ngrok_powerpc64_Linux
10b7b104e9470d35532ab57ac922b4435863c529b59a08373bf37b3b0e8dca68  ./ngrok/ngrok_powerpc64le_Linux
50099f6dd7d3762d75830461c7a31771fdd27948e942872b330d92e6a6b5b1eb  ./ngrok/ngrok_s390x_Linux
```


---

- #### Version
```console
ngrok version 3.14.1

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
29M  ./ngrok/ngrok_amd_x86_64_macOS
28M  ./ngrok/ngrok_amd_x86_Windows.exe
27M  ./ngrok/ngrok_arm_FreeBSD
27M  ./ngrok/ngrok_arm_Linux
27M  ./ngrok/ngrok_i386_Linux
31M  ./ngrok/ngrok_mips64_Linux
31M  ./ngrok/ngrok_mips64le_Linux
30M  ./ngrok/ngrok_mips_Linux
30M  ./ngrok/ngrok_mipsle_Linux
28M  ./ngrok/ngrok_powerpc64_Linux
28M  ./ngrok/ngrok_powerpc64le_Linux
30M  ./ngrok/ngrok_s390x_Linux

```


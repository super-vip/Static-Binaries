
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
./ngrok/ngrok_386_FreeBSD:            ELF 32-bit LSB executable, Intel 80386, version 1 (FreeBSD), statically linked, for FreeBSD 12.3, FreeBSD-style, Go BuildID=N8Yc2GURYTfZUsVty10Q/tIgumjBcyQY2-RTEMCQK/qo0f-p24i5RzUoornp7z/LuBnCsDPJZAN6sxRA1rf, stripped
./ngrok/ngrok_aarch64_arm64_Linux:    ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=eLGhnorA5ps2EKM4rcfv/vbV4GI9uwWL42Zv8kgYj/MTFOUvloYfMY0HX4kuik/Ql8wVMHqgOEhwvjoa_-c, stripped
./ngrok/ngrok_aarch64_arm64_macOS:    Mach-O 64-bit arm64 executable, flags:<NOUNDEFS|DYLDLINK|TWOLEVEL|PIE>
./ngrok/ngrok_amd_x86_64_FreeBSD:     ELF 64-bit LSB executable, x86-64, version 1 (FreeBSD), statically linked, for FreeBSD 12.3, FreeBSD-style, Go BuildID=E6R1-azqhGlN9KQw0ZN6/3d3AsAy-6CZxUOVwvNUJ/rJu7358jWB-OenaaqFM4/KeKn71D3FVuEEZtps9hU, stripped
./ngrok/ngrok_amd_x86_64_Linux:       ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=lrs4dRO8p9KxqWDIY3r9/e24N9rQQNlQDGKQcZ2Sv/XWZbXmh5zuUIrW8Oohhd/z4EHwdFgBgXuO8bZEX6Y, stripped
./ngrok/ngrok_amd_x86_64_Solaris:     ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib/amd64/ld.so.1, Go BuildID=1fW3EWNXlNJvpfjqFziw/j30lW7os8eLeyP6M6lHm/azvplKHXjWIFhvMFxOeL/QX7yEEVGno-OhXso-UEO, stripped
./ngrok/ngrok_amd_x86_64_Windows.exe: PE32+ executable (console) x86-64 (stripped to external PDB), for MS Windows
./ngrok/ngrok_amd_x86_64_macOS:       Mach-O 64-bit x86_64 executable, flags:<NOUNDEFS|DYLDLINK|TWOLEVEL|PIE>
./ngrok/ngrok_amd_x86_Windows.exe:    PE32 executable (console) Intel 80386 (stripped to external PDB), for MS Windows
./ngrok/ngrok_arm_FreeBSD:            ELF 32-bit LSB executable, ARM, EABI5 version 1 (FreeBSD), statically linked, for FreeBSD 12.3, FreeBSD-style, Go BuildID=JwYn32qFu9U-yuLr6q6B/ZOSjXLRfWdwlsrB2cH0J/5DSRDtmOSYDaBhB_ZV2a/pd5v4P7CyARcqA9MA3BB, stripped
./ngrok/ngrok_arm_Linux:              ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=OZjymUGNKE1KxQKlMqWQ/o3mnuKrFoO5ab2CZtbpF/mmyHSlU9IHL-CjLq0V4P/AXLAF2eKuFi17OyZR6BV, stripped
./ngrok/ngrok_i386_Linux:             ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=IHR5moR-d-uO5v0zXreO/1fKcdXpBsmr8oJ48tmFo/tOMupoWNr_KpwoFgVnEg/NTPmPbKm1lDhFzk1Ztb5, stripped
./ngrok/ngrok_mips64_Linux:           ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=ohGUryGEiftnkIU_rY7c/JZJTX9syh0Y1lJRa7T2H/EN5-sFHnDTQzftajDG3l/KS5fPed4zybxRHdi0acY, stripped
./ngrok/ngrok_mips64le_Linux:         ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=lEBDj7Zdp0gzhC9d9my-/fDBpE2bbS3EeRWBl0Gel/rbjUKUEyRW35DyKD8lS4/qpebjGwgyON3_giw216f, stripped
./ngrok/ngrok_mips_Linux:             ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=OkaKzq_6SiiBsY14bYLj/B5n_5MNjMw6bkdQvNLy1/qnuhokgIN_Oenh_SoVgr/5xlYsLVj4RQ4LvhaePC_, stripped
./ngrok/ngrok_mipsle_Linux:           ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=wrNb-n4hxMU7fuNyhYy6/8DcXSx55TWQvZbbAm-9Y/wTU0JZjMmLJlmAebhOsu/ZtpMgOvmlByN6HaW-_dg, stripped
./ngrok/ngrok_powerpc64_Linux:        ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, Go BuildID=vr8TMF_L6OrGnS9FH4cn/zlOWPBHWD0hV_BdKfGiC/5FPHFIq5XLqEQmo8OgQz/XK1t-Ldhtrh4wUwJieiY, stripped
./ngrok/ngrok_powerpc64le_Linux:      ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, Go BuildID=dQhc80-TeO_CAIIXkpqu/TSVvga4grIbIvw1vOhIa/qS8tMBTeZCb1oeqxR8qw/3isPaLwA1G3kB3PgsYrL, stripped
./ngrok/ngrok_s390x_Linux:            ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, Go BuildID=xYrGoe7VdgwTWbn1ZNp_/okpS-z7O6oHP3KfLv8dY/CLdzBbdhuAJBAsMauJUm/rXfMkCo-x8VELOGwtbMK, stripped

--> SHA256SUM
9856f5b427d5501f8dbe8912da3adc47a6c8b6165baf2a74eab29c2047206c85  ./ngrok/ngrok_386_FreeBSD
021e698af6ccff051184e72bf02de4a5ce45b8e4ace28e000f004e8af841db23  ./ngrok/ngrok_aarch64_arm64_Linux
da5112d50a4b4d27163373effff66a09acaa966a733be4197cc96ca5776432fa  ./ngrok/ngrok_aarch64_arm64_macOS
0e3d93e71a0aceeacca4b9a720d92002b0a7c7f30ccac564326a72d58b7a8a69  ./ngrok/ngrok_amd_x86_64_FreeBSD
89212baa906d970831a97a7cc080bea2df32f4b18c2ee71c0f16c48d84d95704  ./ngrok/ngrok_amd_x86_64_Linux
cd00faa7d614efc93fb82bcebb6c788a2f91ada363b61d98b62a982f391c1257  ./ngrok/ngrok_amd_x86_64_Solaris
4e7f39466761f997f0419faab790da43ec915180d05d48c848e089bd93d84df5  ./ngrok/ngrok_amd_x86_64_Windows.exe
f82d9521e8cb4d8e08b0a2b7d7f6ff4c4db2123c64d9e02ed59de71b8c6f98c5  ./ngrok/ngrok_amd_x86_64_macOS
849a5752e4fe094b4df3493017c68e2ceeaf202b4e6c76bd29fc750df3912159  ./ngrok/ngrok_amd_x86_Windows.exe
5b10c676b7ee76132ac0ad36e4b0dce501298cc37d68441c454c1b6197980671  ./ngrok/ngrok_arm_FreeBSD
8baeb05eab0bf3c4adde0a3aba63ec21cdd53f2ade8d1b556dea716597242fb1  ./ngrok/ngrok_arm_Linux
3bbdd0254291dbb77394cac201d37147b652a76aeb21469d3ba573235e0e4abb  ./ngrok/ngrok_i386_Linux
64bc719f393bf098761650c25c7f525b02979f987684aec42bec4ffdc55a7dee  ./ngrok/ngrok_mips64_Linux
8630bdc12c17f81a4e1b2c912ed63c7f3d73936886ae0399fcd8762a341ad7fa  ./ngrok/ngrok_mips64le_Linux
24f4b13e2ce5429e4407ba67c410480c9e5d76170e8c8f473d56fcf200622b34  ./ngrok/ngrok_mips_Linux
d27daecc860f54b7fe42ffbc774e07d71eb8292fa49064ce3f37073bd1ca5924  ./ngrok/ngrok_mipsle_Linux
282bb657b447005d2747b3850cb392956b587e643ba7f4f9ea86b54120174d81  ./ngrok/ngrok_powerpc64_Linux
5fc3a037777eacf7015b3322ac6f0d5e4e01de49edc8c41b3d3d1e69bc174976  ./ngrok/ngrok_powerpc64le_Linux
d7083807397ce7f6d5131ab844ed726543497c713bbce24dcf8e2431cfd277db  ./ngrok/ngrok_s390x_Linux
```


---

- #### Version
```console
ngrok version 3.14.0

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


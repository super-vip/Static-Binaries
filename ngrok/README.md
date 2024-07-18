
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
./ngrok/ngrok_386_FreeBSD:            ELF 32-bit LSB executable, Intel 80386, version 1 (FreeBSD), statically linked, for FreeBSD 12.3, FreeBSD-style, Go BuildID=oe0-T6HFfVDrreCKy6Wd/6ku6t9-UMIkqHQwbqJnP/rasqypIy1O9_JIWxG2jG/-kfYs9FbbrANYtTPVuZB, stripped
./ngrok/ngrok_aarch64_arm64_Linux:    ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=sA0v5BhVmlyOB9cWNGhf/YB51zmg_b1Ru2S3Zw6lj/vf9ajpXewrzKcOoI0HB5/rVbiswE9-09E9mm6l5ia, stripped
./ngrok/ngrok_aarch64_arm64_macOS:    Mach-O 64-bit arm64 executable, flags:<NOUNDEFS|DYLDLINK|TWOLEVEL|PIE>
./ngrok/ngrok_amd_x86_64_FreeBSD:     ELF 64-bit LSB executable, x86-64, version 1 (FreeBSD), statically linked, for FreeBSD 12.3, FreeBSD-style, Go BuildID=-34_dnoIUrNRM2fN-d2P/lXDRNJnMCVOv-udwyuhm/jfe_jEGe2WmKSyixy1ZG/taW3wgLSTYKqxr45W9rB, stripped
./ngrok/ngrok_amd_x86_64_Linux:       ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=zo-BLLpW9jVwJN-Jtbwl/BBIYB3LGwBNL6TELSFBz/nhMuGtl7gKk9JqDxItya/Da8AFwH-G0GByOAFoQu_, stripped
./ngrok/ngrok_amd_x86_64_Solaris:     ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib/amd64/ld.so.1, Go BuildID=t-InjsA7zyzmVantNXcV/IinG1b03cDATFxD6FEsS/gtNj3hOegBsZ77DcioYt/makr0vpfxVueWDs7YTE6, stripped
./ngrok/ngrok_amd_x86_64_Windows.exe: PE32+ executable (console) x86-64 (stripped to external PDB), for MS Windows
./ngrok/ngrok_amd_x86_64_macOS:       Mach-O 64-bit x86_64 executable, flags:<NOUNDEFS|DYLDLINK|TWOLEVEL|PIE>
./ngrok/ngrok_amd_x86_Windows.exe:    PE32 executable (console) Intel 80386 (stripped to external PDB), for MS Windows
./ngrok/ngrok_arm_FreeBSD:            ELF 32-bit LSB executable, ARM, EABI5 version 1 (FreeBSD), statically linked, for FreeBSD 12.3, FreeBSD-style, Go BuildID=kR5JNSFnDmNtAlZO7V1a/tgu2rWgTRjF5eALlfgOT/C1ocy7xvneKylEvihmsK/boEnl6sZQe-DZ3eB0MFL, stripped
./ngrok/ngrok_arm_Linux:              ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=Uklyg2coeUPNFC8uBdSe/_-R5hmStLmLE_M_F2HAB/-ygg8NOus2klgUH-9x9o/Ojt1gl9B8MO7PxuJJPcs, stripped
./ngrok/ngrok_i386_Linux:             ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=Sidp8f6EnZoc2pQj57r_/ij0qZSGZz42HjFPfYBV8/2Ri_ZxARDsiQGx9nB1SI/Xg2WIG5et4kec2gvb4Ca, stripped
./ngrok/ngrok_mips64_Linux:           ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=nmS4jN0CRdoKLG-imuU7/z11Pnos8BYBRGR86M0Ko/O8FObqv4TssOnRP6NcCz/trkCX95YdJRO_BVO3Gcp, stripped
./ngrok/ngrok_mips64le_Linux:         ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=FhjYpT9hAubCBHFMmWHa/lkSiR5A9xGxnzN98_qqN/BiVfjMhRirEhBaRpYuKD/9d3qvoKuaiVsOYAOU6C1, stripped
./ngrok/ngrok_mips_Linux:             ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=onYox2mGCuppVo2AkbRC/X8fNMMUWpMSKux6Os46d/H2ZFZtFBqz0RkLkD1QX0/uf2TlgltQU6TZ3QoYjlQ, stripped
./ngrok/ngrok_mipsle_Linux:           ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=8yS7MKH_cT-Vvbcs6Ow3/XgugIQcfbIAdQSBLd2F-/qNEADdeNDAf-8zsUk-6c/iLxZJSxOVbaq3wllywu8, stripped
./ngrok/ngrok_powerpc64_Linux:        ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, Go BuildID=LBq2nWiuNS93dn5f_iwx/2rFtZTV3DmfWIEOKvpS0/ctprRzT9bgPIACiv3cOJ/_GjZQAUwVKNfCgnFEmG_, stripped
./ngrok/ngrok_powerpc64le_Linux:      ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, Go BuildID=iYxLZIe82qjUQf6LB9k9/8hAo5R4kbF3HQ9U2XFTc/FRxBXNZ3RVCOt6tu_R6b/4vtaTf0mtHqtomoJnWaP, stripped
./ngrok/ngrok_s390x_Linux:            ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, Go BuildID=1yweZ3UuUmquU35O8nzC/JCpTQV1iKvawqZJX_6U1/PSLbCwqjyzx0kdxdeHZ7/C-YfLu4Y84csW_LGDNIr, stripped

--> SHA256SUM
592042f6e73f083357b191d7e039d4a3350b0576ca7634202f47f033838bcc8a  ./ngrok/ngrok_386_FreeBSD
cc827724c59fe508cec6f8b16a22dba5c06171acadc224034679f9cc34b13c03  ./ngrok/ngrok_aarch64_arm64_Linux
aa03fec3b1c111c799d0f5be95a80325ad08448a928b3985fa8a27578cf4b883  ./ngrok/ngrok_aarch64_arm64_macOS
ff14e567d92acfb9f6a8a7b2dcbaaa495277dd52ef1ca74df8ab92fba7f8eed5  ./ngrok/ngrok_amd_x86_64_FreeBSD
f51399b0fa270d811a81591caa5f0893a56ddea5d3a5f3abc6be46c6494fc20e  ./ngrok/ngrok_amd_x86_64_Linux
75f7addae60888fce7b28cc18470101950d3cf5dfca6ff26d29af70af432e8d4  ./ngrok/ngrok_amd_x86_64_Solaris
ab2a923836ca2886a3b7e42d7054eff3e212829b84ea91db03adbdabc479140f  ./ngrok/ngrok_amd_x86_64_Windows.exe
e03fff765e0af568f4131ccf3abe5c5f93fc3b0ebad5a10e115c8012cdb1482b  ./ngrok/ngrok_amd_x86_64_macOS
e5ed50e5b186eafbe6891ee44a491068864b1a1edecfe6f81daa1dfdbc627f47  ./ngrok/ngrok_amd_x86_Windows.exe
e8e877bb3352830b39695f54befdb5455afaaf069d4f327ada267186e2735496  ./ngrok/ngrok_arm_FreeBSD
5d82d847795ad85f0b7d8768e5f6fb8cd8668fc58e4f1434de4601b4e6c920af  ./ngrok/ngrok_arm_Linux
af76a48e1c6763faf5ba54ac74c52828b95547ecd6ad60631b11bc3118863a2e  ./ngrok/ngrok_i386_Linux
b41da9fc4342f5d690d4ef483d33e4681f66909feb863f18810a8a7af75f9119  ./ngrok/ngrok_mips64_Linux
bb6ba0b207d67f0811fffc304b5d09f1282b956be8e1f1033f63d9228ea912db  ./ngrok/ngrok_mips64le_Linux
2c8192ee3bd33d6cddeac3ee53ec09c58d92564fb79230ecf06a8dc188951c6d  ./ngrok/ngrok_mips_Linux
dcd33d8e84b9ea5970d2f232ac4fab9306ac8efccc23c90295834e9509144a35  ./ngrok/ngrok_mipsle_Linux
d4b281f9204e3c49c1e6642918511c512521bcfb697e4aa478debd8867fc6fdc  ./ngrok/ngrok_powerpc64_Linux
a3443126a18edc74eb9bae04009d7cbea06b2e819c018ce9fe17cf118ad13e0d  ./ngrok/ngrok_powerpc64le_Linux
839158c996301af873524a24918f55a7a620bbf18556d80264036fe3ffc984c0  ./ngrok/ngrok_s390x_Linux
```


---

- #### Version
```console
ngrok version 3.13.0

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
26M  ./ngrok/ngrok_386_FreeBSD
28M  ./ngrok/ngrok_aarch64_arm64_Linux
28M  ./ngrok/ngrok_aarch64_arm64_macOS
28M  ./ngrok/ngrok_amd_x86_64_FreeBSD
28M  ./ngrok/ngrok_amd_x86_64_Linux
27M  ./ngrok/ngrok_amd_x86_64_Solaris
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


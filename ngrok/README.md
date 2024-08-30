
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
./ngrok/ngrok_386_FreeBSD:            ELF 32-bit LSB executable, Intel 80386, version 1 (FreeBSD), statically linked, for FreeBSD 12.3, FreeBSD-style, Go BuildID=rsn4K5hBZeZoKefsbdZY/tIgumjBcyQY2-RTEMCQK/qo0f-p24i5RzUoornp7z/0kV4xOYCZARFkOVRdJfv, stripped
./ngrok/ngrok_aarch64_arm64_Linux:    ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=Hpk1ycVjzS8CE-VnFLL2/vbV4GI9uwWL42Zv8kgYj/MTFOUvloYfMY0HX4kuik/P6vsekU8XAn6wbGpl6gX, stripped
./ngrok/ngrok_aarch64_arm64_macOS:    Mach-O 64-bit arm64 executable, flags:<NOUNDEFS|DYLDLINK|TWOLEVEL|PIE>
./ngrok/ngrok_amd_x86_64_FreeBSD:     ELF 64-bit LSB executable, x86-64, version 1 (FreeBSD), statically linked, for FreeBSD 12.3, FreeBSD-style, Go BuildID=0ggO5X4W9D4Otim7AdJ5/3d3AsAy-6CZxUOVwvNUJ/rJu7358jWB-OenaaqFM4/rFRGqpLQHDpSJODRxxNc, stripped
./ngrok/ngrok_amd_x86_64_Linux:       ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=s65xXVS0kf-vf-t7CB37/e24N9rQQNlQDGKQcZ2Sv/XWZbXmh5zuUIrW8Oohhd/xJwlETvB_29qGcWKss8w, stripped
./ngrok/ngrok_amd_x86_64_Solaris:     ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib/amd64/ld.so.1, Go BuildID=bkwde_Z4SaNPH75T2kr4/j30lW7os8eLeyP6M6lHm/azvplKHXjWIFhvMFxOeL/-GZS-Y87fgh_tzM_n2jB, stripped
./ngrok/ngrok_amd_x86_64_Windows.exe: PE32+ executable (console) x86-64 (stripped to external PDB), for MS Windows
./ngrok/ngrok_amd_x86_64_macOS:       Mach-O 64-bit x86_64 executable, flags:<NOUNDEFS|DYLDLINK|TWOLEVEL|PIE>
./ngrok/ngrok_amd_x86_Windows.exe:    PE32 executable (console) Intel 80386 (stripped to external PDB), for MS Windows
./ngrok/ngrok_arm_FreeBSD:            ELF 32-bit LSB executable, ARM, EABI5 version 1 (FreeBSD), statically linked, for FreeBSD 12.3, FreeBSD-style, Go BuildID=aK1HN_iUKCyqasGFaR8j/ZOSjXLRfWdwlsrB2cH0J/5DSRDtmOSYDaBhB_ZV2a/Dw5su5zi2QDez89-gmp8, stripped
./ngrok/ngrok_arm_Linux:              ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=BYqH5cbTdpHI2VEvZkBj/o3mnuKrFoO5ab2CZtbpF/mmyHSlU9IHL-CjLq0V4P/yNYJne65Y-1wllcA23sn, stripped
./ngrok/ngrok_i386_Linux:             ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=--7gBsNEF42Mh4hLJWpR/1fKcdXpBsmr8oJ48tmFo/tOMupoWNr_KpwoFgVnEg/k7d_sRWdxg5BfpEF6ZH3, stripped
./ngrok/ngrok_mips64_Linux:           ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=cuxMTAChOVZQrjGZX2os/JZJTX9syh0Y1lJRa7T2H/EN5-sFHnDTQzftajDG3l/-SVRVrttLIORk2_YVWpc, stripped
./ngrok/ngrok_mips64le_Linux:         ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=pX2IM7IzR83A459HwJIJ/fDBpE2bbS3EeRWBl0Gel/rbjUKUEyRW35DyKD8lS4/GhBt12e7pVyPx0n63MuC, stripped
./ngrok/ngrok_mips_Linux:             ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=zsUvI99y-iECYHNpwUeo/B5n_5MNjMw6bkdQvNLy1/qnuhokgIN_Oenh_SoVgr/WJ3WzPGodDgQi-L4ngOw, stripped
./ngrok/ngrok_mipsle_Linux:           ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=OwnJH9sq355aTylREdKH/8DcXSx55TWQvZbbAm-9Y/wTU0JZjMmLJlmAebhOsu/fsaM2YwPnzjJUMzFjpNd, stripped
./ngrok/ngrok_powerpc64_Linux:        ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, Go BuildID=mQSi8RHdkHR1dNlNFTdT/zlOWPBHWD0hV_BdKfGiC/5FPHFIq5XLqEQmo8OgQz/6Fp4j2FUt2YZTfLDfDHA, stripped
./ngrok/ngrok_powerpc64le_Linux:      ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, Go BuildID=kh9Sp0Ov8kI2DIpNGNp3/TSVvga4grIbIvw1vOhIa/qS8tMBTeZCb1oeqxR8qw/HMNzshwESBOj6893nowS, stripped
./ngrok/ngrok_s390x_Linux:            ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, Go BuildID=qaZ1Vl7T4G0lUeBrG6Hc/okpS-z7O6oHP3KfLv8dY/CLdzBbdhuAJBAsMauJUm/K8ZF0g76MtethM0PEpxS, stripped

--> SHA256SUM
f349db2d49e3e716e35390de8c4dcc76a0afeef6ce1992b4771fb1a08b9bdc2f  ./ngrok/ngrok_386_FreeBSD
71d652d7687ea8f025393848e4fe5f7fa1791aadce7a333b5f9295e3d581262e  ./ngrok/ngrok_aarch64_arm64_Linux
97ecd84b4bc9ec107dc56f99c9e22de5c453f3177225a3558aa7bd89761b9902  ./ngrok/ngrok_aarch64_arm64_macOS
5086ff0b2192d98d7ee20a7f611409b46e1f008c5120bb0be58b2ad04c33a97a  ./ngrok/ngrok_amd_x86_64_FreeBSD
1d22288be49bc112524a5c6006b4872852991384a3d793039006a49985118dd8  ./ngrok/ngrok_amd_x86_64_Linux
84f494e8e95c6fc9696ba7242e4f976e91ff8aa61fa5fb249aea92de1f20fc44  ./ngrok/ngrok_amd_x86_64_Solaris
00856d8cd9d02782a8cd52341ab1485a16ed3ad713332eff8812c8da520e9c65  ./ngrok/ngrok_amd_x86_64_Windows.exe
2d7d5a584579149369158bb548465f602095f0fc0a0ecadb5ee005bc7232468e  ./ngrok/ngrok_amd_x86_64_macOS
2a80f7cfaf4e6f9aeaf037d49c00abc88e057dd4cc8ecac6743b916daaba7350  ./ngrok/ngrok_amd_x86_Windows.exe
a2d5c884bd0e855bfeaba783d8f292b56383679d5c486249ba6969bc5a6164ed  ./ngrok/ngrok_arm_FreeBSD
5cf6b02f610c7ed878d14f7e19c8e1bcee3e70e950b24b135523b47a709fb13b  ./ngrok/ngrok_arm_Linux
38086d71e996f3936cb3b6b14025ba25b2610a5c2191953155e862eb48915fe1  ./ngrok/ngrok_i386_Linux
2a647dec0fa51dae82aee6c325192a1326b6463f883aed764e03d11a897c1c54  ./ngrok/ngrok_mips64_Linux
47c208db4c39102d6d8d473b880a61dfcae54252f455302de7e99bf9d258cefb  ./ngrok/ngrok_mips64le_Linux
2a0fbc6860ff2d7da854e749da1db8e0ef9ce7064af25868c7dacc5a29d54cac  ./ngrok/ngrok_mips_Linux
71da15522d084cc3eb436d18cf95fd49901fa5382153c759e8323427585e0a0b  ./ngrok/ngrok_mipsle_Linux
45e0fb1df61abcd4b06879ec864c2412fe1bdc1abf828f0869eb4437c1dc5d47  ./ngrok/ngrok_powerpc64_Linux
10db709acca074e4d4b5efef0f4bb90adf6587d4fbf86b7d6ebed5bc6b9e307f  ./ngrok/ngrok_powerpc64le_Linux
c734600fcfbd75d9c2a5d90435f6222af72ecace150d24442c7cfe10f931e775  ./ngrok/ngrok_s390x_Linux
```


---

- #### Version
```console
ngrok version 3.15.1

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


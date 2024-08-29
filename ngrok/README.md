
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
./ngrok/ngrok_386_FreeBSD:            ELF 32-bit LSB executable, Intel 80386, version 1 (FreeBSD), statically linked, for FreeBSD 12.3, FreeBSD-style, Go BuildID=3EwJLoATjab6OokAPr4Y/Zdw1DhERpe-4mAkUN8nH/ulBGbijxcXwFH2LXXYag/l-kurpxPylavMPjBX5SX, stripped
./ngrok/ngrok_aarch64_arm64_Linux:    ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=fYMCrSopQQmW6N3T6z99/Ui21bkUVmtKajULpNb6o/aXAAxOnjSkx1t89c7oKK/qeXDcvhZi5fRPyhBrnwS, stripped
./ngrok/ngrok_aarch64_arm64_macOS:    Mach-O 64-bit arm64 executable, flags:<NOUNDEFS|DYLDLINK|TWOLEVEL|PIE>
./ngrok/ngrok_amd_x86_64_FreeBSD:     ELF 64-bit LSB executable, x86-64, version 1 (FreeBSD), statically linked, for FreeBSD 12.3, FreeBSD-style, Go BuildID=YFohn7g3XLa7nz3UOPzV/0gu5KJRtZNCrkupfnPTY/KbGRboN1SLAFnxhPVIrT/cBUmZSz9B9UqEySS8vkr, stripped
./ngrok/ngrok_amd_x86_64_Linux:       ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=Vty2NT4F_pKqGZ-dMnxh/4mP4vwl_jDTNPqKH7WbU/nBm0OOXOvf2VbCuptMcd/cZGj3wUbu4Rj9nEZ6D2V, stripped
./ngrok/ngrok_amd_x86_64_Solaris:     ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib/amd64/ld.so.1, Go BuildID=HHs8BsShwD6bFw4pjEjN/fNbJGwta6o7K0arYmUku/Ik4a-f5vydtYQVggUJ-D/dePzOUKWnXdXWiGf4D2h, stripped
./ngrok/ngrok_amd_x86_64_Windows.exe: PE32+ executable (console) x86-64 (stripped to external PDB), for MS Windows
./ngrok/ngrok_amd_x86_64_macOS:       Mach-O 64-bit x86_64 executable, flags:<NOUNDEFS|DYLDLINK|TWOLEVEL|PIE>
./ngrok/ngrok_amd_x86_Windows.exe:    PE32 executable (console) Intel 80386 (stripped to external PDB), for MS Windows
./ngrok/ngrok_arm_FreeBSD:            ELF 32-bit LSB executable, ARM, EABI5 version 1 (FreeBSD), statically linked, for FreeBSD 12.3, FreeBSD-style, Go BuildID=WCOK_CS2ckefu-u9cH_T/rzzFV-Id9UBnHGOwKurj/XmZejDzZPmULVYsgY6rh/-U7gHRrrFoFxH2Wng3DC, stripped
./ngrok/ngrok_arm_Linux:              ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=Xo8e1KhaGIZPIYvfEpYL/AchR8p1ZGqkaY8Cy4oME/gdmklgzXfxDB1GAAe67D/YyKSQolnjo7BrC-D2R_3, stripped
./ngrok/ngrok_i386_Linux:             ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=LyC9CTnqamMhpgFcsyj6/vvY_bKKGb0EHg-aUGzDA/Owm_WYhSsEKdxA0fPLdj/tfCuRAS_wnx1cs8mJrIq, stripped
./ngrok/ngrok_mips64_Linux:           ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=jJKfM6zMAVwH5TAuMdWU/BQw6H5ZAV6-PIBcv1I-D/vP0SlfXMtKMx3LSQa4wd/orotFiASuWrpGvYQV7-r, stripped
./ngrok/ngrok_mips64le_Linux:         ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=8wDVXbie1tdPHu2DTpo5/sOUPur66WgBZ238KoOR-/cAtH6Bw6qpHe46JhVIfp/Di0R1IWhCViZx7VfWFZS, stripped
./ngrok/ngrok_mips_Linux:             ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=C_jvGAw0uppSUarktQSw/uK4VS3fvhLHXbOJlh9NQ/6XSWJpwBuBqEumacvUz4/c2S8q7RJDKGMxbt89VT-, stripped
./ngrok/ngrok_mipsle_Linux:           ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=BhrRpgdsXq3qcYq51Jdc/KnUj2DccgTwU-_m5J2nn/QQcMe8_lW7eHP-zaZWsi/K4t-18lZKOIrliXA9d0h, stripped
./ngrok/ngrok_powerpc64_Linux:        ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, Go BuildID=BdFCz7IDwW4oDDeogkIn/p2BRSmmrh6KQ6zDFV2I4/rA7bWdBReH55rJsJh6RY/SFtEUWmYLeJ5srhUVWKi, stripped
./ngrok/ngrok_powerpc64le_Linux:      ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, Go BuildID=cNFQVapW9BtVxxvgTJ95/_FU3OO3v_dza8xagm5-1/TwBQyTytofYgXkJktHHD/1QI04KEOdOByWjmbMduk, stripped
./ngrok/ngrok_s390x_Linux:            ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, Go BuildID=5stS91U29MXn-c8pBQZn/s3dcNI5DVRJtPDpRv_B_/MZPkaEB0PZg7WuDLg-Ss/suToxCtw11ksozHujJVD, stripped

--> SHA256SUM
761c55b8df6af39bb084fcc6c7a8b73dadb0b6034149e8116b4b88bde965855f  ./ngrok/ngrok_386_FreeBSD
94df863a4fc1d19ee5c32580b79012cd66401d0110baf3d4f977c045813cd041  ./ngrok/ngrok_aarch64_arm64_Linux
b6dd09abfe8e7bdb239cbb720afe5f46bee820b2ec7a99bc467c33c4df93a5ba  ./ngrok/ngrok_aarch64_arm64_macOS
76e440790ac5a4b0ef4d25623b2009ebb3d0d4022a40791ad95464b925efc3e9  ./ngrok/ngrok_amd_x86_64_FreeBSD
5532b675dd30ea4a90244a2ebc4648441ac1937e2cf6f32fd1341c2c244c0c94  ./ngrok/ngrok_amd_x86_64_Linux
ec2bd6bd4a8b8fedd497bf378f3bf071534df0324cd4e42591cb92c2b2c60718  ./ngrok/ngrok_amd_x86_64_Solaris
2e65be74a772b294492c5de56dc248a1495e317f1a824e6e17e5e0ddbca31f8d  ./ngrok/ngrok_amd_x86_64_Windows.exe
1a25e6e18b8e69b94223194f6423030557498798a6cbad1c48a82c4b3dd68c2e  ./ngrok/ngrok_amd_x86_64_macOS
2142d80e236b7ee193c0c54bd2139ba248ef9b47cc6533f102b747b8ee56bbe0  ./ngrok/ngrok_amd_x86_Windows.exe
149c8d008f20953d9e0592a0b48d03c4a1ecc62c0960752811732dd72ecf3c60  ./ngrok/ngrok_arm_FreeBSD
24ad8aaaac7633e05dc5fee032ae9a52fb38cd6f28bc3b39f2851230ed04e448  ./ngrok/ngrok_arm_Linux
2da41b9b070dce5aec61a8c6e5dda2ac5b4af883aae1b06377a061794e8d7258  ./ngrok/ngrok_i386_Linux
cde9feaca155724fc13218c7abd268d946dfe7c9177512697486324d31a9f64a  ./ngrok/ngrok_mips64_Linux
6ae486a6c4213cc3a494232421d1b12ffb07b1be2637d6bb6011c377e86f3856  ./ngrok/ngrok_mips64le_Linux
3d31dd99fe8f767733a9113c6b2b5dac777d555d05307a46d45502cdc28c7342  ./ngrok/ngrok_mips_Linux
75bb6373348f00e3abb852e980d117367ca5cd7d2db13009ed2648251364dcda  ./ngrok/ngrok_mipsle_Linux
8289aabd5fc22a8568e657b4c08eb61607bf5aa1cd59e01f3fd1286c527f3151  ./ngrok/ngrok_powerpc64_Linux
63cf26f8a24f423e3aab76b7aff8ad8b778f6e5bf3f18370b7216208e0dd54cd  ./ngrok/ngrok_powerpc64le_Linux
0763055fa717e5bf7e907f66b96be562c8e07d123abcba26d57ec371ffea922a  ./ngrok/ngrok_s390x_Linux
```


---

- #### Version
```console
ngrok version 3.15.0

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


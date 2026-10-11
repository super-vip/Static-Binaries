
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
./ngrok/ngrok_386_FreeBSD:            ELF 32-bit LSB executable, Intel 80386, version 1 (FreeBSD), statically linked, for FreeBSD 12.3, FreeBSD-style, Go BuildID=7znIugCPedEIyCQzK68X/uweSIM16mgXBY_zkk5Lc/3VXZgS4odd65FaKdnXAk/9tFZ0wl9aZ8-uTtdwuKl, stripped
./ngrok/ngrok_aarch64_arm64_Linux:    ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=MVd3IYGo4MJ9FucKpVwl/yHyCvaZ0BzycxYwdy8Ld/UrQ17-CdDkEKng96uP32/T5S9kqIYVcsTfOJzC_vb, stripped
./ngrok/ngrok_aarch64_arm64_macOS:    Mach-O 64-bit arm64 executable, flags:<NOUNDEFS|DYLDLINK|TWOLEVEL|PIE>
./ngrok/ngrok_amd_x86_64_FreeBSD:     ELF 64-bit LSB executable, x86-64, version 1 (FreeBSD), statically linked, for FreeBSD 12.3, FreeBSD-style, Go BuildID=QTqdZ_ctjSWk8PM79rfU/0BNL0qSVWCpD7najD4UF/K3RFIlS0sqb6ZLsccym4/IxTv7hY0_Xx6Arff4ZP9, stripped
./ngrok/ngrok_amd_x86_64_Linux:       ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=0GxbkmnzxKKUum8poY45/PmOaWcyJSzagmmkBGHZy/fwEv7x4hKpzcEXhHvlCd/1M_vM_SCuzuScMpLsByP, stripped
./ngrok/ngrok_amd_x86_64_Solaris:     ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib/amd64/ld.so.1, Go BuildID=mQ_bq4e8pZ5bGpm9X3UX/kdyZQmZbYluJqmLrzE1w/1Y4FtJUs1RtPWSTYCPaP/HJMG4y-81qjOl9ky0N0K, stripped
./ngrok/ngrok_amd_x86_64_Windows.exe: PE32+ executable (console) x86-64 (stripped to external PDB), for MS Windows
./ngrok/ngrok_amd_x86_64_macOS:       Mach-O 64-bit x86_64 executable, flags:<NOUNDEFS|DYLDLINK|TWOLEVEL|PIE>
./ngrok/ngrok_amd_x86_Windows.exe:    PE32 executable (console) Intel 80386 (stripped to external PDB), for MS Windows
./ngrok/ngrok_arm_FreeBSD:            ELF 32-bit LSB executable, ARM, EABI5 version 1 (FreeBSD), statically linked, for FreeBSD 12.3, FreeBSD-style, Go BuildID=dcmnYh2fwdX6xApEay_5/dSmtIaJEW_i_90OsJF1F/akQXJum0mOsyHTc0v714/6Jfe7Yb-FqFqqfkfrTsc, stripped
./ngrok/ngrok_arm_Linux:              ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=VQtvWH1IA6eJxuR51dCM/8_vaPkw2RZs7-_9PsPKA/BoH2Wk1ca8XW9aV_QaKG/GSez6TB_eUQ99FmHTM0V, stripped
./ngrok/ngrok_i386_Linux:             ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=W0IqW7OX6tdhuPV-_9u3/-J0wDEFPItmjWWNNCavq/sKNYpRbFPG_Kzt-STBOU/rVhLt83zsl4e85zr3-8I, stripped
./ngrok/ngrok_mips64_Linux:           ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=xWKU163lLF5rFEBqHMhP/DftfBEaS8vwlC0f1Nzv6/Irzftm3Y5fWbvArX7mai/bGRr6rXVejtgI_nTnLY3, stripped
./ngrok/ngrok_mips64le_Linux:         ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=VUOF0SBdBIS8IKzUQJGs/pjWAT_3niEQ398qLQQ8Q/0_86f29yW0ISoACAtCXc/FeHJJ-t9jaqEJJsFWby_, stripped
./ngrok/ngrok_mips_Linux:             ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=UI_Nrfc_q0J4JX2WIKi1/ha4UX__ykMxejH0mZIi-/0-AxRvwJHNXza_GqNleN/UfZZY64pRO4fXk92I_oK, stripped
./ngrok/ngrok_mipsle_Linux:           ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=DMILZkrD70t91lKSuH0u/RNRHGvokV-NTTpBFYtEu/Teok4nwmZXZVlHjwcC8k/APT0mAHqHIrGU1oAEygz, stripped
./ngrok/ngrok_powerpc64_Linux:        ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, Go BuildID=3yOP3mOCZGIVYvFXhfH1/PSuq1uaCa30TQCK6Y0aW/ivq29ljYKCGPlw3PGbRI/V8-o9oCO7NsR39om_YQS, stripped
./ngrok/ngrok_powerpc64le_Linux:      ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, Go BuildID=9-t86mCHNZsmViOwrcYm/cQolIDFUKX5pL8Vy4v6D/rbg17-6zixVmujWu7Okt/5SpHNZ1YrrIhkpmp161I, stripped
./ngrok/ngrok_s390x_Linux:            ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, Go BuildID=LGLv6qX6D2ym1iabYIZw/0lXW8EPQFlu3wbAnqlOb/TbiTON04qaGb3WY9P1UG/ygg4lR5sigCj5pSVupV1, stripped

--> SHA256SUM
d4f0659307036d4c7340de15f34422da28247efe917821e5c61dec2ef02173db  ./ngrok/ngrok_386_FreeBSD
0dbdfdf94b3acb777741e9eeeb27a256cb1975b7d366d1ba404804b863b8fcbb  ./ngrok/ngrok_aarch64_arm64_Linux
9cc3fee7d81157e6bc645f160f6aa5562577c4b9f72db8675143e16d07703816  ./ngrok/ngrok_aarch64_arm64_macOS
ab0252155857677c129d7c94d9d8a0f1003df406c334b326dd2f47271222d25c  ./ngrok/ngrok_amd_x86_64_FreeBSD
62a78928edd4d313a414ac6f3ea9c0a8bf5d267b757210d5d03dfaf0c487fbce  ./ngrok/ngrok_amd_x86_64_Linux
3fc74386e237b3a0ec9581ca3b4a6516d6affac617425c80a5bb5af47f0f3862  ./ngrok/ngrok_amd_x86_64_Solaris
af680c7438e1794e50b22460360fcc0df00077c0565515385cf40ae3e50ab69e  ./ngrok/ngrok_amd_x86_64_Windows.exe
9a1319caf566ee7f85c1a9b2982ee95c08bd549e90d56ac99ef863d5da92b4a4  ./ngrok/ngrok_amd_x86_64_macOS
e6038c7b7427118122ad25e84df4eeec049a10877153841247d05a3480f038eb  ./ngrok/ngrok_amd_x86_Windows.exe
ef4015701579e9dc3c6908e8b01962672cf1e798c61ee446b00f727d5ba9ea9a  ./ngrok/ngrok_arm_FreeBSD
6e7b4723a3a2c936157e4ec7be0bcbf95b49c672223ba0621d54165e8009fd78  ./ngrok/ngrok_arm_Linux
4d0daf0210b420b61fe2cb2b31ead38f799ee12b26bf171ff9de0f2f7181318c  ./ngrok/ngrok_i386_Linux
3cfb6246b9562f4056e9b4decb23ae38a4188853ca8af7b780534a6ea7ea0a91  ./ngrok/ngrok_mips64_Linux
237f704652eb3239aca5ecb4b3fe0d183f1b3423056427e09ac70e45d99e5cce  ./ngrok/ngrok_mips64le_Linux
9323165bf2a534e10b116b14ba7c71322a5dd0e075b38365f6b1750622ee3fd8  ./ngrok/ngrok_mips_Linux
b81a18b1fa9334c3e5f5675a9143a6fc54939d2cf8beaac604cc79409daf7075  ./ngrok/ngrok_mipsle_Linux
583453d8701b36fcc44d905d270e8a0540f42ebbe6416e9ee95eb214f8f5e283  ./ngrok/ngrok_powerpc64_Linux
a162513832e26096dd03ed85f189881592313f1f907ab2e5437c5c97a4d9e25d  ./ngrok/ngrok_powerpc64le_Linux
958305fc711e541f272ea15095b9cf6e9c1dd80ab5550c789bdd6d629317925f  ./ngrok/ngrok_s390x_Linux
```


---

- #### Version
```console
ngrok version 3.18.1

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
29M  ./ngrok/ngrok_mips64_Linux
28M  ./ngrok/ngrok_mips64le_Linux
28M  ./ngrok/ngrok_mips_Linux
28M  ./ngrok/ngrok_mipsle_Linux
26M  ./ngrok/ngrok_powerpc64_Linux
26M  ./ngrok/ngrok_powerpc64le_Linux
27M  ./ngrok/ngrok_s390x_Linux

```



---
- #### Download [TailScale](https://tailscale.com/kb/installation/)
> - **Sources**
> > ```bash
> > --> Android:
> >      - Built using dockercross (Dynamic Only)
> >      - Currently this fails with: loadinternal: cannot find runtime/cgo
> >      - Maybe : https://chat.openai.com/share/541d5f9a-c40d-4eed-8f62-f9e6fa97022a
> >              : https://github.com/ykasidit/android_ndk_c_rust_go_builder
> >              : https://github.com/xxf098/go-tun2socks-build/blob/lite/.github/workflows/main.yml
> >              : https://pkg.go.dev/golang.org/x/mobile/cmd/gomobile?utm_source=godoc
> > 
> > --> Linux:
> >      - https://pkgs.tailscale.com/stable/#static [ Stable Releases ]
> >      - Binaries for 'ppc64' | 'ppc64le' | 's390x' are compiled using go crosscompile
> >      - 'tailscale_merged' is a combined & smaller binary with some omitted features
> >        - !# https://tailscale.com/kb/1207/small-tailscale/
> >        - Build Flag: CGO_ENABLED=0 go build -o tailscale.combined -v -ldflags="-s -w -extldflags '-static'" -tags "ts_omit_aws,ts_omit_bird,ts_omit_tap,ts_omit_kube,ts_include_cli" "./cmd/tailscaled"
> >
> > --> macOS:
> >      - All binaries are compiled & built using macOS runner Image & go cross compile
> >      - 'tailscale_merged' is a combined & smaller binary with some omitted features, built using same flags as Linux
> > 
> > --> Windows:
> >      - https://pkgs.tailscale.com/stable/#static [ Stable Releases ]
> > ```
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
!# For upx, simply append .upx
!# Example: curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscale_aarch64_arm64_Linux"
!#     Upx: curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscale_aarch64_arm64_Linux.upx"


!#For Linux
--> aarch64 || arm64 [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscale_aarch64_arm64_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscaled_aarch64_arm64_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscale_merged_aarch64_arm64_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscaled_aarch64_arm64_systemd.defaults_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscaled_aarch64_arm64_systemd.service_Linux"
--> Amd Geode || x86_64 [32-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscale_amd_geode_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscaled_amd_geode_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscaled_amd_geode_systemd.defaults_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscaled_amd_geode_systemd.service_Linux"
--> Amd x86_64 || x86_64 [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscale_amd_x86_64_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscaled_amd_x86_64_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscale_merged_amd_x86_64_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscaled_amd_x86_64_systemd.defaults_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscaled_amd_x86_64_systemd.service_Linux"
--> ARM_abi|| ARMv4 || ARMv5 || ARMv7 (?) [32-bit]
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscale_arm_abi_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscaled_arm_abi_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscale_merged_arm_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscaled_arm_abi_systemd.defaults_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscaled_arm_abi_systemd.service_Linux"
--> i386 || Intel 80386 [32-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscale_i386_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscaled_i386_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscale_merged_i386_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscaled_i386_systemd.defaults_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscaled_i386_systemd.service_Linux"
--> MIPS (Big-Endian) [32-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscale_mips_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscaled_mips_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscaled_mips_systemd.defaults_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscaled_mips_systemd.service_Linux"
--> MIPSel || MIPSle (Little-Endian) [32-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscale_mipsle_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscaled_mipsle_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscaled_mipsle_systemd.defaults_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscaled_mipsle_systemd.service_Linux"
--> MIPS64 (Big-Endian) [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscale_mips64_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscaled_mips64_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscaled_mips64_systemd.defaults_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscaled_mips64_systemd.service_Linux"
--> MIPS64le (Little-Endian) [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscale_mips64le_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscaled_mips64le_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscaled_mips64le_systemd.defaults_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscaled_mips64le_systemd.service_Linux"
--> powerpc64|| ppc64 || cisco 7500 [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscale_powerpc64_ppc64_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscaled_powerpc64_ppc64_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscale_merged_powerpc64_ppc64_Linux"
--> powerpc64le || ppc64le || cisco 7500 || OpenPOWER ELF V2 ABI (Little-Endian) [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscale_powerpc64le_ppc64le_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscaled_powerpc64le_ppc64le_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscale_merged_powerpc64le_ppc64le_Linux"
--> risc64 || CB RISC-V || RVC [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscale_riscv64_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscaled_riscv64_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscaled_riscv64_systemd.defaults_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscaled_riscv64_systemd.service_Linux"
--> s390x || IBM S/390 [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscale_s390x_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscaled_s390x_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscale_merged_s390x_Linux"

!#For macOS
--> aarch64 || arm64 [64-bit]
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscaled_aarch64_arm64_macOS"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscale_aarch64_arm64_macOS"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscale_merged_aarch64_arm64_macOS"
--> Amd x86_64 || x86_64 [64-bit]
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscale_amd_x86_64_macOS"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscaled_amd_x86_64_macOS"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscale_merged_amd_x86_64_macOS"

!#For Windows
--> x86 || x86_64 || arm64 --> EXE
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscale_setup_Windows.exe"
!# Or using powershell
-->  Invoke-WebRequest -Uri "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscale_setup_Windows.exe" -OutFile "tailscale_setup.exe"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscale_ipn_setup_Windows.exe"
-->  Invoke-WebRequest -Uri "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscale_ipn_setup_Windows.exe" -OutFile "tailscale_ipn_setup.exe"
--> aarch64 || arm64 -> MSI  
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscale_aarch64_arm64_Windows.msi" 
-->  Invoke-WebRequest -Uri "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscale_aarch64_arm64_Windows.msi" -OutFile "tailscale_arm64_setup.msi"
--> amd || x86_64 -> MSI  
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscale_amd_x86_64_Windows.msi"
-->  Invoke-WebRequest -Uri "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscale_amd_x86_64_Windows.msi" -OutFile "tailscale_amd64_setup.msi"
--> amd || x86 -> MSI  
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscale_x86_Windows.msi"
-->  Invoke-WebRequest -Uri "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/tailscale/tailscale_x86_Windows.msi" -OutFile "tailscale_x86_setup.msi"



```
---
- #### Install TailScale
```bash
--> For '.upx' packed files # check if it's not corrupted: https://github.com/Azathothas/Static-Binaries/tree/main/tailscale#upx
!# Decompress
upx -d "$BIN.upx" -o "$BIN"
!# And also optionally verify sha256sum (Compare it with sha256sum pasted on this page)
sham256sum "$UNPACKED_UPX_BIN"

--> Linux || macOS
!# Recommended way to install Tailscale is:
 curl -fsSL https://tailscale.com/install.sh | sh
!# But this requires `root` | `sudo` access and doesn't work on all ARCHS
!# Compile Dynamically using go (Mac OS etc.)
  go install -v tailscale.com/cmd/tailscale@main
  go install -v tailscale.com/cmd/tailscaled@main
!# Equivalent of systemd.service
sudo $HOME/go/bin/tailscaled install-system-daemon
->> /Library/LaunchDaemons/com.tailscale.tailscaled.plist

!# Copy downloaded tailscale binaries to /usr/bin || /usr/local/bin
!# For $HOME/bin
 mkdir -p "$HOME/bin" && export PATH="$HOME/bin:$PATH"

!# Move Downloaded tailscale binaries to that DIR
 mv "$Path_To_tailscale_Binary" "/usr/bin/tailscale"
 mv "$Path_To_tailscaled_Binary" "/usr/bin/tailscaled"

!# For 'merged' | combined binaries, symlink them
 cd "$DIR_To_tailscale_merged_Binary"
 ln -s "$Path_To_tailscale_merged_Binary" tailscale
 ln -s "$Path_To_tailscale_merged_Binary" tailscaled

!# For Systemd Services, you have to move them to
'/etc/systemd/system/' || '/etc/default/'
!# Examples:
 sudo cp "tailscaled_riscv64_systemd.service" "/etc/systemd/system/"
 sudo cp "tailscaled_riscv64_systemd.defaults" "/etc/default/"

!# Give Writeable Perms
 chmod +xwr /usr/bin/tailscale*
```
```powershell
--> Windows
!# Using '.exe' [Recommended]
!# In PowerShell, To Install
Start-Process -Wait -FilePath ".\tailscale-setup.exe" -ArgumentList "/install", "/quiet" ; Start-Sleep -Seconds 10
!# To enable & Run
Start-Process -NoNewWindow -FilePath "C:\Program Files\Tailscale\tailscale.exe" -ArgumentList "up", "--unattended", --hostname="$HOSTNAME", --authkey="$TSKEY"

!# Using '.msi'
!# Ref: https://github.com/tailscale/tailscale/issues/2137#issuecomment-1137058471
!# Note that | Out-Host makes sure powershell waits for the installer to finish
!# This runs the installer which places: "tailscale.exe" | "tailscaled.exe" | "tailscale-ipn.exe" >>  "C:\Program Files\Tailscale\"
& msiexec /i "tailscale-setup.msi" /quiet | Out-Host
!# IPN --> Establishes connection between TailScale Cloud Control Panel & Local [https://pkg.go.dev/tailscale.com/ipn]
& "C:\Program Files\Tailscale\tailscale-ipn.exe" ; Start-Sleep -Seconds 10
!# This starts Tailscale in unattended mode
Start-Process -NoNewWindow -FilePath "C:\Program Files\Tailscale\tailscale.exe" -ArgumentList "up", "--unattended", --hostname="$HOSTNAME", --authkey="$TSKEY" ; Start-Sleep -Seconds 10

!# For Troubleshooting:
!# Restart Tailscale daemons & Services
net stop Tailscale
net start Tailscale
sleep 4
& "C:\Program Files\Tailscale\tailscale.exe" status
sleep 2
net stop Tailscale
taskkill /im tailscale-ipn.exe /f
net start Tailscale
sleep 4
& "C:\Program Files\Tailscale\tailscale.exe" status
```

---
```console

--> METADATA
./tailscale/tailscale_aarch64_arm64_Linux:                   ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, BuildID[sha1]=b2ccafee0d512102bfcfc079e3bdc0eec331c577, with debug_info, not stripped
./tailscale/tailscale_aarch64_arm64_Linux.upx:               ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=soNfjdXRG8c5eCbVCqCK/_KdHggh5LuyMdvj-Oagb/krx7bzsYGkWx0tKEZJzK/h6qzkiCuodFgKF0KmG-g, statically linked, no section header
./tailscale/tailscale_aarch64_arm64_Windows.msi:             Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Arm64;1033, Revision Number: {14F14A91-40CA-43B5-9AD8-2EB1950665A0}, Create Time/Date: Thu Jan 22 20:16:52 2026, Last Saved Time/Date: Thu Jan 22 20:16:52 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscale_aarch64_arm64_macOS:                   Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_amd_geode_Linux:                       ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, BuildID[sha1]=ef1d34c88099c21c91593121a71561e134e3ec4a, stripped
./tailscale/tailscale_amd_geode_Linux.upx:                   ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=h4j2IWHiMLAg9TtYh0_e/mMO07jsBjmn_dDIJ3QAl/ZRN8bmN6RrKQ1vQrrq48/J2OMOZVbTZ3XSThDlVZ2, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Linux:                      ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, BuildID[sha1]=410b73c14796356f5da34546197f27866d2e51fe, stripped
./tailscale/tailscale_amd_x86_64_Linux.upx:                  ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=ZOaixTKnWFwVLL9RAmal/PRhBXwelAYW4eOTLI7S4/Obqrz6OokIB3pyJ4z0pz/_OEP2V5KYsIUUB4zjj9K, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Windows.msi:                Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: x64;1033, Revision Number: {81471192-9AC9-4517-8B0D-ACE1C84577CB}, Create Time/Date: Thu Jan 22 20:16:40 2026, Last Saved Time/Date: Thu Jan 22 20:16:40 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscale_amd_x86_64_macOS:                      Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_arm_abi_Linux:                         ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, BuildID[sha1]=aaa5f3bfd4c42593c6d67e35f34f173d21195a7e, with debug_info, not stripped
./tailscale/tailscale_arm_abi_Linux.upx:                     ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=JRV9naYF8yXGW83GrxB-/FFT2h38MkB-s6WM0PC01/WFP6z9jhPpDa34QyoS45/WWkSY3m3XLj0wPSY5zwq, statically linked, no section header
./tailscale/tailscale_i386_Linux:                            ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, BuildID[sha1]=50d9b43a66a084402007f0bff19134c41ad1283c, stripped
./tailscale/tailscale_i386_Linux.upx:                        ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=IuusgS-QjyePYHET9L8T/eQZLVq6xBXxLShMMGUvR/z75_dGkqTid9esUEKgjS/NCbonAPbYcbkxCsgrA72, statically linked, no section header
./tailscale/tailscale_ipn_setup_Windows.exe:                 HTML document, ASCII text
./tailscale/tailscale_merged_aarch64_arm64_Linux:            ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_merged_aarch64_arm64_Linux.upx:        ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_merged_aarch64_arm64_macOS:            Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_merged_amd_x86_64_Linux:               ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_merged_amd_x86_64_Linux.upx:           ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_merged_amd_x86_64_macOS:               Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_merged_arm_Linux:                      ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_merged_arm_Linux.upx:                  ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), statically linked, no section header
./tailscale/tailscale_merged_i386_Linux:                     ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_merged_i386_Linux.upx:                 ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), statically linked, no section header
./tailscale/tailscale_merged_powerpc64_ppc64_Linux:          ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx:      ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux:      ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx:  ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_merged_s390x_Linux:                    ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_mips64_Linux:                          ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, BuildID[sha1]=d82704a12b74598689a77e4b939398f2531d9c36, with debug_info, not stripped
./tailscale/tailscale_mips64le_Linux:                        ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, BuildID[sha1]=63cce6846156b7d914882c66146a333c534f4686, with debug_info, not stripped
./tailscale/tailscale_mips_Linux:                            ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, BuildID[sha1]=b1cde76398780267a5a5d91244879cedd37dfd83, with debug_info, not stripped
./tailscale/tailscale_mips_Linux.upx:                        ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=zzIA6zyERxCkPXIZMVHi/OHlM-KTUU5FSbB_X5uvt/q7Nr8TYfPr1mntR-kmiR/YbhJtH_3vx_rd1EQe7lx, statically linked, no section header
./tailscale/tailscale_mipsle_Linux:                          ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, BuildID[sha1]=b5839ef994d9f06f07d01c162f40b190ae871269, with debug_info, not stripped
./tailscale/tailscale_mipsle_Linux.upx:                      ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=58KUAoTv5k3yuVblfgSD/9sGMPvImzCCklPEwwzaT/qOHR4NacS_gvIYTMWpqX/p04hhFpSaltt3vzWG7el, statically linked, no section header
./tailscale/tailscale_powerpc64_ppc64_Linux:                 ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64_ppc64_Linux.upx:             ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_powerpc64le_ppc64le_Linux:             ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx:         ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_riscv64_Linux:                         ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, BuildID[sha1]=7d3ce89163721b18469441086b0b27c1604430df, with debug_info, not stripped
./tailscale/tailscale_s390x_Linux:                           ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_setup_Windows.exe:                     PE32 executable (GUI) Intel 80386, for MS Windows, 6 sections
./tailscale/tailscale_x86_Windows.msi:                       Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Intel;1033, Revision Number: {F0ED6911-57B2-4446-AAD3-20FF92CC1C1D}, Create Time/Date: Thu Jan 22 20:16:40 2026, Last Saved Time/Date: Thu Jan 22 20:16:40 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscaled_aarch64_arm64_Linux:                  ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, BuildID[sha1]=87fc1f81e970e99c5c3e41dc13ce721788ca5290, with debug_info, not stripped
./tailscale/tailscaled_aarch64_arm64_Linux.upx:              ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=BtjQGxRH56XTuonWWlZs/2_q-eFdx7Y6m5u3Op8-6/i6WyIqNBtL4SjEny_O2d/yPTqhzrW_rISKXABkPsZ, statically linked, no section header
./tailscale/tailscaled_aarch64_arm64_macOS:                  Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_amd_geode_Linux:                      ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, BuildID[sha1]=afb719b04be485c027be83eec893ff94e1bc91ce, stripped
./tailscale/tailscaled_amd_geode_Linux.upx:                  ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=sdfOUSQU_57BjF4s92Cs/nywlaG1b_a2lwpvqXdUM/N9WOkN3PeRTAfDmW-9lP/05eiGTX8a4FLR6aPKaVZ, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_Linux:                     ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, BuildID[sha1]=9d44c5487a6d84f7c43224de539ab9a199dde130, stripped
./tailscale/tailscaled_amd_x86_64_Linux.upx:                 ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=r_VwT4iStJhe30U2JCFU/yC1n5oW5E86-ni-cEj6J/5EHxhsWHmS2A7zWNFhR9/ea1G4fL1V9ZQ7iJRHr5V, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_macOS:                     Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_arm_abi_Linux:                        ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, BuildID[sha1]=b027eb9e5ce6a30e32a1cc652fdb78d954511a4e, with debug_info, not stripped
./tailscale/tailscaled_arm_abi_Linux.upx:                    ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=3iLm5PAUyWt51ts5rOgh/mL9ge6Y-SX_zyHtzHxyb/Yic4iKmjD2fxFK5wvlVA/N4p9gI_GlG_u1LL-pqeN, statically linked, no section header
./tailscale/tailscaled_i386_Linux:                           ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, BuildID[sha1]=dd2fc2e491ab5ccd8089fcf2dca495c50cd13475, stripped
./tailscale/tailscaled_i386_Linux.upx:                       ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=3ewj9XUmbHt32EssZyM6/DJJ7mbH6tjpoqfxwt9kK/20P7eJjKeWI3iCrOoqzL/8gweI50HlQGyNi4nRkp7, statically linked, no section header
./tailscale/tailscaled_mips64_Linux:                         ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, BuildID[sha1]=5e4e1e7f69877d9032492c5d29bcfed5db32a0fe, with debug_info, not stripped
./tailscale/tailscaled_mips64le_Linux:                       ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, BuildID[sha1]=66c6a5c732d4c1fc3a4e859613371e0e37440d19, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux:                           ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, BuildID[sha1]=3af0d7447954e6fefc50d993e623ec412018b040, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux.upx:                       ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=ZyjIOhBgwQu1nqTaycZM/3BeFmf76FFy2DdAzvrbs/yYq8910K7miyRSeeAoEk/aaA6-oCnv72yfg9zIQRh, statically linked, no section header
./tailscale/tailscaled_mipsle_Linux:                         ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, BuildID[sha1]=a61933e19aa255758c189a5af766d15937cdac06, with debug_info, not stripped
./tailscale/tailscaled_mipsle_Linux.upx:                     ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=3UagGMgrdgqtxYZ4QgTK/nJXWippwiER991NWMQPm/DBKRpdSGAsf6vP1uVJj5/SIgm6tqzN-6XpoUPr4Hd, statically linked, no section header
./tailscale/tailscaled_powerpc64_ppc64_Linux:                ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64_ppc64_Linux.upx:            ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_powerpc64le_ppc64le_Linux:            ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx:        ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_riscv64_Linux:                        ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, BuildID[sha1]=20f632edcd6179afaca08cdecda0be647765e449, with debug_info, not stripped
./tailscale/tailscaled_s390x_Linux:                          ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped

--> SHA256SUM
2a69c926f3b961cc1f508688b777f6fbb23f618c7e493742dadbcb7a6dda6548  ./tailscale/tailscale_aarch64_arm64_Linux
4efa4ede119c11e728d3dee17c0a6f7c6ef1678e66176b32c9e0f581a7e5bbd8  ./tailscale/tailscale_aarch64_arm64_Linux.upx
7b9f8325d52632216e91495f6be35bd588f695944d65bc23bb0eaa2e86ec2c8f  ./tailscale/tailscale_aarch64_arm64_Windows.msi
758bd296723a348a70f5274b294baeb4053abd2e2ce58e2220e210946b618c6f  ./tailscale/tailscale_aarch64_arm64_macOS
bb6ed7706b0d256470af7ecd3b6d399bcd0a5a23bb089350709979578b7bc609  ./tailscale/tailscale_amd_geode_Linux
92f588e2af4225cc9c4ecdd8bde5df74f003802b4a0bb57aa9ba8a3eeae0062e  ./tailscale/tailscale_amd_geode_Linux.upx
9e492ecc2e339d66b651a351505eef9ac604acf2bc41652b510ec38711c34502  ./tailscale/tailscale_amd_x86_64_Linux
b338f9412328e23b37d0ecfc5c38a7603dd4129cf6b5e43ad674b6fadf78be37  ./tailscale/tailscale_amd_x86_64_Linux.upx
212d1f9c1af75fa780c8d5f2ea1516fca62e126c986544a28bf490d6252c6280  ./tailscale/tailscale_amd_x86_64_Windows.msi
248b7930c0c4c650f988bcb90a968da042066e0b826bf58efd8fe3a69fad8e7f  ./tailscale/tailscale_amd_x86_64_macOS
8f20233866b63b6e4a6a1fe2b015b7711bf973a182c7ea1b5b0e0c6ba1cd308d  ./tailscale/tailscale_arm_abi_Linux
0e09620c3443e8a864c2471e04d2e9c0de85fdda6fbe6a81d7415f816f5916ae  ./tailscale/tailscale_arm_abi_Linux.upx
440ad3e9761c1ef725388ae540e80993452c1da5b75e86044c8dfbc07aed228e  ./tailscale/tailscale_i386_Linux
2bc0ab1fa306cfe2f6462f97a387e56190355c9564975be44f6082e1327d8cf3  ./tailscale/tailscale_i386_Linux.upx
0a1cba03dd207e5cc43d81d1055bcb08f2b08b95d297703f78189acc25197662  ./tailscale/tailscale_ipn_setup_Windows.exe
754f1ab4d7a0dfaa4c4b7788e4cd366c57e9fd6e3cc31749ae038dc213081d90  ./tailscale/tailscale_merged_aarch64_arm64_Linux
d0a8f2b960dc706cc274823a0f7c84077723480bb5a995d7cae76a559402f657  ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
68728bde1313493eb44dbd3be2e989eb00f60f4938d0d2845df9d45e32c25df7  ./tailscale/tailscale_merged_aarch64_arm64_macOS
6ff8b4584b7ef1613b2665480001c097a52484bcf6c74ae3ea2a14421f691511  ./tailscale/tailscale_merged_amd_x86_64_Linux
632524c59e9478706a54154093a64017e3c94e58c32cbf27f03f78aceea8c4a3  ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
267bebcfe539dd8353add30caf55a042bf996f8e688aae7910b9ecf61714f3f8  ./tailscale/tailscale_merged_amd_x86_64_macOS
3e3e0b9d705eb0bda960befffc161bf5aa5be07950e653b3f05b8be2b93b0397  ./tailscale/tailscale_merged_arm_Linux
ef9764d927ac266faf4458aaa775521f60533f4b9af1fc4b8f9aec97ef425622  ./tailscale/tailscale_merged_arm_Linux.upx
f9faf70bbce5012bba7f3da4d78a4917c10f1e41bd305141b979da7877fc96d2  ./tailscale/tailscale_merged_i386_Linux
eaad2331306f01b8b931656e9c8ae401f5d73b4ba3e3815a2f13b2d7fc5ac83d  ./tailscale/tailscale_merged_i386_Linux.upx
a090de870e5800bef61202e3194bb759d16ce8da02ec2014ba38739be45c1335  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux
125de31f9b7413c97c72dc9cbd8bdc8e6b9f4d68714fa0c684249a0cb78527e0  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
bab079add4a77a1affac1c49d1a9b69ff17fc5c8491991d2990353d748bbd947  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux
433a0970d0cd77225d49ad8b750054ce3eb8f074cb1e038b4017b125cbdba0cc  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
d30bebbce26f597179edb763c5f7e7809d32c6763247361deed5eb313ed4b534  ./tailscale/tailscale_merged_s390x_Linux
75a7db823184d67fe0100e0f4c97b79f51e66453e37853604a782f83f1416cf4  ./tailscale/tailscale_mips64_Linux
24f020bcd68f3c83564318da18f6a6cb9fe2be1fd9c116f48ddfd54f27944461  ./tailscale/tailscale_mips64le_Linux
adec77b292401527d345ca3d8f6d279f97dbbae4e431c76fad47f8047a02642d  ./tailscale/tailscale_mips_Linux
dc002b9ea36d7055a817b42de2632c1883d0cb5643fa4909e9e730b244bd234c  ./tailscale/tailscale_mips_Linux.upx
cc8b59c9956da644c613dfeea47fee1ffb34cb0654a250ee6225cd08ce9634b0  ./tailscale/tailscale_mipsle_Linux
c76dc4ef00f4cfa872ad0c026debe4f41a686c8c702cc4b58d1b6c9bd36456b9  ./tailscale/tailscale_mipsle_Linux.upx
2ac5f2f3eddac31b00d51b388322b5ffe7544a20526fd8a4ce7a2555795b3420  ./tailscale/tailscale_powerpc64_ppc64_Linux
36885310e12640bf9df64d0514bfc9998c297267bdce1bdeeefee1e01852d802  ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
7eb9489deadee3a74b2c18059e0e87c98051660cd6a2407975d237ac36a191fa  ./tailscale/tailscale_powerpc64le_ppc64le_Linux
6b0ae21db3bfd56e4fa1841c4ace6ae11250290a6251aadc5e6b564a9784684c  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
3b167df3f2831193b79b762cdd567e58910cd5bea0321a5cb00e529cb06590ef  ./tailscale/tailscale_riscv64_Linux
1c3f55e8cef4ff6f342f3f53a0b5066720b856b4d94d443d4a8c3ee755a9fe0e  ./tailscale/tailscale_s390x_Linux
64a8ad28cbb67a6171236abe39f75a039a761a0e1aacdef75b26781887cef9a8  ./tailscale/tailscale_setup_Windows.exe
7e1e46f044d72231da8f2301846d7cccc63a7902a4e2ab0f0fc7f6cbf0adc5d4  ./tailscale/tailscale_x86_Windows.msi
dceed6499206663529c862c7f561704de67c41e862c2eddcecd1ac6985b3cae4  ./tailscale/tailscaled_aarch64_arm64_Linux
981601767fc6c70b364b3619c722eb9adeea7b0a5f66f1dbee40ce46fcacb3dc  ./tailscale/tailscaled_aarch64_arm64_Linux.upx
3045786fe6191b3d64ae9d2b03b5fffcf080e3cb3073a3c2e8e69e57ea05e2cf  ./tailscale/tailscaled_aarch64_arm64_macOS
1ab27bf0ac5fb95bacb74df95d6eab1f436432e19039530df89f841d8ed4ac26  ./tailscale/tailscaled_amd_geode_Linux
ca087523e77c3771d7a925711ac612c201db8e19e26f00476b7e165bcb0b0fb0  ./tailscale/tailscaled_amd_geode_Linux.upx
e5554349c9012cf7277cb0fd8a3c4a30f3c721639d49b25ef03f1282ba975614  ./tailscale/tailscaled_amd_x86_64_Linux
b6bd81b7c5ae228d664130050fc4546638668a123fb8d9ac687eabc6e4abbaca  ./tailscale/tailscaled_amd_x86_64_Linux.upx
b5304b43985998d94d5c2c94e0eeb9e160a76906fa0ecb224af45c3b878e684d  ./tailscale/tailscaled_amd_x86_64_macOS
ad295c53da9526947958f231e7c7bc2d2bf309ed52b137fdeafa4ba136c1a022  ./tailscale/tailscaled_arm_abi_Linux
d1319f454f2b90a3eae35cdaffea989746490b0c955cbc00159f5f187e9d41de  ./tailscale/tailscaled_arm_abi_Linux.upx
627f7f83fc7a6344641f332e9b2a0bb82474b0de074702e2526963d1c5e626af  ./tailscale/tailscaled_i386_Linux
640953bfcffc56439c4b88db1a2e5f9f7dba48d56d10bdfd2edfb4f684258f03  ./tailscale/tailscaled_i386_Linux.upx
f055678809506f5d7af90441562d4ff348885b3d5587ce39b8179d979fcfb533  ./tailscale/tailscaled_mips64_Linux
5ae62103d77103ffbba569820b92e0efa778b2d0844ace8ea767ca9f303fc906  ./tailscale/tailscaled_mips64le_Linux
a6c355e6a469ba957378b0a725bbfe02e24b49d52cab4b90851eb0fd6f2906cb  ./tailscale/tailscaled_mips_Linux
9d1d1d0450662239bd7a3f36c4f3c28924ce5fb27d429f01685adf2839bc689e  ./tailscale/tailscaled_mips_Linux.upx
1ffc459a30d82857f140a8ca97e983061b88e9e591c0af3548af0ecd36ca33cd  ./tailscale/tailscaled_mipsle_Linux
49176187060520892b6142a77c97217d8321fa15a17155fdb9e59035b0b18b40  ./tailscale/tailscaled_mipsle_Linux.upx
fb83ee28ab455026c2c93031ab76425d5869775680f5f05e16afdde8307d5070  ./tailscale/tailscaled_powerpc64_ppc64_Linux
42e2176fe9fb7c8007617b144c86421af6868e353aafbe81e4fd5ee2319fce4c  ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
d90ab2a0382fd91adbed0c160d7784520f84faa0a25113d330d4f77269a5875f  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux
a00ddbc247c50963daec9b532be6c9b76208163c0eb2ac1a714cac254327d223  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
ff065b17119564de9fa9a1c455579a58659c829a36610c3c6fe7228e447921fc  ./tailscale/tailscaled_riscv64_Linux
da4d878e0922658fe42f6560f71111762e71b1d3e660f70379f4f9f31892b99f  ./tailscale/tailscaled_s390x_Linux
```


---

- #### Sizes

```console
28M   ./tailscale/tailscale_aarch64_arm64_Linux
11M   ./tailscale/tailscale_aarch64_arm64_Linux.upx
32M   ./tailscale/tailscale_aarch64_arm64_Windows.msi
11M   ./tailscale/tailscale_aarch64_arm64_macOS
20M   ./tailscale/tailscale_amd_geode_Linux
4.9M  ./tailscale/tailscale_amd_geode_Linux.upx
21M   ./tailscale/tailscale_amd_x86_64_Linux
5.7M  ./tailscale/tailscale_amd_x86_64_Linux.upx
35M   ./tailscale/tailscale_amd_x86_64_Windows.msi
11M   ./tailscale/tailscale_amd_x86_64_macOS
28M   ./tailscale/tailscale_arm_abi_Linux
11M   ./tailscale/tailscale_arm_abi_Linux.upx
20M   ./tailscale/tailscale_i386_Linux
5.4M  ./tailscale/tailscale_i386_Linux.upx
47K   ./tailscale/tailscale_ipn_setup_Windows.exe
32M   ./tailscale/tailscale_merged_aarch64_arm64_Linux
7.4M  ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
20M   ./tailscale/tailscale_merged_aarch64_arm64_macOS
34M   ./tailscale/tailscale_merged_amd_x86_64_Linux
9.0M  ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
20M   ./tailscale/tailscale_merged_amd_x86_64_macOS
32M   ./tailscale/tailscale_merged_arm_Linux
7.2M  ./tailscale/tailscale_merged_arm_Linux.upx
32M   ./tailscale/tailscale_merged_i386_Linux
8.4M  ./tailscale/tailscale_merged_i386_Linux.upx
33M   ./tailscale/tailscale_merged_powerpc64_ppc64_Linux
7.3M  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
33M   ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux
7.6M  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
36M   ./tailscale/tailscale_merged_s390x_Linux
31M   ./tailscale/tailscale_mips64_Linux
31M   ./tailscale/tailscale_mips64le_Linux
30M   ./tailscale/tailscale_mips_Linux
11M   ./tailscale/tailscale_mips_Linux.upx
30M   ./tailscale/tailscale_mipsle_Linux
11M   ./tailscale/tailscale_mipsle_Linux.upx
20M   ./tailscale/tailscale_powerpc64_ppc64_Linux
4.6M  ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
20M   ./tailscale/tailscale_powerpc64le_ppc64le_Linux
4.8M  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
28M   ./tailscale/tailscale_riscv64_Linux
22M   ./tailscale/tailscale_s390x_Linux
51M   ./tailscale/tailscale_setup_Windows.exe
33M   ./tailscale/tailscale_x86_Windows.msi
36M   ./tailscale/tailscaled_aarch64_arm64_Linux
15M   ./tailscale/tailscaled_aarch64_arm64_Linux.upx
19M   ./tailscale/tailscaled_aarch64_arm64_macOS
23M   ./tailscale/tailscaled_amd_geode_Linux
6.6M  ./tailscale/tailscaled_amd_geode_Linux.upx
27M   ./tailscale/tailscaled_amd_x86_64_Linux
7.4M  ./tailscale/tailscaled_amd_x86_64_Linux.upx
19M   ./tailscale/tailscaled_amd_x86_64_macOS
33M   ./tailscale/tailscaled_arm_abi_Linux
14M   ./tailscale/tailscaled_arm_abi_Linux.upx
23M   ./tailscale/tailscaled_i386_Linux
6.6M  ./tailscale/tailscaled_i386_Linux.upx
37M   ./tailscale/tailscaled_mips64_Linux
37M   ./tailscale/tailscaled_mips64le_Linux
36M   ./tailscale/tailscaled_mips_Linux
14M   ./tailscale/tailscaled_mips_Linux.upx
36M   ./tailscale/tailscaled_mipsle_Linux
14M   ./tailscale/tailscaled_mipsle_Linux.upx
24M   ./tailscale/tailscaled_powerpc64_ppc64_Linux
5.7M  ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
24M   ./tailscale/tailscaled_powerpc64le_ppc64le_Linux
5.9M  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
34M   ./tailscale/tailscaled_riscv64_Linux
26M   ./tailscale/tailscaled_s390x_Linux
```

---

- #### UPX
```console

testing ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx [OK]
  24903828 ->   5955188   23.91%   linux/ppc64   ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_merged_arm_Linux.upx [OK]
  32637076 ->   7487324   22.94%    linux/arm    ./tailscale/tailscale_merged_arm_Linux.upx
testing ./tailscale/tailscaled_arm_abi_Linux.upx [OK]
  33906064 ->  14020692   41.35%    linux/arm    ./tailscale/tailscaled_arm_abi_Linux.upx
testing ./tailscale/tailscaled_i386_Linux.upx [OK]
  23811268 ->   6833572   28.70%   linux/i386    ./tailscale/tailscaled_i386_Linux.upx
testing ./tailscale/tailscaled_mips_Linux.upx [OK]
  37741782 ->  14143908   37.48%   linux/mips    ./tailscale/tailscaled_mips_Linux.upx
testing ./tailscale/tailscale_merged_amd_x86_64_Linux.upx [OK]
  35074196 ->   9383324   26.75%   linux/amd64   ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_merged_i386_Linux.upx [OK]
  32874644 ->   8744928   26.60%   linux/i386    ./tailscale/tailscale_merged_i386_Linux.upx
testing ./tailscale/tailscale_amd_geode_Linux.upx [OK]
  20082468 ->   5116376   25.48%   linux/i386    ./tailscale/tailscale_amd_geode_Linux.upx
testing ./tailscale/tailscale_mipsle_Linux.upx [OK]
  31293582 ->  11459380   36.62%  linux/mipsel   ./tailscale/tailscale_mipsle_Linux.upx
testing ./tailscale/tailscale_amd_x86_64_Linux.upx [OK]
  21303176 ->   5957972   27.97%   linux/amd64   ./tailscale/tailscale_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx [OK]
  32833684 ->   7724276   23.53%   linux/arm64   ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx [OK]
  20775060 ->   5004364   24.09%  linux/ppc64le  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscaled_aarch64_arm64_Linux.upx [OK]
  37094884 ->  15158060   40.86%   linux/arm64   ./tailscale/tailscaled_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_aarch64_arm64_Linux.upx [OK]
  28373506 ->  11504440   40.55%   linux/arm64   ./tailscale/tailscale_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx [OK]
  34537620 ->   7646604   22.14%   linux/ppc64   ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_arm_abi_Linux.upx [OK]
  28398922 ->  11440164   40.28%    linux/arm    ./tailscale/tailscale_arm_abi_Linux.upx
testing ./tailscale/tailscale_i386_Linux.upx [OK]
  20029220 ->   5561880   27.77%   linux/i386    ./tailscale/tailscale_i386_Linux.upx
testing ./tailscale/tailscale_powerpc64_ppc64_Linux.upx [OK]
  20775060 ->   4800456   23.11%   linux/ppc64   ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_mips_Linux.upx [OK]
  31429598 ->  11488704   36.55%   linux/mips    ./tailscale/tailscale_mips_Linux.upx
testing ./tailscale/tailscaled_mipsle_Linux.upx [OK]
  37587294 ->  14122768   37.57%  linux/mipsel   ./tailscale/tailscaled_mipsle_Linux.upx
testing ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx [OK]
  24903828 ->   6176616   24.80%  linux/ppc64le  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx [OK]
  34537620 ->   7933812   22.97%  linux/ppc64le  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscaled_amd_x86_64_Linux.upx [OK]
  27525992 ->   7755956   28.18%   linux/amd64   ./tailscale/tailscaled_amd_x86_64_Linux.upx
testing ./tailscale/tailscaled_amd_geode_Linux.upx [OK]
  23852196 ->   6844320   28.69%   linux/i386    ./tailscale/tailscaled_amd_geode_Linux.upx

```

---

- #### Version
```console
$ ./tailscale/tailscale_amd_x86_64_Linux --version
1.94.1
  tailscale commit: 62c6f1cd7560763edcc552251abadf7dd4659f82
  long version: 1.94.1-t62c6f1cd7-g09fea6572
  other commit: 09fea6572e9c7a839b4a8c209420141fdb33fbb4
  go version: go1.25.5

The easiest, most secure way to use WireGuard.

USAGE
  tailscale [flags] <subcommand> [command flags]

For help on subcommands, add --help after: "tailscale status --help".

This CLI is still under active development. Commands and flags will
change in the future.

SUBCOMMANDS
  up           Connect to Tailscale, logging in if needed
  down         Disconnect from Tailscale
  set          Change specified preferences
  login        Log in to a Tailscale account
  logout       Disconnect from Tailscale and expire current node key
  switch       Switch to a different Tailscale account
  configure    Configure the host to enable more Tailscale features
  syspolicy    Diagnose the MDM and system policy configuration
  netcheck     Print an analysis of local network conditions
  ip           Show Tailscale IP addresses
  dns          Diagnose the internal DNS forwarder
  status       Show state of tailscaled and its connections
  metrics      Show Tailscale metrics
  ping         Ping a host at the Tailscale layer, see how it routed
  nc           Connect to a port on a host, connected to stdin/stdout
  ssh          SSH to a Tailscale machine
  funnel       Serve content and local servers on the internet
  serve        Serve content and local servers on your tailnet
  version      Print Tailscale version
  web          Run a web server for controlling Tailscale
  file         Send or receive files
  bugreport    Print a shareable identifier to help diagnose issues
  cert         Get TLS certs
  lock         Manage tailnet lock
  licenses     Get open source license information
  exit-node    Show machines on your tailnet configured as exit nodes
  update       Update Tailscale to the latest/different version
  whois        Show the machine and user associated with a Tailscale IP (v4 or v6)
  drive        Share a directory with your tailnet
  systray      Run a systray application to manage Tailscale
  appc-routes  Print the current app connector routes
  completion   Shell tab-completion scripts

FLAGS
  --socket value
    	path to tailscaled socket (default /var/run/tailscale/tailscaled.sock)

$ ./tailscale/tailscaled_amd_x86_64_Linux -version
1.94.1
  tailscale commit: 62c6f1cd7560763edcc552251abadf7dd4659f82
  long version: 1.94.1-t62c6f1cd7-g09fea6572
  other commit: 09fea6572e9c7a839b4a8c209420141fdb33fbb4
  go version: go1.25.5

Usage of ./tailscale/tailscaled_amd_x86_64_Linux:
  -bird-socket string
    	path of the bird unix socket
  -cleanup
    	clean up system state and exit
  -config string
    	path to config file, or 'vm:user-data' to use the VM's user-data (EC2)
  -debug string
    	listen address ([ip]:port) of optional debug server
  -encrypt-state
    	encrypt the state file on disk; when not set encryption will be enabled if supported on this platform; uses TPM on Linux and Windows, on all other platforms this flag is not supported
  -hardware-attestation
    	use hardware-backed keys to bind node identity to this device when supported
    	by the OS and hardware. Uses TPM 2.0 on Linux and Windows; SecureEnclave on
    	macOS and iOS; and Keystore on Android. Only supported for Tailscale nodes that
    	store state on filesystem.
  -no-logs-no-support
    	disable log uploads; this also disables any technical support
  -outbound-http-proxy-listen string
    	optional [ip]:port to run an outbound HTTP proxy (e.g. "localhost:8080")
  -port value
    	UDP port to listen on for WireGuard and peer-to-peer traffic; 0 means automatically select (default 0)
  -socket string
    	path of the service unix socket (default "/var/run/tailscale/tailscaled.sock")
  -socks5-server string
    	optional [ip]:port to run a SOCK5 server (e.g. "localhost:1080")
  -state string
    	absolute path of state file; use 'kube:<secret-name>' to use Kubernetes secrets or 'arn:aws:ssm:...' to store in AWS SSM; use 'mem:' to not store state and register as an ephemeral node. If empty and --statedir is provided, the default is <statedir>/tailscaled.state. Default: /home/runner/.local/share/tailscale/tailscaled.state
  -statedir string
    	path to directory for storage of config state, TLS certs, temporary incoming Taildrop files, etc. If empty, it's derived from --state when possible.
  -tun string
    	tunnel interface name; use "userspace-networking" (beta) to not use TUN (default "tailscale0")
  -verbose int
    	log verbosity level; 0 is default, 1 or higher are increasingly verbose
  -version
    	print version information and exit

```

---


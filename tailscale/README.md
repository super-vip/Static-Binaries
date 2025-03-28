
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
./tailscale/tailscale_aarch64_arm64_Linux:                   ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, BuildID[sha1]=5f1b93207b3951e1f4dd2b11a76387b7ac9e4237, with debug_info, not stripped
./tailscale/tailscale_aarch64_arm64_Linux.upx:               ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=gamuCmU8fY7asQN86xaU/eJqusO2FbIvWK_9E0nKA/6YucQoL4iAPUs1QjKtn1/NLs-9oIngd9Ck63eJpcx, statically linked, no section header
./tailscale/tailscale_aarch64_arm64_Windows.msi:             Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Arm64;1033, Revision Number: {D6106540-C401-402F-8D1D-2050CFAE4917}, Create Time/Date: Wed Mar 26 23:50:16 2025, Last Saved Time/Date: Wed Mar 26 23:50:16 2025, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscale_aarch64_arm64_macOS:                   Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_amd_geode_Linux:                       ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, BuildID[sha1]=b9638cbf802ce14d586d8e4fb4ada2f3c80cae3c, stripped
./tailscale/tailscale_amd_geode_Linux.upx:                   ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=8X4GnyrWS5Wpf4kn5h01/f6zVO-FgXM6Fmf-SzCOK/HGYhb5wNYJqczTdUNK0n/a2vDU7vgYmK2Pz6Zigy2, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Linux:                      ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, BuildID[sha1]=ff5b3aedb9db97d8d966b867fe232126a1eeaa7a, stripped
./tailscale/tailscale_amd_x86_64_Linux.upx:                  ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=7-FmrU5zdZYIH583bIua/dMh7lwQDrNmIR4oj_cOA/f2-19LMWmRQKXwabeW0e/y9uVohtccKAYPLi8bH9f, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Windows.msi:                Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: x64;1033, Revision Number: {E28861CD-E8B7-4302-AA62-4D39BCE64C03}, Create Time/Date: Wed Mar 26 23:51:05 2025, Last Saved Time/Date: Wed Mar 26 23:51:05 2025, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscale_amd_x86_64_macOS:                      Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_arm_abi_Linux:                         ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, BuildID[sha1]=9a21166fa6cdc4099cb5c4abf60ffc34d9c52d09, with debug_info, not stripped
./tailscale/tailscale_arm_abi_Linux.upx:                     ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=IILxSjNS1C-wx79O2zFk/9Q5jGYWaArgRqTILQS8r/wOTKq7pOOqu8ZfBD7412/dbRJKF8SHN9a59J6p33v, statically linked, no section header
./tailscale/tailscale_i386_Linux:                            ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, BuildID[sha1]=3d420bb2f97102dfdeeaa400e10f4086e925ff42, stripped
./tailscale/tailscale_i386_Linux.upx:                        ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=OrPdt5yCy3arP02D13MV/PTqtMEH8Acfktcz7N6c6/s31AA9mvRHFjjZdX0guU/YQq-nWnK9GrQv_UXPToj, statically linked, no section header
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
./tailscale/tailscale_mips64_Linux:                          ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, BuildID[sha1]=7a788bde50a3de30afac092b045ea4e90662f5fc, with debug_info, not stripped
./tailscale/tailscale_mips64le_Linux:                        ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, BuildID[sha1]=163ccf249808b2da46d1c0c9082643d15c738381, with debug_info, not stripped
./tailscale/tailscale_mips_Linux:                            ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, BuildID[sha1]=e7f12d2a29ec6fde71a00564d8a2cc8fd9ac8009, with debug_info, not stripped
./tailscale/tailscale_mips_Linux.upx:                        ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=dHJTLLKNkPmDcmF99e4x/N3dt9RnKQ5528QkXF4_j/jN5iwkELSwe2Fwp-tWQb/2vZhc7dwdLW-cxds6_mp, statically linked, no section header
./tailscale/tailscale_mipsle_Linux:                          ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, BuildID[sha1]=b3d2946e846f7aca74ef20059fc36915b4edfdac, with debug_info, not stripped
./tailscale/tailscale_mipsle_Linux.upx:                      ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=3cnwUe4yUpS1m1qbciAs/-0dO4wxYJsVQA8nu20_k/rzdKq3pNyn4wiuni4L5y/zl63c09iqBhKoyo-aFlI, statically linked, no section header
./tailscale/tailscale_powerpc64_ppc64_Linux:                 ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64_ppc64_Linux.upx:             ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_powerpc64le_ppc64le_Linux:             ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx:         ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_riscv64_Linux:                         ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, BuildID[sha1]=bbda05cbc8e4132f5e2b37ed857f18cf308696ea, with debug_info, not stripped
./tailscale/tailscale_s390x_Linux:                           ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_setup_Windows.exe:                     PE32 executable (GUI) Intel 80386, for MS Windows, 6 sections
./tailscale/tailscale_x86_Windows.msi:                       Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Intel;1033, Revision Number: {5D9F85B1-323F-44BE-A315-1DBA0F8AB3EF}, Create Time/Date: Wed Mar 26 23:50:16 2025, Last Saved Time/Date: Wed Mar 26 23:50:16 2025, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscaled_aarch64_arm64_Linux:                  ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, BuildID[sha1]=764c9a4326bbc95b2ae1fc55baef429c66c66752, with debug_info, not stripped
./tailscale/tailscaled_aarch64_arm64_Linux.upx:              ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=upuskf9AxsYvp64tDGtq/aSfihBLT_ZwGJw5YDbiZ/5cmoGdqjUdQUjnTO20-r/VDCmNBM6HpXFiA9nwlOK, statically linked, no section header
./tailscale/tailscaled_aarch64_arm64_macOS:                  Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_amd_geode_Linux:                      ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, BuildID[sha1]=0eb445e76e1e2f2840e9953708dc401b56ae3b4d, stripped
./tailscale/tailscaled_amd_geode_Linux.upx:                  ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=UXKKyEFhMUq6vHkB-0gG/gauQD5UuA-di2rty6bHZ/MwItC4kMHinn9gYawyW5/oU8zpdmNbFkuzjayQEQQ, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_Linux:                     ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, BuildID[sha1]=401c10c66964bc0d31a659c93624c615415d612a, stripped
./tailscale/tailscaled_amd_x86_64_Linux.upx:                 ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=4vcefS2a40FUiz3chu7L/ouy9lUlOU-OKW6CqVXAo/jhi3l1BcrmMbZPWyZJwe/BfNFSHgEDnGK3X2e80M4, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_macOS:                     Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_arm_abi_Linux:                        ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, BuildID[sha1]=920043974002b7f7c1353307c10679cf1597a83c, with debug_info, not stripped
./tailscale/tailscaled_arm_abi_Linux.upx:                    ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=4gUOKhh-o9ZqmkU158-H/T4hegR4TjeO6Fxvx_pj8/jGL-cOTKzBrUDLq_OcjO/Fdoit1AoPi9Jdd21hD7z, statically linked, no section header
./tailscale/tailscaled_i386_Linux:                           ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, BuildID[sha1]=155b8fca4be9abbdde4a106fa6b6cf07e27d5472, stripped
./tailscale/tailscaled_i386_Linux.upx:                       ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=NLkFdKCD8_te_EPJo7gQ/Q3V8kAtRwocUBZB3SITv/YJ19z0sfGOomECUpoCj8/CnISmRjrt7efv6wWQd2P, statically linked, no section header
./tailscale/tailscaled_mips64_Linux:                         ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, BuildID[sha1]=92a64a76dda66e13259ac6c9e5990b97508d311e, with debug_info, not stripped
./tailscale/tailscaled_mips64le_Linux:                       ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, BuildID[sha1]=913e54dae6402320ef8e62872cc2088685a29b93, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux:                           ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, BuildID[sha1]=644c966bb2425632db33a737df2f966800c4ec85, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux.upx:                       ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=iB4B2fRXwqOL6UR523W1/B5BTZF-kB6lJcqq7tM-s/on_IN-meRc0EVhDuIy9o/N0yyR_X8M31lSXwj0zHz, statically linked, no section header
./tailscale/tailscaled_mipsle_Linux:                         ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, BuildID[sha1]=210d53e5a23ad8fb17dec9bcb8f5826be103e852, with debug_info, not stripped
./tailscale/tailscaled_mipsle_Linux.upx:                     ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=_-1HsE3uV65tPv_1cCO1/w_6nzNbov4zjeb95fsje/eiDT_BaHfGqlOg607ix-/omhpzKvKZ7K_HgV5C5Sk, statically linked, no section header
./tailscale/tailscaled_powerpc64_ppc64_Linux:                ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64_ppc64_Linux.upx:            ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_powerpc64le_ppc64le_Linux:            ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx:        ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_riscv64_Linux:                        ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, BuildID[sha1]=32eeb7b4cfbc61358e0dfefeedd398ad877d3fdc, with debug_info, not stripped
./tailscale/tailscaled_s390x_Linux:                          ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped

--> SHA256SUM
3b0a9292402cd1e7e0e7b7528016eb8828c34deb271d8490fc89911b5fadbe43  ./tailscale/tailscale_aarch64_arm64_Linux
41704ff4126bb6117e281bc3155d739e76689eebcf124c7a11d82fd89f67c69a  ./tailscale/tailscale_aarch64_arm64_Linux.upx
88bc19c311de33b19df9b98e2a30d6413f003dc6db1168df85ec094cdbdef3f1  ./tailscale/tailscale_aarch64_arm64_Windows.msi
758bd296723a348a70f5274b294baeb4053abd2e2ce58e2220e210946b618c6f  ./tailscale/tailscale_aarch64_arm64_macOS
a764be8eab8d405c12f95a21f3ab8a75d662cdfff5913eb67d5871d582bbed50  ./tailscale/tailscale_amd_geode_Linux
215d4ef7f6bdee784f5a43caaca8d7ea8afc361fb3f3fa5b419f480fc025f5df  ./tailscale/tailscale_amd_geode_Linux.upx
5d1514287cc662ae92f786b2b86d6e9f551378b5739ad656976f5572551ba4cc  ./tailscale/tailscale_amd_x86_64_Linux
9d97b2bffc0096de6e2cd74bef6da140ecaf637d94f4987f28501d1dc7be4eb0  ./tailscale/tailscale_amd_x86_64_Linux.upx
32b8ad3ca2202d090bebe8e2d8108bcdd8c9371d4840ebf7c03288a9af133715  ./tailscale/tailscale_amd_x86_64_Windows.msi
248b7930c0c4c650f988bcb90a968da042066e0b826bf58efd8fe3a69fad8e7f  ./tailscale/tailscale_amd_x86_64_macOS
0470f4904aac013e6278d7f4afc9ac6d139fc075aa0ea180f28daa31767959f8  ./tailscale/tailscale_arm_abi_Linux
9423f03edddc75b11fe96ac553eb77e713d05853c4645958a97de3f9b3ad729a  ./tailscale/tailscale_arm_abi_Linux.upx
dd24975b36fb03ad51221791eb7d3173430befae87394fa93ddfa19a47a08e95  ./tailscale/tailscale_i386_Linux
b187ee397f8548ec2af434fb781aae986656bbfc5cc69bacab08dc28a2fb5289  ./tailscale/tailscale_i386_Linux.upx
4b4e491d4fd90d0d274dd97f43bf203a404e8fca041df1d6e5bf1daec58b372e  ./tailscale/tailscale_ipn_setup_Windows.exe
41b5ffc09e608c8416fee38a819bcb8b70a51e17b024d8ce6cba4be92fc7bb38  ./tailscale/tailscale_merged_aarch64_arm64_Linux
02bbd21be75c80a5c9876a9c4e6a52037e356f8580e403635931f3fbf506a8be  ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
68728bde1313493eb44dbd3be2e989eb00f60f4938d0d2845df9d45e32c25df7  ./tailscale/tailscale_merged_aarch64_arm64_macOS
d297833dd5cf127a776945286f14d4bd5578d1c0dfc457e2101f86ddbceb117c  ./tailscale/tailscale_merged_amd_x86_64_Linux
6ad3ba529a7ed1d1bb356dd5f0e9f94531539a7b683f77b4f9f4efa0282a03ae  ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
267bebcfe539dd8353add30caf55a042bf996f8e688aae7910b9ecf61714f3f8  ./tailscale/tailscale_merged_amd_x86_64_macOS
e0a62d3f3647dcd13685e66d2699245757b8c76114eda7fd893dfccf85b6cda7  ./tailscale/tailscale_merged_arm_Linux
dd38849a56047c1ecb2f4cb7facd35c340cc09b64924da3c36360cfff9d8c882  ./tailscale/tailscale_merged_arm_Linux.upx
02527a86aceea466357d4693a0811fcffaba55dd468303455e7a48ae3d03eefb  ./tailscale/tailscale_merged_i386_Linux
c52c2babe9143fd41d8c8522667be6ea7b8672c1cdbcd83da3fd15a86c78060e  ./tailscale/tailscale_merged_i386_Linux.upx
4759e210232d26e328cad2322c954e8cd925463cd36c5d2b9a3e30c5d7bc5478  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux
540f3530104e54cb03020494832e293987e2970da6ec34595e45b34ff97a8a9e  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
a575f531062e0ef3645245fbee837155abbbfa67511c7764e14c80c642e3c44d  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux
25d45157d01d95701f7fa76192ce412d22e911d8de4c046dd2ccd8c77a690992  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
a9c93e9cfa75574bec4a8f63a14173a48415c799904c6312adc0cb5e38836552  ./tailscale/tailscale_merged_s390x_Linux
bb5ad4a220f6c1b917071f6bbf0437942e90b66451a2f135f6daa0ce8b015543  ./tailscale/tailscale_mips64_Linux
fc200c3b09ff0eeb4e103c9f1203cf300aae8a33ba98daffe7481fb6d39ada7a  ./tailscale/tailscale_mips64le_Linux
b20bbee99a9e7ed8052927ca9a19667e83ff51ae9685a67ebafc63bb5f796442  ./tailscale/tailscale_mips_Linux
160066c0fb10e5f0670ed36a785dae3b846d1d355db04021418c404760f59311  ./tailscale/tailscale_mips_Linux.upx
a9d633ca38d32e71251875f21aef59ba9da634763ca01ca2e03df2205a6d51f9  ./tailscale/tailscale_mipsle_Linux
2fac8abc4101d2ab85c3eda706c9ecf6e270117cb3eb6e9a3be69a28e858edfe  ./tailscale/tailscale_mipsle_Linux.upx
790b332f0fe12d9554379d6859e7e30824ec045112d4b35e6eaa4d922932a092  ./tailscale/tailscale_powerpc64_ppc64_Linux
a60e2352a8100dcc051ebd19b47eddd2b3d286944b983226ce3160e6ce8e589b  ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
abb3d2282eadfda571eab43ff3ddedd755304d9b83df8db94046714833f34e41  ./tailscale/tailscale_powerpc64le_ppc64le_Linux
74337601410b9f9fbaf5e9a85179e941ac36d620edebfad0b41e6eebfe042b12  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
f9814ba802c3bb00d6122094ea24953daa6d209c471ef2872e6aeebaa094face  ./tailscale/tailscale_riscv64_Linux
e4a06a1de2229d76456bdd033d2818f9b2dbd5be9985a28ff4a36abf94f225aa  ./tailscale/tailscale_s390x_Linux
64a8ad28cbb67a6171236abe39f75a039a761a0e1aacdef75b26781887cef9a8  ./tailscale/tailscale_setup_Windows.exe
48b1a37bfdc93e6cd9101cdb0433cfba0f66579506127dc0a8ccbf5b3cc4120b  ./tailscale/tailscale_x86_Windows.msi
1e24a5b9959c73c5f6cf57504fb20427e8f8cb0e201547f1651d95fcfbfc134f  ./tailscale/tailscaled_aarch64_arm64_Linux
14f45bb7c2aa06765aa2fa008f032bb2a0f3d42bd78859e813276324fe8f1063  ./tailscale/tailscaled_aarch64_arm64_Linux.upx
3045786fe6191b3d64ae9d2b03b5fffcf080e3cb3073a3c2e8e69e57ea05e2cf  ./tailscale/tailscaled_aarch64_arm64_macOS
8c5e667da8ef19c6bd8f05244cc5c45f119dcb2d9f32a664cd8c23bafacc5ad2  ./tailscale/tailscaled_amd_geode_Linux
d24252e6abd558e848fad5c94167c09f75ddd1d6b5286ef397b413e389fba2d0  ./tailscale/tailscaled_amd_geode_Linux.upx
c528dbefffbac860dfcc3756656127f787de06c9d49e8c4622f532c3724b8fd9  ./tailscale/tailscaled_amd_x86_64_Linux
7cd8eb0b9ae9a750643e9d5a6b3680cca3721d0f122afd1ea2f2554dce0b7dbd  ./tailscale/tailscaled_amd_x86_64_Linux.upx
b5304b43985998d94d5c2c94e0eeb9e160a76906fa0ecb224af45c3b878e684d  ./tailscale/tailscaled_amd_x86_64_macOS
25e7cde4293ea9b1d5d9ce0a013a4d582d42bd121c551928024f0aee381e191e  ./tailscale/tailscaled_arm_abi_Linux
28d32cbb50d3939341558db2d574c8cc05da7fabf1de9a36a5399307c675feef  ./tailscale/tailscaled_arm_abi_Linux.upx
43f2b5d5b375365b191563cf986e53ac79694d72b343f2f1cf1b61944f49729e  ./tailscale/tailscaled_i386_Linux
48ba064f6fa40143c1c07e2a8c619707142f16f6ccf7e0aa94656f681a30de3d  ./tailscale/tailscaled_i386_Linux.upx
99a0021c99a7736aa72eaf7161a9a53a83ded3d5ee9f0c3b1eba25ef5aecb7b1  ./tailscale/tailscaled_mips64_Linux
def2972cb6877b5940c29d1c05d3e707e9ab5f6f383555976f67ab85ad514240  ./tailscale/tailscaled_mips64le_Linux
7ba5d42e6d73e7e70d8e7477c9e84a6c3eeece36a30b7c6eeb2faa99324b79c9  ./tailscale/tailscaled_mips_Linux
dfd07ca1fca1e4e805d1b57d0af8afafb9e1cb3df021f547cd24fbaa2b7d3adb  ./tailscale/tailscaled_mips_Linux.upx
111f967ec5992695a94df3c5d5beac3f429dd0adffa6f0540a852b07258786ac  ./tailscale/tailscaled_mipsle_Linux
88acac8be6a909388547fc577db386c74fd69e67afd190a0c635820c199232ea  ./tailscale/tailscaled_mipsle_Linux.upx
13fb928120d8d73d0cdb8a58358b8ceebd1eff2499982c97309bdf9b3bf37784  ./tailscale/tailscaled_powerpc64_ppc64_Linux
2a12eb7124f39278c497c3664705ad5c13b7a3c1937c7065b29e515d4d06164d  ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
d30ca81d9d8044a07b56b5fe7f725af782f96a46d74b4e0f6640f586f07b0aa7  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux
54ead7dadbf3f86daa534014263ff0de3e0feef9edc95734783aa0766cd1e8bc  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
91d9fa04f21eb0a16a7e23369047e6c3af30091286e5ce172a8b01f6056dc71d  ./tailscale/tailscaled_riscv64_Linux
21557908f0284fd427c922a8a8f6ba22d6a72da51fa3f591eb99c447098461fe  ./tailscale/tailscaled_s390x_Linux
```


---

- #### Sizes

```console
19M   ./tailscale/tailscale_aarch64_arm64_Linux
8.4M  ./tailscale/tailscale_aarch64_arm64_Linux.upx
31M   ./tailscale/tailscale_aarch64_arm64_Windows.msi
11M   ./tailscale/tailscale_aarch64_arm64_macOS
13M   ./tailscale/tailscale_amd_geode_Linux
3.9M  ./tailscale/tailscale_amd_geode_Linux.upx
14M   ./tailscale/tailscale_amd_x86_64_Linux
4.2M  ./tailscale/tailscale_amd_x86_64_Linux.upx
33M   ./tailscale/tailscale_amd_x86_64_Windows.msi
11M   ./tailscale/tailscale_amd_x86_64_macOS
19M   ./tailscale/tailscale_arm_abi_Linux
8.2M  ./tailscale/tailscale_arm_abi_Linux.upx
13M   ./tailscale/tailscale_i386_Linux
3.6M  ./tailscale/tailscale_i386_Linux.upx
44K   ./tailscale/tailscale_ipn_setup_Windows.exe
23M   ./tailscale/tailscale_merged_aarch64_arm64_Linux
5.9M  ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
20M   ./tailscale/tailscale_merged_aarch64_arm64_macOS
25M   ./tailscale/tailscale_merged_amd_x86_64_Linux
7.1M  ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
20M   ./tailscale/tailscale_merged_amd_x86_64_macOS
23M   ./tailscale/tailscale_merged_arm_Linux
5.7M  ./tailscale/tailscale_merged_arm_Linux.upx
23M   ./tailscale/tailscale_merged_i386_Linux
6.6M  ./tailscale/tailscale_merged_i386_Linux.upx
24M   ./tailscale/tailscale_merged_powerpc64_ppc64_Linux
5.8M  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
24M   ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux
6.0M  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
26M   ./tailscale/tailscale_merged_s390x_Linux
21M   ./tailscale/tailscale_mips64_Linux
21M   ./tailscale/tailscale_mips64le_Linux
21M   ./tailscale/tailscale_mips_Linux
8.3M  ./tailscale/tailscale_mips_Linux.upx
21M   ./tailscale/tailscale_mipsle_Linux
8.2M  ./tailscale/tailscale_mipsle_Linux.upx
14M   ./tailscale/tailscale_powerpc64_ppc64_Linux
3.4M  ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
14M   ./tailscale/tailscale_powerpc64le_ppc64le_Linux
3.5M  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
19M   ./tailscale/tailscale_riscv64_Linux
15M   ./tailscale/tailscale_s390x_Linux
51M   ./tailscale/tailscale_setup_Windows.exe
32M   ./tailscale/tailscale_x86_Windows.msi
35M   ./tailscale/tailscaled_aarch64_arm64_Linux
15M   ./tailscale/tailscaled_aarch64_arm64_Linux.upx
19M   ./tailscale/tailscaled_aarch64_arm64_macOS
22M   ./tailscale/tailscaled_amd_geode_Linux
6.3M  ./tailscale/tailscaled_amd_geode_Linux.upx
26M   ./tailscale/tailscaled_amd_x86_64_Linux
7.2M  ./tailscale/tailscaled_amd_x86_64_Linux.upx
19M   ./tailscale/tailscaled_amd_x86_64_macOS
32M   ./tailscale/tailscaled_arm_abi_Linux
14M   ./tailscale/tailscaled_arm_abi_Linux.upx
22M   ./tailscale/tailscaled_i386_Linux
6.3M  ./tailscale/tailscaled_i386_Linux.upx
36M   ./tailscale/tailscaled_mips64_Linux
36M   ./tailscale/tailscaled_mips64le_Linux
35M   ./tailscale/tailscaled_mips_Linux
14M   ./tailscale/tailscaled_mips_Linux.upx
35M   ./tailscale/tailscaled_mipsle_Linux
14M   ./tailscale/tailscaled_mipsle_Linux.upx
23M   ./tailscale/tailscaled_powerpc64_ppc64_Linux
5.5M  ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
23M   ./tailscale/tailscaled_powerpc64le_ppc64le_Linux
5.7M  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
33M   ./tailscale/tailscaled_riscv64_Linux
25M   ./tailscale/tailscaled_s390x_Linux
```

---

- #### UPX
```console

testing ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx [OK]
  24772756 ->   6224124   25.12%  linux/ppc64le  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_aarch64_arm64_Linux.upx [OK]
  19459858 ->   8806432   45.25%   linux/arm64   ./tailscale/tailscale_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_i386_Linux.upx [OK]
  13251620 ->   3767976   28.43%   linux/i386    ./tailscale/tailscale_i386_Linux.upx
testing ./tailscale/tailscaled_amd_x86_64_Linux.upx [OK]
  26245768 ->   7446832   28.37%   linux/amd64   ./tailscale/tailscaled_amd_x86_64_Linux.upx
testing ./tailscale/tailscaled_aarch64_arm64_Linux.upx [OK]
  36629044 ->  15512648   42.35%   linux/arm64   ./tailscale/tailscaled_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_merged_arm_Linux.upx [OK]
  23789716 ->   5929968   24.93%    linux/arm    ./tailscale/tailscale_merged_arm_Linux.upx
testing ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx [OK]
  23789716 ->   5949888   25.01%  linux/ppc64le  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscaled_i386_Linux.upx [OK]
  22825284 ->   6588096   28.86%   linux/i386    ./tailscale/tailscaled_i386_Linux.upx
testing ./tailscale/tailscaled_amd_geode_Linux.upx [OK]
  22862148 ->   6593392   28.84%   linux/i386    ./tailscale/tailscaled_amd_geode_Linux.upx
testing ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx [OK]
  23986324 ->   6099740   25.43%   linux/arm64   ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx [OK]
  13697172 ->   3663320   26.75%  linux/ppc64le  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscaled_arm_abi_Linux.upx [OK]
  32889641 ->  13922848   42.33%    linux/arm    ./tailscale/tailscaled_arm_abi_Linux.upx
testing ./tailscale/tailscaled_mips_Linux.upx [OK]
  36600405 ->  14079644   38.47%   linux/mips    ./tailscale/tailscaled_mips_Linux.upx
testing ./tailscale/tailscale_arm_abi_Linux.upx [OK]
  19370600 ->   8574844   44.27%    linux/arm    ./tailscale/tailscale_arm_abi_Linux.upx
testing ./tailscale/tailscale_amd_geode_Linux.upx [OK]
  13276164 ->   4065812   30.62%   linux/i386    ./tailscale/tailscale_amd_geode_Linux.upx
testing ./tailscale/tailscale_amd_x86_64_Linux.upx [OK]
  14024168 ->   4325016   30.84%   linux/amd64   ./tailscale/tailscale_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_powerpc64_ppc64_Linux.upx [OK]
  13697172 ->   3488900   25.47%   linux/ppc64   ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_merged_i386_Linux.upx [OK]
  23883924 ->   6891692   28.85%   linux/i386    ./tailscale/tailscale_merged_i386_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx [OK]
  24772756 ->   5982780   24.15%   linux/ppc64   ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_merged_amd_x86_64_Linux.upx [OK]
  25338004 ->   7359568   29.05%   linux/amd64   ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
testing ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx [OK]
  23789716 ->   5715480   24.03%   linux/ppc64   ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscaled_mipsle_Linux.upx [OK]
  36348049 ->  14002340   38.52%  linux/mipsel   ./tailscale/tailscaled_mipsle_Linux.upx
testing ./tailscale/tailscale_mips_Linux.upx [OK]
  21217778 ->   8617796   40.62%   linux/mips    ./tailscale/tailscale_mips_Linux.upx
testing ./tailscale/tailscale_mipsle_Linux.upx [OK]
  21099074 ->   8559296   40.57%  linux/mipsel   ./tailscale/tailscale_mipsle_Linux.upx

```

---

- #### Version
```console
$ ./tailscale/tailscale_amd_x86_64_Linux --version
1.82.0
  tailscale commit: 6676b1261e51e0629553ca06b22e6631f8641100
  other commit: 3ec4bfb9c87718a3806a123585c825189cbceda4
  go version: go1.24.1

The easiest, most secure way to use WireGuard.

USAGE
  tailscale [flags] <subcommand> [command flags]

For help on subcommands, add --help after: "tailscale status --help".

This CLI is still under active development. Commands and flags will
change in the future.

SUBCOMMANDS
  up          Connect to Tailscale, logging in if needed
  down        Disconnect from Tailscale
  set         Change specified preferences
  login       Log in to a Tailscale account
  logout      Disconnect from Tailscale and expire current node key
  switch      Switch to a different Tailscale account
  configure   Configure the host to enable more Tailscale features
  syspolicy   Diagnose the MDM and system policy configuration
  netcheck    Print an analysis of local network conditions
  ip          Show Tailscale IP addresses
  dns         Diagnose the internal DNS forwarder
  status      Show state of tailscaled and its connections
  metrics     Show Tailscale metrics
  ping        Ping a host at the Tailscale layer, see how it routed
  nc          Connect to a port on a host, connected to stdin/stdout
  ssh         SSH to a Tailscale machine
  funnel      Serve content and local servers on the internet
  serve       Serve content and local servers on your tailnet
  version     Print Tailscale version
  web         Run a web server for controlling Tailscale
  file        Send or receive files
  bugreport   Print a shareable identifier to help diagnose issues
  cert        Get TLS certs
  lock        Manage tailnet lock
  licenses    Get open source license information
  exit-node   Show machines on your tailnet configured as exit nodes
  update      Update Tailscale to the latest/different version
  whois       Show the machine and user associated with a Tailscale IP (v4 or v6)
  drive       Share a directory with your tailnet
  completion  Shell tab-completion scripts

FLAGS
  --socket value
    	path to tailscaled socket (default /var/run/tailscale/tailscaled.sock)

$ ./tailscale/tailscaled_amd_x86_64_Linux -version
1.82.0
  tailscale commit: 6676b1261e51e0629553ca06b22e6631f8641100
  other commit: 3ec4bfb9c87718a3806a123585c825189cbceda4
  go version: go1.24.1

Usage of ./tailscale/tailscaled_amd_x86_64_Linux:
  -bird-socket string
    	path of the bird unix socket
  -cleanup
    	clean up system state and exit
  -config string
    	path to config file, or 'vm:user-data' to use the VM's user-data (EC2)
  -debug string
    	listen address ([ip]:port) of optional debug server
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


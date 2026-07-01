
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
./tailscale/tailscale_aarch64_arm64_Linux:                   ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=EwNlFtGnFho1VHWmAaDb/JQvUOsQbfsp6DyKiydnV/XFrBc4JmWOZg-_91oHIB/UQIQZPi0OQdbcGJBesqU, BuildID[sha1]=d856471827d79fc9e7f1a5e5eabb3aec73fef629, with debug_info, not stripped
./tailscale/tailscale_aarch64_arm64_Linux.upx:               ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=EwNlFtGnFho1VHWmAaDb/JQvUOsQbfsp6DyKiydnV/XFrBc4JmWOZg-_91oHIB/UQIQZPi0OQdbcGJBesqU, statically linked, no section header
./tailscale/tailscale_aarch64_arm64_Windows.msi:             Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Arm64;1033, Revision Number: {798739BF-BF3A-4D0C-9405-8192AFAD5A5E}, Create Time/Date: Tue Jun 23 23:09:18 2026, Last Saved Time/Date: Tue Jun 23 23:09:18 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscale_aarch64_arm64_macOS:                   Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_amd_geode_Linux:                       ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=A5pQx26z0b1ny2ZRvh1b/BQpJuhkGu33hWRA_2FSh/2U_JyeXm2M54i6WYU-Nd/YdkJnshGjyMTqDvKTmof, BuildID[sha1]=711183d72c65d56f9dbf68436141e88640a7c947, stripped
./tailscale/tailscale_amd_geode_Linux.upx:                   ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=A5pQx26z0b1ny2ZRvh1b/BQpJuhkGu33hWRA_2FSh/2U_JyeXm2M54i6WYU-Nd/YdkJnshGjyMTqDvKTmof, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Linux:                      ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=NIDSnkMBzYr1MyKSLoLp/BHN6ha3HQMhigulKT4I4/nYuqIpBnxKtOxxDNhuAB/_Vjr_F3lz6sRbkw8BhOP, BuildID[sha1]=2ca171cd5fa62ee5076f5191eeea89ade5a710ca, stripped
./tailscale/tailscale_amd_x86_64_Linux.upx:                  ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=NIDSnkMBzYr1MyKSLoLp/BHN6ha3HQMhigulKT4I4/nYuqIpBnxKtOxxDNhuAB/_Vjr_F3lz6sRbkw8BhOP, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Windows.msi:                Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: x64;1033, Revision Number: {A19AC061-059D-4B6E-ADC4-FA5DF5CDDD08}, Create Time/Date: Tue Jun 23 23:08:53 2026, Last Saved Time/Date: Tue Jun 23 23:08:53 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscale_amd_x86_64_macOS:                      Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_arm_abi_Linux:                         ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=6mPQIaSpgKrTBTMB8QHe/5A_4fBrr_kX6MDThm77_/ofpptNjlyk4paKufUDU_/JVrnn8qfdfFwDQP2vXd0, BuildID[sha1]=e3b61c5f361a78666726e44961280332246af2c7, with debug_info, not stripped
./tailscale/tailscale_arm_abi_Linux.upx:                     ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=6mPQIaSpgKrTBTMB8QHe/5A_4fBrr_kX6MDThm77_/ofpptNjlyk4paKufUDU_/JVrnn8qfdfFwDQP2vXd0, statically linked, no section header
./tailscale/tailscale_i386_Linux:                            ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=yts0WKjpvkHqrHg7pLU3/JH50vCu5CPqG8VAK2Ol1/jPaQUhzrwmxiK3sOSFKw/G5P0V8gyAWfHCy90ZoYX, BuildID[sha1]=f80d9815fc8c21cae4f78d8b18a9861a4b5e0ef7, stripped
./tailscale/tailscale_i386_Linux.upx:                        ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=yts0WKjpvkHqrHg7pLU3/JH50vCu5CPqG8VAK2Ol1/jPaQUhzrwmxiK3sOSFKw/G5P0V8gyAWfHCy90ZoYX, statically linked, no section header
./tailscale/tailscale_ipn_setup_Windows.exe:                 HTML document, Unicode text, UTF-8 text
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
./tailscale/tailscale_mips64_Linux:                          ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=-9rfTPUuVCYYmWJ6gR4x/6Wh6u3GE-1ZeYdmUc_l5/njrKOiasHDHW3ch-8zTx/LZ3e5U1MQL3YTOhhSclp, BuildID[sha1]=c989559114967c58603867bdeae670fe8b79d755, with debug_info, not stripped
./tailscale/tailscale_mips64le_Linux:                        ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=thKCmSV3SsNkQrAcW-C2/MyoRJuRapr511UINOr49/HQ-Cyzi-5Hu-0m01pNre/RB9ESqgHv1qXQxAQDw7z, BuildID[sha1]=00f5e8823a846dcfd877ab89dc8718e3b0554efb, with debug_info, not stripped
./tailscale/tailscale_mips_Linux:                            ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=uGZ54JzsB_2nrjQWpn1H/HS1OecyRJt4hY7nUeMOX/1hhlXXlGdIKrmcuBTAlz/x0uk8wO_eM0s1QwbVUV-, BuildID[sha1]=2167fe629afc2aeaf2285466e6fb2c66215e00f8, with debug_info, not stripped
./tailscale/tailscale_mips_Linux.upx:                        ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=uGZ54JzsB_2nrjQWpn1H/HS1OecyRJt4hY7nUeMOX/1hhlXXlGdIKrmcuBTAlz/x0uk8wO_eM0s1QwbVUV-, statically linked, no section header
./tailscale/tailscale_mipsle_Linux:                          ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=ElHhgXjaE4VvEGzzY3Mo/PH14lnyvLk10xo1AJ43X/o8rq-K9DfCOIm9isnTVm/2CzsxzyBNcP5oyV70rhT, BuildID[sha1]=fa6be6074971a12ce0f0c3f5c7321a3743334115, with debug_info, not stripped
./tailscale/tailscale_mipsle_Linux.upx:                      ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=ElHhgXjaE4VvEGzzY3Mo/PH14lnyvLk10xo1AJ43X/o8rq-K9DfCOIm9isnTVm/2CzsxzyBNcP5oyV70rhT, statically linked, no section header
./tailscale/tailscale_powerpc64_ppc64_Linux:                 ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64_ppc64_Linux.upx:             ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_powerpc64le_ppc64le_Linux:             ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx:         ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_riscv64_Linux:                         ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, Go BuildID=S8HgtUgLiZpKtRvPMCDa/z9z6bsjAm0AOSPd3ewf0/5mFvWFJ3MSwnJ9p0566i/yRBUFGEMG0C5hnbZz0YS, BuildID[sha1]=71a8755051cd49f0371a781752713898eba3a990, with debug_info, not stripped
./tailscale/tailscale_s390x_Linux:                           ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_setup_Windows.exe:                     PE32 executable (GUI) Intel 80386, for MS Windows, 6 sections
./tailscale/tailscale_x86_Windows.msi:                       Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Intel;1033, Revision Number: {A6EC9267-AC22-4FE7-A356-FE03AD1B4B2B}, Create Time/Date: Tue Jun 23 23:09:27 2026, Last Saved Time/Date: Tue Jun 23 23:09:27 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscaled_aarch64_arm64_Linux:                  ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=p1vvfIg0sm0NYH1BxIcC/6Xgio1EM-Adwh18qMkhP/vPXn4ML8VZ0axDzMAoP_/1d9g5az_BOKogc1ncB9l, BuildID[sha1]=fb07572eeadc125387ea90494fe3b6561eef812c, with debug_info, not stripped
./tailscale/tailscaled_aarch64_arm64_Linux.upx:              ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=p1vvfIg0sm0NYH1BxIcC/6Xgio1EM-Adwh18qMkhP/vPXn4ML8VZ0axDzMAoP_/1d9g5az_BOKogc1ncB9l, statically linked, no section header
./tailscale/tailscaled_aarch64_arm64_macOS:                  Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_amd_geode_Linux:                      ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=jR9PwIJFDJIgzy3Rhzoz/K3O7fytYmbuJP_AaKR8p/TFNGzkCQ32LpkCbc9GzP/eB36MbxSkeEY9mUTPcNb, BuildID[sha1]=e351e34e30785ee46b93b3df233efb03fe0b7ef7, stripped
./tailscale/tailscaled_amd_geode_Linux.upx:                  ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=jR9PwIJFDJIgzy3Rhzoz/K3O7fytYmbuJP_AaKR8p/TFNGzkCQ32LpkCbc9GzP/eB36MbxSkeEY9mUTPcNb, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_Linux:                     ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=Ub58wBf4ykY_jtMwiCX3/tbFJGrEhcyxtNt5PQr6F/xpMFE05mK4qtP5MthnR4/VCKq97dbiz67VZ5suBeF, BuildID[sha1]=77f57ad801212c5d5520134d6d17ee416926fc3c, stripped
./tailscale/tailscaled_amd_x86_64_Linux.upx:                 ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=Ub58wBf4ykY_jtMwiCX3/tbFJGrEhcyxtNt5PQr6F/xpMFE05mK4qtP5MthnR4/VCKq97dbiz67VZ5suBeF, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_macOS:                     Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_arm_abi_Linux:                        ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=5SrEW7EEY4BFbscn49gL/2iXGBbNtfibn4y6OuvHx/M-rADLBPO_G72TVZvanq/54LuOPnc17tp2gBO0uT-, BuildID[sha1]=119aeb391ee1dd3d00253b8f8516e8cf567eed9a, with debug_info, not stripped
./tailscale/tailscaled_arm_abi_Linux.upx:                    ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=5SrEW7EEY4BFbscn49gL/2iXGBbNtfibn4y6OuvHx/M-rADLBPO_G72TVZvanq/54LuOPnc17tp2gBO0uT-, statically linked, no section header
./tailscale/tailscaled_i386_Linux:                           ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=lCZT-s-y5QEyCdXdFSi9/HN186i2-aYKMHNlHVW8R/9bDOD2qdLWhoQMf2qumD/cC2dOR-kBFUtkHkDyWKb, BuildID[sha1]=ec56b6dd9c95715cf303107961c56fbac8aec7f4, stripped
./tailscale/tailscaled_i386_Linux.upx:                       ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=lCZT-s-y5QEyCdXdFSi9/HN186i2-aYKMHNlHVW8R/9bDOD2qdLWhoQMf2qumD/cC2dOR-kBFUtkHkDyWKb, statically linked, no section header
./tailscale/tailscaled_mips64_Linux:                         ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=nYT8t1RwcD3kAX1_F_-U/mACZnEIQLOIYK78J1NFI/uWbnaY0QMOjXEWs8k3Di/TUcBwVT636CVMH28KW2F, BuildID[sha1]=7166b4e538bc462f4ea1394b327f485dc53e62df, with debug_info, not stripped
./tailscale/tailscaled_mips64le_Linux:                       ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=WXi8XVhExFDASFQNcA81/sJo075xPUsjk0SMk9gzN/12hCJz1zfrjyH52dqLvv/_25Osx9vlSuavLva8IxQ, BuildID[sha1]=f32e55fce1dc0cff23141fc5cfde8655cfe836db, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux:                           ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=EDuonPwCBuAZ5Eo-xsy-/FbfUqAxceePPY4OOOMeO/Q7SE3CVpfkvHIqMLTrOr/Xecil6yCPb5mElsLCQjN, BuildID[sha1]=26af6fe87435de8e299207fb38191579b35918f9, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux.upx:                       ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=EDuonPwCBuAZ5Eo-xsy-/FbfUqAxceePPY4OOOMeO/Q7SE3CVpfkvHIqMLTrOr/Xecil6yCPb5mElsLCQjN, statically linked, no section header
./tailscale/tailscaled_mipsle_Linux:                         ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=4wwxxkzP2roZ9gytdbrm/XHK_4nZC8BijhZoOod4m/qR-XDGOnhAhqphe9p8IZ/tVNhIEx7U6iOwTfmq9-M, BuildID[sha1]=e47da93b974c65aa742f67845b0267df70878181, with debug_info, not stripped
./tailscale/tailscaled_mipsle_Linux.upx:                     ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=4wwxxkzP2roZ9gytdbrm/XHK_4nZC8BijhZoOod4m/qR-XDGOnhAhqphe9p8IZ/tVNhIEx7U6iOwTfmq9-M, statically linked, no section header
./tailscale/tailscaled_powerpc64_ppc64_Linux:                ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64_ppc64_Linux.upx:            ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_powerpc64le_ppc64le_Linux:            ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx:        ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_riscv64_Linux:                        ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, Go BuildID=GMLJ2Pk_58ZTVa0NuM4e/wWovbNBGuYZig2pDDiOy/Uh14_UAMJ0OPDwoeI7R_/6ppoAc__9t_doNeSIgSM, BuildID[sha1]=f8f0cb9732b79eac4703e9b54f293e89ccee8dd5, with debug_info, not stripped
./tailscale/tailscaled_s390x_Linux:                          ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped

--> SHA256SUM
d5626ec51dc8de2da07976e27c8fd02dae99fae421b5f5f416c135a9fb9c266a  ./tailscale/tailscale_aarch64_arm64_Linux
fd3fb1c45ca6c25e48cf63a1fc764b23a894eab055a76afe8ac29dc002526835  ./tailscale/tailscale_aarch64_arm64_Linux.upx
1692cbaf4b0668b1a4fbbeeb50639dbc7c67b3d56652829eca8b127a1899ce4e  ./tailscale/tailscale_aarch64_arm64_Windows.msi
758bd296723a348a70f5274b294baeb4053abd2e2ce58e2220e210946b618c6f  ./tailscale/tailscale_aarch64_arm64_macOS
778cf0a6f7a722dbbe93eac5610dfb0a37ac7940c34c90dd083dad2b1052e85e  ./tailscale/tailscale_amd_geode_Linux
de210b727b89461ac6428fbcfa7bd7fb5dff1df0d0dae6e459013ba820634ad5  ./tailscale/tailscale_amd_geode_Linux.upx
fb28ed84e222a744e2c000d2097eaee6700a3123b645ffd2fbf1c84b19d4dee7  ./tailscale/tailscale_amd_x86_64_Linux
afcca79abb7b0043ad0209fdc6abbd380291bfbba103aada4f50d14d37355477  ./tailscale/tailscale_amd_x86_64_Linux.upx
37416900f4990abb0e85b9cc26c7c7f96f8f181294cbee1eeb568ec3f355e87d  ./tailscale/tailscale_amd_x86_64_Windows.msi
248b7930c0c4c650f988bcb90a968da042066e0b826bf58efd8fe3a69fad8e7f  ./tailscale/tailscale_amd_x86_64_macOS
7af88aae68c54eef22d3416d747b61abb72ce234d44e89ae98ed0f6d35ae8f43  ./tailscale/tailscale_arm_abi_Linux
8a66a1b2ec04e6dad703f2420c48f367ec35405ea6ea1fb6c085a737f8d537f9  ./tailscale/tailscale_arm_abi_Linux.upx
f3da1dba9a3297cd9db5f9160cd10c6add6d669630aef9695f7c84336b92bae3  ./tailscale/tailscale_i386_Linux
939ab26942050e3aa1a07ca02024998f1a50b6f3498f305ee53687607da89bb3  ./tailscale/tailscale_i386_Linux.upx
33c3393c3ca29be6da4647539998f148bc6446c2723ba5e3e96d809b0dfc5a4d  ./tailscale/tailscale_ipn_setup_Windows.exe
81b27078dc02b87986d3feabffaa94f1794835a6c51a03cf9e7f9733bfff8bc1  ./tailscale/tailscale_merged_aarch64_arm64_Linux
8ecc5c67de25ea7cb0c0e9b4a2f015269ad40de2e072b939d32fd0782638cde2  ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
68728bde1313493eb44dbd3be2e989eb00f60f4938d0d2845df9d45e32c25df7  ./tailscale/tailscale_merged_aarch64_arm64_macOS
3c191731bf5fd34cf14f1a9e4e63488a58ca750de50f8c27e02a82c874ae36c1  ./tailscale/tailscale_merged_amd_x86_64_Linux
d041a77d89818af39c3415373c5f70104614b5100c3bfc0b5ceb005cacf574ba  ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
267bebcfe539dd8353add30caf55a042bf996f8e688aae7910b9ecf61714f3f8  ./tailscale/tailscale_merged_amd_x86_64_macOS
f12b9fca51ec3364cdebcff2c9d8b49e40873f06769a6f88f5461d30bde8023d  ./tailscale/tailscale_merged_arm_Linux
3969fd8a92c227c628ef2ca60b354f9020f529ab2b6a376008d9887882221419  ./tailscale/tailscale_merged_arm_Linux.upx
2d8815ba4f49dc36bf45f3f212d1ee88f639f04ed2c9f8adadd899052a0de722  ./tailscale/tailscale_merged_i386_Linux
155ec6a988232bfe3c3547a9462ee082cbce5460ea2c91beba26ce4c0dd08275  ./tailscale/tailscale_merged_i386_Linux.upx
882c164f76764e76aea205052b30ef77284d075224a40a3bc64fe7ea144256c7  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux
6a2a5ef4f19a490d72d4ac450115b281bc351e446657a69163f92b5d9041dcbc  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
7550a1da6d6073ca7660bc5b8e2a8c4faa58722004e0493c050b37079ba45a86  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux
fe31703b11e579b10ef945e5211452431bc240a6f299dce92eb0f47c5ac052f7  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
08872368ae577c0254d7fb2a1463c663a3e57f53060704b2397d3b3c60057b8e  ./tailscale/tailscale_merged_s390x_Linux
47f3f3557c8e0740bb0adcbed4420349064ee4b3ed655e895971eb3b15ec9c37  ./tailscale/tailscale_mips64_Linux
a65249ae998f9cc810fd4b6ef87cee57cacdd00e29620f9e95e496fb8824c9d9  ./tailscale/tailscale_mips64le_Linux
e2902ad260377ad35dc51e0b04718dc3b5579b0f33df7df1eae6f521f56558fc  ./tailscale/tailscale_mips_Linux
9f0902f6971720a620fa63a0ec8fe2cbef4292b6903755fdeddca10ec284ca99  ./tailscale/tailscale_mips_Linux.upx
ab32340c727c37bcd03a5abdd326ed0aaa7bea152a2b58a91ea6600f077b6f0d  ./tailscale/tailscale_mipsle_Linux
2d997fa5ece0c87032e2adba07f60a2699c9f5d91e7bb67e871ba8d7d9865b45  ./tailscale/tailscale_mipsle_Linux.upx
299783fa5c346398efa79b8115e2697d7cf26c7aac11f171616cf05aa153217f  ./tailscale/tailscale_powerpc64_ppc64_Linux
211e34deb4ea01048f0358fa75dd0e8df9dbee1279806e0001256da45852fd82  ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
c5ccadfb6f23fd7d8a83b32ab64f46bf5858f6fe6221486ae290efe7004837b7  ./tailscale/tailscale_powerpc64le_ppc64le_Linux
d1e666839e9083dec6b04adceeacc919676f7d3ac1d3481e6f2f810d21dc5ed0  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
e907ae13f421bcf4ee94a4c3d7e38e6f3ea857c760c7b410e2b040c1d15bb412  ./tailscale/tailscale_riscv64_Linux
0d54fe4a1a3754c510904a638b9e475dfa349e3b7b05167b2743ac5bc82d3dcc  ./tailscale/tailscale_s390x_Linux
64a8ad28cbb67a6171236abe39f75a039a761a0e1aacdef75b26781887cef9a8  ./tailscale/tailscale_setup_Windows.exe
36b47e4df15ec04969297300da81cca87254ecc5e79fae8360b2cfc90868640e  ./tailscale/tailscale_x86_Windows.msi
a595b290bc114f921b3211fbf760f8157bc39e57ceccb38a6b00d45b144b41f5  ./tailscale/tailscaled_aarch64_arm64_Linux
534493606552d70894e7725bd1677ea17b89b966b0c9fd0340b9ea1a3a9f00ec  ./tailscale/tailscaled_aarch64_arm64_Linux.upx
3045786fe6191b3d64ae9d2b03b5fffcf080e3cb3073a3c2e8e69e57ea05e2cf  ./tailscale/tailscaled_aarch64_arm64_macOS
713c69b6628abbecd056b16f31f7dbbca013ea4e603ca1cf4005e35b31d81ec4  ./tailscale/tailscaled_amd_geode_Linux
65ce499b28d2e31037a366c098206a0207090c8fb49aabba2ea73f89e593579f  ./tailscale/tailscaled_amd_geode_Linux.upx
5e47c852d8842e5d60f41a0d9cc5b295bc1cbfc7e25e27de254728dc2c10200b  ./tailscale/tailscaled_amd_x86_64_Linux
9567cbb1a16ed9188d3f12bb59d89be1b4573742dec689cac2282e96464754d3  ./tailscale/tailscaled_amd_x86_64_Linux.upx
b5304b43985998d94d5c2c94e0eeb9e160a76906fa0ecb224af45c3b878e684d  ./tailscale/tailscaled_amd_x86_64_macOS
44fc4d0945de389c78943a18f4a7115c85ab418ddc9731f8cc53d8822fca4309  ./tailscale/tailscaled_arm_abi_Linux
651c64b6cdfbe32f96134bd6d664564e0c7e70fd20e73a2f9a9bedd16331e86c  ./tailscale/tailscaled_arm_abi_Linux.upx
091923f5efe86711b83b6ea13d91930035286fa3167998a5c5a0d3cdbe8ce9aa  ./tailscale/tailscaled_i386_Linux
355ed1fc6dffd3f3f45fbff2768534f8b45a8a586fe0abad5bcab17c32c823da  ./tailscale/tailscaled_i386_Linux.upx
027d901d12e9accf1a96095b1ecf24b7b1110186627b9bc85f09178a844d70bc  ./tailscale/tailscaled_mips64_Linux
62554fe0f9c7ffbf0dc34623945632f451aa5f68b542f9acd82f8f67ce8c5442  ./tailscale/tailscaled_mips64le_Linux
62895a1cb9866abc1aa853bb43e6723b95adefd90eb33b191616b14201b481cf  ./tailscale/tailscaled_mips_Linux
16f0710fc75d85081af9447a80094ec43a8d354d7c962e63f05d074a74a9bb88  ./tailscale/tailscaled_mips_Linux.upx
917fbd1fcf797353f33be9136f22e041a01e0422745dad00bf89c5e29fc8cd69  ./tailscale/tailscaled_mipsle_Linux
a7c691a554b771a7d30a97c0aa7d944329e78964fad7a89fa59f53c8d8b0afa3  ./tailscale/tailscaled_mipsle_Linux.upx
6b4ea3a078b9d89c45a636fa779be423f6414bcad16a389e716858c9ce9047fb  ./tailscale/tailscaled_powerpc64_ppc64_Linux
db9cbe0869676740c7e3257ef7b8da2e15eedb91129a41a08be66913e63cbb8e  ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
df97c8ce1020957fb1d0d469bc87609acd3a043e6c2256e936cfebffa9f330ea  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux
12b85225dd6648032a2c114753fb5818fc5f69d0c8709232e663f25101e34c92  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
657880dba9f2a21b284635d107c770e171fc0cc7f4a47afc3d19252a0c203a95  ./tailscale/tailscaled_riscv64_Linux
8121f7e5d6888ccb034ae441727506a7ae5e0cac383686946e5b4cefc3151ac8  ./tailscale/tailscaled_s390x_Linux
```


---

- #### Sizes

```console
29M   ./tailscale/tailscale_aarch64_arm64_Linux
12M   ./tailscale/tailscale_aarch64_arm64_Linux.upx
33M   ./tailscale/tailscale_aarch64_arm64_Windows.msi
11M   ./tailscale/tailscale_aarch64_arm64_macOS
20M   ./tailscale/tailscale_amd_geode_Linux
5.1M  ./tailscale/tailscale_amd_geode_Linux.upx
22M   ./tailscale/tailscale_amd_x86_64_Linux
6.0M  ./tailscale/tailscale_amd_x86_64_Linux.upx
35M   ./tailscale/tailscale_amd_x86_64_Windows.msi
11M   ./tailscale/tailscale_amd_x86_64_macOS
28M   ./tailscale/tailscale_arm_abi_Linux
12M   ./tailscale/tailscale_arm_abi_Linux.upx
20M   ./tailscale/tailscale_i386_Linux
5.6M  ./tailscale/tailscale_i386_Linux.upx
69K   ./tailscale/tailscale_ipn_setup_Windows.exe
33M   ./tailscale/tailscale_merged_aarch64_arm64_Linux
7.7M  ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
20M   ./tailscale/tailscale_merged_aarch64_arm64_macOS
36M   ./tailscale/tailscale_merged_amd_x86_64_Linux
9.4M  ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
20M   ./tailscale/tailscale_merged_amd_x86_64_macOS
33M   ./tailscale/tailscale_merged_arm_Linux
7.5M  ./tailscale/tailscale_merged_arm_Linux.upx
33M   ./tailscale/tailscale_merged_i386_Linux
8.8M  ./tailscale/tailscale_merged_i386_Linux.upx
35M   ./tailscale/tailscale_merged_powerpc64_ppc64_Linux
7.7M  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
35M   ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux
7.9M  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
36M   ./tailscale/tailscale_merged_s390x_Linux
32M   ./tailscale/tailscale_mips64_Linux
32M   ./tailscale/tailscale_mips64le_Linux
31M   ./tailscale/tailscale_mips_Linux
12M   ./tailscale/tailscale_mips_Linux.upx
31M   ./tailscale/tailscale_mipsle_Linux
12M   ./tailscale/tailscale_mipsle_Linux.upx
21M   ./tailscale/tailscale_powerpc64_ppc64_Linux
4.8M  ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
21M   ./tailscale/tailscale_powerpc64le_ppc64le_Linux
5.0M  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
28M   ./tailscale/tailscale_riscv64_Linux
22M   ./tailscale/tailscale_s390x_Linux
51M   ./tailscale/tailscale_setup_Windows.exe
34M   ./tailscale/tailscale_x86_Windows.msi
37M   ./tailscale/tailscaled_aarch64_arm64_Linux
16M   ./tailscale/tailscaled_aarch64_arm64_Linux.upx
19M   ./tailscale/tailscaled_aarch64_arm64_macOS
24M   ./tailscale/tailscaled_amd_geode_Linux
6.8M  ./tailscale/tailscaled_amd_geode_Linux.upx
28M   ./tailscale/tailscaled_amd_x86_64_Linux
7.7M  ./tailscale/tailscaled_amd_x86_64_Linux.upx
19M   ./tailscale/tailscaled_amd_x86_64_macOS
34M   ./tailscale/tailscaled_arm_abi_Linux
14M   ./tailscale/tailscaled_arm_abi_Linux.upx
24M   ./tailscale/tailscaled_i386_Linux
6.8M  ./tailscale/tailscaled_i386_Linux.upx
38M   ./tailscale/tailscaled_mips64_Linux
38M   ./tailscale/tailscaled_mips64le_Linux
38M   ./tailscale/tailscaled_mips_Linux
15M   ./tailscale/tailscaled_mips_Linux.upx
38M   ./tailscale/tailscaled_mipsle_Linux
14M   ./tailscale/tailscaled_mipsle_Linux.upx
25M   ./tailscale/tailscaled_powerpc64_ppc64_Linux
5.9M  ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
25M   ./tailscale/tailscaled_powerpc64le_ppc64le_Linux
6.1M  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
34M   ./tailscale/tailscaled_riscv64_Linux
26M   ./tailscale/tailscaled_s390x_Linux
```

---

- #### UPX
```console

testing ./tailscale/tailscaled_i386_Linux.upx [OK]
  24699308 ->   7085144   28.69%   linux/i386    ./tailscale/tailscaled_i386_Linux.upx
testing ./tailscale/tailscale_i386_Linux.upx [OK]
  20718468 ->   5777152   27.88%   linux/i386    ./tailscale/tailscale_i386_Linux.upx
testing ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx [OK]
  34078846 ->   8027364   23.56%   linux/arm64   ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_aarch64_arm64_Linux.upx [OK]
  29579204 ->  12088124   40.87%   linux/arm64   ./tailscale/tailscale_aarch64_arm64_Linux.upx
testing ./tailscale/tailscaled_mips_Linux.upx [OK]
  39035571 ->  14682840   37.61%   linux/mips    ./tailscale/tailscaled_mips_Linux.upx
testing ./tailscale/tailscale_merged_amd_x86_64_Linux.upx [OK]
  36733054 ->   9789224   26.65%   linux/amd64   ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
testing ./tailscale/tailscaled_amd_x86_64_Linux.upx [OK]
  28590232 ->   8009108   28.01%   linux/amd64   ./tailscale/tailscaled_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_mipsle_Linux.upx [OK]
  32243494 ->  11915588   36.96%  linux/mipsel   ./tailscale/tailscale_mipsle_Linux.upx
testing ./tailscale/tailscaled_mipsle_Linux.upx [OK]
  38867659 ->  14655000   37.70%  linux/mipsel   ./tailscale/tailscaled_mipsle_Linux.upx
testing ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx [OK]
  25690238 ->   6158848   23.97%   linux/ppc64   ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_amd_x86_64_Linux.upx [OK]
  22278248 ->   6207204   27.86%   linux/amd64   ./tailscale/tailscale_amd_x86_64_Linux.upx
testing ./tailscale/tailscaled_amd_geode_Linux.upx [OK]
  24736172 ->   7094912   28.68%   linux/i386    ./tailscale/tailscaled_amd_geode_Linux.upx
testing ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx [OK]
  21364862 ->   5191264   24.30%  linux/ppc64le  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscaled_aarch64_arm64_Linux.upx [OK]
  38487580 ->  15814420   41.09%   linux/arm64   ./tailscale/tailscaled_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_amd_geode_Linux.upx [OK]
  20771716 ->   5319560   25.61%   linux/i386    ./tailscale/tailscale_amd_geode_Linux.upx
testing ./tailscale/tailscale_merged_i386_Linux.upx [OK]
  34390142 ->   9146560   26.60%   linux/i386    ./tailscale/tailscale_merged_i386_Linux.upx
testing ./tailscale/tailscale_merged_arm_Linux.upx [OK]
  33882238 ->   7832252   23.12%    linux/arm    ./tailscale/tailscale_merged_arm_Linux.upx
testing ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx [OK]
  25690238 ->   6389216   24.87%  linux/ppc64le  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx [OK]
  35913854 ->   8261228   23.00%  linux/ppc64le  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_powerpc64_ppc64_Linux.upx [OK]
  21364862 ->   4980476   23.31%   linux/ppc64   ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscaled_arm_abi_Linux.upx [OK]
  35040923 ->  14515892   41.43%    linux/arm    ./tailscale/tailscaled_arm_abi_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx [OK]
  35913854 ->   7971152   22.20%   linux/ppc64   ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_mips_Linux.upx [OK]
  32392606 ->  11949236   36.89%   linux/mips    ./tailscale/tailscale_mips_Linux.upx
testing ./tailscale/tailscale_arm_abi_Linux.upx [OK]
  29259774 ->  11844380   40.48%    linux/arm    ./tailscale/tailscale_arm_abi_Linux.upx

```

---

- #### Version
```console
$ ./tailscale/tailscale_amd_x86_64_Linux --version
1.98.8
  tailscale commit: 1241b225bc798707d02db3570992625d3a16594f
  long version: 1.98.8-t1241b225b-g0520dfda5
  other commit: 0520dfda5d034816c38a15a8661160eb9a6d5ac4
  go version: go1.26.3 (tailscale/go e877d97384)

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
  wait         Wait for Tailscale interface/IPs to be ready for binding
  completion   Shell tab-completion scripts

FLAGS
  --socket value
    	path to tailscaled socket (default /var/run/tailscale/tailscaled.sock)

$ ./tailscale/tailscaled_amd_x86_64_Linux -version
1.98.8
  tailscale commit: 1241b225bc798707d02db3570992625d3a16594f
  long version: 1.98.8-t1241b225b-g0520dfda5
  other commit: 0520dfda5d034816c38a15a8661160eb9a6d5ac4
  go version: go1.26.3 (tailscale/go e877d97384)

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


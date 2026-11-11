
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
./tailscale/tailscale_aarch64_arm64_Linux:                   ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=FrxVZvoHhqasOLrIXk6N/2OLb0KV0sOz8AER3E_x6/IcQTGtAlDzVZfhqpmNfm/rTCbQoHzq9ry-5OPa4nF, BuildID[sha1]=d1d98372741eba97351935fdd6c8a69592af57ca, with debug_info, not stripped
./tailscale/tailscale_aarch64_arm64_Linux.upx:               ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=FrxVZvoHhqasOLrIXk6N/2OLb0KV0sOz8AER3E_x6/IcQTGtAlDzVZfhqpmNfm/rTCbQoHzq9ry-5OPa4nF, statically linked, no section header
./tailscale/tailscale_aarch64_arm64_Windows.msi:             Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Arm64;1033, Revision Number: {987126BE-0D74-4702-AFAD-EBA6A69C2B22}, Create Time/Date: Tue Nov 10 23:57:42 2026, Last Saved Time/Date: Tue Nov 10 23:57:42 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (6.0.2.0), Security: 2
./tailscale/tailscale_aarch64_arm64_macOS:                   Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_amd_geode_Linux:                       ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=QYjagioIVE_DU8xZE0Rr/W31whWp2XFpDlTyDn0UA/SxheTwz_pmq93CY4D1BG/JkaO9Y1HFZ84neeY0hbL, BuildID[sha1]=0ef9a6ab5d282f3b00cad2ff2c72bbf677048d73, stripped
./tailscale/tailscale_amd_geode_Linux.upx:                   ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=QYjagioIVE_DU8xZE0Rr/W31whWp2XFpDlTyDn0UA/SxheTwz_pmq93CY4D1BG/JkaO9Y1HFZ84neeY0hbL, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Linux:                      ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=kI1KUPzN8ugpvHtUVyBN/cV9Mu3IM7_ZK--QrUL62/wTdrcBeUhBlaKbgzJ5Cp/Au2bDeM52Gypz9xmfLtn, BuildID[sha1]=7c5492e5de2ba08f2890ffb3f906c0079c694f75, stripped
./tailscale/tailscale_amd_x86_64_Linux.upx:                  ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=kI1KUPzN8ugpvHtUVyBN/cV9Mu3IM7_ZK--QrUL62/wTdrcBeUhBlaKbgzJ5Cp/Au2bDeM52Gypz9xmfLtn, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Windows.msi:                Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: x64;1033, Revision Number: {7F6F9147-16BF-4E18-8D95-6BA84B314AE2}, Create Time/Date: Tue Nov 10 23:56:42 2026, Last Saved Time/Date: Tue Nov 10 23:56:42 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (6.0.2.0), Security: 2
./tailscale/tailscale_amd_x86_64_macOS:                      Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_arm_abi_Linux:                         ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=rC-prtmdzbhZaMhDipaw/Y6kWASRBkYJUiopi_6_o/o8Qjmb8GaTifHXiRpuyk/O5ddt9AY_U4pwLU4p063, BuildID[sha1]=bed67550a3d4f3df79b963976c8b1fd56b5cf182, with debug_info, not stripped
./tailscale/tailscale_arm_abi_Linux.upx:                     ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=rC-prtmdzbhZaMhDipaw/Y6kWASRBkYJUiopi_6_o/o8Qjmb8GaTifHXiRpuyk/O5ddt9AY_U4pwLU4p063, statically linked, no section header
./tailscale/tailscale_i386_Linux:                            ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=kllWTlM2_TnCu8QTz3-O/okvGJms5m_Mznv0CveED/KzCuVVrVWeU_U9nGLKHa/iy-qFqLYpVnLxz-N1_X9, BuildID[sha1]=a552c8527aaa42f08d12a02cbb9237bfa9a67ebb, stripped
./tailscale/tailscale_i386_Linux.upx:                        ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=kllWTlM2_TnCu8QTz3-O/okvGJms5m_Mznv0CveED/KzCuVVrVWeU_U9nGLKHa/iy-qFqLYpVnLxz-N1_X9, statically linked, no section header
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
./tailscale/tailscale_merged_powerpc64_ppc64_Linux:          ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx:      ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux:      ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx:  ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_merged_s390x_Linux:                    ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_mips64_Linux:                          ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=CdYa5Ta9REZacvr8VjZ9/d-kPsuZB57q4DSGbKI5r/dvv_788lz6z2cRUWcO5H/9fMtvz5I2RbuLJShKUAr, BuildID[sha1]=f4487595380ab620ac81ce0c7a804bef86e9ba33, with debug_info, not stripped
./tailscale/tailscale_mips64le_Linux:                        ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=igsolxJNGamc-C0kFyy3/SRbzTZh73HG3RiMzAfda/NXJbdOkmypS19XIdJVAz/Q0FSlf6-wVRSNcd5OE1m, BuildID[sha1]=58ef86e5c23cc1740a40d4b1bb708e6789e5415f, with debug_info, not stripped
./tailscale/tailscale_mips_Linux:                            ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=euh9rph2WXUNa3reTQvU/CrEi8O0Nmjvh3zE4e4FU/qtUV1wwFi0JiT37DQnvK/LwDkvt2FUG_AOPuxKqrm, BuildID[sha1]=a9b1e486a64ff5a252613a0352121f77f4726ed7, with debug_info, not stripped
./tailscale/tailscale_mips_Linux.upx:                        ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=euh9rph2WXUNa3reTQvU/CrEi8O0Nmjvh3zE4e4FU/qtUV1wwFi0JiT37DQnvK/LwDkvt2FUG_AOPuxKqrm, statically linked, no section header
./tailscale/tailscale_mipsle_Linux:                          ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=sNMZ-M__4sqNsIuwu3Ar/xyV5RFwvThb-NGky2R-i/KfW8mztjuDDjWqQKuItA/4xIJ_2HeReB-jN8f69Js, BuildID[sha1]=45ae9fc19eb33f0076501e037e3b1c7192464ac0, with debug_info, not stripped
./tailscale/tailscale_mipsle_Linux.upx:                      ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=sNMZ-M__4sqNsIuwu3Ar/xyV5RFwvThb-NGky2R-i/KfW8mztjuDDjWqQKuItA/4xIJ_2HeReB-jN8f69Js, statically linked, no section header
./tailscale/tailscale_powerpc64_ppc64_Linux:                 ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64_ppc64_Linux.upx:             ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_powerpc64le_ppc64le_Linux:             ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx:         ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_riscv64_Linux:                         ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, Go BuildID=DsM6Lu_E9z9VfWaq8UmN/C8lC60Kb55VadjHOYalW/6fjrhqGi_FKy5ME342tB/sTMPZD5DMDCDVeseQVV5, BuildID[sha1]=68f399ae309a90761e8012e0d85757e8da7cf735, with debug_info, not stripped
./tailscale/tailscale_s390x_Linux:                           ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_setup_Windows.exe:                     PE32 executable (GUI) Intel 80386, for MS Windows, 6 sections
./tailscale/tailscale_x86_Windows.msi:                       Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Intel;1033, Revision Number: {E44CFF7E-1A28-47B5-B19E-927FE28844A2}, Create Time/Date: Tue Nov 10 23:57:42 2026, Last Saved Time/Date: Tue Nov 10 23:57:42 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (6.0.2.0), Security: 2
./tailscale/tailscaled_aarch64_arm64_Linux:                  ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=p5BsJieqU4nBfyooY0Vb/hB3a_DDhJ0xGl6KhZDzF/5hOyD1DyaiQ2NmQVCdg9/MAmCNXQpHcLcFaK7RTRv, BuildID[sha1]=4b620d7e96f84230fc41fd14168b6ed5cc3ee5b9, with debug_info, not stripped
./tailscale/tailscaled_aarch64_arm64_Linux.upx:              ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=p5BsJieqU4nBfyooY0Vb/hB3a_DDhJ0xGl6KhZDzF/5hOyD1DyaiQ2NmQVCdg9/MAmCNXQpHcLcFaK7RTRv, statically linked, no section header
./tailscale/tailscaled_aarch64_arm64_macOS:                  Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_amd_geode_Linux:                      ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=UanBUGmlPaWvxLy7AoiF/PpjkYfMioEdATHmXtzmS/xFKVwxCChI40PmUfn7mY/gvP-I3pc_bvSp3ehEV1V, BuildID[sha1]=4d0270d4a1a8dfef43c8a84dc8df2dd07bf7c620, stripped
./tailscale/tailscaled_amd_geode_Linux.upx:                  ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=UanBUGmlPaWvxLy7AoiF/PpjkYfMioEdATHmXtzmS/xFKVwxCChI40PmUfn7mY/gvP-I3pc_bvSp3ehEV1V, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_Linux:                     ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=viXAlQwplUJVBquzf4I5/Fw8Sku2iOPWSINIc6A8J/gAY2MLe9Fo1iJ4x39jiN/e3etK4Ku7ypZl8d4aAP9, BuildID[sha1]=ddc535ac00afb0a10304f2f952afb2a523ec23ce, stripped
./tailscale/tailscaled_amd_x86_64_Linux.upx:                 ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=viXAlQwplUJVBquzf4I5/Fw8Sku2iOPWSINIc6A8J/gAY2MLe9Fo1iJ4x39jiN/e3etK4Ku7ypZl8d4aAP9, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_macOS:                     Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_arm_abi_Linux:                        ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=W3YxwH3OOfMp9n2BLkKB/yxedR4G-yTwQEYa7VnYP/BzwbhKTHXLND9UAqzwbV/Uqv5VgnyYPGvkbMJjt9m, BuildID[sha1]=d472581862da9dde12ec3c510aa9b40ea68d4e66, with debug_info, not stripped
./tailscale/tailscaled_arm_abi_Linux.upx:                    ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=W3YxwH3OOfMp9n2BLkKB/yxedR4G-yTwQEYa7VnYP/BzwbhKTHXLND9UAqzwbV/Uqv5VgnyYPGvkbMJjt9m, statically linked, no section header
./tailscale/tailscaled_i386_Linux:                           ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=eNF0BY-Qdjdm5VteV6RJ/XKZMSUZ6a63RYIk4pPAu/EOWB0Vk88Z1sPIqqlW20/NK4OdidiI-OksQi3mSpz, BuildID[sha1]=72f2905806e476c1c4e91de4a8069f420ed870ca, stripped
./tailscale/tailscaled_i386_Linux.upx:                       ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=eNF0BY-Qdjdm5VteV6RJ/XKZMSUZ6a63RYIk4pPAu/EOWB0Vk88Z1sPIqqlW20/NK4OdidiI-OksQi3mSpz, statically linked, no section header
./tailscale/tailscaled_mips64_Linux:                         ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=z50tdn7TcYRdzv3NR_ht/aqMPcOLncXqmWttm6CQe/6XVKE5f46ExbUacRgTDt/-KOlJNmZP9qlHu893ZJq, BuildID[sha1]=11ac4d39f263115513724bf5d4d41829850bad39, with debug_info, not stripped
./tailscale/tailscaled_mips64le_Linux:                       ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=aPSrprPGv7K_8jZpLeGF/AJmYHsgb9S8MAGVKKzFa/aUmu3Z6prLvqduO8V4-g/CYz-zFAtmaigRzPqvAot, BuildID[sha1]=a12542231e1862f6cbfbbc0cdbbf635ccac24ec7, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux:                           ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=A3xRiPrz3orqJ6Kq_bMv/otk6j_7oxjdyauOvj5XI/7MG00YLSCdwSVBvIMyyy/yo1ZBEue7metfZpnXLjK, BuildID[sha1]=290cfead509931f732bab0be8bd0776c62ebed53, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux.upx:                       ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=A3xRiPrz3orqJ6Kq_bMv/otk6j_7oxjdyauOvj5XI/7MG00YLSCdwSVBvIMyyy/yo1ZBEue7metfZpnXLjK, statically linked, no section header
./tailscale/tailscaled_mipsle_Linux:                         ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=lr-mBD_2wsAu6N0E_kmH/RAuWsU53jRnPpPHDISOw/r9i3rvmL067mwpcjJgLy/7XJct_gk6KZdooLtJiqE, BuildID[sha1]=0d44191c0a99acb821a281524835641927e51ff1, with debug_info, not stripped
./tailscale/tailscaled_mipsle_Linux.upx:                     ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=lr-mBD_2wsAu6N0E_kmH/RAuWsU53jRnPpPHDISOw/r9i3rvmL067mwpcjJgLy/7XJct_gk6KZdooLtJiqE, statically linked, no section header
./tailscale/tailscaled_powerpc64_ppc64_Linux:                ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64_ppc64_Linux.upx:            ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_powerpc64le_ppc64le_Linux:            ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx:        ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_riscv64_Linux:                        ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, Go BuildID=r0PgomiO9FS1hSvXWl8O/rNte_CApA79yjGT0Odsr/LhNIoH6IDTk5_-JBY2mX/N57NzvG_cp4F_Ma_bouA, BuildID[sha1]=41bf32054d7caaaf29f7461e9bcb66eba8dde80b, with debug_info, not stripped
./tailscale/tailscaled_s390x_Linux:                          ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped

--> SHA256SUM
2e547c5e8acb4e9dc7c3ae576c302346044bd2f30958515cca5b7a91fb5cd636  ./tailscale/tailscale_aarch64_arm64_Linux
2e84bc950251c28243a2909b3278b16a59e64f363d53f01543087729ad1b6271  ./tailscale/tailscale_aarch64_arm64_Linux.upx
2810b17d4edcb6feb0307d0029e67426d2af78f0e4b1092fbbe307f5875c82b7  ./tailscale/tailscale_aarch64_arm64_Windows.msi
758bd296723a348a70f5274b294baeb4053abd2e2ce58e2220e210946b618c6f  ./tailscale/tailscale_aarch64_arm64_macOS
769e424294898af1c792f6fbf94fdf813b2612d2d601d6a9e019b14db824125b  ./tailscale/tailscale_amd_geode_Linux
408dffbda9c562adc3c9aca68919437793acb1e1afe932a4ed96bcb91c58c8f5  ./tailscale/tailscale_amd_geode_Linux.upx
13391054bd1d5a9868eb8908c124bc1bef358a3691e00d6f02a267f6ab6a5875  ./tailscale/tailscale_amd_x86_64_Linux
6bedc78e4c62a18fc30e59bdf93d2462a6a50dbdc4da99a5943dd7dd6bbe9978  ./tailscale/tailscale_amd_x86_64_Linux.upx
8445636f79e258f56e01d324e5562d4ebcdf898ab84c2e618ae05014b8ba90ab  ./tailscale/tailscale_amd_x86_64_Windows.msi
248b7930c0c4c650f988bcb90a968da042066e0b826bf58efd8fe3a69fad8e7f  ./tailscale/tailscale_amd_x86_64_macOS
3ee4af9cf7b35d47650b0231c8a8c7853661ec2168e01c4ea3b22b00f3fc7ada  ./tailscale/tailscale_arm_abi_Linux
34c83f4118ad9d6ba562496ca9736920083e4bccc8e7d79d0e7a3b7dfe6d7af6  ./tailscale/tailscale_arm_abi_Linux.upx
1d8ed236cab2e7a0a8e330552fc2beefbee733507e6236053a339be354f22e23  ./tailscale/tailscale_i386_Linux
57b2a654c26dba9697d0a1936bde6d9d7c91bae8a1a9dce268cf56d7ca467046  ./tailscale/tailscale_i386_Linux.upx
68af7d50ee2b3c8b534918ddfa8f9d4a95d3c96301af9ae950effe8a8b4b44c4  ./tailscale/tailscale_ipn_setup_Windows.exe
48558454d6ae518b35ccdaaf1073b8ba38f55a44c9e000a9f63fb42417caaf49  ./tailscale/tailscale_merged_aarch64_arm64_Linux
d4f0c6100acfe1803b7a2017c345d73d757e7f2708ee5f38dac10567bdd1266f  ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
68728bde1313493eb44dbd3be2e989eb00f60f4938d0d2845df9d45e32c25df7  ./tailscale/tailscale_merged_aarch64_arm64_macOS
15e78c513126bd66b9c21b463b14d406911024c8c3c4e5c9ddf65522a07d072a  ./tailscale/tailscale_merged_amd_x86_64_Linux
995d2fb604a237f454b117e004482eb61c2b9cadaab631f9491cf932ba3b8ca4  ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
267bebcfe539dd8353add30caf55a042bf996f8e688aae7910b9ecf61714f3f8  ./tailscale/tailscale_merged_amd_x86_64_macOS
b9689a035857a76f599bf31b7b785fdae1d154e47618368d4f25f69ac0e1f86d  ./tailscale/tailscale_merged_arm_Linux
2523db75db6d0d04c0d10e1e1f094f09f8044bfb687ed5582d035bd7de510210  ./tailscale/tailscale_merged_arm_Linux.upx
fc1f92fb55c978a63e0be9ed87e85c7fdcbfbaa686b5f7b1c084c5f70b43cd75  ./tailscale/tailscale_merged_i386_Linux
1cf27a946e3493e7eddb1722c16e7d69b8688b940144abf8e6377df224636fcf  ./tailscale/tailscale_merged_i386_Linux.upx
50bc8acce033080fc361b05d52ca37d2e265061bb66b683a013f25408c27c02c  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux
eb0e7a3fd4894fc52817acec9b328426fc22514d6ea2e7d37afbb2b7b77cd694  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
174dbfbb0a2e9a740f0be82b6feff18f27dffd8e0d23de8aa0827935a134e1a6  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux
befeb064ea50ce087d30841c300c7fb927c490035f68c2eea8809d6074958d34  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
ac8a41d6387f1d4ffa79bd46bd7b695f4b3d4f781a96392b21f4d73a9a259d02  ./tailscale/tailscale_merged_s390x_Linux
01045169a47020d3d7637b73b23309fbc95779887245e431b018f32c81371ec1  ./tailscale/tailscale_mips64_Linux
2eb46ea46c143364cebcbd3a875d2afe7d55fa04853e3d17e953e6604ceed89d  ./tailscale/tailscale_mips64le_Linux
b6c90360afe7b91e6c159eb5a264c974e188038d6407b30015dba0fcf03691bc  ./tailscale/tailscale_mips_Linux
e9afa05141311f7e9f43495ef9f819d17c66e7046dd32e45c7f7afaef37316d9  ./tailscale/tailscale_mips_Linux.upx
f91d961b40ca5666382b8a3a222080d2263980433fa3929de68db495dde5b346  ./tailscale/tailscale_mipsle_Linux
675000c357e0410bfcea8f94c4f4b1edcb3d49e0f5d0a052c73e4108d40ca0b3  ./tailscale/tailscale_mipsle_Linux.upx
22982d24e2a892770d53f7fa27403f5c9e3090e634bc12e2ebcaf27a855fd420  ./tailscale/tailscale_powerpc64_ppc64_Linux
dfb6135da0fe0403593a44d6a3a4ef69c9a94009dc8218ea41d78642c9f2b70e  ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
52a056b0ff6e465a0a48c4d080e5a17d1728770bc627619b8de3ac1458354f09  ./tailscale/tailscale_powerpc64le_ppc64le_Linux
cbe2871947e972a9ad40baa221ca04379a65594dcf4e611820217ac37aaad6e3  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
919df018b539f889f14538a853cc923290365e999d668bc94d8a4fba42fed155  ./tailscale/tailscale_riscv64_Linux
26ba1c5e6233fa91883504438d84bda5fa1a8a5a0ef154a8dd0a697078909faa  ./tailscale/tailscale_s390x_Linux
64a8ad28cbb67a6171236abe39f75a039a761a0e1aacdef75b26781887cef9a8  ./tailscale/tailscale_setup_Windows.exe
f2b822e0e567cbedc857eb993e78167b4b49d865801f490a83f36b3b1f6da340  ./tailscale/tailscale_x86_Windows.msi
904044a58d6b22426fa2ff2307f774dc69c0edda0c5053bc3de53fb11a0b8e40  ./tailscale/tailscaled_aarch64_arm64_Linux
829a9abbe8635622fede932ec957f8f0fd20f248c0bfba69b5a7bc6b7b05dd6a  ./tailscale/tailscaled_aarch64_arm64_Linux.upx
3045786fe6191b3d64ae9d2b03b5fffcf080e3cb3073a3c2e8e69e57ea05e2cf  ./tailscale/tailscaled_aarch64_arm64_macOS
2b07617179a2d3814a8e3a21b6e3e88c5c7680d5e36fd7a131f7322281e62abd  ./tailscale/tailscaled_amd_geode_Linux
1a57126f1134ffee64301d745ae00044fb46fbde0a0f21c69c8ee232c3e17011  ./tailscale/tailscaled_amd_geode_Linux.upx
cc6d3e9f24bc408eb8eb84f90bc16688a32958a5be96ded902a0546296b4b305  ./tailscale/tailscaled_amd_x86_64_Linux
5db3b19bef5129b457473b3f6f46b6e6f347610801f5b4435815ddfae18e63f8  ./tailscale/tailscaled_amd_x86_64_Linux.upx
b5304b43985998d94d5c2c94e0eeb9e160a76906fa0ecb224af45c3b878e684d  ./tailscale/tailscaled_amd_x86_64_macOS
747e09defb84e123863da9d91d3602536f3882385066c765ca99476a77397174  ./tailscale/tailscaled_arm_abi_Linux
49f4c61d3b2cd1fb43fdd942158ce3fd4065074b5273a67e5ede237938c5c7a6  ./tailscale/tailscaled_arm_abi_Linux.upx
35cfc5fac0cc52f848dd3b93a72233d6ae36ef34e8843403ca46a8e1d95c6353  ./tailscale/tailscaled_i386_Linux
1299d404c8e03823c4c4703563947e8a835ecd4621918c64102230c8421dad5d  ./tailscale/tailscaled_i386_Linux.upx
458ba61baa73780904ce186cc6c9ac230340863241b57fa64239566f7a210daf  ./tailscale/tailscaled_mips64_Linux
5a5fa5722c86cb6d1f17399669c849b6f5c69b632fb6ae3386eceae74b0363f9  ./tailscale/tailscaled_mips64le_Linux
5ab2fda8f406996fec28a28cbb704f32adec197d3b84f71f1815f42f663312c1  ./tailscale/tailscaled_mips_Linux
0f7bdaf5c18a82c278fdcb7c2a16eb2b17f699ec14aebf2d5d0f6597f4373812  ./tailscale/tailscaled_mips_Linux.upx
cb9098041539320fa6e619ae157e4a80e3e1b7373e886f35c1c7480673d5ea6d  ./tailscale/tailscaled_mipsle_Linux
a8600560946cfdb47043c40b38c8d5a61f87298092bba9f7c61e67f42dee9ec9  ./tailscale/tailscaled_mipsle_Linux.upx
a6b417a23b486151887c9ea3acdab1040ee0d5a83872307129469d92ac4683fa  ./tailscale/tailscaled_powerpc64_ppc64_Linux
56d80611e189cad4c01aed5aba2d5610e486689a9f61eebea76e964a2facae35  ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
22283cf918d15904338142b6ad1b1075ee01d72015e000ca42e263131537fca2  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux
2d485433f4c63ad94f0f7df2f68314c0d7c0dd6bffffef6953c449992a387909  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
482e53356de8919e7a11e973d9e073a5d68cb6a3fb43be074c2f7283dd32a421  ./tailscale/tailscaled_riscv64_Linux
75f320687619299302b7bde105da5e8c220659ef0ea7847afe4ac00fd2d9a61e  ./tailscale/tailscaled_s390x_Linux
```


---

- #### Sizes

```console
31M   ./tailscale/tailscale_aarch64_arm64_Linux
13M   ./tailscale/tailscale_aarch64_arm64_Linux.upx
35M   ./tailscale/tailscale_aarch64_arm64_Windows.msi
11M   ./tailscale/tailscale_aarch64_arm64_macOS
22M   ./tailscale/tailscale_amd_geode_Linux
6.1M  ./tailscale/tailscale_amd_geode_Linux.upx
23M   ./tailscale/tailscale_amd_x86_64_Linux
6.4M  ./tailscale/tailscale_amd_x86_64_Linux.upx
37M   ./tailscale/tailscale_amd_x86_64_Windows.msi
11M   ./tailscale/tailscale_amd_x86_64_macOS
31M   ./tailscale/tailscale_arm_abi_Linux
13M   ./tailscale/tailscale_arm_abi_Linux.upx
22M   ./tailscale/tailscale_i386_Linux
6.1M  ./tailscale/tailscale_i386_Linux.upx
70K   ./tailscale/tailscale_ipn_setup_Windows.exe
35M   ./tailscale/tailscale_merged_aarch64_arm64_Linux
8.3M  ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
20M   ./tailscale/tailscale_merged_aarch64_arm64_macOS
38M   ./tailscale/tailscale_merged_amd_x86_64_Linux
11M   ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
20M   ./tailscale/tailscale_merged_amd_x86_64_macOS
36M   ./tailscale/tailscale_merged_arm_Linux
8.1M  ./tailscale/tailscale_merged_arm_Linux.upx
36M   ./tailscale/tailscale_merged_i386_Linux
9.4M  ./tailscale/tailscale_merged_i386_Linux.upx
37M   ./tailscale/tailscale_merged_powerpc64_ppc64_Linux
8.2M  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
37M   ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux
8.5M  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
39M   ./tailscale/tailscale_merged_s390x_Linux
35M   ./tailscale/tailscale_mips64_Linux
35M   ./tailscale/tailscale_mips64le_Linux
34M   ./tailscale/tailscale_mips_Linux
13M   ./tailscale/tailscale_mips_Linux.upx
34M   ./tailscale/tailscale_mipsle_Linux
13M   ./tailscale/tailscale_mipsle_Linux.upx
23M   ./tailscale/tailscale_powerpc64_ppc64_Linux
5.2M  ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
23M   ./tailscale/tailscale_powerpc64le_ppc64le_Linux
5.4M  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
30M   ./tailscale/tailscale_riscv64_Linux
24M   ./tailscale/tailscale_s390x_Linux
51M   ./tailscale/tailscale_setup_Windows.exe
37M   ./tailscale/tailscale_x86_Windows.msi
40M   ./tailscale/tailscaled_aarch64_arm64_Linux
17M   ./tailscale/tailscaled_aarch64_arm64_Linux.upx
19M   ./tailscale/tailscaled_aarch64_arm64_macOS
26M   ./tailscale/tailscaled_amd_geode_Linux
7.3M  ./tailscale/tailscaled_amd_geode_Linux.upx
29M   ./tailscale/tailscaled_amd_x86_64_Linux
8.2M  ./tailscale/tailscaled_amd_x86_64_Linux.upx
19M   ./tailscale/tailscaled_amd_x86_64_macOS
37M   ./tailscale/tailscaled_arm_abi_Linux
16M   ./tailscale/tailscaled_arm_abi_Linux.upx
25M   ./tailscale/tailscaled_i386_Linux
7.3M  ./tailscale/tailscaled_i386_Linux.upx
41M   ./tailscale/tailscaled_mips64_Linux
41M   ./tailscale/tailscaled_mips64le_Linux
40M   ./tailscale/tailscaled_mips_Linux
16M   ./tailscale/tailscaled_mips_Linux.upx
40M   ./tailscale/tailscaled_mipsle_Linux
16M   ./tailscale/tailscaled_mipsle_Linux.upx
27M   ./tailscale/tailscaled_powerpc64_ppc64_Linux
6.3M  ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
27M   ./tailscale/tailscaled_powerpc64le_ppc64le_Linux
6.5M  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
36M   ./tailscale/tailscaled_riscv64_Linux
28M   ./tailscale/tailscaled_s390x_Linux
```

---

- #### UPX
```console

testing ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx [OK]
  27263100 ->   6807748   24.97%  linux/ppc64le  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscaled_arm_abi_Linux.upx [OK]
  37988468 ->  15959816   42.01%    linux/arm    ./tailscale/tailscaled_arm_abi_Linux.upx
testing ./tailscale/tailscale_mips_Linux.upx [OK]
  34928740 ->  13141792   37.62%   linux/mips    ./tailscale/tailscale_mips_Linux.upx
testing ./tailscale/tailscale_merged_amd_x86_64_Linux.upx [OK]
  39190652 ->  10503028   26.80%   linux/amd64   ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx [OK]
  36307068 ->   8604184   23.70%   linux/arm64   ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
testing ./tailscale/tailscaled_amd_x86_64_Linux.upx [OK]
  30225784 ->   8551408   28.29%   linux/amd64   ./tailscale/tailscaled_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_mipsle_Linux.upx [OK]
  34919384 ->  13265484   37.99%  linux/mipsel   ./tailscale/tailscale_mipsle_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx [OK]
  38273148 ->   8854156   23.13%  linux/ppc64le  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_merged_i386_Linux.upx [OK]
  36761724 ->   9828560   26.74%   linux/i386    ./tailscale/tailscale_merged_i386_Linux.upx
testing ./tailscale/tailscaled_amd_geode_Linux.upx [OK]
  26232460 ->   7587500   28.92%   linux/i386    ./tailscale/tailscaled_amd_geode_Linux.upx
testing ./tailscale/tailscale_amd_geode_Linux.upx [OK]
  22340780 ->   6304644   28.22%   linux/i386    ./tailscale/tailscale_amd_geode_Linux.upx
testing ./tailscale/tailscale_merged_arm_Linux.upx [OK]
  36831356 ->   8437820   22.91%    linux/arm    ./tailscale/tailscale_merged_arm_Linux.upx
testing ./tailscale/tailscaled_mips_Linux.upx [OK]
  41693918 ->  15949756   38.25%   linux/mips    ./tailscale/tailscaled_mips_Linux.upx
testing ./tailscale/tailscale_powerpc64_ppc64_Linux.upx [OK]
  23068796 ->   5409792   23.45%   linux/ppc64   ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscaled_mipsle_Linux.upx [OK]
  41691314 ->  16098328   38.61%  linux/mipsel   ./tailscale/tailscaled_mipsle_Linux.upx
testing ./tailscale/tailscaled_i386_Linux.upx [OK]
  26195596 ->   7578088   28.93%   linux/i386    ./tailscale/tailscaled_i386_Linux.upx
testing ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx [OK]
  27263100 ->   6565660   24.08%   linux/ppc64   ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx [OK]
  38338684 ->   8546836   22.29%   linux/ppc64   ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_aarch64_arm64_Linux.upx [OK]
  31911825 ->  13431444   42.09%   linux/arm64   ./tailscale/tailscale_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_arm_abi_Linux.upx [OK]
  32010133 ->  13205268   41.25%    linux/arm    ./tailscale/tailscale_arm_abi_Linux.upx
testing ./tailscale/tailscale_i386_Linux.upx [OK]
  22287532 ->   6292656   28.23%   linux/i386    ./tailscale/tailscale_i386_Linux.upx
testing ./tailscale/tailscale_amd_x86_64_Linux.upx [OK]
  23739672 ->   6696780   28.21%   linux/amd64   ./tailscale/tailscale_amd_x86_64_Linux.upx
testing ./tailscale/tailscaled_aarch64_arm64_Linux.upx [OK]
  40983698 ->  17377928   42.40%   linux/arm64   ./tailscale/tailscaled_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx [OK]
  23068796 ->   5617648   24.35%  linux/ppc64le  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx

```

---

- #### Version
```console
$ ./tailscale/tailscale_amd_x86_64_Linux --version
1.104.6
  tailscale commit: 3b273a64cef3fe6d3d495afae7bb6a553344ce64
  long version: 1.104.6-t3b273a64c-gdf9d2ed85
  other commit: df9d2ed85fe8d628d95cd3827089ab763de8a293
  go version: go1.27.3 (tailscale/go 7ef7b40364)

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
  get          Show current preference values
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
  service      Interact with Tailscale Services
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
  whoami       Show the machine and user identity of the current machine
  drive        Share a directory with your tailnet
  systray      Run a systray application to manage Tailscale
  appc-routes  Print the current app connector routes
  wait         Wait for Tailscale interface/IPs to be ready for binding
  completion   Shell tab-completion scripts

FLAGS
  --socket value
    	path to tailscaled socket (default /var/run/tailscale/tailscaled.sock)

$ ./tailscale/tailscaled_amd_x86_64_Linux -version
1.104.6
  tailscale commit: 3b273a64cef3fe6d3d495afae7bb6a553344ce64
  long version: 1.104.6-t3b273a64c-gdf9d2ed85
  other commit: df9d2ed85fe8d628d95cd3827089ab763de8a293
  go version: go1.27.3 (tailscale/go 7ef7b40364)

Usage of ./tailscale/tailscaled_amd_x86_64_Linux:
  -bird-socket string
    	path of the bird unix socket
  -cleanup
    	clean up system state and exit
  -config string
    	path to config file, or 'vm:user-data' to use the VM's user-data (EC2); prefix with 'optional:' to boot unconfigured when the source is absent instead of failing
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
  -syslog
    	log to the system syslog daemon instead of stderr
  -syspolicy-file string
    	path to a JSON syspolicy file applied as a device-scope policy source; empty disables (default "/etc/tailscale/syspolicy.json")
  -tun string
    	tunnel interface name; use "userspace-networking" (beta) to not use TUN (default "tailscale0")
  -verbose int
    	log verbosity level; 0 is default, 1 or higher are increasingly verbose
  -version
    	print version information and exit

```

---


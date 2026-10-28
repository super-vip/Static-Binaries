
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
./tailscale/tailscale_aarch64_arm64_Linux:                   ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=HnpT1aTbPodGVvsKZQuz/NuvjYRMjlJJ2DRqDoEce/6DJgKPUbImZwHeP9LgXk/0VaLkzYrensJc5aWTv88, BuildID[sha1]=9b004507f70250c65656d825430b02c784301ef7, with debug_info, not stripped
./tailscale/tailscale_aarch64_arm64_Linux.upx:               ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=HnpT1aTbPodGVvsKZQuz/NuvjYRMjlJJ2DRqDoEce/6DJgKPUbImZwHeP9LgXk/0VaLkzYrensJc5aWTv88, statically linked, no section header
./tailscale/tailscale_aarch64_arm64_Windows.msi:             Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Arm64;1033, Revision Number: {47D80D96-AB0B-4CED-A8EA-426C9B986C47}, Create Time/Date: Wed Oct 28 00:29:11 2026, Last Saved Time/Date: Wed Oct 28 00:29:11 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscale_aarch64_arm64_macOS:                   Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_amd_geode_Linux:                       ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=1GUULnrTjybELTM3D3gk/LMk48taVnK5rIWOBjaXK/5BWwD-Uc0Bb_dife-ngW/TLQPoI3Bp9ye0YS_jF6a, BuildID[sha1]=c396a309386d9946fbf780e28966e55c6e996939, stripped
./tailscale/tailscale_amd_geode_Linux.upx:                   ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=1GUULnrTjybELTM3D3gk/LMk48taVnK5rIWOBjaXK/5BWwD-Uc0Bb_dife-ngW/TLQPoI3Bp9ye0YS_jF6a, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Linux:                      ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=7CFS-oswRU6CFMCTfHpq/kZ4-i022sbEHOlYM9cOD/tY1npHGDN8_U063NlKbN/AOrsEFC2D7NO-VZxGXV7, BuildID[sha1]=80dfe1bfb86ea16055bd11a2f22225a5a6000ff0, stripped
./tailscale/tailscale_amd_x86_64_Linux.upx:                  ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=7CFS-oswRU6CFMCTfHpq/kZ4-i022sbEHOlYM9cOD/tY1npHGDN8_U063NlKbN/AOrsEFC2D7NO-VZxGXV7, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Windows.msi:                Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: x64;1033, Revision Number: {24386ABE-CC73-4964-9DFD-CC19646DC31B}, Create Time/Date: Wed Oct 28 00:29:42 2026, Last Saved Time/Date: Wed Oct 28 00:29:42 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscale_amd_x86_64_macOS:                      Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_arm_abi_Linux:                         ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=NzquY0Wq5F8akqBRbQW_/zPVk0oGAHe1JVW-gj6Zn/ocslcMrtUs5Qz4dJUAE9/VvUwJmIZujUlNy4gUU0X, BuildID[sha1]=b46cefe1de0cd618d88b1198fe6c7a53906cc738, with debug_info, not stripped
./tailscale/tailscale_arm_abi_Linux.upx:                     ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=NzquY0Wq5F8akqBRbQW_/zPVk0oGAHe1JVW-gj6Zn/ocslcMrtUs5Qz4dJUAE9/VvUwJmIZujUlNy4gUU0X, statically linked, no section header
./tailscale/tailscale_i386_Linux:                            ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=qRhLhijsACgPQ_InJJ4Y/WY8kvdAR-UHBoR7laXPW/FWCERu_BV4uuANScww_x/19fQ0kiLaGxR563zL12C, BuildID[sha1]=a04eeb0e09a19f4d840d87cbdc883a83cb32c180, stripped
./tailscale/tailscale_i386_Linux.upx:                        ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=qRhLhijsACgPQ_InJJ4Y/WY8kvdAR-UHBoR7laXPW/FWCERu_BV4uuANScww_x/19fQ0kiLaGxR563zL12C, statically linked, no section header
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
./tailscale/tailscale_mips64_Linux:                          ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=hzaxDsXOT9d_IDFXqsjM/-WDBp_oO5VthX6SYguEQ/B-OtR1h76YvPd8UpvXmW/MdSYniMdRP8MwD3DNrle, BuildID[sha1]=e4a07e34ec46db008c9af69879ff8cd0409a6be0, with debug_info, not stripped
./tailscale/tailscale_mips64le_Linux:                        ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=d0qF2zbeBMU_q2d6u_UE/h-PZN3RB8j4fj2OMqT9o/4lCulsET0IVVvOHjtjwD/31-MTiHW72YVxyLiTMow, BuildID[sha1]=759206603c50f48f7ec8637c97941077d42a9641, with debug_info, not stripped
./tailscale/tailscale_mips_Linux:                            ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=5iEnKclGSl6kVFZlUL6A/eMA41xt-uv8tr72vRphY/Pl6G-wHtXQkLGeAO96Bu/cSUGXd3wRq8bw-PBCSek, BuildID[sha1]=05e629385a5476df1c20258de523b9f63be9a1c1, with debug_info, not stripped
./tailscale/tailscale_mips_Linux.upx:                        ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=5iEnKclGSl6kVFZlUL6A/eMA41xt-uv8tr72vRphY/Pl6G-wHtXQkLGeAO96Bu/cSUGXd3wRq8bw-PBCSek, statically linked, no section header
./tailscale/tailscale_mipsle_Linux:                          ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=D7gIhFH-Z0Z5_Wd9tBRz/JsglsKHUZIioU6_UrDmy/VUzxbMsIEl8k52NET4ID/GxuR9Xg1m4mxHKPfVYgg, BuildID[sha1]=38b6a7e64dc92c4ec04b29839f88f80c566d3f32, with debug_info, not stripped
./tailscale/tailscale_mipsle_Linux.upx:                      ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=D7gIhFH-Z0Z5_Wd9tBRz/JsglsKHUZIioU6_UrDmy/VUzxbMsIEl8k52NET4ID/GxuR9Xg1m4mxHKPfVYgg, statically linked, no section header
./tailscale/tailscale_powerpc64_ppc64_Linux:                 ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64_ppc64_Linux.upx:             ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_powerpc64le_ppc64le_Linux:             ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx:         ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_riscv64_Linux:                         ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, Go BuildID=8_Knk0lIbAw021nF9JBx/_bzoPohQSypKJoCOH4ep/G2cvRmYSYJfcf9KUvUPw/XZAclsg-oaXQZp0Qm7uH, BuildID[sha1]=2c1b5874b958ad30c25f73c1895998d9017ff54d, with debug_info, not stripped
./tailscale/tailscale_s390x_Linux:                           ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_setup_Windows.exe:                     PE32 executable (GUI) Intel 80386, for MS Windows, 6 sections
./tailscale/tailscale_x86_Windows.msi:                       Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Intel;1033, Revision Number: {146D2AA8-0C55-49F3-A884-0BA1E54C189B}, Create Time/Date: Wed Oct 28 00:29:02 2026, Last Saved Time/Date: Wed Oct 28 00:29:02 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscaled_aarch64_arm64_Linux:                  ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=wuLQRUhEaneL0nbqNVUD/gyIsyb8r6mMfxtSRaHw6/FO0ftdmohZgdYgzJvSk5/b0lr7VtZuUjkskA_wq4r, BuildID[sha1]=e1a25b93d96606621fc48fa842f38dd94663e0c0, with debug_info, not stripped
./tailscale/tailscaled_aarch64_arm64_Linux.upx:              ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=wuLQRUhEaneL0nbqNVUD/gyIsyb8r6mMfxtSRaHw6/FO0ftdmohZgdYgzJvSk5/b0lr7VtZuUjkskA_wq4r, statically linked, no section header
./tailscale/tailscaled_aarch64_arm64_macOS:                  Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_amd_geode_Linux:                      ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=EqJNtAD6_qvG2QOaJfkN/mmMf5_zzeuZNJSU7t_BJ/t9POfCtrMMAa8teCgXBd/nh6stVPWu9bWBknu-NLy, BuildID[sha1]=3a055d0ff6a4ce17fdbf58afa1e303417e8a94d9, stripped
./tailscale/tailscaled_amd_geode_Linux.upx:                  ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=EqJNtAD6_qvG2QOaJfkN/mmMf5_zzeuZNJSU7t_BJ/t9POfCtrMMAa8teCgXBd/nh6stVPWu9bWBknu-NLy, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_Linux:                     ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=42QbY4GTUVdLnl9NNxln/s8bdLxbKYmnuZwodeeic/DpsY31LlNl4CY3nMPRyp/vfVQf-uPcdNVc6YVj7P8, BuildID[sha1]=5d7eb96ff168d7773e1d5a170fef06cdabc4d3b7, stripped
./tailscale/tailscaled_amd_x86_64_Linux.upx:                 ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=42QbY4GTUVdLnl9NNxln/s8bdLxbKYmnuZwodeeic/DpsY31LlNl4CY3nMPRyp/vfVQf-uPcdNVc6YVj7P8, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_macOS:                     Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_arm_abi_Linux:                        ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=vdZ0BfdiVICiuxT2thTg/YDDwOfaucJ7uwGW__f5w/a5-rQqQw5gExdVCJmlTW/cxZwbr-ZM7WhzK5dJz07, BuildID[sha1]=7527c909cf38f15a6dd200ddf10fff940222ed76, with debug_info, not stripped
./tailscale/tailscaled_arm_abi_Linux.upx:                    ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=vdZ0BfdiVICiuxT2thTg/YDDwOfaucJ7uwGW__f5w/a5-rQqQw5gExdVCJmlTW/cxZwbr-ZM7WhzK5dJz07, statically linked, no section header
./tailscale/tailscaled_i386_Linux:                           ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=KAca2fZaYfPmQbc22BP5/G7TK5cYH-ZRPp8hj6LN5/KQLaigqULn6OxqWhLSRR/pss_E2v6GxYUmJAKilhB, BuildID[sha1]=7020eeec3989bb157112d56e776a356e311547ce, stripped
./tailscale/tailscaled_i386_Linux.upx:                       ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=KAca2fZaYfPmQbc22BP5/G7TK5cYH-ZRPp8hj6LN5/KQLaigqULn6OxqWhLSRR/pss_E2v6GxYUmJAKilhB, statically linked, no section header
./tailscale/tailscaled_mips64_Linux:                         ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=PxFJzAPmNAnIiQzQHgdQ/Pie--_HaEWu5tSu-TwqI/l-7sxtdLmkwvahQVr2QS/OVJYj_uHMbWEIEqzr0y-, BuildID[sha1]=0a045bbc1f5ff7c5f206396dae997de6a21d5e45, with debug_info, not stripped
./tailscale/tailscaled_mips64le_Linux:                       ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=7ayC0eaULO0c6RMMkjxn/4kHps-xMcOAlEEs-lqM-/e05817Q5-IFAb6AgRUfx/GxKEX6oMueAqRPTlZNNE, BuildID[sha1]=1345e449e568e250794a8642b20568400639b85f, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux:                           ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=2HM1MBfHO6QoONzBwomg/6kat8N08IzFmLSG5PHQM/1N6SJnWBmZtQj58Aj5wo/ULiEdjs9HBboHP1lHVL_, BuildID[sha1]=7b201a133a48e88398acd5a93e1926bf0853fca5, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux.upx:                       ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=2HM1MBfHO6QoONzBwomg/6kat8N08IzFmLSG5PHQM/1N6SJnWBmZtQj58Aj5wo/ULiEdjs9HBboHP1lHVL_, statically linked, no section header
./tailscale/tailscaled_mipsle_Linux:                         ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=1waiGZbsfMmQGF64SZ7n/uPy9TwfykffKStHMSy3E/eQnxgg64TcGQvKRrZt8M/PfjAbJLFtKKL4IjJYk9w, BuildID[sha1]=5d3fb695b97b7ba02fcf75d940a8fa5c79eb7aa7, with debug_info, not stripped
./tailscale/tailscaled_mipsle_Linux.upx:                     ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=1waiGZbsfMmQGF64SZ7n/uPy9TwfykffKStHMSy3E/eQnxgg64TcGQvKRrZt8M/PfjAbJLFtKKL4IjJYk9w, statically linked, no section header
./tailscale/tailscaled_powerpc64_ppc64_Linux:                ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64_ppc64_Linux.upx:            ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_powerpc64le_ppc64le_Linux:            ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx:        ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_riscv64_Linux:                        ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, Go BuildID=kCnpStmNJ6nQkSIfdpXR/xb9yiTeAXqu7KgxA1Xue/BRVlzRqZZrZh9cPkDOwO/YZ4ggMs-3aN1xVBkifsS, BuildID[sha1]=85544522b70bd1eb574abb987a31331aa301a554, with debug_info, not stripped
./tailscale/tailscaled_s390x_Linux:                          ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped

--> SHA256SUM
01c657aa13af9a13789aa5f5fa70327c200d5387f2ac8cf245ec73e213b15217  ./tailscale/tailscale_aarch64_arm64_Linux
79b3d190b76371d038b5cc3b469d9395584a779f1ab4c103ede6bbcdc42e2dc9  ./tailscale/tailscale_aarch64_arm64_Linux.upx
929fa96795d7fd8c1c1c7fa9060ae487c69095a89214c47e2e6a276fc847684c  ./tailscale/tailscale_aarch64_arm64_Windows.msi
758bd296723a348a70f5274b294baeb4053abd2e2ce58e2220e210946b618c6f  ./tailscale/tailscale_aarch64_arm64_macOS
2ca2331c82bda5ccf3c317691e6d70c1cc7f2b5d10130bf7c8a48f9bdc6cbf9c  ./tailscale/tailscale_amd_geode_Linux
01454dd99f2d6049c9094f3ea80385fdf4e573d875f4584f5f8b529bcdf8535a  ./tailscale/tailscale_amd_geode_Linux.upx
09d725bfdd0454c7fb83b3416e432e91a6b0705248bf75dbe998e6521030cf8b  ./tailscale/tailscale_amd_x86_64_Linux
1773c406478cd01daabcdc1cedbfe47ccf288245ccbf273f1a352f1ef61ddefb  ./tailscale/tailscale_amd_x86_64_Linux.upx
1d12cd8b1d6dbb447da8579b1a5268ae2fc050967bebfaa02e32d2bb645ef6ee  ./tailscale/tailscale_amd_x86_64_Windows.msi
248b7930c0c4c650f988bcb90a968da042066e0b826bf58efd8fe3a69fad8e7f  ./tailscale/tailscale_amd_x86_64_macOS
aa42fef7f6ea4aa9f1c8216d39a209fd01dce43711ed5ab0d0d0394d64be4d00  ./tailscale/tailscale_arm_abi_Linux
991830e91261d0f82cc2533e89b248fc15f575ed78a8b79c8038925da92b9861  ./tailscale/tailscale_arm_abi_Linux.upx
0ab571d3660032d98f171dedc40cec52e9cb015eab5c78b6138d585afc9c703a  ./tailscale/tailscale_i386_Linux
3e024cf916526c528e46544c1619a713e032f45160bb895a02ebffba06cdcd86  ./tailscale/tailscale_i386_Linux.upx
04f0914063ebcf0557b479c1d16613b04f90404d9e859db4d3bd2bfaa9f29a95  ./tailscale/tailscale_ipn_setup_Windows.exe
a9958f2a2e66e5469f1ccfb196d7ba892bc4dcec51afaccbd05a5beb8fcc6400  ./tailscale/tailscale_merged_aarch64_arm64_Linux
4ca785c768ba9ba402da4915208b8befcbb22dc7d1ca28ee16d7251412fc396d  ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
68728bde1313493eb44dbd3be2e989eb00f60f4938d0d2845df9d45e32c25df7  ./tailscale/tailscale_merged_aarch64_arm64_macOS
f25e48ba3d7a7b24768958bf6afb8d6f6e5660a79482f0ea868df8c59c5d4a6b  ./tailscale/tailscale_merged_amd_x86_64_Linux
2cc7c4cd46ba42a1eaf63c3556acd754b65e935fb84d114b4cb2925b88f281f8  ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
267bebcfe539dd8353add30caf55a042bf996f8e688aae7910b9ecf61714f3f8  ./tailscale/tailscale_merged_amd_x86_64_macOS
8172fb679bbdb063ecc907109ce2f6bcba3f291768b91d0afb1c03bc28887c8c  ./tailscale/tailscale_merged_arm_Linux
08f0c5fce1856375125eebb93535f974220fbf61fd0b1f145778d21629720e34  ./tailscale/tailscale_merged_arm_Linux.upx
158741f8adad31b6f5fa00a03aeeb6ed36fd190b717f123922d9044cebe6a2df  ./tailscale/tailscale_merged_i386_Linux
39f3eb7f76cc57af21af7d16c3ed4a3d66b18b1b583283a80882a84ee3c6173d  ./tailscale/tailscale_merged_i386_Linux.upx
86720b3bb5088ee552ec741b7795b9c16540c9075320d43296e7a8710d2bcdb1  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux
be0c276e0beaff634a0508f96b9407f00d8d9c121e1e4052e67154091e68ddc3  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
4f28ff5d77db339f1d46640f46f3e512dc5b44f2634ede6214676b346b4e5a2b  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux
4947855423016e6b45d88858a19cd5b0d27310350d86bf2a8e9f06bfedeace3d  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
c973cc05cd821bd18b221dce2280364838f2c41ce1823a5d5ec95cc8df019f4a  ./tailscale/tailscale_merged_s390x_Linux
a1743598e86c0174ea777b3a91aff548b3ce0ed4075eaf0ff98f8523cc44824f  ./tailscale/tailscale_mips64_Linux
6f94ea51e45ae801ae87d3d749450d332f4bd1a5f3fec81b7311fea1b83e6888  ./tailscale/tailscale_mips64le_Linux
f47d9218d5959d431ab268e483aa531744f551fbd3d1fa5db6c19c5f7d6e262c  ./tailscale/tailscale_mips_Linux
4d61c5327bbee394d4b015020a2fa2367920266fa7f5186873df04a95c0e5df7  ./tailscale/tailscale_mips_Linux.upx
f6712bddf591ffb331753a7d3c7dd898b02e3ba619c3ecba5c038973ae52bf50  ./tailscale/tailscale_mipsle_Linux
cc3982d15bb9b44276af7e38e41f9bcfb14f46d628646fbf6314d0cdca0ad5eb  ./tailscale/tailscale_mipsle_Linux.upx
432edfc2f684c1a35660cf85b25a331e0d79bfae14d6ab2f0111d4e1511a728b  ./tailscale/tailscale_powerpc64_ppc64_Linux
64ed52e184a02999acbb8eb59afacdfb389195860fe6ac060fce043f91d2128f  ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
ff2773a701faba6d53d8ea47cdd92953874faf59afd9949e0a679d3f5d2789db  ./tailscale/tailscale_powerpc64le_ppc64le_Linux
aeb9b7d4db3ce77cf81b89e791e74c2bd5ce7ccea9f142d268db43e315330408  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
61f48a825de9ba85907990024cd53cc2d40a019d15d6c5a340d613b33e4f3741  ./tailscale/tailscale_riscv64_Linux
8903c02d05d70348497392ddc8d971047a531bcb62838d2ed9414a21c90c432f  ./tailscale/tailscale_s390x_Linux
64a8ad28cbb67a6171236abe39f75a039a761a0e1aacdef75b26781887cef9a8  ./tailscale/tailscale_setup_Windows.exe
bdc4769b777bb89d47ec707403cbfae2c0289123ca3c4bf15336d94dd4694b8b  ./tailscale/tailscale_x86_Windows.msi
c8c80d2f0919eb48b0a86a9f1ddd2289d07ded51a886066db8059cd6461e5aa3  ./tailscale/tailscaled_aarch64_arm64_Linux
7f03d19e60ff27f9d34521403926228cf5e4b9db44ecdfb3dc01e475feddfe5e  ./tailscale/tailscaled_aarch64_arm64_Linux.upx
3045786fe6191b3d64ae9d2b03b5fffcf080e3cb3073a3c2e8e69e57ea05e2cf  ./tailscale/tailscaled_aarch64_arm64_macOS
543c6393750cc523e50a2e85dd63b5501b84e8c723b0a3ba03107347006dd669  ./tailscale/tailscaled_amd_geode_Linux
86a64e24c62fd1ff3b6b4da9244e240a148053f3c35c2532459d0df829cb2694  ./tailscale/tailscaled_amd_geode_Linux.upx
c3a3e692ee3afd19333b136b9a02f9eece157f194032b749c47da8fae073637b  ./tailscale/tailscaled_amd_x86_64_Linux
6f54e5b0c81d3e4ef9008a49e88fe223910c8d023e797a8411a0e71c1ee4260d  ./tailscale/tailscaled_amd_x86_64_Linux.upx
b5304b43985998d94d5c2c94e0eeb9e160a76906fa0ecb224af45c3b878e684d  ./tailscale/tailscaled_amd_x86_64_macOS
3ca1fef6454005930e45d8ab236b1ff8f9783c34cc97f55cc78296612d1e2d51  ./tailscale/tailscaled_arm_abi_Linux
e3dd5561a6186556e25fa0952626d5eb8086a94739eec47d6f2bf5a505e5b98a  ./tailscale/tailscaled_arm_abi_Linux.upx
a78dd0c362962e5676445a82d53d80f71bc62db82fd240ba208cee7e5a94a71f  ./tailscale/tailscaled_i386_Linux
f17a1a9f83049e37f7c3cfd25fa8f2a09242633699a3f93d6d9e097542d85fe2  ./tailscale/tailscaled_i386_Linux.upx
5a9721b0d99993cfa94b5a1b19f7f7d36327eaf5df3abf8254137431a6a923e6  ./tailscale/tailscaled_mips64_Linux
a792fde40e0fb5e78ecd2b2853f062f05c05040a29902d8014fb52115b7f3fe7  ./tailscale/tailscaled_mips64le_Linux
c9da2d0eb5b6eb1668386f688ac809e8c73cc9b50737843ea320ddacd3589120  ./tailscale/tailscaled_mips_Linux
53391eed774a8f648e1754825eb353176dc36efb208ccd028c7552ce7bf31c55  ./tailscale/tailscaled_mips_Linux.upx
7cf9efeb16fb09c0696c468a64e4d83000308674abaae6c93ebb3700af1a4fa3  ./tailscale/tailscaled_mipsle_Linux
b74fa8fc926dfaf4b5ef21f5a9b807c503f0d2f5782b6ecd104d4b9682d728fe  ./tailscale/tailscaled_mipsle_Linux.upx
5cd5ae4540c4ea4bc8996e33cd5c6a8f644eedbd09a6d4550e2c6e5403f71f38  ./tailscale/tailscaled_powerpc64_ppc64_Linux
c001dfe6b0d0bed0eef3ec7d19452a8d6c408e33a80022c92c1da0d77fca32ea  ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
3e90e74146147d22492afe5b19feec7ad8d1d651a90ab942f6e3d7f9a4b889ea  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux
4cf4ceb8f9ce187a746ff5c0c2cb649da386d472bbec4e9ce3fdaf197236f538  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
c0068967f7b198f6ec95b6e098ab3be7ad7af5abf2aed3d17093f303eecf2118  ./tailscale/tailscaled_riscv64_Linux
1e115860001f20ba180637332250d1e6f4c8e0389a31f0b0408880670a363ddc  ./tailscale/tailscaled_s390x_Linux
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
6.0M  ./tailscale/tailscale_i386_Linux.upx
70K   ./tailscale/tailscale_ipn_setup_Windows.exe
35M   ./tailscale/tailscale_merged_aarch64_arm64_Linux
8.2M  ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
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
25M   ./tailscale/tailscaled_amd_geode_Linux
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
  27263100 ->   6801096   24.95%  linux/ppc64le  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscaled_arm_abi_Linux.upx [OK]
  37911096 ->  15941116   42.05%    linux/arm    ./tailscale/tailscaled_arm_abi_Linux.upx
testing ./tailscale/tailscale_mips_Linux.upx [OK]
  34926585 ->  13139864   37.62%   linux/mips    ./tailscale/tailscale_mips_Linux.upx
testing ./tailscale/tailscale_merged_amd_x86_64_Linux.upx [OK]
  39161980 ->  10490840   26.79%   linux/amd64   ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx [OK]
  36307068 ->   8597360   23.68%   linux/arm64   ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
testing ./tailscale/tailscaled_amd_x86_64_Linux.upx [OK]
  30192664 ->   8537592   28.28%   linux/amd64   ./tailscale/tailscaled_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_mipsle_Linux.upx [OK]
  34917513 ->  13263172   37.98%  linux/mipsel   ./tailscale/tailscale_mipsle_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx [OK]
  38273148 ->   8845884   23.11%  linux/ppc64le  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_merged_i386_Linux.upx [OK]
  36733052 ->   9820008   26.73%   linux/i386    ./tailscale/tailscale_merged_i386_Linux.upx
testing ./tailscale/tailscaled_amd_geode_Linux.upx [OK]
  26203596 ->   7581104   28.93%   linux/i386    ./tailscale/tailscaled_amd_geode_Linux.upx
testing ./tailscale/tailscale_amd_geode_Linux.upx [OK]
  22340716 ->   6303936   28.22%   linux/i386    ./tailscale/tailscale_amd_geode_Linux.upx
testing ./tailscale/tailscale_merged_arm_Linux.upx [OK]
  36765820 ->   8429656   22.93%    linux/arm    ./tailscale/tailscale_merged_arm_Linux.upx
testing ./tailscale/tailscaled_mips_Linux.upx [OK]
  41553358 ->  15937732   38.35%   linux/mips    ./tailscale/tailscaled_mips_Linux.upx
testing ./tailscale/tailscale_powerpc64_ppc64_Linux.upx [OK]
  23068796 ->   5407480   23.44%   linux/ppc64   ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscaled_mipsle_Linux.upx [OK]
  41548698 ->  16080204   38.70%  linux/mipsel   ./tailscale/tailscaled_mipsle_Linux.upx
testing ./tailscale/tailscaled_i386_Linux.upx [OK]
  26166732 ->   7572716   28.94%   linux/i386    ./tailscale/tailscaled_i386_Linux.upx
testing ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx [OK]
  27263100 ->   6558636   24.06%   linux/ppc64   ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx [OK]
  38273148 ->   8538204   22.31%   linux/ppc64   ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_aarch64_arm64_Linux.upx [OK]
  31910274 ->  13432616   42.09%   linux/arm64   ./tailscale/tailscale_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_arm_abi_Linux.upx [OK]
  32009494 ->  13203496   41.25%    linux/arm    ./tailscale/tailscale_arm_abi_Linux.upx
testing ./tailscale/tailscale_i386_Linux.upx [OK]
  22283372 ->   6290704   28.23%   linux/i386    ./tailscale/tailscale_i386_Linux.upx
testing ./tailscale/tailscale_amd_x86_64_Linux.upx [OK]
  23735416 ->   6697824   28.22%   linux/amd64   ./tailscale/tailscale_amd_x86_64_Linux.upx
testing ./tailscale/tailscaled_aarch64_arm64_Linux.upx [OK]
  40906750 ->  17363060   42.45%   linux/arm64   ./tailscale/tailscaled_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx [OK]
  23068796 ->   5616312   24.35%  linux/ppc64le  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx

```

---

- #### Version
```console
$ ./tailscale/tailscale_amd_x86_64_Linux --version
1.104.4
  tailscale commit: 9382131983ca16de1357091618fd903e35db3c4e
  long version: 1.104.4-t938213198-gd38c96d6a
  other commit: d38c96d6afce903d0a81e5f3e32d7048bc33b660
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
1.104.4
  tailscale commit: 9382131983ca16de1357091618fd903e35db3c4e
  long version: 1.104.4-t938213198-gd38c96d6a
  other commit: d38c96d6afce903d0a81e5f3e32d7048bc33b660
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


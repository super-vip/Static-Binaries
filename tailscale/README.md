
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
./tailscale/tailscale_aarch64_arm64_Linux:                   ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=Dpb4AOaUd2VzX4FpN16k/se6izReaRODxXU7sqWQI/F34stbjLSKfXTzcSdcU7/Eoug1t4Lft2-F5vBRVfC, BuildID[sha1]=a76f2caf33374ec318a856a5361fa66d583f5f92, with debug_info, not stripped
./tailscale/tailscale_aarch64_arm64_Linux.upx:               ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=Dpb4AOaUd2VzX4FpN16k/se6izReaRODxXU7sqWQI/F34stbjLSKfXTzcSdcU7/Eoug1t4Lft2-F5vBRVfC, statically linked, no section header
./tailscale/tailscale_aarch64_arm64_Windows.msi:             Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Arm64;1033, Revision Number: {B749FFE0-EAC5-4062-836F-BF6CE6699C97}, Create Time/Date: Tue Oct 20 18:56:34 2026, Last Saved Time/Date: Tue Oct 20 18:56:34 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscale_aarch64_arm64_macOS:                   Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_amd_geode_Linux:                       ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=rXKeGqc4Uk4pjUvVqZu4/uDXQD9iMnmG1goNVYkrn/4XVs06namyG2F2bbRNtE/PSTw0aWFfMe9NIG9iVWH, BuildID[sha1]=9773bc0370a1a1899a3b76a1cb4cba8e7cfc4f0d, stripped
./tailscale/tailscale_amd_geode_Linux.upx:                   ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=rXKeGqc4Uk4pjUvVqZu4/uDXQD9iMnmG1goNVYkrn/4XVs06namyG2F2bbRNtE/PSTw0aWFfMe9NIG9iVWH, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Linux:                      ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=IO7-kvlSw-oPTQUMVkfQ/WngZWds8x480wsw_4LKh/_PT9Rgm2u9j2w7piIdIC/eloJOwCWenUCwmKsT_1C, BuildID[sha1]=380f55c5289094b76f1a70ac07a06e6b41635bb1, stripped
./tailscale/tailscale_amd_x86_64_Linux.upx:                  ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=IO7-kvlSw-oPTQUMVkfQ/WngZWds8x480wsw_4LKh/_PT9Rgm2u9j2w7piIdIC/eloJOwCWenUCwmKsT_1C, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Windows.msi:                Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: x64;1033, Revision Number: {DCCEAC9C-9E05-479C-9946-2F63A7BF4DE3}, Create Time/Date: Tue Oct 20 18:56:34 2026, Last Saved Time/Date: Tue Oct 20 18:56:34 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscale_amd_x86_64_macOS:                      Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_arm_abi_Linux:                         ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=JKD9EeRruWlf1JChggbf/-VuYRsD_PdXCMV2SOkYN/UWOp_GbWEkXYBmkOUQdP/wiTnjfKpfFMkyqnyIy2d, BuildID[sha1]=78a73907ffddcf7526bf33f1f819ec9dd80c815c, with debug_info, not stripped
./tailscale/tailscale_arm_abi_Linux.upx:                     ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=JKD9EeRruWlf1JChggbf/-VuYRsD_PdXCMV2SOkYN/UWOp_GbWEkXYBmkOUQdP/wiTnjfKpfFMkyqnyIy2d, statically linked, no section header
./tailscale/tailscale_i386_Linux:                            ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=V9GqFEal6f_b2mUn-qMN/KgS0PBJ9RnegrjZwesaF/0IwA_dCZYG3X80jXJCdj/gP1Z1cu590iwDg-yRASI, BuildID[sha1]=8066f625882070ae451679a6ea71e2e4c7675815, stripped
./tailscale/tailscale_i386_Linux.upx:                        ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=V9GqFEal6f_b2mUn-qMN/KgS0PBJ9RnegrjZwesaF/0IwA_dCZYG3X80jXJCdj/gP1Z1cu590iwDg-yRASI, statically linked, no section header
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
./tailscale/tailscale_mips64_Linux:                          ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=hSZYNdHOh8RtrNoiCovf/r4_Vsrm6tdx7ZNv2WYlC/NkWJj_vHdUY_rXSj-A2K/VzwyYt7vVl8RuZY4-Mxx, BuildID[sha1]=2e2a303f875c1d380af6141741b374c491d1d15d, with debug_info, not stripped
./tailscale/tailscale_mips64le_Linux:                        ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=k8YGvK6YGbChZDUdIuyq/902aE8L10BQKYZ38epZH/8JPJX4CojqSQKsQD4ccU/UJTOOsD5A1ojc6ovScYY, BuildID[sha1]=6a0ab03ae6ae62ce95f3754e203b2931f3964d76, with debug_info, not stripped
./tailscale/tailscale_mips_Linux:                            ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=mQQ2ip_-4Ub1xwMcZTvJ/lol1jnitqHy7fpDUAryc/dyy4Q2rrzXKPjxnrDllG/ppW64sAEvcU1AYjN1TG6, BuildID[sha1]=df82b14e9baeb2fcfb51066b272d663ee9ce7143, with debug_info, not stripped
./tailscale/tailscale_mips_Linux.upx:                        ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=mQQ2ip_-4Ub1xwMcZTvJ/lol1jnitqHy7fpDUAryc/dyy4Q2rrzXKPjxnrDllG/ppW64sAEvcU1AYjN1TG6, statically linked, no section header
./tailscale/tailscale_mipsle_Linux:                          ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=p2Mwa2ItmSLJVt6xgONX/y8NpaqoIPkqmQ9Rjt2xw/6yranbXN2_u3IjKDAHoj/II61FBGXkBLLUKgrNqPj, BuildID[sha1]=e6f578dc5405f3647a559fed941259bcfa3e6eda, with debug_info, not stripped
./tailscale/tailscale_mipsle_Linux.upx:                      ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=p2Mwa2ItmSLJVt6xgONX/y8NpaqoIPkqmQ9Rjt2xw/6yranbXN2_u3IjKDAHoj/II61FBGXkBLLUKgrNqPj, statically linked, no section header
./tailscale/tailscale_powerpc64_ppc64_Linux:                 ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64le_ppc64le_Linux:             ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx:         ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_riscv64_Linux:                         ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, Go BuildID=_4uItYQZjtK1rWmHShs1/gyDQFAYcZY0RKZoun9FN/doo_51IuNPfU1EUcMsfO/Xo0c6UGW_pKTWrLpxevG, BuildID[sha1]=945dc4fd3e7c781482348f3b4712ea837e95f588, with debug_info, not stripped
./tailscale/tailscale_s390x_Linux:                           ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_setup_Windows.exe:                     PE32 executable (GUI) Intel 80386, for MS Windows, 6 sections
./tailscale/tailscale_x86_Windows.msi:                       Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Intel;1033, Revision Number: {4F60099C-9052-4ECF-BB8A-E49F300C9CDC}, Create Time/Date: Tue Oct 20 18:56:34 2026, Last Saved Time/Date: Tue Oct 20 18:56:34 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscaled_aarch64_arm64_Linux:                  ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=eDOdybkrSU3YsFW2Toz6/CoqirWVq-GkU862v7vsi/kfzihR1Hlf7dtnD9p1Xo/ICmxtfNp3AkhiEHzHoB5, BuildID[sha1]=623838ab68caecff76d6fb0153bffc64720b0a2c, with debug_info, not stripped
./tailscale/tailscaled_aarch64_arm64_Linux.upx:              ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=eDOdybkrSU3YsFW2Toz6/CoqirWVq-GkU862v7vsi/kfzihR1Hlf7dtnD9p1Xo/ICmxtfNp3AkhiEHzHoB5, statically linked, no section header
./tailscale/tailscaled_aarch64_arm64_macOS:                  Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_amd_geode_Linux:                      ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=KFFoObMDcMCuQrUViWDA/FhFUnLUaeGQ1Cey_pwgT/u5DI2t0yBG8ukkoT972r/_ob5SHj-k13r0WXRLD0Z, BuildID[sha1]=5a164bc03fa349bbc5f48a7908615000e208ca60, stripped
./tailscale/tailscaled_amd_geode_Linux.upx:                  ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=KFFoObMDcMCuQrUViWDA/FhFUnLUaeGQ1Cey_pwgT/u5DI2t0yBG8ukkoT972r/_ob5SHj-k13r0WXRLD0Z, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_Linux:                     ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=woKnTB6520Fw2y20aEJu/M4wzwc1DhylvQXNsEKuk/EMJZL3YPsAJzPWK64TgJ/pSis9ZHrfSstsoOICNvl, BuildID[sha1]=807ad29cb4c5792d743da3e880cfb50e38507c87, stripped
./tailscale/tailscaled_amd_x86_64_Linux.upx:                 ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=woKnTB6520Fw2y20aEJu/M4wzwc1DhylvQXNsEKuk/EMJZL3YPsAJzPWK64TgJ/pSis9ZHrfSstsoOICNvl, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_macOS:                     Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_arm_abi_Linux:                        ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=HIZKxjEC9w1eoAJA8KmN/Ci08zUKZD1SL9FujqctJ/A99FEDdtzcwrkZ6vX5G5/jx2Yzvf9nbTZq58Jvw6j, BuildID[sha1]=d69d0f64dfb18105225f05422e0a024b94d7dda5, with debug_info, not stripped
./tailscale/tailscaled_arm_abi_Linux.upx:                    ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=HIZKxjEC9w1eoAJA8KmN/Ci08zUKZD1SL9FujqctJ/A99FEDdtzcwrkZ6vX5G5/jx2Yzvf9nbTZq58Jvw6j, statically linked, no section header
./tailscale/tailscaled_i386_Linux:                           ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=IfxT1nhPZEgwc7oO6M94/BJUdUWSTp5oFo64yUKvJ/ib2GYMcBITAlRAojoCIj/oki5Je_-ItYZYGkRNEAX, BuildID[sha1]=11896feaa13ffcf8eae5571719c47b7f2651da9e, stripped
./tailscale/tailscaled_i386_Linux.upx:                       ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=IfxT1nhPZEgwc7oO6M94/BJUdUWSTp5oFo64yUKvJ/ib2GYMcBITAlRAojoCIj/oki5Je_-ItYZYGkRNEAX, statically linked, no section header
./tailscale/tailscaled_mips64_Linux:                         ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=x0uAyKsYPZuX8HG2w9ti/BiC_EpCLrcfhTXFfrR4W/aLoPDX6bI1kqlvpOdyzA/F9sUwU3X-ECgnN_UbUk9, BuildID[sha1]=c1e30f74e3eb1e81d0508f1383018a604bcbe9d3, with debug_info, not stripped
./tailscale/tailscaled_mips64le_Linux:                       ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=QhPHA8KqGJc5Nrx6szZU/u8vuiPw1Fh1zUMe8Ee_T/FrUGMkddfSwkEeuzaXec/Yuzp3egxa6AHe_ikQkAy, BuildID[sha1]=83da399d0bce93bf25f0f6a1b9f4e38629bcf4ec, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux:                           ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=ZaMxQy3yA8i2vV57oMRR/dHksigNaYh5a_VrEBA1A/AvT0XeUGarvxdPMsXSw0/9u2DrPaCHPZ0SA8tXIdR, BuildID[sha1]=94cff8f23b247993fd6121414fb8013b9814ad15, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux.upx:                       ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=ZaMxQy3yA8i2vV57oMRR/dHksigNaYh5a_VrEBA1A/AvT0XeUGarvxdPMsXSw0/9u2DrPaCHPZ0SA8tXIdR, statically linked, no section header
./tailscale/tailscaled_mipsle_Linux:                         ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=MZDaJXAKnUKoRC7469h9/l6sSFoemcpA7v-J3-7BB/CnkCGB7W0mpmxbjudA9W/OktH0CE37MrMepNECWNs, BuildID[sha1]=c03c01eb926049eeb1b16b9dc2afda6d73a8644f, with debug_info, not stripped
./tailscale/tailscaled_mipsle_Linux.upx:                     ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=MZDaJXAKnUKoRC7469h9/l6sSFoemcpA7v-J3-7BB/CnkCGB7W0mpmxbjudA9W/OktH0CE37MrMepNECWNs, statically linked, no section header
./tailscale/tailscaled_powerpc64_ppc64_Linux:                ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64_ppc64_Linux.upx:            ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_powerpc64le_ppc64le_Linux:            ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx:        ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_riscv64_Linux:                        ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, Go BuildID=4Rqfccs4u_VVNwmltwj_/tFjeaZimUySuWtilgaIZ/NPhV4FTBbKRx5Igs1fcD/m6ztU9TfMlfxi3zzKtW1, BuildID[sha1]=b54d53adca086be4e54904100c09d72c0b84caf8, with debug_info, not stripped
./tailscale/tailscaled_s390x_Linux:                          ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped

--> SHA256SUM
f56aaf3f64e2e9843b55dd4760bb097c62df01b255dae79b4d2680b387dae464  ./tailscale/tailscale_aarch64_arm64_Linux
341b07e2940e79259b83a549f6c993aad6e1bd15228e02e552091e87c35a0c07  ./tailscale/tailscale_aarch64_arm64_Linux.upx
457d31e4dceb2d3f0510588342d071c81647627e6ba9985c9d47bcf8fa3e9148  ./tailscale/tailscale_aarch64_arm64_Windows.msi
758bd296723a348a70f5274b294baeb4053abd2e2ce58e2220e210946b618c6f  ./tailscale/tailscale_aarch64_arm64_macOS
a395f687bbe50e5e882dabf172a0d816c77708520646479d8c583f24e13b55ed  ./tailscale/tailscale_amd_geode_Linux
0d24b49969af3a121a4c8da2be08edb403e7a2575c1cfc3939602037a39e0ded  ./tailscale/tailscale_amd_geode_Linux.upx
e75f788c9ad9a3f278cd073f3330173837f597d96f127c1719edfe9e66462c25  ./tailscale/tailscale_amd_x86_64_Linux
362df14c3635b3af10138639fa1f0f5947ddfdde1bf51f300d04a378b4273130  ./tailscale/tailscale_amd_x86_64_Linux.upx
7eff4abdcbcf592ac9bce28f2b9f0fd51f8fc09194c955fbe8253b67b531e7f5  ./tailscale/tailscale_amd_x86_64_Windows.msi
248b7930c0c4c650f988bcb90a968da042066e0b826bf58efd8fe3a69fad8e7f  ./tailscale/tailscale_amd_x86_64_macOS
55204bc4e8d86d9de829f6a19b8541810bbf78bea3480ed1b168120bc91b8a56  ./tailscale/tailscale_arm_abi_Linux
de428204221e64ee439f02bd0a186fc89d52a1cae5db1a4448e276d32fd07a40  ./tailscale/tailscale_arm_abi_Linux.upx
a4c1d263dd8bff397f4cd363cdb68081dcbb48c980037623648dba286f2b2b38  ./tailscale/tailscale_i386_Linux
9964634f118177019f152623e5e293fafb78de1c211f071fdd1f66869cabd96b  ./tailscale/tailscale_i386_Linux.upx
59c983331e1930a9425ac8a0f6dc94621e5f45adf38853a50a003de5ba933c4a  ./tailscale/tailscale_ipn_setup_Windows.exe
c4ff35fe79074f44dc5a7f97cb4ed8ffda0c784de59c965e67cb58259820c457  ./tailscale/tailscale_merged_aarch64_arm64_Linux
766ffaf1febfa7e2981112853be094ea1cb1cbf25ab60f841a3d9491943f5417  ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
68728bde1313493eb44dbd3be2e989eb00f60f4938d0d2845df9d45e32c25df7  ./tailscale/tailscale_merged_aarch64_arm64_macOS
b55126ac82f2ef3d6fbf3d936248ba1dcdb261d4e88df55b29550811d5f07428  ./tailscale/tailscale_merged_amd_x86_64_Linux
58a305de871d43343ce90c579448dbd38a0af7b572e9550eab03d25e74783eea  ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
267bebcfe539dd8353add30caf55a042bf996f8e688aae7910b9ecf61714f3f8  ./tailscale/tailscale_merged_amd_x86_64_macOS
28e3f27373cd0265eadaf90e67c099bae9c5aaf75a03c1ccb0c8ea173cea405f  ./tailscale/tailscale_merged_arm_Linux
c4b39951116c9de5f787ef38b2631795a2c818ecc973e630517d208cdecaa05d  ./tailscale/tailscale_merged_arm_Linux.upx
5069bc702aee95f95a9619856e6b5da817aa0e331e05d7ef66a5b894db68ca05  ./tailscale/tailscale_merged_i386_Linux
63bdf568760cbf30cee5e39381b95bb98775ad75c2fd1b6e9a9b2b5ebcf859c6  ./tailscale/tailscale_merged_i386_Linux.upx
19baa3bd6744baebe8e0710d8f4c3e2d1c061aa9d1b3f74b5851431b2320b65d  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux
0afeab682d026171b38459b0d2183829406050f41d5181a5701ed5461df31c02  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
c54110f1e49f27e6d71c1ba86eedd151e3b8dbeafbe299f5617c52cb084c106a  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux
3ab9346ace93a29f32c9adfab6253f21906d1c8a2a4f024e7d889ac00e873505  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
9ea1968b78284ed06150e5de977a95176bbdd57848680a4e8eec68ac5f443b86  ./tailscale/tailscale_merged_s390x_Linux
fbb976808e4e1aeb00e59f7a2cf45ccbca3e65aaaecbac09cc2c3c48d10ee4f2  ./tailscale/tailscale_mips64_Linux
aaf5247d833df23d7be2e62888986d17ce9ad3440f7591df0abaeb14000f9f77  ./tailscale/tailscale_mips64le_Linux
4eeabcbeef1fde15a67721ba74deff3059b1054cdfe762ac7e021392a773e0b0  ./tailscale/tailscale_mips_Linux
4c5ca57464f4dedfceb4167d2eff9314d1588e75033c31a44e64d901843b7592  ./tailscale/tailscale_mips_Linux.upx
c0818517847217640e3d9ba634c4c5b5f8a192c13e1466d5dc607cfa8c290625  ./tailscale/tailscale_mipsle_Linux
55b0e8e63834cb792ced22a407a33b23eb6e9419811aabb6f8694f8c67f06e19  ./tailscale/tailscale_mipsle_Linux.upx
9608ae1b00746295e22512eaaee81ae79f3a8ae310b4cc46b2ac9f0ac0cb7c04  ./tailscale/tailscale_powerpc64_ppc64_Linux
fe186e153859c038d71c7b9efcaba698c2e8665719fbad0c5814d5aeab9e9d66  ./tailscale/tailscale_powerpc64le_ppc64le_Linux
32bf0f82b233869b8197f99e42a34b0e0dd019a33a5e59c8afacce635b7a4fa4  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
4aeb34f0d74557d8e07e0580da86aff88533c9a77a6da57f1086e9c7dca211d7  ./tailscale/tailscale_riscv64_Linux
23461b121d232214f6c947c24757fd78a283a9563cdede709150f37450d017dd  ./tailscale/tailscale_s390x_Linux
64a8ad28cbb67a6171236abe39f75a039a761a0e1aacdef75b26781887cef9a8  ./tailscale/tailscale_setup_Windows.exe
a48dc6bdf6cddbd1df23371bd549eede510cf601f278287681fd1d0475b1cde4  ./tailscale/tailscale_x86_Windows.msi
3978859251e2f996d0c8dd44a5966c51876c15221eb6970fd6b4239f2457544b  ./tailscale/tailscaled_aarch64_arm64_Linux
f7588de80d7e0b3816927967d9ee081ff51c32f28a2ef17eeac4919aa1158532  ./tailscale/tailscaled_aarch64_arm64_Linux.upx
3045786fe6191b3d64ae9d2b03b5fffcf080e3cb3073a3c2e8e69e57ea05e2cf  ./tailscale/tailscaled_aarch64_arm64_macOS
311e5e4ccaadfc726fbaf2ca7e3ad09fa2aa3088c14f5a77de5a0e87d84d9823  ./tailscale/tailscaled_amd_geode_Linux
3a37fc852c49830e9801583776863f92083c9085880952c1a30745b72fc74e74  ./tailscale/tailscaled_amd_geode_Linux.upx
d9143e4c528e313934257a7d613a4f8de03750d9143c5d63882bb1bf2a8a06a1  ./tailscale/tailscaled_amd_x86_64_Linux
1af369906c2a7165f841b2cf83efc1c3d988b087c01bd914ad7e5f9f92a01b51  ./tailscale/tailscaled_amd_x86_64_Linux.upx
b5304b43985998d94d5c2c94e0eeb9e160a76906fa0ecb224af45c3b878e684d  ./tailscale/tailscaled_amd_x86_64_macOS
9404866023e64385091fe5e9faebe88f9051f035b26785b656c410f174e5eb25  ./tailscale/tailscaled_arm_abi_Linux
7cc7ccb6e99c4b185e210e3b95f136a36c8c748c7940fc925ffd315a084c5a40  ./tailscale/tailscaled_arm_abi_Linux.upx
70b4335d198c97f3205db3b0740e44c54fe58893e884fa81f3bddf5ccf59ab45  ./tailscale/tailscaled_i386_Linux
38794ffb357ec8cdfef66166174cfacf465f9c75ec647c27d63ab701f90c2593  ./tailscale/tailscaled_i386_Linux.upx
24c28ff6fe79d210685e72d77efb485a27cef14cf185c17fb5f41b7f16db54bd  ./tailscale/tailscaled_mips64_Linux
7fd6f7d4e96c51ae83db2d2b07326682a1d06c4cb426dca6c6c0311bb873e59a  ./tailscale/tailscaled_mips64le_Linux
65d5e0ed81fd4e9fba82c42f5295bcb2ad60f5f7cb12892da26336cc18cbd348  ./tailscale/tailscaled_mips_Linux
83e9692e9c04d7769e14098b17700ee643fba358776669f607eb40bf0bc25ccd  ./tailscale/tailscaled_mips_Linux.upx
08ffe7cffa659b5a573e379dfbd53549c30fdb79378fab3f68ba92a2f73d2a09  ./tailscale/tailscaled_mipsle_Linux
f48b930f7f1f886e16d2651e3d40e2d6932b51564e4f9fc4724921d012597b85  ./tailscale/tailscaled_mipsle_Linux.upx
6e716bd3096be1ec0c306b3752149c2e2d4dc2d9a8347a71d40eb1810726bb11  ./tailscale/tailscaled_powerpc64_ppc64_Linux
4bb9668508d2cbe179ff13b603769eadbc056348a241e50bc9285b01c9c20acc  ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
c89acb6160544068150d7431c74d89f9fe089bebbfb27f39988099b78378c71b  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux
5db838c5a296096993ad6754e9e23f9fe51c3e94b65a1d8e40d362216c2b75a7  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
e2813805a607d1dedd8759fe7e84e7a6ab2c476e81ccd31a6bc9cf3f2439640b  ./tailscale/tailscaled_riscv64_Linux
f8e416f6366b80c82d2ff091ea4d5c74854ca61695acdb4dcd0eea2303b4c00a  ./tailscale/tailscaled_s390x_Linux
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
10M   ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
20M   ./tailscale/tailscale_merged_amd_x86_64_macOS
35M   ./tailscale/tailscale_merged_arm_Linux
8.0M  ./tailscale/tailscale_merged_arm_Linux.upx
35M   ./tailscale/tailscale_merged_i386_Linux
9.4M  ./tailscale/tailscale_merged_i386_Linux.upx
37M   ./tailscale/tailscale_merged_powerpc64_ppc64_Linux
8.1M  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
37M   ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux
8.4M  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
38M   ./tailscale/tailscale_merged_s390x_Linux
35M   ./tailscale/tailscale_mips64_Linux
35M   ./tailscale/tailscale_mips64le_Linux
34M   ./tailscale/tailscale_mips_Linux
13M   ./tailscale/tailscale_mips_Linux.upx
34M   ./tailscale/tailscale_mipsle_Linux
13M   ./tailscale/tailscale_mipsle_Linux.upx
23M   ./tailscale/tailscale_powerpc64_ppc64_Linux
23M   ./tailscale/tailscale_powerpc64le_ppc64le_Linux
5.4M  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
30M   ./tailscale/tailscale_riscv64_Linux
24M   ./tailscale/tailscale_s390x_Linux
51M   ./tailscale/tailscale_setup_Windows.exe
37M   ./tailscale/tailscale_x86_Windows.msi
39M   ./tailscale/tailscaled_aarch64_arm64_Linux
17M   ./tailscale/tailscaled_aarch64_arm64_Linux.upx
19M   ./tailscale/tailscaled_aarch64_arm64_macOS
25M   ./tailscale/tailscaled_amd_geode_Linux
7.2M  ./tailscale/tailscaled_amd_geode_Linux.upx
29M   ./tailscale/tailscaled_amd_x86_64_Linux
8.1M  ./tailscale/tailscaled_amd_x86_64_Linux.upx
19M   ./tailscale/tailscaled_amd_x86_64_macOS
36M   ./tailscale/tailscaled_arm_abi_Linux
16M   ./tailscale/tailscaled_arm_abi_Linux.upx
25M   ./tailscale/tailscaled_i386_Linux
7.2M  ./tailscale/tailscaled_i386_Linux.upx
41M   ./tailscale/tailscaled_mips64_Linux
41M   ./tailscale/tailscaled_mips64le_Linux
40M   ./tailscale/tailscaled_mips_Linux
16M   ./tailscale/tailscaled_mips_Linux.upx
40M   ./tailscale/tailscaled_mipsle_Linux
16M   ./tailscale/tailscaled_mipsle_Linux.upx
26M   ./tailscale/tailscaled_powerpc64_ppc64_Linux
6.2M  ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
26M   ./tailscale/tailscaled_powerpc64le_ppc64le_Linux
6.5M  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
36M   ./tailscale/tailscaled_riscv64_Linux
27M   ./tailscale/tailscaled_s390x_Linux
```

---

- #### UPX
```console

testing ./tailscale/tailscaled_arm_abi_Linux.upx [OK]
  37540801 ->  15790472   42.06%    linux/arm    ./tailscale/tailscaled_arm_abi_Linux.upx
testing ./tailscale/tailscale_mips_Linux.upx [OK]
  34926040 ->  13137736   37.62%   linux/mips    ./tailscale/tailscale_mips_Linux.upx
testing ./tailscale/tailscale_aarch64_arm64_Linux.upx [OK]
  31909581 ->  13431824   42.09%   linux/arm64   ./tailscale/tailscale_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_merged_arm_Linux.upx [OK]
  36569212 ->   8371964   22.89%    linux/arm    ./tailscale/tailscale_merged_arm_Linux.upx
testing ./tailscale/tailscale_amd_geode_Linux.upx [OK]
  22336620 ->   6302640   28.22%   linux/i386    ./tailscale/tailscale_amd_geode_Linux.upx
testing ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx [OK]
  27000956 ->   6493036   24.05%   linux/ppc64   ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx [OK]
  38011004 ->   8477512   22.30%   linux/ppc64   ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscaled_aarch64_arm64_Linux.upx [OK]
  40593913 ->  17208164   42.39%   linux/arm64   ./tailscale/tailscaled_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx [OK]
  23068796 ->   5616004   24.34%  linux/ppc64le  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx [OK]
  36044924 ->   8536416   23.68%   linux/arm64   ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx [OK]
  38011004 ->   8775964   23.09%  linux/ppc64le  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_merged_amd_x86_64_Linux.upx [OK]
  38879356 ->  10415936   26.79%   linux/amd64   ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
testing ./tailscale/tailscaled_i386_Linux.upx [OK]
  25907660 ->   7502056   28.96%   linux/i386    ./tailscale/tailscaled_i386_Linux.upx
testing ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx [OK]
  26935420 ->   6729124   24.98%  linux/ppc64le  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_amd_x86_64_Linux.upx [OK]
  23731352 ->   6696532   28.22%   linux/amd64   ./tailscale/tailscale_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_arm_abi_Linux.upx [OK]
  32009445 ->  13203696   41.25%    linux/arm    ./tailscale/tailscale_arm_abi_Linux.upx
testing ./tailscale/tailscaled_amd_geode_Linux.upx [OK]
  25944524 ->   7509732   28.95%   linux/i386    ./tailscale/tailscaled_amd_geode_Linux.upx
testing ./tailscale/tailscale_mipsle_Linux.upx [OK]
  34917028 ->  13262416   37.98%  linux/mipsel   ./tailscale/tailscale_mipsle_Linux.upx
testing ./tailscale/tailscale_merged_i386_Linux.upx [OK]
  36470908 ->   9752164   26.74%   linux/i386    ./tailscale/tailscale_merged_i386_Linux.upx
testing ./tailscale/tailscaled_mipsle_Linux.upx [OK]
  41173213 ->  15923540   38.67%  linux/mipsel   ./tailscale/tailscaled_mipsle_Linux.upx
testing ./tailscale/tailscaled_mips_Linux.upx [OK]
  41173949 ->  15777112   38.32%   linux/mips    ./tailscale/tailscaled_mips_Linux.upx
testing ./tailscale/tailscale_i386_Linux.upx [OK]
  22283372 ->   6290740   28.23%   linux/i386    ./tailscale/tailscale_i386_Linux.upx
testing ./tailscale/tailscaled_amd_x86_64_Linux.upx [OK]
  29908024 ->   8461604   28.29%   linux/amd64   ./tailscale/tailscaled_amd_x86_64_Linux.upx

```

---

- #### Version
```console
$ ./tailscale/tailscale_amd_x86_64_Linux --version
1.104.2
  tailscale commit: c3430f0d2b8a1d646ad3ae867e3470bac07f1fe0
  long version: 1.104.2-tc3430f0d2-g598b63867
  other commit: 598b63867959ac210c6a32b7961bb33eb57314db
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
1.104.2
  tailscale commit: c3430f0d2b8a1d646ad3ae867e3470bac07f1fe0
  long version: 1.104.2-tc3430f0d2-g598b63867
  other commit: 598b63867959ac210c6a32b7961bb33eb57314db
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


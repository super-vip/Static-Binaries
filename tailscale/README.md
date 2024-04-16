
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
./tailscale/tailscale_aarch64_arm64_Linux:                   ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=U5sGa2eTKrY2LJN098hv/lSiExxQkkASLsJXSOhAC/Hfz-Uft7sIdPJRChhxCE/CXY6_3VrUErYUyIGnJ0V, with debug_info, not stripped
./tailscale/tailscale_aarch64_arm64_Linux.upx:               ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_aarch64_arm64_Windows.msi:             Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard.WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Arm64;1033, Revision Number: {2E3BE344-0AD3-48F8-9D94-6C6AB71701B5}, Create Time/Date: Thu Apr 11 18:57:38 2024, Last Saved Time/Date: Thu Apr 11 18:57:38 2024, Number of Pages: 500, Number of Words: 2, Name of Creating Application: Windows Installer XML Toolset (), Security: 2
./tailscale/tailscale_aarch64_arm64_macOS:                   Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_amd_geode_Linux:                       ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=onJ5QmnUFstaYJ8vw64Y/FooL4U-5CGNV1Zm-ZNYM/Ob6fKcicITep2F6CF6AI/vq8w2SkUqSJMCNfmD0_B, stripped
./tailscale/tailscale_amd_geode_Linux.upx:                   ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), statically linked, no section header
./tailscale/tailscale_amd_x86_64_Linux:                      ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=2yGkD3h4voxr37bqVnX2/a8OqHhDZHNBLpKX0S89v/IxhCZ8MfPbsZEsOfkG-q/MmPd3LcVxlfBwgZ97dHY, stripped
./tailscale/tailscale_amd_x86_64_Linux.upx:                  ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_amd_x86_64_Windows.msi:                Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard.WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: x64;1033, Revision Number: {058C5598-2323-45E5-9F64-F601D21644AC}, Create Time/Date: Thu Apr 11 18:57:44 2024, Last Saved Time/Date: Thu Apr 11 18:57:44 2024, Number of Pages: 500, Number of Words: 2, Name of Creating Application: Windows Installer XML Toolset (), Security: 2
./tailscale/tailscale_amd_x86_64_macOS:                      Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_arm_abi_Linux:                         ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=_-adi9xfAMyhxp7h-ZBP/Rnc8PJPKMEpvFFWobXce/KeRTffnbMHo4JtQ3CUsp/kVEaUWSf4WTLV7nRF3p0, with debug_info, not stripped
./tailscale/tailscale_arm_abi_Linux.upx:                     ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), statically linked, no section header
./tailscale/tailscale_i386_Linux:                            ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=aY24BdTHKv2L4ZVIveHm/0zMUubvGZLGJe__eEvx7/yPWdrjwc1fSIheiL5Xef/CtUwXajn-3ZO7J-8WkNZ, stripped
./tailscale/tailscale_i386_Linux.upx:                        ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), statically linked, no section header
./tailscale/tailscale_ipn_setup_Windows.exe:                 PE32 executable (GUI) Intel 80386, for MS Windows, Nullsoft Installer self-extracting archive
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
./tailscale/tailscale_mips64_Linux:                          ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=W81e44Vq4m2j-MUGl36E/iWi1dfBuIzuaJ7clNVOj/pSJrigeY-eXqF9F74Fm3/50WRHI_KkkGNp0RGEoeQ, with debug_info, not stripped
./tailscale/tailscale_mips64le_Linux:                        ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=8CajNpK9Hm0IKjLsftDi/jGOZAy1cMXvmIA2fYQJQ/qyjEdTJPEdSePRYsQtWT/aL60BjVnhAO_dYF9ktjh, with debug_info, not stripped
./tailscale/tailscale_mips_Linux:                            ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=J9PnSW4rjmmn90OZz29t/buZ6KdBzjU_Vw5BVV_K3/waWAghQIpKlh-VItJyxQ/8BqVbitMKMd_NKEzTNnq, with debug_info, not stripped
./tailscale/tailscale_mips_Linux.upx:                        ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_mipsle_Linux:                          ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=nNHW5FGiZEU-XXn4IULz/EkoqDPMOMH88Dk9mfIvd/Qc86AT-qu56kT1gmCKFF/qcjec3-AgolAcRh-O3y-, with debug_info, not stripped
./tailscale/tailscale_mipsle_Linux.upx:                      ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_powerpc64_ppc64_Linux:                 ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64_ppc64_Linux.upx:             ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_powerpc64le_ppc64le_Linux:             ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx:         ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_riscv64_Linux:                         ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, Go BuildID=o5sRvI2FZRWIOV4wYVEX/J4fbm9BEmCGZk67-oku1/W5GGkfzhVYG8nqBesSJa/T1s-mRHKcKMp0k0wMZwV, with debug_info, not stripped
./tailscale/tailscale_s390x_Linux:                           ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_setup_Windows.exe:                     PE32 executable (GUI) Intel 80386, for MS Windows
./tailscale/tailscale_x86_Windows.msi:                       Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard.WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Intel;1033, Revision Number: {56D306D2-D620-41BC-969D-295894F91AD3}, Create Time/Date: Thu Apr 11 18:57:38 2024, Last Saved Time/Date: Thu Apr 11 18:57:38 2024, Number of Pages: 500, Number of Words: 2, Name of Creating Application: Windows Installer XML Toolset (), Security: 2
./tailscale/tailscaled_aarch64_arm64_Linux:                  ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=rQrLNJmmwNpIqc2BmX4D/DmxtP3VkV4vgUb2HNtQ9/8SVkTBt_Wk27e7jeGxJo/3aL5mcPld9dTGj6TqTtk, with debug_info, not stripped
./tailscale/tailscaled_aarch64_arm64_Linux.upx:              ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_aarch64_arm64_macOS:                  Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_amd_geode_Linux:                      ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=k34nxi8O3RGSRip0FOgg/W6XvmYssSlmqMS7m6d63/TdPyzwZS3Olnv5qZ_qLg/QHEqQ5nuwBSi_qZHPPzR, stripped
./tailscale/tailscaled_amd_geode_Linux.upx:                  ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), statically linked, no section header
./tailscale/tailscaled_amd_x86_64_Linux:                     ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=ybS4kymtLzwFhyo9WBJW/HVvbxD0_j7YUy5V1DpEg/bDSbk2Xqx72hZigQYueB/1HpvzkHRC_SgW_W8n-PH, stripped
./tailscale/tailscaled_amd_x86_64_Linux.upx:                 ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_amd_x86_64_macOS:                     Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_arm_abi_Linux:                        ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=E3FmR8Q79_SoVvtT_BBU/-im7DS-PtU39zTaz8O2V/ilkfSmTDO26id7fc2sfi/blDjmAFSc_BI5uMCHPvc, with debug_info, not stripped
./tailscale/tailscaled_arm_abi_Linux.upx:                    ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), statically linked, no section header
./tailscale/tailscaled_i386_Linux:                           ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=vP_Mk2UC69FC5zGdAZy_/5p_eZ6OvHHAPCHISQ0SJ/Orh9s9ERYeUt_4ZV48V1/LGU3iFGqnt0FM-_KHgsq, stripped
./tailscale/tailscaled_i386_Linux.upx:                       ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), statically linked, no section header
./tailscale/tailscaled_mips64_Linux:                         ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=PqWw8oemEcsMkrnaEw6m/LMP8PeaRBS5sKJ1YPnEd/ee-vkn5QID3FjW5otkQj/OLKJ__YYFEPq5VdzUSEM, with debug_info, not stripped
./tailscale/tailscaled_mips64le_Linux:                       ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=qXCFt9fasueOH2YW0mY7/cKRvph3phK0W8kzdE5UN/th61pJlG1o9agyUNjhDm/jRJERmRy39fFhsfBur8U, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux:                           ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=pYDs1ChKZLTmYhQBZDDX/BGfk1dqp5phRYy5XAxIV/hwSI1LKTUoRQusDZw2Ov/igfeMTLxHh295Lk4A4sg, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux.upx:                       ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_mipsle_Linux:                         ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=U-H-FJbvh9-6WFtQpIvi/RMT3s1Ms-Upcn8E1bC4L/vS0iQFEC64Tuq4LtogwB/k8GP8MiQaFrbUWCfmJfb, with debug_info, not stripped
./tailscale/tailscaled_mipsle_Linux.upx:                     ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_powerpc64_ppc64_Linux:                ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64_ppc64_Linux.upx:            ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_powerpc64le_ppc64le_Linux:            ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx:        ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_riscv64_Linux:                        ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, Go BuildID=CRj_MdeGoOp8suDcIG_W/qc1kqAMgse7kuGznSJbq/ytBaQpd_ZuyOL8Ky6q98/NJazpAxPliyjWCdnOOj8, with debug_info, not stripped
./tailscale/tailscaled_s390x_Linux:                          ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped

--> SHA256SUM
b11454fddf8f08ecf5501ca63cf7c4ba9daf92c9f61ffe6b4c0794110cd47b80  ./tailscale/tailscale_aarch64_arm64_Linux
57bc17da351454e98b64fabd2801c014b83a87e2a81f335518168267cd2a5279  ./tailscale/tailscale_aarch64_arm64_Linux.upx
2113a42904168ea49d49a5fec34fb0e84d043e3e7ed227fc4a842f62874fd544  ./tailscale/tailscale_aarch64_arm64_Windows.msi
8367e2f4dbbab5b62839492814a18b0fdf4ad2fd44e3ee2a5b2827240162831c  ./tailscale/tailscale_aarch64_arm64_macOS
57b820fb28c95171637914390ef89e40b04a901bc0d86643f827232994ea2b46  ./tailscale/tailscale_amd_geode_Linux
2277ef4bc90dc024daedfa8fa3b3ce27855609a989f335ad6093adc0119b24a1  ./tailscale/tailscale_amd_geode_Linux.upx
32e4fa633ec74b5aada9a4dea0f20a2061ddfa4e7e32f06663504b861330e4f9  ./tailscale/tailscale_amd_x86_64_Linux
a708024a018e747659cda34ca00d85f840c0394b2b0a25927a159195f47461f7  ./tailscale/tailscale_amd_x86_64_Linux.upx
46e61cd7037887f7049373545f07ba31dafaaf213299ae35fc8a5073332cfcc8  ./tailscale/tailscale_amd_x86_64_Windows.msi
c18f27df6257e05b209e6e3fdcaa5f0aa3eba89456e1ed713b1411bfd0cc2211  ./tailscale/tailscale_amd_x86_64_macOS
74690e29e88a6d400e7f2f609e64e61072f75b8a5841a0096de4b2d231195e7d  ./tailscale/tailscale_arm_abi_Linux
9f94595647a2820e37816485f1d8f7950cdb6a38225932353c4559889c7871ed  ./tailscale/tailscale_arm_abi_Linux.upx
9e29f420c0ffd7431183b1e9610e2312831482f202cc6a7355405b3fefaebffd  ./tailscale/tailscale_i386_Linux
18d37af9c07abc15e437188ebf77ab65337ea84915bc2c10ddb45946363ab501  ./tailscale/tailscale_i386_Linux.upx
25b2e47e9d973d385b542848ea54f66db204030a2f06497c53a0533d26f18d72  ./tailscale/tailscale_ipn_setup_Windows.exe
5f10b0a9f90c4bfc66b3901afb8318c236496b33715b1bd7a47bad8d6130f13f  ./tailscale/tailscale_merged_aarch64_arm64_Linux
ce9aac53b6197343997332a3739cf82f202ae18853233198cd8c3ac1ec0dd7d2  ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
ac1e895429b2fe0f9e87f1bfda6dbc713dedb7b395f55765d34cd4c3cfa95561  ./tailscale/tailscale_merged_aarch64_arm64_macOS
5e40da5a9e3e385fac443ab655a0674f063a3b6594c81d4671d6896964c9c6d0  ./tailscale/tailscale_merged_amd_x86_64_Linux
1f91f004e557aab9814763be03d5dbc10afc4daaaf709391232779285680e458  ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
7a9b38dfa6d331c1135a227e986fe5994bf9980d70b2a0c63d0006563d883e5f  ./tailscale/tailscale_merged_amd_x86_64_macOS
4b0891d267bfba613ab9ae2a70decbf4ef8609f673d0b19bf1ce597663963955  ./tailscale/tailscale_merged_arm_Linux
bb19b7873ac8e2b877936144d53b82ef1ecef0c5b3396ef4e9030ebfdb7add4e  ./tailscale/tailscale_merged_arm_Linux.upx
5b2c20e80f2263585108d998b15922bf72d3508dce615164fe437907e981b62f  ./tailscale/tailscale_merged_i386_Linux
59ae80c937d18dcb752f6c4b6e33aa5184f6e284befdcb9719f64256d1f78ff3  ./tailscale/tailscale_merged_i386_Linux.upx
b8e743f0af3321b4d5155616d753ef358cd62154817b2716c7846e9b025793fa  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux
7c7cb102b190f538c926fdbe31382ea84be2a8445fa3a2c422e8e881f78a9ad0  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
2a69d78e517f3a81ae8f885e4871ef0b4f15f09cdcb72d3dd439644c205831e6  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux
2e202634b34580992358820da09675f78f31ccb8cc49dcb58563f74e71130f1e  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
3d44509502d55de711aa0c30c09cf90898c690eec0b168c7f20b3f62d49fbd9b  ./tailscale/tailscale_merged_s390x_Linux
3f80d1b2c19b0545a3e07b715445494b4fe2a6daaf2b6b89096ad5840c773dec  ./tailscale/tailscale_mips64_Linux
7bc660f9e7fa3f254e40d1bcc71106b250158dccb3ff9c490bcefbd5485568eb  ./tailscale/tailscale_mips64le_Linux
3edfbb0dea90f791aaa55504aca3bfc700cf0c5dc8049bd6d4d42897fa2ec7e6  ./tailscale/tailscale_mips_Linux
2de0e4a74794a431b4f556951993ff81d917e5556c7da556e799942a18c1dfff  ./tailscale/tailscale_mips_Linux.upx
7c0b9bca22aa7090bc2c8c6302cf91d43cd3dd0d9c1c42fa6141e157a12a2ce0  ./tailscale/tailscale_mipsle_Linux
465a5b13167be16bdf0813867d19d494daefbfc927e8dbd4c5a3caa1a5e6b8db  ./tailscale/tailscale_mipsle_Linux.upx
404eef9350def6344ccdec8e0c72c66f0050192550c26ff3cdaf6d7c39165667  ./tailscale/tailscale_powerpc64_ppc64_Linux
5b180c5da46d02b7a0ffaf9cee79a4eb03900a93ca88b50038283c26915aaddd  ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
78d44933e42ab2d96a305196462273275c38418b22a646216222d3748c3c9641  ./tailscale/tailscale_powerpc64le_ppc64le_Linux
e7892f58099b0945a7c5abe2fb700748c1f5e027193b26b37d15f1b4a0eda80a  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
d53ddc002d18b04efde01fb62ba9e9703ac69919a8c158ed7a106b91b3fd5fa2  ./tailscale/tailscale_riscv64_Linux
88e6795014f975ddd6d3d4d7c5a75dfefed983a01d3eb94fc11fda670e3956c5  ./tailscale/tailscale_s390x_Linux
64a8ad28cbb67a6171236abe39f75a039a761a0e1aacdef75b26781887cef9a8  ./tailscale/tailscale_setup_Windows.exe
f6bdac3aa1f65341f988a667ec3cb5122df4f190fd72582020109a073b7b8d62  ./tailscale/tailscale_x86_Windows.msi
7a0bc6d37f3cb30d1027078e74da20f34d4ccb481754bbc616fe6a8f4f582465  ./tailscale/tailscaled_aarch64_arm64_Linux
4b4aa2eb27ebffea7af8d9fe7cc7d365c2b5da17fa41f2d4f43d1ed97186d778  ./tailscale/tailscaled_aarch64_arm64_Linux.upx
b4e609e9ac2e2d982e3af3e77196492cc4762d65ebc9f8d34617c85df0d9490e  ./tailscale/tailscaled_aarch64_arm64_macOS
33d0913747bfc459a9c73d9b7f2febd9c063c72cba3d410b725fbbf810b1e5de  ./tailscale/tailscaled_amd_geode_Linux
4b0e4c3f6831c96316adb4c666055ef4fc56b98a9a278b5c41d5a31f5fd3d022  ./tailscale/tailscaled_amd_geode_Linux.upx
729039d6f28336b8f56cd7736d5d042d5916d8e65511919ff4593301d005ad49  ./tailscale/tailscaled_amd_x86_64_Linux
cbd9d14116866f9ab1185ae38845d65cbdbb7411359d427b8ad46c977fb5e2ef  ./tailscale/tailscaled_amd_x86_64_Linux.upx
9d7d7e934f36598a9b286bb4ec12095a7b41e4c9ca75c26fbc6fe0d9cd585fbe  ./tailscale/tailscaled_amd_x86_64_macOS
256ab22aa8994042c92c6da73aa1a5c4d3856914c4ece233b417ada25dcf0459  ./tailscale/tailscaled_arm_abi_Linux
7a153c4aecb97ef2f1ebec1622107f93803a347e40389a81cf3f1ee0c90d9e91  ./tailscale/tailscaled_arm_abi_Linux.upx
88a577f25bb35b4ec444f56e274595c92fe6fc15b6aa37b6f688d99789178c0a  ./tailscale/tailscaled_i386_Linux
f2c49f4363e687e9c701154e79bf2ba55ffd7e4ee95607fe9561d454e99383d0  ./tailscale/tailscaled_i386_Linux.upx
337745f3f3b626fa0969a46fd2a207ca7db35db9f995d1ddde1a937f1a6a5b26  ./tailscale/tailscaled_mips64_Linux
ebdfbed7f5b3cc44cf6fd2a4fc4cb65b9f9740251368477929ca37037ccdcbf0  ./tailscale/tailscaled_mips64le_Linux
f168e602f7337e56bf77d42ab592b255f3f412477661dbc4a53cf3d1d14d967b  ./tailscale/tailscaled_mips_Linux
3517aa95d1acf7458e1e4f324df3a9278a9019214a49ee63adc0e6ad4b8053b7  ./tailscale/tailscaled_mips_Linux.upx
6c357508900e328347c8cc20c03674735f3a1bf4c45319ffb69550bc3c3e6614  ./tailscale/tailscaled_mipsle_Linux
68087214e54aa4184abfec2dec121a454577473c4abc2cee0b8c7d888dc354cb  ./tailscale/tailscaled_mipsle_Linux.upx
a9e275d3879ef6a226ff75a410d3bd85fa7eb4a0ddbdd1cac91e412bc0fe4c1f  ./tailscale/tailscaled_powerpc64_ppc64_Linux
b43ccfb1894ca9fbabddf9b8d2fe4e3c3479d05455820665e97248529e619679  ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
06a2f9b5caa02551fdc48b17eb8c2ca41be4ba5cf481df5d1203bbc2bec9ee32  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux
f3cf49eb43310acca823c9c675cf3614a9a24f2f8523d913994438470a903a57  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
2183b63c7fc381807f1f18faccb7e9af631ccf380df779061292b2b42bd10a03  ./tailscale/tailscaled_riscv64_Linux
613b20b75b720b9c376159fe95d9896b41f3796a6acdc2c7ce6a86ffcf6785a4  ./tailscale/tailscaled_s390x_Linux
```


---

- #### Sizes

```console
16M   ./tailscale/tailscale_aarch64_arm64_Linux
7.2M  ./tailscale/tailscale_aarch64_arm64_Linux.upx
24M   ./tailscale/tailscale_aarch64_arm64_Windows.msi
11M   ./tailscale/tailscale_aarch64_arm64_macOS
11M   ./tailscale/tailscale_amd_geode_Linux
3.1M  ./tailscale/tailscale_amd_geode_Linux.upx
12M   ./tailscale/tailscale_amd_x86_64_Linux
3.6M  ./tailscale/tailscale_amd_x86_64_Linux.upx
26M   ./tailscale/tailscale_amd_x86_64_Windows.msi
11M   ./tailscale/tailscale_amd_x86_64_macOS
16M   ./tailscale/tailscale_arm_abi_Linux
6.9M  ./tailscale/tailscale_arm_abi_Linux.upx
11M   ./tailscale/tailscale_i386_Linux
3.1M  ./tailscale/tailscale_i386_Linux.upx
46M   ./tailscale/tailscale_ipn_setup_Windows.exe
21M   ./tailscale/tailscale_merged_aarch64_arm64_Linux
5.3M  ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
20M   ./tailscale/tailscale_merged_aarch64_arm64_macOS
21M   ./tailscale/tailscale_merged_amd_x86_64_Linux
6.3M  ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
20M   ./tailscale/tailscale_merged_amd_x86_64_macOS
20M   ./tailscale/tailscale_merged_arm_Linux
5.0M  ./tailscale/tailscale_merged_arm_Linux.upx
20M   ./tailscale/tailscale_merged_i386_Linux
5.8M  ./tailscale/tailscale_merged_i386_Linux.upx
21M   ./tailscale/tailscale_merged_powerpc64_ppc64_Linux
5.1M  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
21M   ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux
5.4M  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
23M   ./tailscale/tailscale_merged_s390x_Linux
18M   ./tailscale/tailscale_mips64_Linux
18M   ./tailscale/tailscale_mips64le_Linux
17M   ./tailscale/tailscale_mips_Linux
7.0M  ./tailscale/tailscale_mips_Linux.upx
17M   ./tailscale/tailscale_mipsle_Linux
6.9M  ./tailscale/tailscale_mipsle_Linux.upx
11M   ./tailscale/tailscale_powerpc64_ppc64_Linux
2.9M  ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
12M   ./tailscale/tailscale_powerpc64le_ppc64le_Linux
3.1M  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
16M   ./tailscale/tailscale_riscv64_Linux
12M   ./tailscale/tailscale_s390x_Linux
51M   ./tailscale/tailscale_setup_Windows.exe
25M   ./tailscale/tailscale_x86_Windows.msi
31M   ./tailscale/tailscaled_aarch64_arm64_Linux
14M   ./tailscale/tailscaled_aarch64_arm64_Linux.upx
19M   ./tailscale/tailscaled_aarch64_arm64_macOS
21M   ./tailscale/tailscaled_amd_geode_Linux
5.9M  ./tailscale/tailscaled_amd_geode_Linux.upx
22M   ./tailscale/tailscaled_amd_x86_64_Linux
6.4M  ./tailscale/tailscaled_amd_x86_64_Linux.upx
19M   ./tailscale/tailscaled_amd_x86_64_macOS
30M   ./tailscale/tailscaled_arm_abi_Linux
13M   ./tailscale/tailscaled_arm_abi_Linux.upx
21M   ./tailscale/tailscaled_i386_Linux
5.9M  ./tailscale/tailscaled_i386_Linux.upx
34M   ./tailscale/tailscaled_mips64_Linux
34M   ./tailscale/tailscaled_mips64le_Linux
33M   ./tailscale/tailscaled_mips_Linux
13M   ./tailscale/tailscaled_mips_Linux.upx
33M   ./tailscale/tailscaled_mipsle_Linux
13M   ./tailscale/tailscaled_mipsle_Linux.upx
22M   ./tailscale/tailscaled_powerpc64_ppc64_Linux
5.1M  ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
22M   ./tailscale/tailscaled_powerpc64le_ppc64le_Linux
5.4M  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
31M   ./tailscale/tailscaled_riscv64_Linux
24M   ./tailscale/tailscaled_s390x_Linux
```

---

- #### UPX
```console

testing ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx [OK]
  11534471 ->   3214624   27.87%  linux/ppc64le  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx [OK]
  21168263 ->   5490516   25.94%   linux/arm64   ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_mipsle_Linux.upx [OK]
  17579035 ->   7214152   41.04%  linux/mipsel   ./tailscale/tailscale_mipsle_Linux.upx
testing ./tailscale/tailscale_amd_x86_64_Linux.upx [OK]
  11751688 ->   3773908   32.11%   linux/amd64   ./tailscale/tailscale_amd_x86_64_Linux.upx
testing ./tailscale/tailscaled_arm_abi_Linux.upx [OK]
  30900913 ->  12912008   41.79%    linux/arm    ./tailscale/tailscaled_arm_abi_Linux.upx
testing ./tailscale/tailscaled_mipsle_Linux.upx [OK]
  34218578 ->  13065868   38.18%  linux/mipsel   ./tailscale/tailscaled_mipsle_Linux.upx
testing ./tailscale/tailscaled_amd_geode_Linux.upx [OK]
  21492764 ->   6150324   28.62%   linux/i386    ./tailscale/tailscaled_amd_geode_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx [OK]
  21561479 ->   5269872   24.44%   linux/ppc64   ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_powerpc64_ppc64_Linux.upx [OK]
  11403399 ->   2959792   25.96%   linux/ppc64   ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_amd_geode_Linux.upx [OK]
  11157044 ->   3213804   28.81%   linux/i386    ./tailscale/tailscale_amd_geode_Linux.upx
testing ./tailscale/tailscaled_mips_Linux.upx [OK]
  34390496 ->  13141016   38.21%   linux/mips    ./tailscale/tailscaled_mips_Linux.upx
testing ./tailscale/tailscale_aarch64_arm64_Linux.upx [OK]
  16406245 ->   7504092   45.74%   linux/arm64   ./tailscale/tailscale_aarch64_arm64_Linux.upx
testing ./tailscale/tailscaled_aarch64_arm64_Linux.upx [OK]
  32162105 ->  13708700   42.62%   linux/arm64   ./tailscale/tailscaled_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx [OK]
  21627015 ->   5579752   25.80%  linux/ppc64le  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_arm_abi_Linux.upx [OK]
  16102408 ->   7207192   44.76%    linux/arm    ./tailscale/tailscale_arm_abi_Linux.upx
testing ./tailscale/tailscale_merged_amd_x86_64_Linux.upx [OK]
  22003847 ->   6580604   29.91%   linux/amd64   ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_i386_Linux.upx [OK]
  11128340 ->   3207348   28.82%   linux/i386    ./tailscale/tailscale_i386_Linux.upx
testing ./tailscale/tailscaled_i386_Linux.upx [OK]
  21455868 ->   6138332   28.61%   linux/i386    ./tailscale/tailscaled_i386_Linux.upx
testing ./tailscale/tailscale_merged_arm_Linux.upx [OK]
  20775047 ->   5242244   25.23%    linux/arm    ./tailscale/tailscale_merged_arm_Linux.upx
testing ./tailscale/tailscaled_amd_x86_64_Linux.upx [OK]
  22836984 ->   6691032   29.30%   linux/amd64   ./tailscale/tailscaled_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_mips_Linux.upx [OK]
  17674501 ->   7265164   41.11%   linux/mips    ./tailscale/tailscale_mips_Linux.upx
testing ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx [OK]
  22544519 ->   5654392   25.08%  linux/ppc64le  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx [OK]
  22413447 ->   5339092   23.82%   linux/ppc64   ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_merged_i386_Linux.upx [OK]
  20734087 ->   6061204   29.23%   linux/i386    ./tailscale/tailscale_merged_i386_Linux.upx

```

---

- #### Version
```console
$ ./tailscale/tailscale_amd_x86_64_Linux --version
1.64.0
  tailscale commit: 7e9bebdb2470dfbb6e08a3f12a289a7d88128dfb
  other commit: f314c5be5350431460b89f703275de6b89a30460
  go version: go1.22.2

The easiest, most secure way to use WireGuard.

USAGE
  tailscale [flags] <subcommand> [command flags]

For help on subcommands, add --help after: "tailscale status --help".

This CLI is still under active development. Commands and flags will
change in the future.

SUBCOMMANDS
  up         Connect to Tailscale, logging in if needed
  down       Disconnect from Tailscale
  set        Change specified preferences
  login      Log in to a Tailscale account
  logout     Disconnect from Tailscale and expire current node key
  switch     Switches to a different Tailscale account
  configure  [ALPHA] Configure the host to enable more Tailscale features
  netcheck   Print an analysis of local network conditions
  ip         Show Tailscale IP addresses
  status     Show state of tailscaled and its connections
  ping       Ping a host at the Tailscale layer, see how it routed
  nc         Connect to a port on a host, connected to stdin/stdout
  ssh        SSH to a Tailscale machine
  funnel     Serve content and local servers on the internet
  serve      Serve content and local servers on your tailnet
  version    Print Tailscale version
  web        Run a web server for controlling Tailscale
  file       Send or receive files
  bugreport  Print a shareable identifier to help diagnose issues
  cert       Get TLS certs
  lock       Manage tailnet lock
  licenses   Get open source license information
  exit-node  Show machines on your tailnet configured as exit nodes
  update     Update Tailscale to the latest/different version
  whois      Show the machine and user associated with a Tailscale IP (v4 or v6)
  drive      Share a directory with your tailnet

FLAGS
  --socket string
    	path to tailscaled socket (default /var/run/tailscale/tailscaled.sock)

$ ./tailscale/tailscaled_amd_x86_64_Linux -version
1.64.0
  tailscale commit: 7e9bebdb2470dfbb6e08a3f12a289a7d88128dfb
  other commit: f314c5be5350431460b89f703275de6b89a30460
  go version: go1.22.2

Usage of ./tailscale/tailscaled_amd_x86_64_Linux:
  -bird-socket string
    	path of the bird unix socket
  -cleanup
    	clean up system state and exit
  -config string
    	path to config file
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


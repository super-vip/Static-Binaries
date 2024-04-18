
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
./tailscale/tailscale_aarch64_arm64_Windows.msi:             Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard.WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Arm64;1033, Revision Number: {A6C25593-C5EB-4DF2-815B-3110760D956F}, Create Time/Date: Wed Apr 17 15:59:02 2024, Last Saved Time/Date: Wed Apr 17 15:59:02 2024, Number of Pages: 500, Number of Words: 2, Name of Creating Application: Windows Installer XML Toolset (), Security: 2
./tailscale/tailscale_aarch64_arm64_macOS:                   Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_amd_geode_Linux:                       ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=onJ5QmnUFstaYJ8vw64Y/FooL4U-5CGNV1Zm-ZNYM/Ob6fKcicITep2F6CF6AI/vq8w2SkUqSJMCNfmD0_B, stripped
./tailscale/tailscale_amd_geode_Linux.upx:                   ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), statically linked, no section header
./tailscale/tailscale_amd_x86_64_Linux:                      ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=2yGkD3h4voxr37bqVnX2/a8OqHhDZHNBLpKX0S89v/IxhCZ8MfPbsZEsOfkG-q/MmPd3LcVxlfBwgZ97dHY, stripped
./tailscale/tailscale_amd_x86_64_Linux.upx:                  ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_amd_x86_64_Windows.msi:                Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard.WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: x64;1033, Revision Number: {F3DBCBD5-52D7-4037-97FD-BE79D91541C2}, Create Time/Date: Wed Apr 17 15:59:09 2024, Last Saved Time/Date: Wed Apr 17 15:59:09 2024, Number of Pages: 500, Number of Words: 2, Name of Creating Application: Windows Installer XML Toolset (), Security: 2
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
./tailscale/tailscale_x86_Windows.msi:                       Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard.WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Intel;1033, Revision Number: {8BEF33F2-0D66-4890-9CE1-369AB878AF23}, Create Time/Date: Wed Apr 17 15:59:02 2024, Last Saved Time/Date: Wed Apr 17 15:59:02 2024, Number of Pages: 500, Number of Words: 2, Name of Creating Application: Windows Installer XML Toolset (), Security: 2
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
5cfa0a982b834eb4c6a5f3892cda9920b06318638c349f64aab18bb9a0af47f9  ./tailscale/tailscale_aarch64_arm64_Windows.msi
8b948542124de5a8a820d8a9a58885944309f75ed5b855b1f98e86d8bcf38cde  ./tailscale/tailscale_aarch64_arm64_macOS
57b820fb28c95171637914390ef89e40b04a901bc0d86643f827232994ea2b46  ./tailscale/tailscale_amd_geode_Linux
2277ef4bc90dc024daedfa8fa3b3ce27855609a989f335ad6093adc0119b24a1  ./tailscale/tailscale_amd_geode_Linux.upx
32e4fa633ec74b5aada9a4dea0f20a2061ddfa4e7e32f06663504b861330e4f9  ./tailscale/tailscale_amd_x86_64_Linux
a708024a018e747659cda34ca00d85f840c0394b2b0a25927a159195f47461f7  ./tailscale/tailscale_amd_x86_64_Linux.upx
f44940a25327b0a90ee08d3b6f70d588aa80c66bf05e3f6d9ef8c82fe6832dd6  ./tailscale/tailscale_amd_x86_64_Windows.msi
5e7742cbbef0cfd6610a0ce9ee55e87c3e1ee81a7ec34a0cb736d8c7f05ab42d  ./tailscale/tailscale_amd_x86_64_macOS
74690e29e88a6d400e7f2f609e64e61072f75b8a5841a0096de4b2d231195e7d  ./tailscale/tailscale_arm_abi_Linux
9f94595647a2820e37816485f1d8f7950cdb6a38225932353c4559889c7871ed  ./tailscale/tailscale_arm_abi_Linux.upx
9e29f420c0ffd7431183b1e9610e2312831482f202cc6a7355405b3fefaebffd  ./tailscale/tailscale_i386_Linux
18d37af9c07abc15e437188ebf77ab65337ea84915bc2c10ddb45946363ab501  ./tailscale/tailscale_i386_Linux.upx
e157714e173f2cc2b77d376da0b94a01bdebf824b925301ac0dcdbb683be8763  ./tailscale/tailscale_ipn_setup_Windows.exe
edf4e8c7643b78a3b0f740afd65e8b150fe5e6dee4c25c8c1d13c92be4a59b48  ./tailscale/tailscale_merged_aarch64_arm64_Linux
f44daaf15cf5063ac937d6d78e6f1261cfd3264fb391243a0f71bcb244739447  ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
a8f07cf6c8563d054cff91b8ef6ebf6fbafa4ab082159e2b480e71ccab44cda3  ./tailscale/tailscale_merged_aarch64_arm64_macOS
018318028c5ddddc07e2bb2d91da5fcbdcc579de30a85a9f985b71517cbc52cb  ./tailscale/tailscale_merged_amd_x86_64_Linux
f4ee8ff2d141810ca371252a4175c09b7d598cda1257f93136ae2be3e7476380  ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
cea3edbe4bcab76301b70e3151f3d6a061f1ef7c2cdac9620f9a96e935b37288  ./tailscale/tailscale_merged_amd_x86_64_macOS
abfdb459ac9647d2fe5a7ab5d53d22044b4370baa2d0ecbdfacdb2457451c969  ./tailscale/tailscale_merged_arm_Linux
7330c20d462dc9e2c3debfc93afc379d3c52adc0a0abdf5f875e5739752f990a  ./tailscale/tailscale_merged_arm_Linux.upx
2c2927dc096b432d4941d26252cf5bb821adb0a8a0221fc7c9267b90ee622b25  ./tailscale/tailscale_merged_i386_Linux
90c102ae2cf18d8eaab8c7dc0a859f26dc48f6f8d927226e980bb615b2ab26c9  ./tailscale/tailscale_merged_i386_Linux.upx
8b0e9b61bfbcde93c5819d4c0c774f9c4bcb45fb897b1b5f665fb17485d328b7  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux
88aff5f369074588b5cdb94e24ffaaba15be6fa76295979e71308ed69ad59e20  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
ab511651c7c1fffd6c6081ba8388dd7db8c183b26929fe1808acb98262382e34  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux
d576ef96ab40d15d90ebab1c874b1412ca3ee0abd75df5ad06fc9359ec7d8b01  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
3b3c4f3c6126f76f7ed453c7215c39dd96cdd4619c67c9aeff4de30e97b4847f  ./tailscale/tailscale_merged_s390x_Linux
3f80d1b2c19b0545a3e07b715445494b4fe2a6daaf2b6b89096ad5840c773dec  ./tailscale/tailscale_mips64_Linux
7bc660f9e7fa3f254e40d1bcc71106b250158dccb3ff9c490bcefbd5485568eb  ./tailscale/tailscale_mips64le_Linux
3edfbb0dea90f791aaa55504aca3bfc700cf0c5dc8049bd6d4d42897fa2ec7e6  ./tailscale/tailscale_mips_Linux
2de0e4a74794a431b4f556951993ff81d917e5556c7da556e799942a18c1dfff  ./tailscale/tailscale_mips_Linux.upx
7c0b9bca22aa7090bc2c8c6302cf91d43cd3dd0d9c1c42fa6141e157a12a2ce0  ./tailscale/tailscale_mipsle_Linux
465a5b13167be16bdf0813867d19d494daefbfc927e8dbd4c5a3caa1a5e6b8db  ./tailscale/tailscale_mipsle_Linux.upx
d226cf206af8d2a954a309e33aeac19df9589686e5fa510a5d9ea14d2c062a13  ./tailscale/tailscale_powerpc64_ppc64_Linux
b26fcd693e782f49be70230251b95830c5016f1492a4e569cd69f1a22b63d562  ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
ef5ecbd8aa206305dfdb86b6cd531d6068e45f27caf593e1ed1c26a148274f86  ./tailscale/tailscale_powerpc64le_ppc64le_Linux
32bde307177d37daa667a3edcbeec70845821e47c5e5c25e6d8ae128500eb712  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
d53ddc002d18b04efde01fb62ba9e9703ac69919a8c158ed7a106b91b3fd5fa2  ./tailscale/tailscale_riscv64_Linux
d64cd7310ce5019a574be036e356c413c650594c5f8ff02c903290d0c9068181  ./tailscale/tailscale_s390x_Linux
64a8ad28cbb67a6171236abe39f75a039a761a0e1aacdef75b26781887cef9a8  ./tailscale/tailscale_setup_Windows.exe
f3d94d5b2f1a967371f6c957f9d2c78768c72baa0ec3d94441d9567e63f3587c  ./tailscale/tailscale_x86_Windows.msi
7a0bc6d37f3cb30d1027078e74da20f34d4ccb481754bbc616fe6a8f4f582465  ./tailscale/tailscaled_aarch64_arm64_Linux
4b4aa2eb27ebffea7af8d9fe7cc7d365c2b5da17fa41f2d4f43d1ed97186d778  ./tailscale/tailscaled_aarch64_arm64_Linux.upx
e4761d4c82ca27cbdf49673e043b7193526ef016190d70423c086a44554eecc1  ./tailscale/tailscaled_aarch64_arm64_macOS
33d0913747bfc459a9c73d9b7f2febd9c063c72cba3d410b725fbbf810b1e5de  ./tailscale/tailscaled_amd_geode_Linux
4b0e4c3f6831c96316adb4c666055ef4fc56b98a9a278b5c41d5a31f5fd3d022  ./tailscale/tailscaled_amd_geode_Linux.upx
729039d6f28336b8f56cd7736d5d042d5916d8e65511919ff4593301d005ad49  ./tailscale/tailscaled_amd_x86_64_Linux
cbd9d14116866f9ab1185ae38845d65cbdbb7411359d427b8ad46c977fb5e2ef  ./tailscale/tailscaled_amd_x86_64_Linux.upx
694eb298e3c054a9ddd9f1b4ff49fea2175e0ca4675486183128d3a4906ade6c  ./tailscale/tailscaled_amd_x86_64_macOS
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
7fde74e6afa617a2cd62458d585661e712fca54eb8689f1e3f247f29c2597850  ./tailscale/tailscaled_powerpc64_ppc64_Linux
50dab11efe9e02ef12b03ed1358158b8808e004dc121ae52c136854ac895cd3c  ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
700c77ae84519e5c65cafa86f10ea7579c3a396450ee69fda76f85cacd6852af  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux
2de3681b83d61e3f5241566d6b720d68573445345087ddbaf162bfe7c658fbcf  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
2183b63c7fc381807f1f18faccb7e9af631ccf380df779061292b2b42bd10a03  ./tailscale/tailscaled_riscv64_Linux
141360777f1aa8ca03faa56124420181094583bd3bc3de4e970e3f924bd25494  ./tailscale/tailscaled_s390x_Linux
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

testing ./tailscale/tailscaled_amd_geode_Linux.upx [OK]
  21492764 ->   6150324   28.62%   linux/i386    ./tailscale/tailscaled_amd_geode_Linux.upx
testing ./tailscale/tailscale_merged_i386_Linux.upx [OK]
  20734087 ->   6058564   29.22%   linux/i386    ./tailscale/tailscale_merged_i386_Linux.upx
testing ./tailscale/tailscaled_i386_Linux.upx [OK]
  21455868 ->   6138332   28.61%   linux/i386    ./tailscale/tailscaled_i386_Linux.upx
testing ./tailscale/tailscaled_amd_x86_64_Linux.upx [OK]
  22836984 ->   6691032   29.30%   linux/amd64   ./tailscale/tailscaled_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx [OK]
  21561479 ->   5270032   24.44%   linux/ppc64   ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx [OK]
  21627015 ->   5579816   25.80%  linux/ppc64le  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_amd_x86_64_Linux.upx [OK]
  11751688 ->   3773908   32.11%   linux/amd64   ./tailscale/tailscale_amd_x86_64_Linux.upx
testing ./tailscale/tailscaled_aarch64_arm64_Linux.upx [OK]
  32162105 ->  13708700   42.62%   linux/arm64   ./tailscale/tailscaled_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_arm_abi_Linux.upx [OK]
  16102408 ->   7207192   44.76%    linux/arm    ./tailscale/tailscale_arm_abi_Linux.upx
testing ./tailscale/tailscale_i386_Linux.upx [OK]
  11128340 ->   3207348   28.82%   linux/i386    ./tailscale/tailscale_i386_Linux.upx
testing ./tailscale/tailscale_amd_geode_Linux.upx [OK]
  11157044 ->   3213804   28.81%   linux/i386    ./tailscale/tailscale_amd_geode_Linux.upx
testing ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx [OK]
  11534471 ->   3214680   27.87%  linux/ppc64le  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscaled_arm_abi_Linux.upx [OK]
  30900913 ->  12912008   41.79%    linux/arm    ./tailscale/tailscaled_arm_abi_Linux.upx
testing ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx [OK]
  21168263 ->   5490420   25.94%   linux/arm64   ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
testing ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx [OK]
  22544519 ->   5654312   25.08%  linux/ppc64le  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscaled_mipsle_Linux.upx [OK]
  34218578 ->  13065868   38.18%  linux/mipsel   ./tailscale/tailscaled_mipsle_Linux.upx
testing ./tailscale/tailscale_mipsle_Linux.upx [OK]
  17579035 ->   7214152   41.04%  linux/mipsel   ./tailscale/tailscale_mipsle_Linux.upx
testing ./tailscale/tailscaled_mips_Linux.upx [OK]
  34390496 ->  13141016   38.21%   linux/mips    ./tailscale/tailscaled_mips_Linux.upx
testing ./tailscale/tailscale_merged_amd_x86_64_Linux.upx [OK]
  22003847 ->   6580940   29.91%   linux/amd64   ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
testing ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx [OK]
  22413447 ->   5339164   23.82%   linux/ppc64   ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_aarch64_arm64_Linux.upx [OK]
  16406245 ->   7504092   45.74%   linux/arm64   ./tailscale/tailscale_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_mips_Linux.upx [OK]
  17674501 ->   7265164   41.11%   linux/mips    ./tailscale/tailscale_mips_Linux.upx
testing ./tailscale/tailscale_merged_arm_Linux.upx [OK]
  20775047 ->   5242676   25.24%    linux/arm    ./tailscale/tailscale_merged_arm_Linux.upx
testing ./tailscale/tailscale_powerpc64_ppc64_Linux.upx [OK]
  11403399 ->   2959784   25.96%   linux/ppc64   ./tailscale/tailscale_powerpc64_ppc64_Linux.upx

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


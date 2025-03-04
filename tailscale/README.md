
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
./tailscale/tailscale_aarch64_arm64_Linux:                   ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=pte62u-SCWBymP6c2eY8/NhyXbJkGrQmljmv8hdHg/TUTmKbVmwhsEa-4cK2cc/LliLGaZom7S8vfcSoNqK, with debug_info, not stripped
./tailscale/tailscale_aarch64_arm64_Linux.upx:               ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=pte62u-SCWBymP6c2eY8/NhyXbJkGrQmljmv8hdHg/TUTmKbVmwhsEa-4cK2cc/LliLGaZom7S8vfcSoNqK, statically linked, no section header
./tailscale/tailscale_aarch64_arm64_Windows.msi:             Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard.WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Arm64;1033, Revision Number: {AC427109-C736-4F0B-839C-B6D31D68BEBE}, Create Time/Date: Wed Feb 12 18:54:47 2025, Last Saved Time/Date: Wed Feb 12 18:54:47 2025, Number of Pages: 500, Number of Words: 2, Name of Creating Application: Windows Installer XML Toolset (), Security: 2
./tailscale/tailscale_aarch64_arm64_macOS:                   Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_amd_geode_Linux:                       ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=r0tglJnz46avTHNrc3sn/R-MKHq_9K6oUcQLf1N8l/bXN9Z5E9WqCzx05S4Lm4/8DpUvFtmEPHGQKjck2qG, stripped
./tailscale/tailscale_amd_geode_Linux.upx:                   ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=r0tglJnz46avTHNrc3sn/R-MKHq_9K6oUcQLf1N8l/bXN9Z5E9WqCzx05S4Lm4/8DpUvFtmEPHGQKjck2qG, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Linux:                      ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=9iGN21CZE8hr-xJY76Vu/6cdbQVhM5d4tSpydpF6C/Rmkh8bTJBS9UFPuB7qzn/BItRf2PfsJvlaijQPL1f, stripped
./tailscale/tailscale_amd_x86_64_Linux.upx:                  ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=9iGN21CZE8hr-xJY76Vu/6cdbQVhM5d4tSpydpF6C/Rmkh8bTJBS9UFPuB7qzn/BItRf2PfsJvlaijQPL1f, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Windows.msi:                Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard.WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: x64;1033, Revision Number: {1002A674-BEFE-4A8A-83CD-2FDA49782C71}, Create Time/Date: Wed Feb 12 18:54:16 2025, Last Saved Time/Date: Wed Feb 12 18:54:16 2025, Number of Pages: 500, Number of Words: 2, Name of Creating Application: Windows Installer XML Toolset (), Security: 2
./tailscale/tailscale_amd_x86_64_macOS:                      Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_arm_abi_Linux:                         ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=iG2N6_8IJ-rdE0rB35JJ/tDkY-qZe2vP0ycfoiecF/YeQd_hfbGo99aaPONc8H/z4qcDXDTNv0n-qVmHdcn, with debug_info, not stripped
./tailscale/tailscale_arm_abi_Linux.upx:                     ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=iG2N6_8IJ-rdE0rB35JJ/tDkY-qZe2vP0ycfoiecF/YeQd_hfbGo99aaPONc8H/z4qcDXDTNv0n-qVmHdcn, statically linked, no section header
./tailscale/tailscale_i386_Linux:                            ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=9Sdj0UAgsZcd6Qkig-Y3/V7HECEtZpieMQ89S6bUW/ce6yGUjOpTTA0Z_zbjiQ/JLRbgpXbVKZMaEi0oLju, stripped
./tailscale/tailscale_i386_Linux.upx:                        ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=9Sdj0UAgsZcd6Qkig-Y3/V7HECEtZpieMQ89S6bUW/ce6yGUjOpTTA0Z_zbjiQ/JLRbgpXbVKZMaEi0oLju, statically linked, no section header
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
./tailscale/tailscale_mips64_Linux:                          ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=u9tU66JSUmKI9nbPLo7h/8qyI14eniNK2uJciwseV/5v_gEAa4hEdh9Hkinv-v/p4TO1wavcUPDhLoAVuY2, with debug_info, not stripped
./tailscale/tailscale_mips64le_Linux:                        ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=VOjZGLjg5oJ6abnevv-y/9zxtTiwqcYmIMlXItMII/F9bhPfzeHdB56FLoH4FA/2STkAVZCBwyjGKQxnXqI, with debug_info, not stripped
./tailscale/tailscale_mips_Linux:                            ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=mUxxf_YNpqi_VG2WBrVg/27VmD2bt6NptOUpSy0U-/0d2ypm0UusFhhC58dlcB/8sPBpLSs5qIQbonqLmNa, with debug_info, not stripped
./tailscale/tailscale_mips_Linux.upx:                        ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=mUxxf_YNpqi_VG2WBrVg/27VmD2bt6NptOUpSy0U-/0d2ypm0UusFhhC58dlcB/8sPBpLSs5qIQbonqLmNa, statically linked, no section header
./tailscale/tailscale_mipsle_Linux:                          ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=8l8EEgIFJOQkMjxENsTz/-pOdU1a6h1GNE7XvKyXn/VjNM3AGDfVLbfPMKsv_y/94ARW1KXlIyL8q-B-kWJ, with debug_info, not stripped
./tailscale/tailscale_mipsle_Linux.upx:                      ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=8l8EEgIFJOQkMjxENsTz/-pOdU1a6h1GNE7XvKyXn/VjNM3AGDfVLbfPMKsv_y/94ARW1KXlIyL8q-B-kWJ, statically linked, no section header
./tailscale/tailscale_powerpc64_ppc64_Linux:                 ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64_ppc64_Linux.upx:             ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_powerpc64le_ppc64le_Linux:             ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx:         ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_riscv64_Linux:                         ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, Go BuildID=1pfuf_TX44oVNJN7NzWO/ZKNvuKu6wTrJsGvHs-LE/_4gV_ov8L4kGNrpEMJBa/jSIpJZ0aVEaHhU-a-sKs, with debug_info, not stripped
./tailscale/tailscale_s390x_Linux:                           ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_setup_Windows.exe:                     PE32 executable (GUI) Intel 80386, for MS Windows, 6 sections
./tailscale/tailscale_x86_Windows.msi:                       Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard.WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Intel;1033, Revision Number: {9D70B63F-43DA-4B9F-A742-5D510D19082D}, Create Time/Date: Wed Feb 12 18:54:40 2025, Last Saved Time/Date: Wed Feb 12 18:54:40 2025, Number of Pages: 500, Number of Words: 2, Name of Creating Application: Windows Installer XML Toolset (), Security: 2
./tailscale/tailscaled_aarch64_arm64_Linux:                  ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=qdwwJZEwm9xwhySDrzSI/AlaoEunoedhWbtunkf6Q/GWPnLEhZqpyZC2fDu3V7/rwtzbWaheJAxSwvUZzMd, with debug_info, not stripped
./tailscale/tailscaled_aarch64_arm64_Linux.upx:              ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=qdwwJZEwm9xwhySDrzSI/AlaoEunoedhWbtunkf6Q/GWPnLEhZqpyZC2fDu3V7/rwtzbWaheJAxSwvUZzMd, statically linked, no section header
./tailscale/tailscaled_aarch64_arm64_macOS:                  Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_amd_geode_Linux:                      ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=CP6XKBt5553uq7RuMl8C/jVM5L_AIdbpP9Qc_NB0q/kkrXpCjP7SuX_D4pztDO/53gXi8PTVI2gD8xclY8w, stripped
./tailscale/tailscaled_amd_geode_Linux.upx:                  ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=CP6XKBt5553uq7RuMl8C/jVM5L_AIdbpP9Qc_NB0q/kkrXpCjP7SuX_D4pztDO/53gXi8PTVI2gD8xclY8w, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_Linux:                     ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=OZ5QbK4cHDY8OqVKf09_/2nT3ubCUYuqgQplQSdy3/OYViyF40q1DVoEeGMfvF/EgpzS3bZK17gt8-nnmI9, stripped
./tailscale/tailscaled_amd_x86_64_Linux.upx:                 ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=OZ5QbK4cHDY8OqVKf09_/2nT3ubCUYuqgQplQSdy3/OYViyF40q1DVoEeGMfvF/EgpzS3bZK17gt8-nnmI9, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_macOS:                     Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_arm_abi_Linux:                        ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=mePdEBttV6bMtPizzBef/-3fcUpCu2vbhks9xz4qa/qqkO0n6z-ev8Lmfu4fXL/aIyooDzXJjFoH8aHospo, with debug_info, not stripped
./tailscale/tailscaled_arm_abi_Linux.upx:                    ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=mePdEBttV6bMtPizzBef/-3fcUpCu2vbhks9xz4qa/qqkO0n6z-ev8Lmfu4fXL/aIyooDzXJjFoH8aHospo, statically linked, no section header
./tailscale/tailscaled_i386_Linux:                           ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=fsFUaHCDcIV0hRNAAZdk/rxdoutiyIr35LlzC_0tf/e7M7SdXjuzO8_gJuXyb7/moZ_GHxjGVkFbvydpSYo, stripped
./tailscale/tailscaled_i386_Linux.upx:                       ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=fsFUaHCDcIV0hRNAAZdk/rxdoutiyIr35LlzC_0tf/e7M7SdXjuzO8_gJuXyb7/moZ_GHxjGVkFbvydpSYo, statically linked, no section header
./tailscale/tailscaled_mips64_Linux:                         ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=XUtDigvDp4NzKGSOGd1W/FU69CEdbFILIL3BJeLTP/pNVL-HI-6om1peACPOyN/thrFiHKXt__Qc1fpdi4b, with debug_info, not stripped
./tailscale/tailscaled_mips64le_Linux:                       ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=BirmjqE4b2pdE5yEZDbK/F2bcmjQ-ErU4rhyCJOwS/FAcA_q13VszuUo_Fg7PZ/lk6ro7QlYd24z3D6YPxK, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux:                           ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=Mky8PmP_uWU5EtUdkDT4/EZY0gvbjS3L6Fv6GOq2j/FgiNh-Shu5AgonTvMP_L/qJ8guTguzsLvZLha59sB, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux.upx:                       ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=Mky8PmP_uWU5EtUdkDT4/EZY0gvbjS3L6Fv6GOq2j/FgiNh-Shu5AgonTvMP_L/qJ8guTguzsLvZLha59sB, statically linked, no section header
./tailscale/tailscaled_mipsle_Linux:                         ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=19ft5Ofizik4Ik72ACtU/qLPEEFMmndHou4l7M__c/fMnwyHWcOp3U-lus4TgL/B2OveuqQ-lUoIbl4pExo, with debug_info, not stripped
./tailscale/tailscaled_mipsle_Linux.upx:                     ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=19ft5Ofizik4Ik72ACtU/qLPEEFMmndHou4l7M__c/fMnwyHWcOp3U-lus4TgL/B2OveuqQ-lUoIbl4pExo, statically linked, no section header
./tailscale/tailscaled_powerpc64_ppc64_Linux:                ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64_ppc64_Linux.upx:            ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_powerpc64le_ppc64le_Linux:            ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx:        ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_riscv64_Linux:                        ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, Go BuildID=-NCSyYnukEBsFfVLdXiu/OMEeI9TYFwXw1EzKUIs2/i1nUiHBptmYM6MOXWVZw/bMuO5gJTHvWLKppVWC3m, with debug_info, not stripped
./tailscale/tailscaled_s390x_Linux:                          ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped

--> SHA256SUM
3d2a974605b11cde84295e35ef0855cfb2675c3b04feee16283348f7f51864de  ./tailscale/tailscale_aarch64_arm64_Linux
57d9dbace2894fb0d980e74704de64198618cbf94cdf226afc897433ed26e0e7  ./tailscale/tailscale_aarch64_arm64_Linux.upx
991dd6a5301dae186f4d74964909de0d7f802820eeaaf30eb5f8bf190e968003  ./tailscale/tailscale_aarch64_arm64_Windows.msi
758bd296723a348a70f5274b294baeb4053abd2e2ce58e2220e210946b618c6f  ./tailscale/tailscale_aarch64_arm64_macOS
5bffa049936d3de5d0961826a3d3f555c669a139cc02ba6d213f27c2a0def858  ./tailscale/tailscale_amd_geode_Linux
e4443ea4257d223616b89cd15da5bfc8364647f5c328dd621438a42354555bf7  ./tailscale/tailscale_amd_geode_Linux.upx
94cfc94dcf20cbfe2c6466982103f980c4976dacfe034cc26616bdb1365995d0  ./tailscale/tailscale_amd_x86_64_Linux
8f395ce65adcd3f2ba834ac731c066c446b468b51eafc3abd8c1772ce144459d  ./tailscale/tailscale_amd_x86_64_Linux.upx
72b0d39adb0c88ccf435875a0a5db6d809230a5f85d1447792d0fe091981beef  ./tailscale/tailscale_amd_x86_64_Windows.msi
248b7930c0c4c650f988bcb90a968da042066e0b826bf58efd8fe3a69fad8e7f  ./tailscale/tailscale_amd_x86_64_macOS
65a86a17c43dfe9f7478e7ce99ed724a5ef1d48940a797f5fb03ae87f048a281  ./tailscale/tailscale_arm_abi_Linux
74a8a0a940a9ab82dfc4e06a1f202794a4f5b4100518e7e09b3e881a9c4288e4  ./tailscale/tailscale_arm_abi_Linux.upx
683893603a9d1049f2881874b554f38c27f9f00bfcf13300a46bcb67d0b7c0d0  ./tailscale/tailscale_i386_Linux
ae9f05bd487f5733f644346a15801e1cc8042e5ada0024fc9c392bc5b223741d  ./tailscale/tailscale_i386_Linux.upx
caffe8a0f8d2820cfe11dc4fd862435fe83f41d2c9ee8178cc662a7e7f8ea99f  ./tailscale/tailscale_ipn_setup_Windows.exe
6fba7cdf0247c28099f2e042bd7e7b68b12de331948fc78383926029ee47b43c  ./tailscale/tailscale_merged_aarch64_arm64_Linux
3b5673a4d76fb6342c34d92fa7f12cac47e5a5ee01baec104d2dd9cc411bdf65  ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
68728bde1313493eb44dbd3be2e989eb00f60f4938d0d2845df9d45e32c25df7  ./tailscale/tailscale_merged_aarch64_arm64_macOS
0125736a3c6405a2076065ddcb096ec6bcb45dc352cc47eb4dcf0b771ed49d7b  ./tailscale/tailscale_merged_amd_x86_64_Linux
c3d4b59f2ea16cce21cb02c027350eb04399ea80400bfbc2af95ade7de9c2852  ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
267bebcfe539dd8353add30caf55a042bf996f8e688aae7910b9ecf61714f3f8  ./tailscale/tailscale_merged_amd_x86_64_macOS
a855e35239067c24a77860521dae5e131b20359d7c41d631331b130f9745a1dc  ./tailscale/tailscale_merged_arm_Linux
83c97087a2a658b3325c4b3fbfd86cf9ba9f5f7ab28a578c7dd476efec512403  ./tailscale/tailscale_merged_arm_Linux.upx
d017f476f59136703dc69552f187c2d8865fa05cea784811cfab21c5f1c6d409  ./tailscale/tailscale_merged_i386_Linux
c348648eaf8858079bc6ac1ba1f5bbcb49583fd35dfce5c076e62c5a5a6ef120  ./tailscale/tailscale_merged_i386_Linux.upx
24242f7489d92b747b4c6e1a1be4cdd6e629ae77c0003e4bce5f2888c8cd9019  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux
bf3be7f702c6172c94b0d1e9547818e16d9b2468fde05aec9ea683af8205b680  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
a8596d6a0819690d492ace1ed1e98efb7ed4709ebb8f22473d01e9c3851adf61  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux
3cbfa6e3a4b26fc8b8a4e32e5258b01c6521b5d9e28b05e71361c319c55e70c3  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
17ed0c98cda6a080ef10c5129ba5c3dcf8ae5c88d06ffeae5ee7cf97a42a4b54  ./tailscale/tailscale_merged_s390x_Linux
d8bb7e97b21a4b365cbfed373c58035c889112a3994549d797cb37617d9cc934  ./tailscale/tailscale_mips64_Linux
d3073646194bf33e0ece783af8f7c523d0fcd653a14c1cccd50e14f6bb62f947  ./tailscale/tailscale_mips64le_Linux
ca9f8ddfd28d3fd2c63f5b29b1da6113baa537b654dde8216fa3a8c8d3e97670  ./tailscale/tailscale_mips_Linux
58770654efc785ea46b9675d825794cf86292cfd8c22ce7cef3e4c1d6832381b  ./tailscale/tailscale_mips_Linux.upx
9e4f3d14d05a89fcefaab34ddc37a12686e9fb2eb05129cd172cf7c99ff462d7  ./tailscale/tailscale_mipsle_Linux
277f3d1706eb10327066bbb3afba053ebf40aef87e76be7dd59c5cf8f53fe425  ./tailscale/tailscale_mipsle_Linux.upx
9a5d2c6161a292e78488430119c93e8830e6948ac365328a865762ad357bbcad  ./tailscale/tailscale_powerpc64_ppc64_Linux
2019c084e72d9e262df9b94587ece39b4e668556ca9cb2d015a25970593ec644  ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
c697d4e506c26b3540982dec3be4764babc6a9500689cb4d2d786968a16c7778  ./tailscale/tailscale_powerpc64le_ppc64le_Linux
cf2332a4f47e3ca6aa643bb1723d4e1ee1b3463f1b21c463c46e1a50b3e06bfb  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
469d3e665c2370b7153748b94789e571111d1db0b19af12d0e783f3d0c935dcf  ./tailscale/tailscale_riscv64_Linux
e6d232cc515c38db89534b874786155477ccd20b00b271280c7dc325eb290aed  ./tailscale/tailscale_s390x_Linux
64a8ad28cbb67a6171236abe39f75a039a761a0e1aacdef75b26781887cef9a8  ./tailscale/tailscale_setup_Windows.exe
f148ae1043e1c1bb6346e06f582724147b2e2d442fd27441c7356ac8328094c6  ./tailscale/tailscale_x86_Windows.msi
76ab3e3bf03859d64f559e349ccfd98726cb34382533fde2af2e97627fb7f6d1  ./tailscale/tailscaled_aarch64_arm64_Linux
7cbd9f14863ef3b5e8036d906dcc54d2a9cb62bd27d439fac32dbadf2d7ed1e3  ./tailscale/tailscaled_aarch64_arm64_Linux.upx
3045786fe6191b3d64ae9d2b03b5fffcf080e3cb3073a3c2e8e69e57ea05e2cf  ./tailscale/tailscaled_aarch64_arm64_macOS
7a630edf4c33386463b17fda7b23214b5a342b3464dd5b0fc72f72572f56c9d9  ./tailscale/tailscaled_amd_geode_Linux
e6645688851e4d0bc65b727290e2fd4abc8215f34ad3dfa690b8b902487f1127  ./tailscale/tailscaled_amd_geode_Linux.upx
ad6068dc127e2cbda3c65bbe22df3d084d751badbbe1a74091be5c92ddc0b741  ./tailscale/tailscaled_amd_x86_64_Linux
3c841f39e006a01926b26d6af1b2e7e1192adfb0e7e48e66599696fa20129789  ./tailscale/tailscaled_amd_x86_64_Linux.upx
b5304b43985998d94d5c2c94e0eeb9e160a76906fa0ecb224af45c3b878e684d  ./tailscale/tailscaled_amd_x86_64_macOS
517cdeaa3bb67556a0eb3ea70d2596070edb3ee040ff0650c212005fdc58701f  ./tailscale/tailscaled_arm_abi_Linux
f6c9dfb621eee240fd55de9b9c3d21d7c96fad7de226a48bf1ebabc404d19d22  ./tailscale/tailscaled_arm_abi_Linux.upx
79105e25975c2013bc6332d4799a041b048999cf22e2400db114e1104de3458f  ./tailscale/tailscaled_i386_Linux
132834f4d9931124b3c3c690020d2187987fe9886fad37f6d8893199d4f0a8b7  ./tailscale/tailscaled_i386_Linux.upx
37e8ec134715c52e8cecb0cb459c99a5b5f46e83cb567156744c6b379e282a64  ./tailscale/tailscaled_mips64_Linux
c9b3c43a31cdaeb97b72eb2458349920f4e25be79d38644885028c7f5eb38de7  ./tailscale/tailscaled_mips64le_Linux
5a3a71301385cdad58972d29fd6fba41bd5da2fcde82ab58e1d9e407d6764a00  ./tailscale/tailscaled_mips_Linux
64b82fa32b00c8fe9bdeb1a42e0dc4ba9012197b2285849d97fa852174f8497c  ./tailscale/tailscaled_mips_Linux.upx
7a88529f05ee6cc3bc810e27b6186ae561a8d567cf594993c0a2d13fdfb840fe  ./tailscale/tailscaled_mipsle_Linux
2d5ef6aa6710a128d20d8a8b5492bf491cb2b0e5a89d2667eecf0ddd705d4898  ./tailscale/tailscaled_mipsle_Linux.upx
1f535a5b03adc74ab8412b569317713aabdfa566cfadf853b37aac13acfefa9a  ./tailscale/tailscaled_powerpc64_ppc64_Linux
7bbebb268f08b4604ad140afa8e584a4503abfd1b010c7574694e75f48d4d765  ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
55443d934261aa258cceb5d426598fb32d697421f9cff87b595401e4fa2191e5  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux
04850f78484698187e92a4daca661a62720e997c628cbb61b01547cf6e7ebaa4  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
65d51de5b5db94a0e7065c4232405cd9fc9eeadcde2bbf9570e899ab54ced540  ./tailscale/tailscaled_riscv64_Linux
e8eb108d1356c106620673b17f69f9d8765b7352f395ee2b3f2ac67c54fdd05d  ./tailscale/tailscaled_s390x_Linux
```


---

- #### Sizes

```console
18M   ./tailscale/tailscale_aarch64_arm64_Linux
8.1M  ./tailscale/tailscale_aarch64_arm64_Linux.upx
29M   ./tailscale/tailscale_aarch64_arm64_Windows.msi
11M   ./tailscale/tailscale_aarch64_arm64_macOS
12M   ./tailscale/tailscale_amd_geode_Linux
3.4M  ./tailscale/tailscale_amd_geode_Linux.upx
13M   ./tailscale/tailscale_amd_x86_64_Linux
4.0M  ./tailscale/tailscale_amd_x86_64_Linux.upx
31M   ./tailscale/tailscale_amd_x86_64_Windows.msi
11M   ./tailscale/tailscale_amd_x86_64_macOS
18M   ./tailscale/tailscale_arm_abi_Linux
7.7M  ./tailscale/tailscale_arm_abi_Linux.upx
12M   ./tailscale/tailscale_i386_Linux
3.7M  ./tailscale/tailscale_i386_Linux.upx
44K   ./tailscale/tailscale_ipn_setup_Windows.exe
23M   ./tailscale/tailscale_merged_aarch64_arm64_Linux
5.8M  ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
20M   ./tailscale/tailscale_merged_aarch64_arm64_macOS
24M   ./tailscale/tailscale_merged_amd_x86_64_Linux
7.0M  ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
20M   ./tailscale/tailscale_merged_amd_x86_64_macOS
23M   ./tailscale/tailscale_merged_arm_Linux
5.7M  ./tailscale/tailscale_merged_arm_Linux.upx
23M   ./tailscale/tailscale_merged_i386_Linux
6.6M  ./tailscale/tailscale_merged_i386_Linux.upx
24M   ./tailscale/tailscale_merged_powerpc64_ppc64_Linux
5.7M  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
24M   ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux
5.9M  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
26M   ./tailscale/tailscale_merged_s390x_Linux
20M   ./tailscale/tailscale_mips64_Linux
20M   ./tailscale/tailscale_mips64le_Linux
20M   ./tailscale/tailscale_mips_Linux
7.8M  ./tailscale/tailscale_mips_Linux.upx
19M   ./tailscale/tailscale_mipsle_Linux
7.7M  ./tailscale/tailscale_mipsle_Linux.upx
14M   ./tailscale/tailscale_powerpc64_ppc64_Linux
3.4M  ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
14M   ./tailscale/tailscale_powerpc64le_ppc64le_Linux
3.5M  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
18M   ./tailscale/tailscale_riscv64_Linux
15M   ./tailscale/tailscale_s390x_Linux
51M   ./tailscale/tailscale_setup_Windows.exe
30M   ./tailscale/tailscale_x86_Windows.msi
34M   ./tailscale/tailscaled_aarch64_arm64_Linux
15M   ./tailscale/tailscaled_aarch64_arm64_Linux.upx
19M   ./tailscale/tailscaled_aarch64_arm64_macOS
21M   ./tailscale/tailscaled_amd_geode_Linux
6.1M  ./tailscale/tailscaled_amd_geode_Linux.upx
24M   ./tailscale/tailscaled_amd_x86_64_Linux
7.0M  ./tailscale/tailscaled_amd_x86_64_Linux.upx
19M   ./tailscale/tailscaled_amd_x86_64_macOS
31M   ./tailscale/tailscaled_arm_abi_Linux
13M   ./tailscale/tailscaled_arm_abi_Linux.upx
21M   ./tailscale/tailscaled_i386_Linux
6.1M  ./tailscale/tailscaled_i386_Linux.upx
35M   ./tailscale/tailscaled_mips64_Linux
35M   ./tailscale/tailscaled_mips64le_Linux
34M   ./tailscale/tailscaled_mips_Linux
13M   ./tailscale/tailscaled_mips_Linux.upx
34M   ./tailscale/tailscaled_mipsle_Linux
13M   ./tailscale/tailscaled_mipsle_Linux.upx
23M   ./tailscale/tailscaled_powerpc64_ppc64_Linux
5.5M  ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
23M   ./tailscale/tailscaled_powerpc64le_ppc64le_Linux
5.7M  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
32M   ./tailscale/tailscaled_riscv64_Linux
25M   ./tailscale/tailscaled_s390x_Linux
```

---

- #### UPX
```console

testing ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx [OK]
  24641684 ->   6184448   25.10%  linux/ppc64le  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_aarch64_arm64_Linux.upx [OK]
  18696210 ->   8429944   45.09%   linux/arm64   ./tailscale/tailscale_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_i386_Linux.upx [OK]
  12508756 ->   3824964   30.58%   linux/i386    ./tailscale/tailscale_i386_Linux.upx
testing ./tailscale/tailscaled_amd_x86_64_Linux.upx [OK]
  25158904 ->   7244872   28.80%   linux/amd64   ./tailscale/tailscaled_amd_x86_64_Linux.upx
testing ./tailscale/tailscaled_aarch64_arm64_Linux.upx [OK]
  35491336 ->  15017748   42.31%   linux/arm64   ./tailscale/tailscaled_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_merged_arm_Linux.upx [OK]
  23658644 ->   5892068   24.90%    linux/arm    ./tailscale/tailscale_merged_arm_Linux.upx
testing ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx [OK]
  23658644 ->   5913108   24.99%  linux/ppc64le  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscaled_i386_Linux.upx [OK]
  21844732 ->   6327956   28.97%   linux/i386    ./tailscale/tailscaled_i386_Linux.upx
testing ./tailscale/tailscaled_amd_geode_Linux.upx [OK]
  21877532 ->   6333996   28.95%   linux/i386    ./tailscale/tailscaled_amd_geode_Linux.upx
testing ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx [OK]
  23789716 ->   6063164   25.49%   linux/arm64   ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx [OK]
  13697172 ->   3655460   26.69%  linux/ppc64le  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscaled_arm_abi_Linux.upx [OK]
  31544076 ->  13310964   42.20%    linux/arm    ./tailscale/tailscaled_arm_abi_Linux.upx
testing ./tailscale/tailscaled_mips_Linux.upx [OK]
  35155724 ->  13528072   38.48%   linux/mips    ./tailscale/tailscaled_mips_Linux.upx
testing ./tailscale/tailscale_arm_abi_Linux.upx [OK]
  18180314 ->   8069180   44.38%    linux/arm    ./tailscale/tailscale_arm_abi_Linux.upx
testing ./tailscale/tailscale_amd_geode_Linux.upx [OK]
  12537396 ->   3549964   28.32%   linux/i386    ./tailscale/tailscale_amd_geode_Linux.upx
testing ./tailscale/tailscale_amd_x86_64_Linux.upx [OK]
  13304456 ->   4165788   31.31%   linux/amd64   ./tailscale/tailscale_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_powerpc64_ppc64_Linux.upx [OK]
  13631636 ->   3482884   25.55%   linux/ppc64   ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_merged_i386_Linux.upx [OK]
  23724180 ->   6850364   28.88%   linux/i386    ./tailscale/tailscale_merged_i386_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx [OK]
  24576148 ->   5942088   24.18%   linux/ppc64   ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_merged_amd_x86_64_Linux.upx [OK]
  25133204 ->   7315780   29.11%   linux/amd64   ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
testing ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx [OK]
  23593108 ->   5680736   24.08%   linux/ppc64   ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscaled_mipsle_Linux.upx [OK]
  34979348 ->  13449080   38.45%  linux/mipsel   ./tailscale/tailscaled_mipsle_Linux.upx
testing ./tailscale/tailscale_mips_Linux.upx [OK]
  20025531 ->   8126536   40.58%   linux/mips    ./tailscale/tailscale_mips_Linux.upx
testing ./tailscale/tailscale_mipsle_Linux.upx [OK]
  19918971 ->   8070812   40.52%  linux/mipsel   ./tailscale/tailscale_mipsle_Linux.upx

```

---

- #### Version
```console
$ ./tailscale/tailscale_amd_x86_64_Linux --version
1.80.2
  tailscale commit: 62b8bf6a082c4bea1b9e6ee1962c81c6ee5263d3
  other commit: 3c35ee9872cbeac18fbf544a96e594ab9e9f05a4
  go version: go1.23.5

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
1.80.2
  tailscale commit: 62b8bf6a082c4bea1b9e6ee1962c81c6ee5263d3
  other commit: 3c35ee9872cbeac18fbf544a96e594ab9e9f05a4
  go version: go1.23.5

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


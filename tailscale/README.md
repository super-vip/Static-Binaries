
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
./tailscale/tailscale_aarch64_arm64_Linux:                   ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=ZnkSX4iSDhIw1g3TtENu/jdfq2dYH3aj2ClSzNiw8/nWbYKblpyJmuOYNsbfeD/FbT7Rt3P-pbJIXQKakgF, with debug_info, not stripped
./tailscale/tailscale_aarch64_arm64_Linux.upx:               ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=ZnkSX4iSDhIw1g3TtENu/jdfq2dYH3aj2ClSzNiw8/nWbYKblpyJmuOYNsbfeD/FbT7Rt3P-pbJIXQKakgF, statically linked, no section header
./tailscale/tailscale_aarch64_arm64_Windows.msi:             Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard.WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Arm64;1033, Revision Number: {AC427109-C736-4F0B-839C-B6D31D68BEBE}, Create Time/Date: Wed Feb 12 18:54:47 2025, Last Saved Time/Date: Wed Feb 12 18:54:47 2025, Number of Pages: 500, Number of Words: 2, Name of Creating Application: Windows Installer XML Toolset (), Security: 2
./tailscale/tailscale_aarch64_arm64_macOS:                   Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_amd_geode_Linux:                       ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=5c_bKw4UHiHzIT8Xv4eN/kl6DVSvbCSuETPrL3dUR/mOlwWZASwoNA9p6IyGnm/YnAwtSmTmRMCqyLvUirE, stripped
./tailscale/tailscale_amd_geode_Linux.upx:                   ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=5c_bKw4UHiHzIT8Xv4eN/kl6DVSvbCSuETPrL3dUR/mOlwWZASwoNA9p6IyGnm/YnAwtSmTmRMCqyLvUirE, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Linux:                      ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=UvQUEU49ay_uAeD8kaKx/JRg057gpPdZbyZgP43Ga/RTNfZNrUBhuUb1aDJLg2/tBpK_sASkxjm2MK866mr, stripped
./tailscale/tailscale_amd_x86_64_Linux.upx:                  ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=UvQUEU49ay_uAeD8kaKx/JRg057gpPdZbyZgP43Ga/RTNfZNrUBhuUb1aDJLg2/tBpK_sASkxjm2MK866mr, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Windows.msi:                Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard.WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: x64;1033, Revision Number: {1002A674-BEFE-4A8A-83CD-2FDA49782C71}, Create Time/Date: Wed Feb 12 18:54:16 2025, Last Saved Time/Date: Wed Feb 12 18:54:16 2025, Number of Pages: 500, Number of Words: 2, Name of Creating Application: Windows Installer XML Toolset (), Security: 2
./tailscale/tailscale_amd_x86_64_macOS:                      Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_arm_abi_Linux:                         ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=jGccSkl6FDaubXapcApu/vyetdqLuI_8dOUJS1D8F/MGnVaoCte6Z-1_LwdJMY/goQc6Fg-iGgJ2OtJS1P7, with debug_info, not stripped
./tailscale/tailscale_arm_abi_Linux.upx:                     ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=jGccSkl6FDaubXapcApu/vyetdqLuI_8dOUJS1D8F/MGnVaoCte6Z-1_LwdJMY/goQc6Fg-iGgJ2OtJS1P7, statically linked, no section header
./tailscale/tailscale_i386_Linux:                            ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=DVC79KRgDqJYjrJi1aH9/oahSgjji60Rgc0ei-foI/SsGz6_s3CPo-Y8Iy0Ztw/t14J2qyqgPj7w8hY0B1i, stripped
./tailscale/tailscale_i386_Linux.upx:                        ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=DVC79KRgDqJYjrJi1aH9/oahSgjji60Rgc0ei-foI/SsGz6_s3CPo-Y8Iy0Ztw/t14J2qyqgPj7w8hY0B1i, statically linked, no section header
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
./tailscale/tailscale_mips64_Linux:                          ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=3T8GLNN_LfZ1I-v63HTi/9t2_I_jsrKC293iLKX8j/DfrgykuoNJp_umTKpFh8/Mxu5_zittwq_56sZegz_, with debug_info, not stripped
./tailscale/tailscale_mips64le_Linux:                        ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=7u7mr18oOtq7yYfCDA2F/nf1o2sdbKZ2KBofqZ8qH/2JUo_MDNKUk8XkgFNTBu/uv99M5WWt8ODsmGr3vCw, with debug_info, not stripped
./tailscale/tailscale_mips_Linux:                            ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=IKYDfPRqGsTPplo83Tvy/hJm-of3qOobvDiS02Dw7/CsVudT2DOskA0jQfR3Re/0ARXXWdk3DdysEhqLKvv, with debug_info, not stripped
./tailscale/tailscale_mips_Linux.upx:                        ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=IKYDfPRqGsTPplo83Tvy/hJm-of3qOobvDiS02Dw7/CsVudT2DOskA0jQfR3Re/0ARXXWdk3DdysEhqLKvv, statically linked, no section header
./tailscale/tailscale_mipsle_Linux:                          ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=KO2yegXlylo_cGLDpsrM/3QjaxhWLu_KG2f_7RFMR/Hv-oGlany5jMz29SN2Fu/3K7lVuxPdI1VvO1wTgHO, with debug_info, not stripped
./tailscale/tailscale_mipsle_Linux.upx:                      ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=KO2yegXlylo_cGLDpsrM/3QjaxhWLu_KG2f_7RFMR/Hv-oGlany5jMz29SN2Fu/3K7lVuxPdI1VvO1wTgHO, statically linked, no section header
./tailscale/tailscale_powerpc64_ppc64_Linux:                 ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64_ppc64_Linux.upx:             ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_powerpc64le_ppc64le_Linux:             ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx:         ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_riscv64_Linux:                         ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, Go BuildID=aNPyqZYzjceHuNHX1p1r/Ou8C-KonBOy-VZDnuXKQ/YUDBCF8dMsaejXltwXE-/mRdxWZhZwATjWcIuvYW1, with debug_info, not stripped
./tailscale/tailscale_s390x_Linux:                           ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_setup_Windows.exe:                     PE32 executable (GUI) Intel 80386, for MS Windows, 6 sections
./tailscale/tailscale_x86_Windows.msi:                       Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard.WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Intel;1033, Revision Number: {9D70B63F-43DA-4B9F-A742-5D510D19082D}, Create Time/Date: Wed Feb 12 18:54:40 2025, Last Saved Time/Date: Wed Feb 12 18:54:40 2025, Number of Pages: 500, Number of Words: 2, Name of Creating Application: Windows Installer XML Toolset (), Security: 2
./tailscale/tailscaled_aarch64_arm64_Linux:                  ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=URxseH3x70kHiC5eSmoD/NU7zPEdSwuYNLgZ_Z_E0/b7GB-m_vsVojkhKcLl_C/E6DMmYMABgdTYnq7MA0Z, with debug_info, not stripped
./tailscale/tailscaled_aarch64_arm64_Linux.upx:              ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=URxseH3x70kHiC5eSmoD/NU7zPEdSwuYNLgZ_Z_E0/b7GB-m_vsVojkhKcLl_C/E6DMmYMABgdTYnq7MA0Z, statically linked, no section header
./tailscale/tailscaled_aarch64_arm64_macOS:                  Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_amd_geode_Linux:                      ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=6XKBr2atnONMbGuVAvIx/E2h1uBPIdV4pK62P3-IN/KBX135IZir2DlTot51-p/HFml-7kwptxnZso81yoD, stripped
./tailscale/tailscaled_amd_geode_Linux.upx:                  ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=6XKBr2atnONMbGuVAvIx/E2h1uBPIdV4pK62P3-IN/KBX135IZir2DlTot51-p/HFml-7kwptxnZso81yoD, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_Linux:                     ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=Omz_L4gijqzq_WQco9m-/Dt_pF2vq3Z8z5Xx5RCbD/Egt4rjOGcoMMxTYK4EmM/I79iQweeGjraGQgHmECg, stripped
./tailscale/tailscaled_amd_x86_64_Linux.upx:                 ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=Omz_L4gijqzq_WQco9m-/Dt_pF2vq3Z8z5Xx5RCbD/Egt4rjOGcoMMxTYK4EmM/I79iQweeGjraGQgHmECg, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_macOS:                     Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_arm_abi_Linux:                        ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=sfh25NCRJWYRGiwIt8Zi/Ga_bty1urvUgZZaICn64/duy79VCjY56_c5uZzmec/nZPn-lWnA7aSpWa46x9H, with debug_info, not stripped
./tailscale/tailscaled_arm_abi_Linux.upx:                    ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=sfh25NCRJWYRGiwIt8Zi/Ga_bty1urvUgZZaICn64/duy79VCjY56_c5uZzmec/nZPn-lWnA7aSpWa46x9H, statically linked, no section header
./tailscale/tailscaled_i386_Linux:                           ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=gPvMFjhIBNC42unbtfDO/hRwX83r63fP9Si-g9Slw/5cplXPQlvSiqhocpVUHV/N2W7_aplVPAd2YhBNLW2, stripped
./tailscale/tailscaled_i386_Linux.upx:                       ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=gPvMFjhIBNC42unbtfDO/hRwX83r63fP9Si-g9Slw/5cplXPQlvSiqhocpVUHV/N2W7_aplVPAd2YhBNLW2, statically linked, no section header
./tailscale/tailscaled_mips64_Linux:                         ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=tvW5NUYxsqcWmbdyKGFf/F9NFOajQv_LMcnkBRl6S/aOdVakTJ5_Vbna6n4XYl/m-nUzACUjRMSpAiuNQRe, with debug_info, not stripped
./tailscale/tailscaled_mips64le_Linux:                       ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=9FE5VZA-mdc-P4S788jX/sboHLr53qSau-1QD-0qa/Pq-iMrv90Q4W5FFv9Jpq/W31MZYvWByyhEjMXPMnq, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux:                           ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=XwP4ekWmoiWXAG40GaxH/vXvxLyXExKn3O1z97JtY/DWeduq742D1czuyyKtCl/U23JTJkEwcs4FSwya2tW, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux.upx:                       ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=XwP4ekWmoiWXAG40GaxH/vXvxLyXExKn3O1z97JtY/DWeduq742D1czuyyKtCl/U23JTJkEwcs4FSwya2tW, statically linked, no section header
./tailscale/tailscaled_mipsle_Linux:                         ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=s0iCYTRbmtecfv3ccjOw/DqWSpPwOX5YheF_nh2Dn/ymvgB_4VovB8_2WSztTZ/_0ZKUfMNtvwqLWh4e3KU, with debug_info, not stripped
./tailscale/tailscaled_mipsle_Linux.upx:                     ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=s0iCYTRbmtecfv3ccjOw/DqWSpPwOX5YheF_nh2Dn/ymvgB_4VovB8_2WSztTZ/_0ZKUfMNtvwqLWh4e3KU, statically linked, no section header
./tailscale/tailscaled_powerpc64_ppc64_Linux:                ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64_ppc64_Linux.upx:            ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_powerpc64le_ppc64le_Linux:            ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx:        ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_riscv64_Linux:                        ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, Go BuildID=gHDl4Dbg2x-B-GOrXKNh/PJLYORohqAOVvba7T9hC/YfxVm28gEhi2e7AvscK6/tiBeIxFokcYTcbwm60RN, with debug_info, not stripped
./tailscale/tailscaled_s390x_Linux:                          ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped

--> SHA256SUM
b201616c4fa827e577ebf3450f30fef4e2a67c3037e7ad270bb2877b1d42d147  ./tailscale/tailscale_aarch64_arm64_Linux
09a00f95b0345b9c3f52d3d1f45a7a2e106299777ef286d153e1436a39bbaf29  ./tailscale/tailscale_aarch64_arm64_Linux.upx
991dd6a5301dae186f4d74964909de0d7f802820eeaaf30eb5f8bf190e968003  ./tailscale/tailscale_aarch64_arm64_Windows.msi
758bd296723a348a70f5274b294baeb4053abd2e2ce58e2220e210946b618c6f  ./tailscale/tailscale_aarch64_arm64_macOS
9e101d0058ed2d1c9074b6410ba53ee8f9ddd5504f2479f4c7300c3c3efb8ccc  ./tailscale/tailscale_amd_geode_Linux
f3bf2c6e088ec26883b9941c0c4d2ecc4aabd9627d4564af8c28614ea0d54342  ./tailscale/tailscale_amd_geode_Linux.upx
6b950c4b0a0634d3240acfe3db9278a1c9a2749cc6d755b159c1ac5b1a05d7c4  ./tailscale/tailscale_amd_x86_64_Linux
7a0bc5bbce0c3a1abd0ba3aae80cec3f6a588d43761f2a44da114cec8406e04d  ./tailscale/tailscale_amd_x86_64_Linux.upx
72b0d39adb0c88ccf435875a0a5db6d809230a5f85d1447792d0fe091981beef  ./tailscale/tailscale_amd_x86_64_Windows.msi
248b7930c0c4c650f988bcb90a968da042066e0b826bf58efd8fe3a69fad8e7f  ./tailscale/tailscale_amd_x86_64_macOS
8be18807bb5b667ef821c5c23e6cfd1403087a5fe7ba4ce69c368e2fa8ac8b2c  ./tailscale/tailscale_arm_abi_Linux
4645df1380cdff3c84c43e98cf837c830f39592f260a361baea6cda38eaeaf8a  ./tailscale/tailscale_arm_abi_Linux.upx
b2cdb8d9dbfaf7765e4c2373f253b928cbc5b623fe99001face172e53cc87484  ./tailscale/tailscale_i386_Linux
dafc975c9b065c722793b4bd5ccab7e922ac526921343ec99a0de3307e28ac9f  ./tailscale/tailscale_i386_Linux.upx
9e7e178ff00c42e8d1c52388632435267c71db6f8dd4808931f97ee9f3a4ca9f  ./tailscale/tailscale_ipn_setup_Windows.exe
8800eb6a7913cbec3fafbb5c2f02fbbb0ee10b5e186dc4e5d3dd071aa7a8d532  ./tailscale/tailscale_merged_aarch64_arm64_Linux
dbc64e4d6b7be50f0b12c5c9db643cf3be61170f96341191410d6831ba0154f6  ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
68728bde1313493eb44dbd3be2e989eb00f60f4938d0d2845df9d45e32c25df7  ./tailscale/tailscale_merged_aarch64_arm64_macOS
988149e5e9cbde7c06ab2cc465efbb52b24b27eddea21081c339976d571db168  ./tailscale/tailscale_merged_amd_x86_64_Linux
03fa858f671d1453abfb18eac0489b73ed7fe33a8eae43e36b4ef8b798ace6d9  ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
267bebcfe539dd8353add30caf55a042bf996f8e688aae7910b9ecf61714f3f8  ./tailscale/tailscale_merged_amd_x86_64_macOS
67a400ec6612cfb4b81885441c2e2174e5030f47cba3ce42df83810e3b552407  ./tailscale/tailscale_merged_arm_Linux
1f3cc69d16a34282087e672677ef01986b3458b7a7b753391fe65fc2702aa77d  ./tailscale/tailscale_merged_arm_Linux.upx
a2c1be3c9ea488de7f488870048cd12ef8ff1b43d16e8f6946cb2f4b6777f383  ./tailscale/tailscale_merged_i386_Linux
ef6c33416ca67fd258473446c49d7b63896aa813f57653dbab09adf40c14a132  ./tailscale/tailscale_merged_i386_Linux.upx
3ba77f6579f2ceb165f218ce8331f9992063fc2a2d5b9a254081c999979c1dfb  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux
e4a7b67e02ddfdc83ebcab56bd1ea56eca30640cee34098ba3d6cdf5e9c271c8  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
f145e59a91beb07553ba40fcc9e1c5f89bf1363d23a4efdfcc230751e3db6c4f  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux
873301fe560a0f3b286105c31371042d069c46c9e2b59f4df1360bbcf8d19ada  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
8e0512fa444f95b872e9118efbf841658482978fcc6ff56eadbcbeae69601439  ./tailscale/tailscale_merged_s390x_Linux
85c0c7ed24479aff0ae40427a5981b939916d36bba5103a5ae0217eefebe3e8e  ./tailscale/tailscale_mips64_Linux
2b09351d92d1f00aa64d1c181ccde3444c2ae80563c7b50dc95e923c6a262097  ./tailscale/tailscale_mips64le_Linux
dccf66bc62b9c0f1c9a914b6dd67bd1febae3e97a77d647106759216248fc2ad  ./tailscale/tailscale_mips_Linux
1974be0538caca1af68dc3a0bace81c77891ffadbfc74f96388d6a2a78844c1c  ./tailscale/tailscale_mips_Linux.upx
6262e8c0c756ff963b9846e5ee7e38387e0bdc5ca6e5d3497277a0f0aed84dac  ./tailscale/tailscale_mipsle_Linux
ec5a74b0f70e3f414acc5e3712d5f40d83261a4f085a038ea6f96df313d4c32d  ./tailscale/tailscale_mipsle_Linux.upx
825f1faa4f9fd47f4367591b17b18bb6f6666a6d4967b5ebf1dcb915150a6731  ./tailscale/tailscale_powerpc64_ppc64_Linux
c62ab76d6c0e364b3ca12ec159af626a156e3ce1e2afe20d89685b253408b6c1  ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
202280e79deb154013ef60cb1b28a3cae0d152b8e3843981f026137895ab72fc  ./tailscale/tailscale_powerpc64le_ppc64le_Linux
c0a501fb8c7d6a7f4fd49ec89ee479a4f2c59f0c5eef62434a297f43dec2a9c0  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
0ce2970b7d417068f444ac892391da60dee8c087cb446071b4447a9617064202  ./tailscale/tailscale_riscv64_Linux
ada67398204903f2288c0f2c2ca0bf316e16107df00b8042850606b181b66801  ./tailscale/tailscale_s390x_Linux
64a8ad28cbb67a6171236abe39f75a039a761a0e1aacdef75b26781887cef9a8  ./tailscale/tailscale_setup_Windows.exe
f148ae1043e1c1bb6346e06f582724147b2e2d442fd27441c7356ac8328094c6  ./tailscale/tailscale_x86_Windows.msi
34db4c0476b9348eff4a647db287de29d3b9932eb6c5134413f5c08e3c6fe4c5  ./tailscale/tailscaled_aarch64_arm64_Linux
5a85828de629c9ebc3a9d6a3ad24d6434621681cb0addb13754d111bdcaeeff3  ./tailscale/tailscaled_aarch64_arm64_Linux.upx
3045786fe6191b3d64ae9d2b03b5fffcf080e3cb3073a3c2e8e69e57ea05e2cf  ./tailscale/tailscaled_aarch64_arm64_macOS
a07cca94db2d0f8da57b110cd21bb55371c4fc6383f70265c2aa14aa6d16355b  ./tailscale/tailscaled_amd_geode_Linux
ebce5b2d48ce09c0da86a53857956a629962f4098309856b403ac24d9f782e16  ./tailscale/tailscaled_amd_geode_Linux.upx
ee5e0f7cebb4e05129ea6cd181134495f7abef10b0a9898e0aa50a9c7839146e  ./tailscale/tailscaled_amd_x86_64_Linux
aab40959ca53c2895acb52123c91bd590d6fd9c45f5637cdea59b8a68f5b0472  ./tailscale/tailscaled_amd_x86_64_Linux.upx
b5304b43985998d94d5c2c94e0eeb9e160a76906fa0ecb224af45c3b878e684d  ./tailscale/tailscaled_amd_x86_64_macOS
891c1310286eaa60b49c24d34275478d78e9fd71e93a905a353e2a9deb4b9a02  ./tailscale/tailscaled_arm_abi_Linux
e331a4d3b9ac58a28440fd3ed96d8bb730997b36936b48faf4fc19356cc2f8f6  ./tailscale/tailscaled_arm_abi_Linux.upx
e6c6f379a88a8df3ebaf24d8fa9607f44a140f3b5bfec0dc652338cad9e4bfc7  ./tailscale/tailscaled_i386_Linux
50e1c2630cc984114ac2aea78725551725468474e4a56d124dd6e4baa9bc2766  ./tailscale/tailscaled_i386_Linux.upx
c62b31214a051e3ae1c76e561db35d7880ea5cb4ac00211dd84ab079b2b66cd5  ./tailscale/tailscaled_mips64_Linux
c47b2655256383844407bf8ce5696f3a7053e87e8eafb5b250271b05f8470ad7  ./tailscale/tailscaled_mips64le_Linux
51caa8989f8f8ec5736f9a70f3136937911b21ebdc32a969e73f706d732638a5  ./tailscale/tailscaled_mips_Linux
6d3ae7a85d098046984c0683d2192081dcb8fbddfee157215a2ffd06d261a81d  ./tailscale/tailscaled_mips_Linux.upx
298f081d50856bfa6898bf221f956f74136bf4989466017dd2fb33fed11bf8f1  ./tailscale/tailscaled_mipsle_Linux
547483d319f9ee0a80a63c5708b70ff4d2e3341b544a04d95de9e2e08b82c896  ./tailscale/tailscaled_mipsle_Linux.upx
6a902b50485bff001eaec31edd12eb1838849744f2f26241e5071d5ad182b303  ./tailscale/tailscaled_powerpc64_ppc64_Linux
acf21bc55465304b4324df8bb658b6f5c9918c73ca44e0eead425c1e94370423  ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
f585a1aafc8b5889782a565551c708b13a5a119ce97a20ba67cf367279e42c9a  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux
f0244d362e2e9a464cdf7efbb4ae31c838c7a676de914e920a1b4346c0a60501  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
29f295bf17fba3d12cce86e5354dc27e990d70fd82bea2a156ea1ca66e2d8c4a  ./tailscale/tailscaled_riscv64_Linux
e9cac644871c5e53110310bd9cfd648e9c9268135c9d7c1a4f00eaa0f4334232  ./tailscale/tailscaled_s390x_Linux
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
3.4M  ./tailscale/tailscale_i386_Linux.upx
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
6.0M  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
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
5.6M  ./tailscale/tailscaled_i386_Linux.upx
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
  24641684 ->   6187428   25.11%  linux/ppc64le  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_aarch64_arm64_Linux.upx [OK]
  18678930 ->   8422624   45.09%   linux/arm64   ./tailscale/tailscale_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_i386_Linux.upx [OK]
  12508756 ->   3542676   28.32%   linux/i386    ./tailscale/tailscale_i386_Linux.upx
testing ./tailscale/tailscaled_amd_x86_64_Linux.upx [OK]
  25158904 ->   7242336   28.79%   linux/amd64   ./tailscale/tailscaled_amd_x86_64_Linux.upx
testing ./tailscale/tailscaled_aarch64_arm64_Linux.upx [OK]
  35487485 ->  15016128   42.31%   linux/arm64   ./tailscale/tailscaled_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_merged_arm_Linux.upx [OK]
  23593108 ->   5893496   24.98%    linux/arm    ./tailscale/tailscale_merged_arm_Linux.upx
testing ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx [OK]
  23658644 ->   5916116   25.01%  linux/ppc64le  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscaled_i386_Linux.upx [OK]
  21844732 ->   5804424   26.57%   linux/i386    ./tailscale/tailscaled_i386_Linux.upx
testing ./tailscale/tailscaled_amd_geode_Linux.upx [OK]
  21881628 ->   6336364   28.96%   linux/i386    ./tailscale/tailscaled_amd_geode_Linux.upx
testing ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx [OK]
  23789716 ->   6063676   25.49%   linux/arm64   ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx [OK]
  13697172 ->   3655564   26.69%  linux/ppc64le  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscaled_arm_abi_Linux.upx [OK]
  31543597 ->  13306012   42.18%    linux/arm    ./tailscale/tailscaled_arm_abi_Linux.upx
testing ./tailscale/tailscaled_mips_Linux.upx [OK]
  35155185 ->  13528472   38.48%   linux/mips    ./tailscale/tailscaled_mips_Linux.upx
testing ./tailscale/tailscale_arm_abi_Linux.upx [OK]
  18180446 ->   8070660   44.39%    linux/arm    ./tailscale/tailscale_arm_abi_Linux.upx
testing ./tailscale/tailscale_amd_geode_Linux.upx [OK]
  12537396 ->   3548604   28.30%   linux/i386    ./tailscale/tailscale_amd_geode_Linux.upx
testing ./tailscale/tailscale_amd_x86_64_Linux.upx [OK]
  13304456 ->   4166092   31.31%   linux/amd64   ./tailscale/tailscale_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_powerpc64_ppc64_Linux.upx [OK]
  13631636 ->   3481696   25.54%   linux/ppc64   ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_merged_i386_Linux.upx [OK]
  23724180 ->   6850096   28.87%   linux/i386    ./tailscale/tailscale_merged_i386_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx [OK]
  24576148 ->   5942096   24.18%   linux/ppc64   ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_merged_amd_x86_64_Linux.upx [OK]
  25137300 ->   7318556   29.11%   linux/amd64   ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
testing ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx [OK]
  23593108 ->   5684024   24.09%   linux/ppc64   ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscaled_mipsle_Linux.upx [OK]
  34979685 ->  13451480   38.46%  linux/mipsel   ./tailscale/tailscaled_mipsle_Linux.upx
testing ./tailscale/tailscale_mips_Linux.upx [OK]
  20025295 ->   8125984   40.58%   linux/mips    ./tailscale/tailscale_mips_Linux.upx
testing ./tailscale/tailscale_mipsle_Linux.upx [OK]
  19918871 ->   8069812   40.51%  linux/mipsel   ./tailscale/tailscale_mipsle_Linux.upx

```

---

- #### Version
```console
$ ./tailscale/tailscale_amd_x86_64_Linux --version
1.80.3
  tailscale commit: b107adf2b69868e710d109a0a6992c00790b6e8e
  other commit: 9497b39a50d6db0e3e14d8856d22372c91b9953b
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
1.80.3
  tailscale commit: b107adf2b69868e710d109a0a6992c00790b6e8e
  other commit: 9497b39a50d6db0e3e14d8856d22372c91b9953b
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



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
./tailscale/tailscale_aarch64_arm64_Linux:                   ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=tHnvkEhIuOFIgEjoD7G7/P4JOPwSTp_ASL_88oktG/M5KN8RYnARZfYxW3nAkL/PsCMzkqgWiJsGmJWYjka, BuildID[sha1]=06345e1b5e6232ff0d30e6acd0f16f80f3938e15, with debug_info, not stripped
./tailscale/tailscale_aarch64_arm64_Linux.upx:               ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=tHnvkEhIuOFIgEjoD7G7/P4JOPwSTp_ASL_88oktG/M5KN8RYnARZfYxW3nAkL/PsCMzkqgWiJsGmJWYjka, statically linked, no section header
./tailscale/tailscale_aarch64_arm64_Windows.msi:             Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Arm64;1033, Revision Number: {9B8D0BE6-A64F-4E8B-8474-8F27A4A8E7A4}, Create Time/Date: Thu May 28 22:37:03 2026, Last Saved Time/Date: Thu May 28 22:37:03 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscale_aarch64_arm64_macOS:                   Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_amd_geode_Linux:                       ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=3c96BvtIZ4zbYV9y8DGf/p6rhoLw5ijX4L-ZHY7Dh/sjEsVMLj32o3DnAnWUwk/YtiqD5tFmpSXOP1cSKzi, BuildID[sha1]=bffe93377404147a461da7a003cbfde378eb99a4, stripped
./tailscale/tailscale_amd_geode_Linux.upx:                   ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=3c96BvtIZ4zbYV9y8DGf/p6rhoLw5ijX4L-ZHY7Dh/sjEsVMLj32o3DnAnWUwk/YtiqD5tFmpSXOP1cSKzi, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Linux:                      ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=ZADtHOFrAENMH0jGDxVL/mg6L0my-_kA2dQqDJHbc/G2dFMeHd-SrjL0JxTa_j/j56THX5tu_0ZDCzWrDEX, BuildID[sha1]=77bd6fbb08df38ed593e4d2ff45730a2374e68f5, stripped
./tailscale/tailscale_amd_x86_64_Linux.upx:                  ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=ZADtHOFrAENMH0jGDxVL/mg6L0my-_kA2dQqDJHbc/G2dFMeHd-SrjL0JxTa_j/j56THX5tu_0ZDCzWrDEX, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Windows.msi:                Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: x64;1033, Revision Number: {57FEA46F-D214-48C6-9BED-539EF74BA2D4}, Create Time/Date: Thu May 28 22:35:09 2026, Last Saved Time/Date: Thu May 28 22:35:09 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscale_amd_x86_64_macOS:                      Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_arm_abi_Linux:                         ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=P-YV4F-ER7HJxYNxKe-G/sBcqHT8USpzApy_qoCJq/d6J3IX2BFgmGg4G-sovY/WXiqRWIzgc8BA4yrKpGk, BuildID[sha1]=80ff12f87836a932755da1355b1b0246e4da64bf, with debug_info, not stripped
./tailscale/tailscale_arm_abi_Linux.upx:                     ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=P-YV4F-ER7HJxYNxKe-G/sBcqHT8USpzApy_qoCJq/d6J3IX2BFgmGg4G-sovY/WXiqRWIzgc8BA4yrKpGk, statically linked, no section header
./tailscale/tailscale_i386_Linux:                            ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=A6ej3BOMAsOucl6AEv2Z/tg_hzfwbC74GHjKe-b0f/01eTIP0rAR5M8Vltdbcz/A7jBuPwG__aaf559feYC, BuildID[sha1]=8ea026bd47c0564f945f025f211f1376978824a1, stripped
./tailscale/tailscale_i386_Linux.upx:                        ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=A6ej3BOMAsOucl6AEv2Z/tg_hzfwbC74GHjKe-b0f/01eTIP0rAR5M8Vltdbcz/A7jBuPwG__aaf559feYC, statically linked, no section header
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
./tailscale/tailscale_mips64_Linux:                          ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=FTdnuuoBE3gliMDZPtAH/2i-1aUPZtpQn_lEnkKPR/1nlsAFSo-nwjvkdGr8EW/uA7BAHNCKcJKmmcKclDs, BuildID[sha1]=cf4a20769c72efae25831c82e2a552ccac523d21, with debug_info, not stripped
./tailscale/tailscale_mips64le_Linux:                        ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=PmHRBLIZmYeW9T-q9DUQ/yKVG_uv7ZAxQCivVo6LP/qXGo4NvYB9305_pkto1i/wQaBRixCJOAuZQ-TMkAR, BuildID[sha1]=8bc2ce6cb3757149eb118b88b559a92402edbee6, with debug_info, not stripped
./tailscale/tailscale_mips_Linux:                            ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=CRdkItT-c6uWxfd_jVQl/8NK-3uJtL94owi1z03nM/WCUlrEBAE08eLRUwcfYA/lqiiUT6eNn48CkhNw9qq, BuildID[sha1]=4c573bcdc6c019be63f883204c9c7c9064327230, with debug_info, not stripped
./tailscale/tailscale_mips_Linux.upx:                        ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=CRdkItT-c6uWxfd_jVQl/8NK-3uJtL94owi1z03nM/WCUlrEBAE08eLRUwcfYA/lqiiUT6eNn48CkhNw9qq, statically linked, no section header
./tailscale/tailscale_mipsle_Linux:                          ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=vHF8ilLlJ0LgqOKQ9jA7/YHyfAwdptiu9KIKr9b77/_261DcEY72WptmPJ8jhh/NkPp8iT4nIQxUFFgff1S, BuildID[sha1]=270da1b8b542bf0072d7bde81daa9e6c95e6c3dc, with debug_info, not stripped
./tailscale/tailscale_mipsle_Linux.upx:                      ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=vHF8ilLlJ0LgqOKQ9jA7/YHyfAwdptiu9KIKr9b77/_261DcEY72WptmPJ8jhh/NkPp8iT4nIQxUFFgff1S, statically linked, no section header
./tailscale/tailscale_powerpc64_ppc64_Linux:                 ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64_ppc64_Linux.upx:             ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_powerpc64le_ppc64le_Linux:             ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx:         ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_riscv64_Linux:                         ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, Go BuildID=QZHCKASjr11KUHYNJM8f/dQez0HvwuZaQvyBKEx6f/RChD8ywOUnjcCZiwm0y5/GNhJ43BOWxO2_zMie-88, BuildID[sha1]=5d61dc71699e3bd1d10121d835cac8d34b50f8d0, with debug_info, not stripped
./tailscale/tailscale_s390x_Linux:                           ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_setup_Windows.exe:                     PE32 executable (GUI) Intel 80386, for MS Windows, 6 sections
./tailscale/tailscale_x86_Windows.msi:                       Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Intel;1033, Revision Number: {60056218-BE75-4EBC-BB09-8BB45D57338D}, Create Time/Date: Thu May 28 22:37:03 2026, Last Saved Time/Date: Thu May 28 22:37:03 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscaled_aarch64_arm64_Linux:                  ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=Qmyd9Mc01P4b6xxb2qoj/vFIcEnKZi8MQnTIe2gpO/OqlVeC_x11PApOLg3qnj/Pe7vbBuohv1-OB8OtMEr, BuildID[sha1]=b076ac798dac6871de126e0c6fa7c8eb8c6fc945, with debug_info, not stripped
./tailscale/tailscaled_aarch64_arm64_Linux.upx:              ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=Qmyd9Mc01P4b6xxb2qoj/vFIcEnKZi8MQnTIe2gpO/OqlVeC_x11PApOLg3qnj/Pe7vbBuohv1-OB8OtMEr, statically linked, no section header
./tailscale/tailscaled_aarch64_arm64_macOS:                  Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_amd_geode_Linux:                      ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=2nCXa1i6zxp-Vh0OtpyX/sfhAIDl8_13pUXOcD880/eQ2iuwSsitNc4JnFTgIT/ZyzHoc5L7C2NMPiTUHYW, BuildID[sha1]=e6982c74bb1608cea88e13c7f608d46e090c362c, stripped
./tailscale/tailscaled_amd_geode_Linux.upx:                  ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=2nCXa1i6zxp-Vh0OtpyX/sfhAIDl8_13pUXOcD880/eQ2iuwSsitNc4JnFTgIT/ZyzHoc5L7C2NMPiTUHYW, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_Linux:                     ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=l1Cyj0ygKggFFUw5zf5n/LXFSWJCKpyjSWffisWLy/-K8K_YORbJVjc8cRoZfx/zhi_QViIxOT2qLNM1-Qm, BuildID[sha1]=ac0fa89564a776374847b6c453621547d6b1b5bc, stripped
./tailscale/tailscaled_amd_x86_64_Linux.upx:                 ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=l1Cyj0ygKggFFUw5zf5n/LXFSWJCKpyjSWffisWLy/-K8K_YORbJVjc8cRoZfx/zhi_QViIxOT2qLNM1-Qm, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_macOS:                     Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_arm_abi_Linux:                        ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=EPphS2j8irFfRHQT5cf3/tiiwytca3myagT7Ed74k/U3JXM-XArnfQK150uw0j/FRyqOB_gf6fKUerlC4C0, BuildID[sha1]=2e8ad367e7a22bc457e218c4c79fd982ac8e34f2, with debug_info, not stripped
./tailscale/tailscaled_arm_abi_Linux.upx:                    ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=EPphS2j8irFfRHQT5cf3/tiiwytca3myagT7Ed74k/U3JXM-XArnfQK150uw0j/FRyqOB_gf6fKUerlC4C0, statically linked, no section header
./tailscale/tailscaled_i386_Linux:                           ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=NHKSjc0DdBHtSAB_DcAH/GKj1YkcoEMhWEFdw0d12/1J6chuTsBi8D2nXUbMlK/-2euaTWHvDaqs-kqHall, BuildID[sha1]=eaa8f86492a0e7193cfae7dbd96254bf24a4b3b9, stripped
./tailscale/tailscaled_i386_Linux.upx:                       ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=NHKSjc0DdBHtSAB_DcAH/GKj1YkcoEMhWEFdw0d12/1J6chuTsBi8D2nXUbMlK/-2euaTWHvDaqs-kqHall, statically linked, no section header
./tailscale/tailscaled_mips64_Linux:                         ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=wkXmwh-0eSIUfgdSnmLf/blnmkPwwp0Thcaqklkro/SeuRvF4MFeQy8QGcCKVI/w7f736vZRGqxYVi_NN_M, BuildID[sha1]=9d0d77a3e5f556913c00f4c13c0729d2ec382097, with debug_info, not stripped
./tailscale/tailscaled_mips64le_Linux:                       ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=sKw8YGWt86UZxxdkt4fC/vIgogHdz08ndKiA7fYDM/hKdyIfw7Lg_fI_2jB1U3/eAUwdPjk46fDKAJWVMzj, BuildID[sha1]=b6c3a26ba08ae3f6ceac9420686138295e8e6469, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux:                           ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=isXCVMFaJ3dficjOp57v/1M_IlKDkf_nDRNim6X4v/0F50AnNwHZZg39OOazjN/wx9w92TAag4MnMrcO0XT, BuildID[sha1]=b9ea631db8349f69695f58966d138b11af2a85d4, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux.upx:                       ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=isXCVMFaJ3dficjOp57v/1M_IlKDkf_nDRNim6X4v/0F50AnNwHZZg39OOazjN/wx9w92TAag4MnMrcO0XT, statically linked, no section header
./tailscale/tailscaled_mipsle_Linux:                         ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=DYlqfVqL0jdP3QMYV_WZ/4iK5nsV1vQlcghbmunX4/h0lNZku-7dylB5WbJ-W3/Dnw2nyjvbBo1jvtGbU2-, BuildID[sha1]=7c7fb94f14567ba580e56c542133e9e030ab19ae, with debug_info, not stripped
./tailscale/tailscaled_mipsle_Linux.upx:                     ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=DYlqfVqL0jdP3QMYV_WZ/4iK5nsV1vQlcghbmunX4/h0lNZku-7dylB5WbJ-W3/Dnw2nyjvbBo1jvtGbU2-, statically linked, no section header
./tailscale/tailscaled_powerpc64_ppc64_Linux:                ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64_ppc64_Linux.upx:            ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_powerpc64le_ppc64le_Linux:            ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx:        ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_riscv64_Linux:                        ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, Go BuildID=Z05RKmucQlspBfiajWZx/65P-2zvwjnFwluJh3_IZ/zqkkYQxh6glm-dL4QScE/zuT-xiiB08RF3gAH7DWh, BuildID[sha1]=0cc563cd89d108fa50c9ed65717d493e46736802, with debug_info, not stripped
./tailscale/tailscaled_s390x_Linux:                          ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped

--> SHA256SUM
95c92aa6a174294eb82f1301ccb2a4812077f96883a2f56e6ed2ebc7f0162903  ./tailscale/tailscale_aarch64_arm64_Linux
7ccce4947bfdcb92e5fef1f3adabd43e8d1e2faab120392062f447748af8f7f3  ./tailscale/tailscale_aarch64_arm64_Linux.upx
1005335109e43a430fa8ebc0e598270cb77da5fe356b52b1ea476dc8e5db7d94  ./tailscale/tailscale_aarch64_arm64_Windows.msi
758bd296723a348a70f5274b294baeb4053abd2e2ce58e2220e210946b618c6f  ./tailscale/tailscale_aarch64_arm64_macOS
b152e5aa54487f3100bc16d91a987121d19b5241525cdc7c689372549ab58d81  ./tailscale/tailscale_amd_geode_Linux
c36f7374b939cda97559fdc4919d2f8be3900566b1ee499a4ed0ea8ee48594e6  ./tailscale/tailscale_amd_geode_Linux.upx
5c8e0b24beca61bc8548770a7e20098d9c1532753981741f7d1e7181377e4041  ./tailscale/tailscale_amd_x86_64_Linux
5ec4b121c09e1c49db167c0ea3b535a97050473bd90eae090d5efe693416d441  ./tailscale/tailscale_amd_x86_64_Linux.upx
95fa8601a7195411f5d0685bb650f239b2831d9939456c8d3ae8e286c85b1746  ./tailscale/tailscale_amd_x86_64_Windows.msi
248b7930c0c4c650f988bcb90a968da042066e0b826bf58efd8fe3a69fad8e7f  ./tailscale/tailscale_amd_x86_64_macOS
289d4822d3e4ad021e0ff8a7742af094df14661797e937e085790b9c097fb540  ./tailscale/tailscale_arm_abi_Linux
2a3b7a76665c780526e99eb82a6b90502bc2ccb8e0842c0ee24bcbbfb3e85f7b  ./tailscale/tailscale_arm_abi_Linux.upx
fb806c432df3bd2ac6efbc0b767784117b3582de417703655bdeac137fbeb2ac  ./tailscale/tailscale_i386_Linux
a08c480f15e23f9304e079dc96c014f31136ab57452e2814abf6c912cd5dae09  ./tailscale/tailscale_i386_Linux.upx
44203ce8f7e625ec2883501ca3404a239ec5bf2ecb2da5e6c5b2116f17aa48b8  ./tailscale/tailscale_ipn_setup_Windows.exe
b6cf3df320b4799d6461eee2db64d9c0d0c79009c22611dd72f74b1815a9b7bd  ./tailscale/tailscale_merged_aarch64_arm64_Linux
1d9af16de2ee804ce071bd1720b8ef1d38b8fedc636e27af8c8c4b82f19177ca  ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
68728bde1313493eb44dbd3be2e989eb00f60f4938d0d2845df9d45e32c25df7  ./tailscale/tailscale_merged_aarch64_arm64_macOS
19bc484e8b88a49eeef6e5d08ed5995ca957884cb1613406a72e05c5c5053140  ./tailscale/tailscale_merged_amd_x86_64_Linux
112914be37a5f7cfc7b2463cd99ac16c64e1746bbfb9a60774a92819f80ee0e7  ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
267bebcfe539dd8353add30caf55a042bf996f8e688aae7910b9ecf61714f3f8  ./tailscale/tailscale_merged_amd_x86_64_macOS
40434f2294cc3ec7bd6fcdee661847d941c48a155e031e26728b4f8e57c1fb6a  ./tailscale/tailscale_merged_arm_Linux
60b1f52fc8a80502f695c698f16fb4ebe52b72807781619bcbc01ba02a865940  ./tailscale/tailscale_merged_arm_Linux.upx
fc36973efeec297940d95ec0bb187f765ed4889cab79f46f844feadb24724cc7  ./tailscale/tailscale_merged_i386_Linux
2f32b962a780200926d683a591c7d05e4376095c9cc0ca44d48dd83ea5496335  ./tailscale/tailscale_merged_i386_Linux.upx
4b6bb4ba1e1df759c2a35a7e2ad775f93e0af2aa95a50bc914e09da1e245500b  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux
a25821e2c483912ac577ecff6add9166576e47e16f29b6df7d6e13b4462a3d92  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
41b62576ab63e246e38e19127107ced9478842c800a9f82bcff76aaf93ce9cc4  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux
497434c2c83ddadc892651ba2829dbd25cf56a1453d16d052efb6683bd124f41  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
580287925ac38e3aa27a1cf068162e9d577a46d8f490f324db4cc6555fcd7863  ./tailscale/tailscale_merged_s390x_Linux
d581b861a37752ce263229d889fbe24b772805cb6fd59ff17cd9d4f8346adbd3  ./tailscale/tailscale_mips64_Linux
52b4065f3165452b92f6a77d3c7e9669b87e20a5bba4616e8237bd42c8a1b523  ./tailscale/tailscale_mips64le_Linux
eea3bbde8b93b6b93e3477a88afeaa1c4930c25111450ab0cc897325b4fa13de  ./tailscale/tailscale_mips_Linux
0dcbdaf5f0dcf988a9f138b88920f3c3a348759815da5ebd6b1171be1ca87db5  ./tailscale/tailscale_mips_Linux.upx
eb033ad35cad132aa1ededf2ee5eeb3cdb37443edbaec8141a6fb5be9af55bdb  ./tailscale/tailscale_mipsle_Linux
fccc19e310f4b5e48c28f40139b391f061b580d69254d18e417edbf19d28289d  ./tailscale/tailscale_mipsle_Linux.upx
329da0672036c18cbec12feaca359d4b14423eed1cfc8183fbee2f9bbb0363d7  ./tailscale/tailscale_powerpc64_ppc64_Linux
77bf57d2897b1da674f0f2ac6feefdf0d39663078c7ed3526338053cdeca94f2  ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
05e41ae600ebf2d3ee0bcfdd87128cd9568204e5516aebf836b895233430ccf5  ./tailscale/tailscale_powerpc64le_ppc64le_Linux
ada1e67ba1e7371d85f6353710a9cf1107956a559840a35b219eae92415315c8  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
37eef4df13426d8a9180834283e3dcc16056e39e81738e918095f0b250671e0d  ./tailscale/tailscale_riscv64_Linux
5cd78a478c58e22c66921450ac419c78576dac8d69014517156a48c2b0b65f74  ./tailscale/tailscale_s390x_Linux
64a8ad28cbb67a6171236abe39f75a039a761a0e1aacdef75b26781887cef9a8  ./tailscale/tailscale_setup_Windows.exe
42ab5af3a91a7d8f23c0dcf3f022a890e9489cc2412c747686cd460838f50e13  ./tailscale/tailscale_x86_Windows.msi
c659d5148ce1c736cdc35fcbee8541728e72ba8ba7a2d8c0fa933356c2cc27d4  ./tailscale/tailscaled_aarch64_arm64_Linux
1591f99dae59ada4a227fa1f3ba4d252db7d44a45e030a02fc047eb65439698e  ./tailscale/tailscaled_aarch64_arm64_Linux.upx
3045786fe6191b3d64ae9d2b03b5fffcf080e3cb3073a3c2e8e69e57ea05e2cf  ./tailscale/tailscaled_aarch64_arm64_macOS
d1a2aaa243f25d42377e7f1838a9ca51052692c3a84ac5af881bc2534e82efb9  ./tailscale/tailscaled_amd_geode_Linux
effe26bdcc9a58b8d931b2933bbf531d12c59591ad5b682f669a71718a4820b0  ./tailscale/tailscaled_amd_geode_Linux.upx
d2b18b25dbcd85fc1e120f3053075dfceb817876357a6f20f7a5228be57b79ff  ./tailscale/tailscaled_amd_x86_64_Linux
563336621c68ea1f12379fcbc75a8e003a984c7372bdded2b650cb6334c6185c  ./tailscale/tailscaled_amd_x86_64_Linux.upx
b5304b43985998d94d5c2c94e0eeb9e160a76906fa0ecb224af45c3b878e684d  ./tailscale/tailscaled_amd_x86_64_macOS
a14c4db5803348d56882b7825c62b0946b8219073c429cb9d46b82ab037ed9d0  ./tailscale/tailscaled_arm_abi_Linux
73b8d92aae7ed4daa303d54397c27213f3bc9d6d3ef8cb74fdd36c88fb17d76d  ./tailscale/tailscaled_arm_abi_Linux.upx
c4752ae168ff3ccd2cf14f0fbe764fe8831471f1deef372cafc77845b59e887b  ./tailscale/tailscaled_i386_Linux
693e2ab81063c668a21a0652c108c946fe946a26fbdc017dbf362fd12a9e3b12  ./tailscale/tailscaled_i386_Linux.upx
87aca58699fcaa733481613ecb72b43f0a79021caf8d982c065286c33f632434  ./tailscale/tailscaled_mips64_Linux
fe4dbc045d2888eb7f4e838dbb0d9e1d16c91536b94b2f504b7f5b666c20b7d8  ./tailscale/tailscaled_mips64le_Linux
89471b3a3e6342f44cd70cf711a74f25aaa2bce27cc39805d3c29ceec8451123  ./tailscale/tailscaled_mips_Linux
2668e0a73333c1575f73dfd6d0002cc42d52c74337733e9456b845fc8d8798d7  ./tailscale/tailscaled_mips_Linux.upx
60ae1b51b734040c2a9bdcc6eb33612b61424287403c25ba92bfb5807b609b7c  ./tailscale/tailscaled_mipsle_Linux
30661586ad4ed101eaae7913db15d86b2832031f13696fefde2fba07853e8f19  ./tailscale/tailscaled_mipsle_Linux.upx
d8021686e48abb2d74ff3f5a1c94a6d62a09bd10772e87838d4f1a498d5e75d1  ./tailscale/tailscaled_powerpc64_ppc64_Linux
378ad4470d5565d08a79454cdb0202ea0777ac69eae96987b17f2acc01d99803  ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
648d45d8e3236863187bb8217467e900efa6c78548538850b808e0dc13362f48  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux
efc1a58699c23798d2fe10357b77de9eea60485308b98fc5bc7c46461440fe7f  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
c478a0e1c5249005b31a49b84f9f2fd372717d077e509dfbbc765b9e1a21b099  ./tailscale/tailscaled_riscv64_Linux
78bbca28393a65a4c77883b29d36d8f6ad9f3ecf366ab27e7f2b5591a15e4f7b  ./tailscale/tailscaled_s390x_Linux
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

testing ./tailscale/tailscaled_mips_Linux.upx [OK]
  39036115 ->  14683392   37.61%   linux/mips    ./tailscale/tailscaled_mips_Linux.upx
testing ./tailscale/tailscale_arm_abi_Linux.upx [OK]
  29259794 ->  11844864   40.48%    linux/arm    ./tailscale/tailscale_arm_abi_Linux.upx
testing ./tailscale/tailscale_merged_i386_Linux.upx [OK]
  34394238 ->   9145240   26.59%   linux/i386    ./tailscale/tailscale_merged_i386_Linux.upx
testing ./tailscale/tailscale_amd_x86_64_Linux.upx [OK]
  22278248 ->   6207460   27.86%   linux/amd64   ./tailscale/tailscale_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_mips_Linux.upx [OK]
  32392606 ->  11949956   36.89%   linux/mips    ./tailscale/tailscale_mips_Linux.upx
testing ./tailscale/tailscaled_mipsle_Linux.upx [OK]
  38869047 ->  14651852   37.70%  linux/mipsel   ./tailscale/tailscaled_mipsle_Linux.upx
testing ./tailscale/tailscale_merged_amd_x86_64_Linux.upx [OK]
  36733054 ->   9794096   26.66%   linux/amd64   ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_powerpc64_ppc64_Linux.upx [OK]
  21364862 ->   4980236   23.31%   linux/ppc64   ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx [OK]
  21364862 ->   5191544   24.30%  linux/ppc64le  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_i386_Linux.upx [OK]
  20718468 ->   5776252   27.88%   linux/i386    ./tailscale/tailscale_i386_Linux.upx
testing ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx [OK]
  34078846 ->   8022656   23.54%   linux/arm64   ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
testing ./tailscale/tailscaled_amd_x86_64_Linux.upx [OK]
  28590232 ->   8013296   28.03%   linux/amd64   ./tailscale/tailscaled_amd_x86_64_Linux.upx
testing ./tailscale/tailscaled_amd_geode_Linux.upx [OK]
  24736140 ->   7093424   28.68%   linux/i386    ./tailscale/tailscaled_amd_geode_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx [OK]
  35913854 ->   8265936   23.02%  linux/ppc64le  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_merged_arm_Linux.upx [OK]
  33882238 ->   7833156   23.12%    linux/arm    ./tailscale/tailscale_merged_arm_Linux.upx
testing ./tailscale/tailscaled_i386_Linux.upx [OK]
  24699276 ->   7085816   28.69%   linux/i386    ./tailscale/tailscaled_i386_Linux.upx
testing ./tailscale/tailscale_aarch64_arm64_Linux.upx [OK]
  29579212 ->  12088080   40.87%   linux/arm64   ./tailscale/tailscale_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_mipsle_Linux.upx [OK]
  32243494 ->  11916444   36.96%  linux/mipsel   ./tailscale/tailscale_mipsle_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx [OK]
  35913854 ->   7972888   22.20%   linux/ppc64   ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscaled_arm_abi_Linux.upx [OK]
  35041119 ->  14515084   41.42%    linux/arm    ./tailscale/tailscaled_arm_abi_Linux.upx
testing ./tailscale/tailscaled_aarch64_arm64_Linux.upx [OK]
  38489596 ->  15817248   41.09%   linux/arm64   ./tailscale/tailscaled_aarch64_arm64_Linux.upx
testing ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx [OK]
  25690238 ->   6393776   24.89%  linux/ppc64le  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx [OK]
  25690238 ->   6157864   23.97%   linux/ppc64   ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_amd_geode_Linux.upx [OK]
  20771716 ->   5319628   25.61%   linux/i386    ./tailscale/tailscale_amd_geode_Linux.upx

```

---

- #### Version
```console
$ ./tailscale/tailscale_amd_x86_64_Linux --version
1.98.4
  tailscale commit: 9e69045b291a7cb1edc714442d68e83b95d05e6b
  long version: 1.98.4-t9e69045b2-ged3a62f14
  other commit: ed3a62f143dd73c8aae368d9c639ea49de878f9b
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
1.98.4
  tailscale commit: 9e69045b291a7cb1edc714442d68e83b95d05e6b
  long version: 1.98.4-t9e69045b2-ged3a62f14
  other commit: ed3a62f143dd73c8aae368d9c639ea49de878f9b
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


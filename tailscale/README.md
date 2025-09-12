
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
./tailscale/tailscale_aarch64_arm64_Linux:                   ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, BuildID[sha1]=50823823b7c50714fbbfbda685e53cb03ec13a9e, with debug_info, not stripped
./tailscale/tailscale_aarch64_arm64_Linux.upx:               ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=t7empvEqDSxFo0jZ11pr/gIyG5D0q2gw_217HrQHP/x2PEyfnpG_9Wyvy_bihE/Ke4UHkQnunFd3k0VAxH7, statically linked, no section header
./tailscale/tailscale_aarch64_arm64_Windows.msi:             Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Arm64;1033, Revision Number: {0D464D1F-EC4A-401C-9002-5730CE183CDF}, Create Time/Date: Thu Sep 11 20:43:18 2025, Last Saved Time/Date: Thu Sep 11 20:43:18 2025, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscale_aarch64_arm64_macOS:                   Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_amd_geode_Linux:                       ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, BuildID[sha1]=b442924e22d84e8c6b48cbe5117cb8c7fb635dd6, stripped
./tailscale/tailscale_amd_geode_Linux.upx:                   ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=77mhMFKb-0mgOOHhgw4A/APKlwr4OqQdDAcKl6xX6/lkpPy7pj8QnD4nUmI-rT/sPNCYjiywRowrCkPGQ4L, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Linux:                      ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, BuildID[sha1]=e4863192bdf82ad3876cbb2bb01bf15a12ecdf99, stripped
./tailscale/tailscale_amd_x86_64_Linux.upx:                  ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=01YUX4Ghl11M_uFRMnpR/bU1YNg8kXDF_smFyt-5k/WvnybAmsYHh4igQ_NhPl/ohUpVnF6D0M07Uetw1w1, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Windows.msi:                Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: x64;1033, Revision Number: {F4540D1E-1FBC-4C2B-A716-E03BCDAC4F83}, Create Time/Date: Thu Sep 11 20:43:18 2025, Last Saved Time/Date: Thu Sep 11 20:43:18 2025, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscale_amd_x86_64_macOS:                      Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_arm_abi_Linux:                         ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, BuildID[sha1]=1aa36379d906885f1e3d4bdf95362a509e808fb7, with debug_info, not stripped
./tailscale/tailscale_arm_abi_Linux.upx:                     ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=XXjf61guQjj7YNpvQk4O/5rCF8dvWXnjacFWfd0x5/sKkKJEjaK9Je3VrMypoD/GZO6IJX97vy26s7bmOVL, statically linked, no section header
./tailscale/tailscale_i386_Linux:                            ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, BuildID[sha1]=7643977a7954065417d40fbcaf8e9bc4608c681b, stripped
./tailscale/tailscale_i386_Linux.upx:                        ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=FJyG9UoOThWN1lhzXrFA/l4OVQ0Luf8Igk4OWRkGh/-BCO0NksoRVLxYguSfSb/rPO4qy3QsrQCS7mkSV-Q, statically linked, no section header
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
./tailscale/tailscale_mips64_Linux:                          ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, BuildID[sha1]=390a33310d7b18fe78a4a8dd9f9c709b6315ed94, with debug_info, not stripped
./tailscale/tailscale_mips64le_Linux:                        ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, BuildID[sha1]=1254f81553bcc8b08122bd4f3bfa8e6cff99ca93, with debug_info, not stripped
./tailscale/tailscale_mips_Linux:                            ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, BuildID[sha1]=f982dbacb00eacb14fceca8c6efddb04b36c854c, with debug_info, not stripped
./tailscale/tailscale_mips_Linux.upx:                        ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=bvA7DHBj-kLIypy3K_tQ/VJpn5_TueD7q1jy92uDF/9K3QfUf8eOURiO2sYiMJ/EH6PJlIl8Iku3Mz2TIsf, statically linked, no section header
./tailscale/tailscale_mipsle_Linux:                          ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, BuildID[sha1]=6e6ce1e843b549df4bbbc2010bb8d2bdf3d052af, with debug_info, not stripped
./tailscale/tailscale_mipsle_Linux.upx:                      ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=gb-vWVyiYC6cUBRe3oR6/vsIzfeSl_3FIaa_5bIgS/tu2mzDhGyiwRhGKsH36O/kyTzmjWBLDKEKSEokbsQ, statically linked, no section header
./tailscale/tailscale_powerpc64_ppc64_Linux:                 ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64_ppc64_Linux.upx:             ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_powerpc64le_ppc64le_Linux:             ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx:         ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_riscv64_Linux:                         ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, BuildID[sha1]=223552351900fa026255f5ff1a57caabab0e872e, with debug_info, not stripped
./tailscale/tailscale_s390x_Linux:                           ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_setup_Windows.exe:                     PE32 executable (GUI) Intel 80386, for MS Windows, 6 sections
./tailscale/tailscale_x86_Windows.msi:                       Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Intel;1033, Revision Number: {DBAE9E47-B7DD-4C1C-A8BC-F908B2FFC90E}, Create Time/Date: Thu Sep 11 20:43:18 2025, Last Saved Time/Date: Thu Sep 11 20:43:18 2025, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscaled_aarch64_arm64_Linux:                  ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, BuildID[sha1]=ce5c4bff92822c9f3a8762704745ae6ce3a4c243, with debug_info, not stripped
./tailscale/tailscaled_aarch64_arm64_Linux.upx:              ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=l8VJxGmeZcSmGMZpXxne/b_TZSeweS_pKi3HuFkL-/v8c54lqDXcKDOFrChma1/4VeP3GdDkVSsUpqfXIJt, statically linked, no section header
./tailscale/tailscaled_aarch64_arm64_macOS:                  Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_amd_geode_Linux:                      ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, BuildID[sha1]=41459af9f7cc58097e0657e1a72431e027937962, stripped
./tailscale/tailscaled_amd_geode_Linux.upx:                  ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=G0snxMhieVGijGMtoY0v/x4bZqZQMTimKFndMTsI8/aGvgKjjLsuiG9r27rKBZ/9dV04bLQpQYlvuBRetMc, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_Linux:                     ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, BuildID[sha1]=f5b5509053a383dba119d3e7836443daac4a07c3, stripped
./tailscale/tailscaled_amd_x86_64_Linux.upx:                 ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=b8xlvdTzJbqZj6sftREo/E9rPkyKoxYkRoOEzngvo/sGoAOSzXyhImgyTdYKxc/xybzvnlYLcV3tB7mlSGp, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_macOS:                     Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_arm_abi_Linux:                        ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, BuildID[sha1]=f27668700833e8e320a70240340cd73556df555b, with debug_info, not stripped
./tailscale/tailscaled_arm_abi_Linux.upx:                    ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=R8fjJGpNn1rJHUrLe5LV/c_UeZ8mJd4fn1RCvLeCZ/MuR0H7_kvF2RGNsazEfz/rBYidAje9bj8WHTYG4My, statically linked, no section header
./tailscale/tailscaled_i386_Linux:                           ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, BuildID[sha1]=f593931fec8586dca793bf032a0130f6b3677e8b, stripped
./tailscale/tailscaled_i386_Linux.upx:                       ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=5JElYUUlK1s0ndMUHuUM/gDWE2LyStoqcBBHi_Uyi/VR_Veu1agI2edPevdOB1/BI4fYLXvlRritCM6Wr7L, statically linked, no section header
./tailscale/tailscaled_mips64_Linux:                         ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, BuildID[sha1]=fdec1d56873fc851bcf153b02fe1cd0e17bd84f9, with debug_info, not stripped
./tailscale/tailscaled_mips64le_Linux:                       ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, BuildID[sha1]=776716fab41a6868a68a0bec04c1cfa5a0549a3f, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux:                           ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, BuildID[sha1]=ae44bbe2532fd62b58a20511c1ed4a5bbbc3478b, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux.upx:                       ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=GtL1BI5712QTtEF0nJ8a/_DGJrHk3bicDvPNkn6AH/RGl5lhC39jwC6lauHGPH/2z-GjlenCvCP3OpRCQyD, statically linked, no section header
./tailscale/tailscaled_mipsle_Linux:                         ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, BuildID[sha1]=d3198e257629bc3ba45faa4bd0c23ad8ec601a63, with debug_info, not stripped
./tailscale/tailscaled_mipsle_Linux.upx:                     ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=Y4CvgykZ3S0q5tD_Q9KY/0DKeuEzCWyNdVUee150w/zqF1X-ZZwhlOjhi3MAjN/qxgHj_Pl1CO_SDvEKRKh, statically linked, no section header
./tailscale/tailscaled_powerpc64_ppc64_Linux:                ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64_ppc64_Linux.upx:            ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_powerpc64le_ppc64le_Linux:            ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx:        ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_riscv64_Linux:                        ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, BuildID[sha1]=1c7da25cb41563acc034b0001c3090ff628e148b, with debug_info, not stripped
./tailscale/tailscaled_s390x_Linux:                          ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped

--> SHA256SUM
5ecfa5a9c70a81fc6bfac585371fd0aac24fa9955a07ca11379edef5d9801ebb  ./tailscale/tailscale_aarch64_arm64_Linux
2d0abfc78603706fdd5a5cd4320119419e069eaf619f8fe0452a6bf56c5802ed  ./tailscale/tailscale_aarch64_arm64_Linux.upx
ef0318882b02219f1c73990dcb59d9edb726410a49e4479167a0cdce95416373  ./tailscale/tailscale_aarch64_arm64_Windows.msi
758bd296723a348a70f5274b294baeb4053abd2e2ce58e2220e210946b618c6f  ./tailscale/tailscale_aarch64_arm64_macOS
ffaf6cbb1041dc6f62f3a2e04c62b57a23bb088030bdc420f97040013e5b28ff  ./tailscale/tailscale_amd_geode_Linux
35575656f7f77da6b4df23f253057bf631053d7ae238c39082eee1ffaf9ad479  ./tailscale/tailscale_amd_geode_Linux.upx
22d62b53a07c3125091578559947cf7ad9bd994bffdd3a7ebd910a0e03818c10  ./tailscale/tailscale_amd_x86_64_Linux
308630b81b9b4da9d8ee76bffed788e6851e1e7d0176daa8508669cf2d824269  ./tailscale/tailscale_amd_x86_64_Linux.upx
816827b4857e3bab0f4df6f522b9a7e0291eb13882a11f556fbddef8d30b4281  ./tailscale/tailscale_amd_x86_64_Windows.msi
248b7930c0c4c650f988bcb90a968da042066e0b826bf58efd8fe3a69fad8e7f  ./tailscale/tailscale_amd_x86_64_macOS
b75e283c9df3fd516cff5f0f87e6dddc81e0167710277fde48b4a7626f05bf67  ./tailscale/tailscale_arm_abi_Linux
7082ac78fdc4b49e1c15750f66cb051f01082f9790c440110e3fcab843b062fc  ./tailscale/tailscale_arm_abi_Linux.upx
34a800367ca85cf37bcc33eec5662a7f3468a35732ddecf0a675a1dad882112b  ./tailscale/tailscale_i386_Linux
14a7a8215b08b594e90a53cca93bc7a1b0b29bca16429bd9bb956a13e8157e6c  ./tailscale/tailscale_i386_Linux.upx
e28cb8fef99d5961ca106cdaf75ec7bcf8a892194d3d41a3bcc1322026106bd4  ./tailscale/tailscale_ipn_setup_Windows.exe
c00a4896daccb119e22091fc0a12de912cc56e0b59bbfef30867dc8124a90b74  ./tailscale/tailscale_merged_aarch64_arm64_Linux
aa1d9d12a5aa547edf5361da9325da84b965ea436f5c599aebf4046e6eef9209  ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
68728bde1313493eb44dbd3be2e989eb00f60f4938d0d2845df9d45e32c25df7  ./tailscale/tailscale_merged_aarch64_arm64_macOS
7366dae7bdb138e7645b69ffe3fe9dced217c177b3e13d47ce2a61f24d6616d6  ./tailscale/tailscale_merged_amd_x86_64_Linux
7d9f98dff76eb5050af104e6ea40553a5ccf6f3991978877d294f9dbfff06b90  ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
267bebcfe539dd8353add30caf55a042bf996f8e688aae7910b9ecf61714f3f8  ./tailscale/tailscale_merged_amd_x86_64_macOS
fbf88294093400120fd7c99048c621af1a30054623a0dc3f59aaf93057cc324b  ./tailscale/tailscale_merged_arm_Linux
df3d36ddbe8e458983184bf2a5e1bc358dd03a56171afd2513ada7e976176383  ./tailscale/tailscale_merged_arm_Linux.upx
19a34a755b01d016bacfc8f4da657098dd6b8bacfab699abe49e5a970c81ed50  ./tailscale/tailscale_merged_i386_Linux
d474f06b45a6b445e29ea2ab94e476272941275c021656989bb7f8cb3c524cb0  ./tailscale/tailscale_merged_i386_Linux.upx
10de59292fc09527103f292c23dd0837a727167687fd3c388c9f1a7e124998a0  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux
a756badfac58c9e092ed80e3e65cfad4214cf6ef37411c5f1b016220324f36c9  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
4c67b8265362d6fad31a0334141d7a72be7fc7cf5284e164a1ca7caef023729a  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux
83a43ff797a04bcc93ac85b5665b3a39e81da2ae4113d2a6adf3a6addd41268f  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
156ed799dce90a5cefb8ffdefafb504856040f1fd3564fe77ba0d8e56daadf39  ./tailscale/tailscale_merged_s390x_Linux
2edc42ed7ed03bb4d7af82572bf9dde6881032081968f8e29b881f9482567cf6  ./tailscale/tailscale_mips64_Linux
9e84153ff0abf5861900dccc6cb5b3a3e6bf960eba1f4fc02665f1c4536e8408  ./tailscale/tailscale_mips64le_Linux
bba94293d8fce3a42b50660fc9eaf66de3a24bdcebbac27f1e1287232ee35738  ./tailscale/tailscale_mips_Linux
dcea260bfdc32a795f8e85ec75893a33a65a6d34528394cc74da37317640aa7f  ./tailscale/tailscale_mips_Linux.upx
25d1a8ef54ab845d684a735f7d6244c3be6bd163395eff86fb526d1ec2d82bdd  ./tailscale/tailscale_mipsle_Linux
f691667600e72e78fcd7cbddbbebe62ece8bdb20068914a17bf315268693ff95  ./tailscale/tailscale_mipsle_Linux.upx
4aa40c972b18e0ec1d46d7fd89d17f0e8f5dfa1a4ef164a3210572ceaaf598d1  ./tailscale/tailscale_powerpc64_ppc64_Linux
ff25a90c017ac74f7ba7506b7a4582d2dd20a99bffd5f6a806c262f31c100bc7  ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
49374edce6550650a43cf940a1b87da737f149a087092a34dd584ef34e683bba  ./tailscale/tailscale_powerpc64le_ppc64le_Linux
a2fb6806cf6eb4512897dbfa7321da1796bbe8d04eb915902a9afc677fdce782  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
60de129e7b6ad78460ea0dc73bc92536851dd322f2b11635c3a834c39aa9efb4  ./tailscale/tailscale_riscv64_Linux
3cb64cd3305b458159f12dbc58571c3905131a1a7cb96824afb918951fa87a2c  ./tailscale/tailscale_s390x_Linux
64a8ad28cbb67a6171236abe39f75a039a761a0e1aacdef75b26781887cef9a8  ./tailscale/tailscale_setup_Windows.exe
17a1f2c4ae2a5173bd0c21c1463cacb0ec05cf26c761ee1c5f4f704611a5fa69  ./tailscale/tailscale_x86_Windows.msi
41f50024807b80370415eb32dd4125f9d0739a448dbfb3c4e375912cb1d66073  ./tailscale/tailscaled_aarch64_arm64_Linux
eabe6d46b9a4b64e8a0d1bf699fd40dd79f02fccb053fdc468e19fd30410ea12  ./tailscale/tailscaled_aarch64_arm64_Linux.upx
3045786fe6191b3d64ae9d2b03b5fffcf080e3cb3073a3c2e8e69e57ea05e2cf  ./tailscale/tailscaled_aarch64_arm64_macOS
9a9eb5c1b9977d5359e701b7659a53f53bd6f045802dd08bf834cf76a5d9310c  ./tailscale/tailscaled_amd_geode_Linux
66bd970c06736be0c9f298d370a40deeb4e1995911565a84bc02e675e23c31c4  ./tailscale/tailscaled_amd_geode_Linux.upx
fbc4b2605db081474b4b010f4de0ed89a7a8d67b4e5d86fefb615613347e347e  ./tailscale/tailscaled_amd_x86_64_Linux
f31271244189278f2cdc3819f2715fe3c5a2f67acb178dc542b9915ff053ebef  ./tailscale/tailscaled_amd_x86_64_Linux.upx
b5304b43985998d94d5c2c94e0eeb9e160a76906fa0ecb224af45c3b878e684d  ./tailscale/tailscaled_amd_x86_64_macOS
615ff973e13c876eb58649ac2a2fc00215cc7e1381695a74be64d24712e1edf0  ./tailscale/tailscaled_arm_abi_Linux
e822d10b6db3a4c2b14d17802fcd3c23e5ce1382fca8f95922b0e87d3f6de61b  ./tailscale/tailscaled_arm_abi_Linux.upx
2c638c957a1103ab77e2168a9ee5090359b72ce7ad53f5aa1cb1f1685d06de3f  ./tailscale/tailscaled_i386_Linux
126fed90d9106a2343d8992afd6f777db7e1e7f38a18e6490381f7c637d43d06  ./tailscale/tailscaled_i386_Linux.upx
6c8c1c39d14aca6216da83dabefb7b4caff48ed75780ed4965e14c8d1ef1a0cb  ./tailscale/tailscaled_mips64_Linux
78bedadf356483a03cd635e93106ecd98084dd66571ead5a1ea80ec8fcbd14f7  ./tailscale/tailscaled_mips64le_Linux
e8a0a1927c44ec641834d7b4ce6cb0f98060d6fa2a6d9f81d146d6460b482482  ./tailscale/tailscaled_mips_Linux
659cc06f37b8fd8497125cf06061af6c40bfbdf479d2af27720ed34b4b989eb2  ./tailscale/tailscaled_mips_Linux.upx
7c4888f0b9f19cc4d3dec6f16fcd2b375f5ea4c0945ac5adb3a4059f7f4700b2  ./tailscale/tailscaled_mipsle_Linux
de17516a222d153063a1608d2581b11e19c3e93a655326a224d7bacbb27939aa  ./tailscale/tailscaled_mipsle_Linux.upx
aa786fd98bee75054c61fb5b976951a6753bb23545bf0aea8989d1e8b2233b72  ./tailscale/tailscaled_powerpc64_ppc64_Linux
28bb6b2b5745775910d2aeb1527ba2a0576294cfbbbae85a767eba143bc29c31  ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
2a12e2b3c1adda585f64d8a4aa558d40fd38fd295224febd8f45de796d33ae99  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux
a017c632460bb70a14b772461c866d822e27a08ed2887166b1f73f7a0e942b66  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
78ecb86d4c416846ebc801e674205db403927a982608ad234b769b9974217cc6  ./tailscale/tailscaled_riscv64_Linux
b207d199de64bbb7b68d6fb034649ff8831fe1e50e79920aaace4418d6bfb479  ./tailscale/tailscaled_s390x_Linux
```


---

- #### Sizes

```console
25M   ./tailscale/tailscale_aarch64_arm64_Linux
11M   ./tailscale/tailscale_aarch64_arm64_Linux.upx
31M   ./tailscale/tailscale_aarch64_arm64_Windows.msi
11M   ./tailscale/tailscale_aarch64_arm64_macOS
17M   ./tailscale/tailscale_amd_geode_Linux
5.0M  ./tailscale/tailscale_amd_geode_Linux.upx
18M   ./tailscale/tailscale_amd_x86_64_Linux
5.3M  ./tailscale/tailscale_amd_x86_64_Linux.upx
33M   ./tailscale/tailscale_amd_x86_64_Windows.msi
11M   ./tailscale/tailscale_amd_x86_64_macOS
25M   ./tailscale/tailscale_arm_abi_Linux
11M   ./tailscale/tailscale_arm_abi_Linux.upx
17M   ./tailscale/tailscale_i386_Linux
4.9M  ./tailscale/tailscale_i386_Linux.upx
45K   ./tailscale/tailscale_ipn_setup_Windows.exe
30M   ./tailscale/tailscale_merged_aarch64_arm64_Linux
7.1M  ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
20M   ./tailscale/tailscale_merged_aarch64_arm64_macOS
31M   ./tailscale/tailscale_merged_amd_x86_64_Linux
8.6M  ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
20M   ./tailscale/tailscale_merged_amd_x86_64_macOS
30M   ./tailscale/tailscale_merged_arm_Linux
6.9M  ./tailscale/tailscale_merged_arm_Linux.upx
30M   ./tailscale/tailscale_merged_i386_Linux
8.0M  ./tailscale/tailscale_merged_i386_Linux.upx
31M   ./tailscale/tailscale_merged_powerpc64_ppc64_Linux
7.0M  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
31M   ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux
7.3M  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
33M   ./tailscale/tailscale_merged_s390x_Linux
27M   ./tailscale/tailscale_mips64_Linux
27M   ./tailscale/tailscale_mips64le_Linux
27M   ./tailscale/tailscale_mips_Linux
11M   ./tailscale/tailscale_mips_Linux.upx
27M   ./tailscale/tailscale_mipsle_Linux
11M   ./tailscale/tailscale_mipsle_Linux.upx
18M   ./tailscale/tailscale_powerpc64_ppc64_Linux
4.3M  ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
18M   ./tailscale/tailscale_powerpc64le_ppc64le_Linux
4.5M  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
25M   ./tailscale/tailscale_riscv64_Linux
19M   ./tailscale/tailscale_s390x_Linux
51M   ./tailscale/tailscale_setup_Windows.exe
33M   ./tailscale/tailscale_x86_Windows.msi
36M   ./tailscale/tailscaled_aarch64_arm64_Linux
15M   ./tailscale/tailscaled_aarch64_arm64_Linux.upx
19M   ./tailscale/tailscaled_aarch64_arm64_macOS
23M   ./tailscale/tailscaled_amd_geode_Linux
6.6M  ./tailscale/tailscaled_amd_geode_Linux.upx
27M   ./tailscale/tailscaled_amd_x86_64_Linux
7.4M  ./tailscale/tailscaled_amd_x86_64_Linux.upx
19M   ./tailscale/tailscaled_amd_x86_64_macOS
33M   ./tailscale/tailscaled_arm_abi_Linux
14M   ./tailscale/tailscaled_arm_abi_Linux.upx
23M   ./tailscale/tailscaled_i386_Linux
6.6M  ./tailscale/tailscaled_i386_Linux.upx
37M   ./tailscale/tailscaled_mips64_Linux
37M   ./tailscale/tailscaled_mips64le_Linux
37M   ./tailscale/tailscaled_mips_Linux
14M   ./tailscale/tailscaled_mips_Linux.upx
37M   ./tailscale/tailscaled_mipsle_Linux
14M   ./tailscale/tailscaled_mipsle_Linux.upx
24M   ./tailscale/tailscaled_powerpc64_ppc64_Linux
5.8M  ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
24M   ./tailscale/tailscaled_powerpc64le_ppc64le_Linux
6.0M  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
34M   ./tailscale/tailscaled_riscv64_Linux
26M   ./tailscale/tailscaled_s390x_Linux
```

---

- #### UPX
```console

testing ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx [OK]
  30605460 ->   7359892   24.05%   linux/arm64   ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_amd_x86_64_Linux.upx [OK]
  18736232 ->   5477232   29.23%   linux/amd64   ./tailscale/tailscale_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx [OK]
  32112788 ->   7563808   23.55%  linux/ppc64le  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_merged_i386_Linux.upx [OK]
  30572692 ->   8354576   27.33%   linux/i386    ./tailscale/tailscale_merged_i386_Linux.upx
testing ./tailscale/tailscale_powerpc64_ppc64_Linux.upx [OK]
  18481300 ->   4452980   24.09%   linux/ppc64   ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscaled_amd_x86_64_Linux.upx [OK]
  27483400 ->   7745512   28.18%   linux/amd64   ./tailscale/tailscaled_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx [OK]
  18481300 ->   4639832   25.11%  linux/ppc64le  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_merged_amd_x86_64_Linux.upx [OK]
  32497812 ->   8928220   27.47%   linux/amd64   ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_merged_arm_Linux.upx [OK]
  30408852 ->   7151136   23.52%    linux/arm    ./tailscale/tailscale_merged_arm_Linux.upx
testing ./tailscale/tailscaled_arm_abi_Linux.upx [OK]
  34215312 ->  14111100   41.24%    linux/arm    ./tailscale/tailscaled_arm_abi_Linux.upx
testing ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx [OK]
  25100436 ->   6209844   24.74%  linux/ppc64le  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_aarch64_arm64_Linux.upx [OK]
  25196696 ->  10559312   41.91%   linux/arm64   ./tailscale/tailscale_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_amd_geode_Linux.upx [OK]
  17747428 ->   5148472   29.01%   linux/i386    ./tailscale/tailscale_amd_geode_Linux.upx
testing ./tailscale/tailscale_arm_abi_Linux.upx [OK]
  25316697 ->  10532548   41.60%    linux/arm    ./tailscale/tailscale_arm_abi_Linux.upx
testing ./tailscale/tailscaled_amd_geode_Linux.upx [OK]
  24060708 ->   6876404   28.58%   linux/i386    ./tailscale/tailscaled_amd_geode_Linux.upx
testing ./tailscale/tailscale_i386_Linux.upx [OK]
  17690084 ->   5136924   29.04%   linux/i386    ./tailscale/tailscale_i386_Linux.upx
testing ./tailscale/tailscaled_mipsle_Linux.upx [OK]
  37894000 ->  14216556   37.52%  linux/mipsel   ./tailscale/tailscaled_mipsle_Linux.upx
testing ./tailscale/tailscale_mips_Linux.upx [OK]
  27926724 ->  10574984   37.87%   linux/mips    ./tailscale/tailscale_mips_Linux.upx
testing ./tailscale/tailscaled_i386_Linux.upx [OK]
  24019748 ->   6866636   28.59%   linux/i386    ./tailscale/tailscaled_i386_Linux.upx
testing ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx [OK]
  25100436 ->   5983404   23.84%   linux/ppc64   ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_mipsle_Linux.upx [OK]
  27804948 ->  10549708   37.94%  linux/mipsel   ./tailscale/tailscale_mipsle_Linux.upx
testing ./tailscale/tailscaled_mips_Linux.upx [OK]
  38049648 ->  14241976   37.43%   linux/mips    ./tailscale/tailscaled_mips_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx [OK]
  32112788 ->   7296728   22.72%   linux/ppc64   ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscaled_aarch64_arm64_Linux.upx [OK]
  36997456 ->  15157732   40.97%   linux/arm64   ./tailscale/tailscaled_aarch64_arm64_Linux.upx

```

---

- #### Version
```console
$ ./tailscale/tailscale_amd_x86_64_Linux --version
1.88.1
  tailscale commit: 032962f4bc982fe8b6b58df01c33cf2904d07d67
  long version: 1.88.1-t032962f4b-gc5ad3b22f
  other commit: c5ad3b22fdb5813c46501f20144c6b29b61acf54
  go version: go1.25.1

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
  systray     Run a systray application to manage Tailscale
  completion  Shell tab-completion scripts

FLAGS
  --socket value
    	path to tailscaled socket (default /var/run/tailscale/tailscaled.sock)

$ ./tailscale/tailscaled_amd_x86_64_Linux -version
1.88.1
  tailscale commit: 032962f4bc982fe8b6b58df01c33cf2904d07d67
  long version: 1.88.1-t032962f4b-gc5ad3b22f
  other commit: c5ad3b22fdb5813c46501f20144c6b29b61acf54
  go version: go1.25.1

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
    	encrypt the state file on disk; uses TPM on Linux and Windows, on all other platforms this flag is not supported
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


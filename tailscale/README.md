
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
./tailscale/tailscale_aarch64_arm64_Linux:                   ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=6XfTXEiIbH-7mVJU2HTE/vG2gTkQBRoaHlgVSdfRI/znhZ-33fbY3-NQs8wUi_/Ln2EVR4RjO7_NOcpvaqe, BuildID[sha1]=b76242a1d1aa64757e0096b988ac6307e0df99e2, with debug_info, not stripped
./tailscale/tailscale_aarch64_arm64_Linux.upx:               ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=6XfTXEiIbH-7mVJU2HTE/vG2gTkQBRoaHlgVSdfRI/znhZ-33fbY3-NQs8wUi_/Ln2EVR4RjO7_NOcpvaqe, statically linked, no section header
./tailscale/tailscale_aarch64_arm64_Windows.msi:             Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Arm64;1033, Revision Number: {58CE9ECD-8B11-4E94-A8F0-9206F12E4079}, Create Time/Date: Wed Mar 18 16:03:58 2026, Last Saved Time/Date: Wed Mar 18 16:03:58 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscale_aarch64_arm64_macOS:                   Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_amd_geode_Linux:                       ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=y8VddvmU90_Bcu7dlDyP/HNL7uybiTlgqu0fA7CTL/HEX_GxJ5pxCRzRTB32nD/KkaV27o298vgedhAPFc8, BuildID[sha1]=d876a29b17a23420e11017c24a5227ae7c4b1d8d, stripped
./tailscale/tailscale_amd_geode_Linux.upx:                   ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=y8VddvmU90_Bcu7dlDyP/HNL7uybiTlgqu0fA7CTL/HEX_GxJ5pxCRzRTB32nD/KkaV27o298vgedhAPFc8, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Linux:                      ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=WyCp4dpTzsHdyu9wrQ00/qS71uyBsSP-ncyYjCP-H/hIAJo0OhZO6-nCQ2drzj/SgOpKGOJTgodyOojqtUp, BuildID[sha1]=cb2085dbd1eac5f5419134265744076aa82869c6, stripped
./tailscale/tailscale_amd_x86_64_Linux.upx:                  ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=WyCp4dpTzsHdyu9wrQ00/qS71uyBsSP-ncyYjCP-H/hIAJo0OhZO6-nCQ2drzj/SgOpKGOJTgodyOojqtUp, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Windows.msi:                Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: x64;1033, Revision Number: {635FA62B-C24B-40F4-BECC-87771C74D803}, Create Time/Date: Wed Mar 18 16:03:58 2026, Last Saved Time/Date: Wed Mar 18 16:03:58 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscale_amd_x86_64_macOS:                      Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_arm_abi_Linux:                         ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=22FuOudQBQjeG1F6b5e7/mvZUcDKalYYwP7NAaKxH/Q8JN0jO3bOyYyjlh3CGq/jTOOjS7eMELziV8wJtJM, BuildID[sha1]=4c75775b794182793edba32dcb684d6dbd5f6e61, with debug_info, not stripped
./tailscale/tailscale_arm_abi_Linux.upx:                     ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=22FuOudQBQjeG1F6b5e7/mvZUcDKalYYwP7NAaKxH/Q8JN0jO3bOyYyjlh3CGq/jTOOjS7eMELziV8wJtJM, statically linked, no section header
./tailscale/tailscale_i386_Linux:                            ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=LjjgLlXYJrRqBnjtIvkE/xHMQXR-UUy1JncXvXlWb/ApQhh7Orv0xzwDGHKwCI/fLzvnaGv3OXDtmWehaWu, BuildID[sha1]=e8bb7066fa4e956440f71d16bc1929cd23729f1d, stripped
./tailscale/tailscale_i386_Linux.upx:                        ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=LjjgLlXYJrRqBnjtIvkE/xHMQXR-UUy1JncXvXlWb/ApQhh7Orv0xzwDGHKwCI/fLzvnaGv3OXDtmWehaWu, statically linked, no section header
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
./tailscale/tailscale_mips64_Linux:                          ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=AmZr1uiPlWc0Uuxb2a_q/asw48FKdBP3tJMnzvYI2/f-XJR445WYbjI3_GYt-v/yk67i4NhHjOAu1K9x1Tl, BuildID[sha1]=aa681fb9911efe7d67124822313f8f8f110169e5, with debug_info, not stripped
./tailscale/tailscale_mips64le_Linux:                        ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=rdukfp8GaTJzXadO0LCP/cyuEolZsbXummRiHi8Kt/9mQZPXEZiZ3tJT3p7j7V/PJar88j96615kFx9BthM, BuildID[sha1]=b8342dc8228f8ef5391929463dfc71cf1d7e71bb, with debug_info, not stripped
./tailscale/tailscale_mips_Linux:                            ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=0qP8UYxUwNU6KPW4UJqs/u1qJPyzIkspibMHGwuIT/aUPx_R1JuKdAqqrFMEFI/YIKyFysWqs61jYNYum9r, BuildID[sha1]=faf5e204bd8cf7874229cb49aeda6824aaef1468, with debug_info, not stripped
./tailscale/tailscale_mips_Linux.upx:                        ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=0qP8UYxUwNU6KPW4UJqs/u1qJPyzIkspibMHGwuIT/aUPx_R1JuKdAqqrFMEFI/YIKyFysWqs61jYNYum9r, statically linked, no section header
./tailscale/tailscale_mipsle_Linux:                          ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=7jxl1ZHLw5ZUMo_s4Q7N/CO-lWFHmZnvn-9TnibgJ/ogbq4tesMVhdnfpYqHIE/JIyHgKwhvgrVJcl0m0MS, BuildID[sha1]=6813ea79bbea2ca88e9f36e41778af4b4c1b8d80, with debug_info, not stripped
./tailscale/tailscale_mipsle_Linux.upx:                      ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=7jxl1ZHLw5ZUMo_s4Q7N/CO-lWFHmZnvn-9TnibgJ/ogbq4tesMVhdnfpYqHIE/JIyHgKwhvgrVJcl0m0MS, statically linked, no section header
./tailscale/tailscale_powerpc64_ppc64_Linux:                 ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64_ppc64_Linux.upx:             ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_powerpc64le_ppc64le_Linux:             ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx:         ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_riscv64_Linux:                         ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, Go BuildID=S1DvdQ7pYPqfCDCCMNKV/_APyl4z86XBKAfDbaUS3/6bsWXgs686zHPH5Ep_k0/2irqIsmbAWo1zXjek1I1, BuildID[sha1]=5578b107ee9b647585ad6902c81e45725f6ed4f2, with debug_info, not stripped
./tailscale/tailscale_s390x_Linux:                           ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_setup_Windows.exe:                     PE32 executable (GUI) Intel 80386, for MS Windows, 6 sections
./tailscale/tailscale_x86_Windows.msi:                       Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Intel;1033, Revision Number: {78701F24-7CC2-49E5-BDD5-D569B4679497}, Create Time/Date: Wed Mar 18 16:03:58 2026, Last Saved Time/Date: Wed Mar 18 16:03:58 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscaled_aarch64_arm64_Linux:                  ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=6xxjfNps4PDkXApZjAvy/hus7A1rNdEm2maDGC3i6/kbjKZYoYmIWiBU1Hud5T/UXMU69KYQMCVUcy4T95c, BuildID[sha1]=cc37642511e8d69c4aaf52988ea88b69a535f654, with debug_info, not stripped
./tailscale/tailscaled_aarch64_arm64_Linux.upx:              ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=6xxjfNps4PDkXApZjAvy/hus7A1rNdEm2maDGC3i6/kbjKZYoYmIWiBU1Hud5T/UXMU69KYQMCVUcy4T95c, statically linked, no section header
./tailscale/tailscaled_aarch64_arm64_macOS:                  Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_amd_geode_Linux:                      ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=UF92ipmANdBfUoW8RVFS/CWuu2agTEWGbO4nREhKi/If2Im01HXZBSAZRfUZJC/g8xVM9hYBQqIF08PWld-, BuildID[sha1]=b0abeac2fbf197b7ec3190aaf784ff86e64f966c, stripped
./tailscale/tailscaled_amd_geode_Linux.upx:                  ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=UF92ipmANdBfUoW8RVFS/CWuu2agTEWGbO4nREhKi/If2Im01HXZBSAZRfUZJC/g8xVM9hYBQqIF08PWld-, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_Linux:                     ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=W-aSvS0yPQwIUpgvL6c9/yoX7IWFNJGPA0taZVbWj/rGb-MsO9gz07yqxJ3fVA/Xp09nR86sP7uFigslxMg, BuildID[sha1]=d57f639a14fa1f63bea97e791fb66cf97d623c87, stripped
./tailscale/tailscaled_amd_x86_64_Linux.upx:                 ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=W-aSvS0yPQwIUpgvL6c9/yoX7IWFNJGPA0taZVbWj/rGb-MsO9gz07yqxJ3fVA/Xp09nR86sP7uFigslxMg, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_macOS:                     Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_arm_abi_Linux:                        ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=QPTsuQPfe8-UQLguwow7/stPFhPpdLdbOA8_ccGKZ/WA5uSg3RbdJ9VXSI1eXO/i_abv5JOfAye08ZBIyZg, BuildID[sha1]=20077c8154def90234210f7d92bb8abfaa884de1, with debug_info, not stripped
./tailscale/tailscaled_arm_abi_Linux.upx:                    ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=QPTsuQPfe8-UQLguwow7/stPFhPpdLdbOA8_ccGKZ/WA5uSg3RbdJ9VXSI1eXO/i_abv5JOfAye08ZBIyZg, statically linked, no section header
./tailscale/tailscaled_i386_Linux:                           ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=kiKjozHnjRCd00lusl9j/IiCKwyfnc7cCOV9ggK6i/s0sHkV69hYyXGgkw86Ks/bVV9eLDZFktIMtgtLE1g, BuildID[sha1]=eea64dbca5a90788d4b3ff3e5903260cdefca600, stripped
./tailscale/tailscaled_i386_Linux.upx:                       ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=kiKjozHnjRCd00lusl9j/IiCKwyfnc7cCOV9ggK6i/s0sHkV69hYyXGgkw86Ks/bVV9eLDZFktIMtgtLE1g, statically linked, no section header
./tailscale/tailscaled_mips64_Linux:                         ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=qley7Vgu_0DIv3UjINd2/1hZUiwG3TeF7xRJAnIHz/hpoy9kFslXnjW-UUp0-l/k74fzI2EIsCnVmYcuBRc, BuildID[sha1]=9dcd6e4a8526f54fef7370275b8a7a69e9d7a152, with debug_info, not stripped
./tailscale/tailscaled_mips64le_Linux:                       ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=e85CP3SW2kHKOeqNN9o-/KZ0Lzd7pkC6hFfkCqLqw/PmCW2I3LOFC0Jy7FqVwu/neJQ3UNcXRArRGLR_JpY, BuildID[sha1]=52dabdbf61edafda8fc0baa8c5ffd36d6db3df49, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux:                           ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=0WFvnHMkZ_pxGMLlp-rk/SU1VGiWaF1BpNA7iKWtl/M62_6tA8yQRbQdTbU6yR/tsGhjVB4iXsoJ_gpECpW, BuildID[sha1]=66dc9420935016d0cd66664e21ccb3fb2fb8d5ef, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux.upx:                       ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=0WFvnHMkZ_pxGMLlp-rk/SU1VGiWaF1BpNA7iKWtl/M62_6tA8yQRbQdTbU6yR/tsGhjVB4iXsoJ_gpECpW, statically linked, no section header
./tailscale/tailscaled_mipsle_Linux:                         ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=G_JUV2KYzCx26_6UThGA/VCpAhNdhwuk5AGWHtKpr/e4F-mzeAJLHViVM5umpL/e4oDsG2kChxm2Sdisz2n, BuildID[sha1]=4d8131ae54633e3bfb3f5f580cc9a35f9f575946, with debug_info, not stripped
./tailscale/tailscaled_mipsle_Linux.upx:                     ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=G_JUV2KYzCx26_6UThGA/VCpAhNdhwuk5AGWHtKpr/e4F-mzeAJLHViVM5umpL/e4oDsG2kChxm2Sdisz2n, statically linked, no section header
./tailscale/tailscaled_powerpc64_ppc64_Linux:                ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64_ppc64_Linux.upx:            ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_powerpc64le_ppc64le_Linux:            ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx:        ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_riscv64_Linux:                        ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, Go BuildID=OfZbF9ynH8BSd3UIZ44a/VXfh3TA654mXptJCgj6W/1Ivsawr9yR52dyU-jvHe/kRYi3SmGmtfeitYRn2Z5, BuildID[sha1]=bf26cf9a015728aa2141a85098d41b6085705762, with debug_info, not stripped
./tailscale/tailscaled_s390x_Linux:                          ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped

--> SHA256SUM
bbdd60fb0245dfe3ef6921412e6cd86b6d3dd09d4fd9d23618cf072a8479ee8b  ./tailscale/tailscale_aarch64_arm64_Linux
b26d86c1b4695f27496b1332cfc4314ea761fcd31312d80d196ce9649d07520e  ./tailscale/tailscale_aarch64_arm64_Linux.upx
fc704c9a3078962517b95dddb270c4cd4556b41b9a39eb928da4cebd46b2b818  ./tailscale/tailscale_aarch64_arm64_Windows.msi
758bd296723a348a70f5274b294baeb4053abd2e2ce58e2220e210946b618c6f  ./tailscale/tailscale_aarch64_arm64_macOS
8fc2971910a45c5b7a4361d691a7718f27a73813e36c935d23aca3685979f9f1  ./tailscale/tailscale_amd_geode_Linux
5e2e5efe536b73ff07215884e33797c8a75130397e4e9ef0ecdf6b063074861c  ./tailscale/tailscale_amd_geode_Linux.upx
b1ca649bb8d9e8c39e3e20e32ff805cf4e0315a80a4b7cee81f9416bc4b2fdbc  ./tailscale/tailscale_amd_x86_64_Linux
6d6500da6c970521d98275d0e426cc7f866b24e860645c4185fc48018848fff9  ./tailscale/tailscale_amd_x86_64_Linux.upx
167ca8c9413d780db44424526f978dad16fc32701a40b7c6c373bc1561e406e6  ./tailscale/tailscale_amd_x86_64_Windows.msi
248b7930c0c4c650f988bcb90a968da042066e0b826bf58efd8fe3a69fad8e7f  ./tailscale/tailscale_amd_x86_64_macOS
9fe46ecb35de3f5bf47afbb67d54d79aaa5798a9112aa02af6946a09b6a7301e  ./tailscale/tailscale_arm_abi_Linux
7399f9d6e096916cc3339e8eadc9710a6688e56b26e752cfdd5278f5c6783c0b  ./tailscale/tailscale_arm_abi_Linux.upx
23e9a32e608b4959a69b76244ca30b4370276f06d78909f1485526410d7f5a78  ./tailscale/tailscale_i386_Linux
70fe907d4e8258f602fdf697e55ac2d5a500fbce82ae04ed252732904adf1c54  ./tailscale/tailscale_i386_Linux.upx
ca385af68497e8456d9e84e00dc8a5c6a2adb85e3e4c828cc97c4a7c8c77aea8  ./tailscale/tailscale_ipn_setup_Windows.exe
6489b12bc5a89e51260422b19ec057d42113670a8f98c092e8d193a045100300  ./tailscale/tailscale_merged_aarch64_arm64_Linux
b7240e21646c2fd673187c049f3ffea8e0073ebfa9b490840c983a4f212aa4e6  ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
68728bde1313493eb44dbd3be2e989eb00f60f4938d0d2845df9d45e32c25df7  ./tailscale/tailscale_merged_aarch64_arm64_macOS
e416496a2ebf84e6889b3635300e97955e31d5e48133fe7c47ddac850ae28225  ./tailscale/tailscale_merged_amd_x86_64_Linux
ecb2382504aaf13f1eddded38b35cf4a7403c6e4c91508687f992aaf9c3a3eb0  ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
267bebcfe539dd8353add30caf55a042bf996f8e688aae7910b9ecf61714f3f8  ./tailscale/tailscale_merged_amd_x86_64_macOS
eb3270096ebb3c5e4fd036d7a5085e1cfc7ead40bbbd5bc7c3573244c65bcb21  ./tailscale/tailscale_merged_arm_Linux
0d3f666f2fd738312b38f466fe0834f8be9b0a1f83639f8466e80db795c9c005  ./tailscale/tailscale_merged_arm_Linux.upx
3b074c5509294f4319e8973e703f3f2d7166ab08d29486af84e7a121494b82d8  ./tailscale/tailscale_merged_i386_Linux
86f012f2b7a23aed6c8df2a0e8b6cb81a5efbcdf5d617c2720ee0922b5dc61a5  ./tailscale/tailscale_merged_i386_Linux.upx
102aa72f842a4f25e88251312369d0b302669014acadc8cfe9e7d7933449782a  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux
a5f28a486ff6afc9c581a904385221cdf82f0ca912945543dbf6da6bc9f004f4  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
607423600beed96c708d90883f23ebca95cbb1d6aafaa4a77fa96e0ff7e2a324  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux
4348778ac21c3113187e54eaa8f2da06f8c8b785cca4e60da68dcf9adb64ce17  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
70436b831ffa91a0a2509c0d322d79805fac3014ef0c0d0023c3523cba6e7076  ./tailscale/tailscale_merged_s390x_Linux
d83ec01126cbd4cdc5ec1f80c7ca02b9eeb6aeeb4819dd4b88cf14820204c392  ./tailscale/tailscale_mips64_Linux
3aad957aed025a22ff5ced9dac2383ab95c38216e9784c3e296b68b119ac1f2c  ./tailscale/tailscale_mips64le_Linux
e4f58ea4e01110f255239f15c5c96d36d154747bafedeea7ebbc8531b2ae0d3e  ./tailscale/tailscale_mips_Linux
731a4f7a024cdaae1b57bef6696105c500b092a31d9ea79529b792aa086dde8a  ./tailscale/tailscale_mips_Linux.upx
8f0706e54703d895dd24564520ec7813cd834aa16ba1aa9c5ca9fc3e0087f714  ./tailscale/tailscale_mipsle_Linux
4f51396c8100d92733bcf172937254da4c2544c3ac7ed214b0a7856476abe0b8  ./tailscale/tailscale_mipsle_Linux.upx
492f0200e106f8a8e1906a8034ed5bc07e254455db1c346d8e495762f4c10300  ./tailscale/tailscale_powerpc64_ppc64_Linux
cb868a795e98abfc196dfcffd97cf75480e6eab8f4603b18d3cc8359095b1ee7  ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
61acbf209ab8d7ff1f2a0ac7ecec04aa3a3b3d7074b6e120ec7b803507d20cef  ./tailscale/tailscale_powerpc64le_ppc64le_Linux
178161a51e0b5b91cffd2762d757e7fa9e0b50042a3852076b0c45c42580a775  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
fa848abfc2f3c46af3f5844c40f049e00faaf6fa820e8742df7d7b4e1be4404b  ./tailscale/tailscale_riscv64_Linux
6d23e6c45e2b3f0db85ae0c4c3d0274a285b9ec4936c4d3afc65281b77ee7926  ./tailscale/tailscale_s390x_Linux
64a8ad28cbb67a6171236abe39f75a039a761a0e1aacdef75b26781887cef9a8  ./tailscale/tailscale_setup_Windows.exe
6f2624fbd6b1a8cd8cfa387373425d0d9189c8a1b1382d6ded2f9cc365a3cced  ./tailscale/tailscale_x86_Windows.msi
6e1e49e4236553b69712d7ce72a2a4a0573eba584ffd132fed6c47bcd06e7cc5  ./tailscale/tailscaled_aarch64_arm64_Linux
8b259d29e34a4a4ec537bf3e189a5339300b06830723369d6497aec2541fa569  ./tailscale/tailscaled_aarch64_arm64_Linux.upx
3045786fe6191b3d64ae9d2b03b5fffcf080e3cb3073a3c2e8e69e57ea05e2cf  ./tailscale/tailscaled_aarch64_arm64_macOS
168ac4e66d6329bfe6253de9ab1699d833e8bc9c39239b1cb9c4aba8a5ab73ba  ./tailscale/tailscaled_amd_geode_Linux
6a10d54f2318bf867c8fbca1493c84153dac64c93f7429130d3f5d6619fde960  ./tailscale/tailscaled_amd_geode_Linux.upx
e344279fedf07e4f9bc38a8007d6b7667bdf5b63efc12e35c0dacea3c91c395a  ./tailscale/tailscaled_amd_x86_64_Linux
db7c952a7f74bb3ff19c0fa332a1d434b9c4be4366b4226bc77de7168b4650d1  ./tailscale/tailscaled_amd_x86_64_Linux.upx
b5304b43985998d94d5c2c94e0eeb9e160a76906fa0ecb224af45c3b878e684d  ./tailscale/tailscaled_amd_x86_64_macOS
d2397016739a3d0cf6455fb15bca8190a0ed2aaaea90c26e273a7b3960918972  ./tailscale/tailscaled_arm_abi_Linux
39398c1f4a36d5af0fdf990b73b9b0d595cc3011604f6a41118be382d47bd5e5  ./tailscale/tailscaled_arm_abi_Linux.upx
825aa0335fc251a769642cda4b9a105a92a09af54ebfde4bb6858e9918f5cf18  ./tailscale/tailscaled_i386_Linux
b3748ba14b206239d88b41ebb1de95bc9f30187fc2dcb897d8c31e69a5f267f7  ./tailscale/tailscaled_i386_Linux.upx
a8a2f20ae5c7024a68451afa786d71b448c4a9e02c030e28c9daf9446ead74d1  ./tailscale/tailscaled_mips64_Linux
fdfe7cf5c1d47f4a5b88eed83738c62fd08a7571d22fe49b2758ceb4dbde6d56  ./tailscale/tailscaled_mips64le_Linux
0554736e8c4eb4f8e621dba8c7b915e0cd8a271372042b7ca2cc66adcd9cfa88  ./tailscale/tailscaled_mips_Linux
14090da1577a9f7a8f1b740cbb383bcd2bdcd08b2dc789722d37fb5e33a7f5d4  ./tailscale/tailscaled_mips_Linux.upx
2c8eacb15dfb83f92c4198935a151ece75cd4c248da9fca8700cabdf4b4c415b  ./tailscale/tailscaled_mipsle_Linux
213b848aa71f79f37b7ae198240fbb67ad7281d38b60a8ebd4e30ed9b0b8e707  ./tailscale/tailscaled_mipsle_Linux.upx
a07824ceaa974936483776ae71c76355472c4ff7c912a5690e770a2615d94dce  ./tailscale/tailscaled_powerpc64_ppc64_Linux
6cc3c4727f2fc4c633b08bc36b84834203e3ad83c95f1fc2aae48d5a6cee41f8  ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
8252e6527c28a520c63b0e4f80ebbd80fe5ea2247f512f43c88c81a2301de163  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux
a9bc75af2699beb70b512d9cc28d82f811960436444aef81f10dd7c14117b80c  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
a8584e37b8ab4c75ba14e104ff11901a398c05d16d46d7ebfc7a4dcf8bbf8487  ./tailscale/tailscaled_riscv64_Linux
557a5012878f4ef3f7a9e3062a713ee49e99bb9c27ed407f62302e4b9981aec4  ./tailscale/tailscaled_s390x_Linux
```


---

- #### Sizes

```console
28M   ./tailscale/tailscale_aarch64_arm64_Linux
12M   ./tailscale/tailscale_aarch64_arm64_Linux.upx
33M   ./tailscale/tailscale_aarch64_arm64_Windows.msi
11M   ./tailscale/tailscale_aarch64_arm64_macOS
20M   ./tailscale/tailscale_amd_geode_Linux
5.1M  ./tailscale/tailscale_amd_geode_Linux.upx
21M   ./tailscale/tailscale_amd_x86_64_Linux
5.9M  ./tailscale/tailscale_amd_x86_64_Linux.upx
35M   ./tailscale/tailscale_amd_x86_64_Windows.msi
11M   ./tailscale/tailscale_amd_x86_64_macOS
28M   ./tailscale/tailscale_arm_abi_Linux
12M   ./tailscale/tailscale_arm_abi_Linux.upx
20M   ./tailscale/tailscale_i386_Linux
5.5M  ./tailscale/tailscale_i386_Linux.upx
48K   ./tailscale/tailscale_ipn_setup_Windows.exe
32M   ./tailscale/tailscale_merged_aarch64_arm64_Linux
7.6M  ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
20M   ./tailscale/tailscale_merged_aarch64_arm64_macOS
35M   ./tailscale/tailscale_merged_amd_x86_64_Linux
9.2M  ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
20M   ./tailscale/tailscale_merged_amd_x86_64_macOS
32M   ./tailscale/tailscale_merged_arm_Linux
7.4M  ./tailscale/tailscale_merged_arm_Linux.upx
33M   ./tailscale/tailscale_merged_i386_Linux
8.6M  ./tailscale/tailscale_merged_i386_Linux.upx
34M   ./tailscale/tailscale_merged_powerpc64_ppc64_Linux
7.5M  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
34M   ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux
7.8M  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
36M   ./tailscale/tailscale_merged_s390x_Linux
32M   ./tailscale/tailscale_mips64_Linux
31M   ./tailscale/tailscale_mips64le_Linux
31M   ./tailscale/tailscale_mips_Linux
12M   ./tailscale/tailscale_mips_Linux.upx
31M   ./tailscale/tailscale_mipsle_Linux
12M   ./tailscale/tailscale_mipsle_Linux.upx
21M   ./tailscale/tailscale_powerpc64_ppc64_Linux
4.7M  ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
21M   ./tailscale/tailscale_powerpc64le_ppc64le_Linux
4.9M  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
28M   ./tailscale/tailscale_riscv64_Linux
22M   ./tailscale/tailscale_s390x_Linux
51M   ./tailscale/tailscale_setup_Windows.exe
34M   ./tailscale/tailscale_x86_Windows.msi
37M   ./tailscale/tailscaled_aarch64_arm64_Linux
15M   ./tailscale/tailscaled_aarch64_arm64_Linux.upx
19M   ./tailscale/tailscaled_aarch64_arm64_macOS
24M   ./tailscale/tailscaled_amd_geode_Linux
6.7M  ./tailscale/tailscaled_amd_geode_Linux.upx
27M   ./tailscale/tailscaled_amd_x86_64_Linux
7.6M  ./tailscale/tailscaled_amd_x86_64_Linux.upx
19M   ./tailscale/tailscaled_amd_x86_64_macOS
33M   ./tailscale/tailscaled_arm_abi_Linux
14M   ./tailscale/tailscaled_arm_abi_Linux.upx
24M   ./tailscale/tailscaled_i386_Linux
6.7M  ./tailscale/tailscaled_i386_Linux.upx
38M   ./tailscale/tailscaled_mips64_Linux
38M   ./tailscale/tailscaled_mips64le_Linux
37M   ./tailscale/tailscaled_mips_Linux
14M   ./tailscale/tailscaled_mips_Linux.upx
37M   ./tailscale/tailscaled_mipsle_Linux
14M   ./tailscale/tailscaled_mipsle_Linux.upx
25M   ./tailscale/tailscaled_powerpc64_ppc64_Linux
5.8M  ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
25M   ./tailscale/tailscaled_powerpc64le_ppc64le_Linux
6.1M  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
34M   ./tailscale/tailscaled_riscv64_Linux
26M   ./tailscale/tailscaled_s390x_Linux
```

---

- #### UPX
```console

testing ./tailscale/tailscale_arm_abi_Linux.upx [OK]
  28886145 ->  11702624   40.51%    linux/arm    ./tailscale/tailscale_arm_abi_Linux.upx
testing ./tailscale/tailscaled_arm_abi_Linux.upx [OK]
  34556009 ->  14319608   41.44%    linux/arm    ./tailscale/tailscaled_arm_abi_Linux.upx
testing ./tailscale/tailscaled_mipsle_Linux.upx [OK]
  38249177 ->  14446372   37.77%  linux/mipsel   ./tailscale/tailscaled_mipsle_Linux.upx
testing ./tailscale/tailscale_merged_arm_Linux.upx [OK]
  33292414 ->   7706740   23.15%    linux/arm    ./tailscale/tailscale_merged_arm_Linux.upx
testing ./tailscale/tailscale_i386_Linux.upx [OK]
  20451492 ->   5710172   27.92%   linux/i386    ./tailscale/tailscale_i386_Linux.upx
testing ./tailscale/tailscale_aarch64_arm64_Linux.upx [OK]
  29189826 ->  11931292   40.87%   linux/arm64   ./tailscale/tailscale_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_amd_x86_64_Linux.upx [OK]
  21977800 ->   6132612   27.90%   linux/amd64   ./tailscale/tailscale_amd_x86_64_Linux.upx
testing ./tailscale/tailscaled_amd_geode_Linux.upx [OK]
  24362380 ->   6998964   28.73%   linux/i386    ./tailscale/tailscaled_amd_geode_Linux.upx
testing ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx [OK]
  33423486 ->   7890584   23.61%   linux/arm64   ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_amd_geode_Linux.upx [OK]
  20504740 ->   5259308   25.65%   linux/i386    ./tailscale/tailscale_amd_geode_Linux.upx
testing ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx [OK]
  25362558 ->   6068188   23.93%   linux/ppc64   ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscaled_aarch64_arm64_Linux.upx [OK]
  37926648 ->  15604148   41.14%   linux/arm64   ./tailscale/tailscaled_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_mips_Linux.upx [OK]
  32006785 ->  11794632   36.85%   linux/mips    ./tailscale/tailscale_mips_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx [OK]
  35192958 ->   7838428   22.27%   linux/ppc64   ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx [OK]
  35192958 ->   8129752   23.10%  linux/ppc64le  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx [OK]
  25297022 ->   6297524   24.89%  linux/ppc64le  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_powerpc64_ppc64_Linux.upx [OK]
  20971646 ->   4910424   23.41%   linux/ppc64   ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx [OK]
  20971646 ->   5121184   24.42%  linux/ppc64le  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_merged_amd_x86_64_Linux.upx [OK]
  35999870 ->   9622008   26.73%   linux/amd64   ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
testing ./tailscale/tailscaled_amd_x86_64_Linux.upx [OK]
  28170424 ->   7903200   28.05%   linux/amd64   ./tailscale/tailscaled_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_merged_i386_Linux.upx [OK]
  33726590 ->   8993556   26.67%   linux/i386    ./tailscale/tailscale_merged_i386_Linux.upx
testing ./tailscale/tailscaled_i386_Linux.upx [OK]
  24325516 ->   6990720   28.74%   linux/i386    ./tailscale/tailscaled_i386_Linux.upx
testing ./tailscale/tailscaled_mips_Linux.upx [OK]
  38478845 ->  14475204   37.62%   linux/mips    ./tailscale/tailscaled_mips_Linux.upx
testing ./tailscale/tailscale_mipsle_Linux.upx [OK]
  31795357 ->  11765200   37.00%  linux/mipsel   ./tailscale/tailscale_mipsle_Linux.upx

```

---

- #### Version
```console
$ ./tailscale/tailscale_amd_x86_64_Linux --version
1.96.2
  tailscale commit: d916d86519b58d788ca175124feef93115c398d3
  long version: 1.96.2-td916d8651-gd905b0868
  other commit: d905b086818c463956e4d677b10a0a1558fbdd2d
  go version: go1.26.1

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
1.96.2
  tailscale commit: d916d86519b58d788ca175124feef93115c398d3
  long version: 1.96.2-td916d8651-gd905b0868
  other commit: d905b086818c463956e4d677b10a0a1558fbdd2d
  go version: go1.26.1

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


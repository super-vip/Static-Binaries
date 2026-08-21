
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
./tailscale/tailscale_aarch64_arm64_Linux:                   ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=jPCtie_JsJsCqLc6-Kb0/IvFVxLUe8UYcWZZzXjin/c7QyjlLE90u7DMR2AIKv/gNFL3QH2-2xJMJEQ7EDs, BuildID[sha1]=4da6d19b3d63042997a69640b3b17baf2c74d46a, with debug_info, not stripped
./tailscale/tailscale_aarch64_arm64_Linux.upx:               ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=jPCtie_JsJsCqLc6-Kb0/IvFVxLUe8UYcWZZzXjin/c7QyjlLE90u7DMR2AIKv/gNFL3QH2-2xJMJEQ7EDs, statically linked, no section header
./tailscale/tailscale_aarch64_arm64_Windows.msi:             Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Arm64;1033, Revision Number: {D1278E65-BA81-4404-A806-9843FD8773B5}, Create Time/Date: Wed Aug 19 23:57:46 2026, Last Saved Time/Date: Wed Aug 19 23:57:46 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscale_aarch64_arm64_macOS:                   Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_amd_geode_Linux:                       ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=W9z69lOB_0VdgsMYfpub/mQBnJyMtm4wSsb3ROUdY/HA_cBUTzZJu0xZEbisgP/2X8XMoE7SJIgcQ_gX0hP, BuildID[sha1]=2436d79025c2b6e8fc8a4e20569d4f4510855b18, stripped
./tailscale/tailscale_amd_geode_Linux.upx:                   ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=W9z69lOB_0VdgsMYfpub/mQBnJyMtm4wSsb3ROUdY/HA_cBUTzZJu0xZEbisgP/2X8XMoE7SJIgcQ_gX0hP, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Linux:                      ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=xP4-C_PW2zEp9mp5jdzA/AJWzscyKsHbB34RLDQYz/wa2wWcM3gyAvCwpqv0A_/xDFY3NNyckmKoVtWUVaS, BuildID[sha1]=fa50023a6e90dcb2947d8d0db1aa4deee1b52732, stripped
./tailscale/tailscale_amd_x86_64_Linux.upx:                  ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=xP4-C_PW2zEp9mp5jdzA/AJWzscyKsHbB34RLDQYz/wa2wWcM3gyAvCwpqv0A_/xDFY3NNyckmKoVtWUVaS, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Windows.msi:                Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: x64;1033, Revision Number: {A05332A7-A931-4472-B474-B0A938FA6ABE}, Create Time/Date: Wed Aug 19 23:57:45 2026, Last Saved Time/Date: Wed Aug 19 23:57:45 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscale_amd_x86_64_macOS:                      Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_arm_abi_Linux:                         ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=d9zHGjq-Cfx8d3pzqTIm/B0xkkKXjp3cBVjbiNC6a/lCM9KGIsxSDebpPz1Wri/vTikODINxBvMwmaG28jO, BuildID[sha1]=ad5d9d59188b8c9ef3a5ad15dd68a874a93fbd9d, with debug_info, not stripped
./tailscale/tailscale_arm_abi_Linux.upx:                     ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=d9zHGjq-Cfx8d3pzqTIm/B0xkkKXjp3cBVjbiNC6a/lCM9KGIsxSDebpPz1Wri/vTikODINxBvMwmaG28jO, statically linked, no section header
./tailscale/tailscale_i386_Linux:                            ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=lb-em0XKrjNnO7-uw6W4/_mKnWd39YNZtI-THadnx/Go31n36Xmj53omktQsp6/7HwCpWCV7uPGTMJ90CGJ, BuildID[sha1]=29bb4d0c84192d3155b54da158fce54e4068aede, stripped
./tailscale/tailscale_i386_Linux.upx:                        ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=lb-em0XKrjNnO7-uw6W4/_mKnWd39YNZtI-THadnx/Go31n36Xmj53omktQsp6/7HwCpWCV7uPGTMJ90CGJ, statically linked, no section header
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
./tailscale/tailscale_mips64_Linux:                          ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=O7vpVe6QsDiM5JI8M-Yi/HpU1olHW_s0KF_bU9Pvh/O4phUwOytGbCadZYcaaU/V0eN1EVFYt4IONjYN7dW, BuildID[sha1]=a8566c5d50ba0c4f1cf4a19467455fe058f2a44d, with debug_info, not stripped
./tailscale/tailscale_mips64le_Linux:                        ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=TVWQV37Lr6MIrmZfXdqJ/dw8J21OjTTBJq7bc3tj9/Gqh5oql30JCG6tAXR4c9/qj1X30gGix77vsAOyiP1, BuildID[sha1]=bd30c4ee174364b1288a01eeda87596d2b14861f, with debug_info, not stripped
./tailscale/tailscale_mips_Linux:                            ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=HTQBQlXkz3XyxjWMcw2p/3jowzWTD6XmCPyb8CqOe/HgX2kbDc94GWxNblWnTm/RmWI78Qrw3ePnqz2mDtO, BuildID[sha1]=55fc622f55a48285e0d08b045816aad90ad8f2c1, with debug_info, not stripped
./tailscale/tailscale_mips_Linux.upx:                        ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=HTQBQlXkz3XyxjWMcw2p/3jowzWTD6XmCPyb8CqOe/HgX2kbDc94GWxNblWnTm/RmWI78Qrw3ePnqz2mDtO, statically linked, no section header
./tailscale/tailscale_mipsle_Linux:                          ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=6LmVvq4cXavzsyT7qTum/2-GfZcGvhnQE2rguxVX7/Qk8T1SB0koTELZIUGMDs/_vCHzHRHRR0kTj_g1iYg, BuildID[sha1]=6e5a502cd42b3a901af2218ddd8e25e54d90d006, with debug_info, not stripped
./tailscale/tailscale_mipsle_Linux.upx:                      ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=6LmVvq4cXavzsyT7qTum/2-GfZcGvhnQE2rguxVX7/Qk8T1SB0koTELZIUGMDs/_vCHzHRHRR0kTj_g1iYg, statically linked, no section header
./tailscale/tailscale_powerpc64_ppc64_Linux:                 ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64_ppc64_Linux.upx:             ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_powerpc64le_ppc64le_Linux:             ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx:         ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_riscv64_Linux:                         ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, Go BuildID=oBq08Di0GEgLWNMCO0RW/QS_Fe2b_eX7QU9ZPUIUN/hAXevVR12udqiW3-8_NL/AujJuE1-TzeelK-m_52u, BuildID[sha1]=58fab22446cdcaca7931aef2a9b9122319bc9152, with debug_info, not stripped
./tailscale/tailscale_s390x_Linux:                           ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_setup_Windows.exe:                     PE32 executable (GUI) Intel 80386, for MS Windows, 6 sections
./tailscale/tailscale_x86_Windows.msi:                       Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Intel;1033, Revision Number: {6E8EC910-179E-44EE-80BC-1BCE3DB83C74}, Create Time/Date: Wed Aug 19 23:57:46 2026, Last Saved Time/Date: Wed Aug 19 23:57:46 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscaled_aarch64_arm64_Linux:                  ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=BIZiHW_eZwcdyGIq4hjq/C-D9tZ1P_Bac_TG9zI2p/i1k3uKdmwUXaWX-nYrkS/gaOJx5zmG1szqhFvPIut, BuildID[sha1]=197aa94ba1b2a05f8f2ac130833e6771a8284ef8, with debug_info, not stripped
./tailscale/tailscaled_aarch64_arm64_Linux.upx:              ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=BIZiHW_eZwcdyGIq4hjq/C-D9tZ1P_Bac_TG9zI2p/i1k3uKdmwUXaWX-nYrkS/gaOJx5zmG1szqhFvPIut, statically linked, no section header
./tailscale/tailscaled_aarch64_arm64_macOS:                  Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_amd_geode_Linux:                      ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=zvKW-f9kvCyraE55Ksrc/k8FNSvEU-fobOSSvB74G/Hw9e68sGkLt7ECq1_JRn/AhFre2jKznpCcTBOg5dk, BuildID[sha1]=04759d90d33df1227f6c73f6b1183df4e3a2beba, stripped
./tailscale/tailscaled_amd_geode_Linux.upx:                  ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=zvKW-f9kvCyraE55Ksrc/k8FNSvEU-fobOSSvB74G/Hw9e68sGkLt7ECq1_JRn/AhFre2jKznpCcTBOg5dk, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_Linux:                     ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=kvVzjC9MtH8NqoHl-vP_/CP1l9ZOGpPiaeJRE27Vk/wu2hR5JoAzc5ioj5UaSS/Bkpv30CvfgAhbj-2K8CE, BuildID[sha1]=2307cff2d40aa2edcb09017eb3423fd5669f186e, stripped
./tailscale/tailscaled_amd_x86_64_Linux.upx:                 ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=kvVzjC9MtH8NqoHl-vP_/CP1l9ZOGpPiaeJRE27Vk/wu2hR5JoAzc5ioj5UaSS/Bkpv30CvfgAhbj-2K8CE, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_macOS:                     Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_arm_abi_Linux:                        ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=3LoPqm1apFyFhjGFpm59/uADqh3TCd9HWxLWxlKcN/-ZNSl3v4R64mhH2BVUhW/O5yOQaWkMzTkJs5pnliz, BuildID[sha1]=e2d57b4ac4fa683874aebd56c819dff9308fb223, with debug_info, not stripped
./tailscale/tailscaled_arm_abi_Linux.upx:                    ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=3LoPqm1apFyFhjGFpm59/uADqh3TCd9HWxLWxlKcN/-ZNSl3v4R64mhH2BVUhW/O5yOQaWkMzTkJs5pnliz, statically linked, no section header
./tailscale/tailscaled_i386_Linux:                           ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=Xb3jjppwjKRYDMLlht9j/Acny1fpgOZ8jvrzTg2vB/ZDpe1oyBfRQv1uQLKEJX/xAXNtDdKBDnQl6xLNTyO, BuildID[sha1]=acb07340d14224f7ec5a799ecf6be5827c2a30f2, stripped
./tailscale/tailscaled_i386_Linux.upx:                       ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=Xb3jjppwjKRYDMLlht9j/Acny1fpgOZ8jvrzTg2vB/ZDpe1oyBfRQv1uQLKEJX/xAXNtDdKBDnQl6xLNTyO, statically linked, no section header
./tailscale/tailscaled_mips64_Linux:                         ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=CwVDCDA93HkzWs0U_DCX/9Xw4mui2bTN5H_4gCYbk/5tNgCez25ug0YLwT01WD/8jgC0nuXMvezyn1AImH8, BuildID[sha1]=223ebc380e3bfeaf3553fc7e7461ce705b3f4ef9, with debug_info, not stripped
./tailscale/tailscaled_mips64le_Linux:                       ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=Ab_qO8xw_rMtWpE-4Qi7/eM7lFUggq_BVYmL7ty0l/ZY_JsmD_lnFW3bYkDZf0/ZVXXwwBP4ehY65jDVScs, BuildID[sha1]=ee591213adb6aabf705504bd64d73f2b4e19012d, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux:                           ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=hIp3g_6zwT-wuNw37nlF/yRjiZIqpozi12VbB8oJg/fRrbEbZVH9QJQMBksiSk/w4gYyyzZ6vlSGvnqL3Ss, BuildID[sha1]=2faa026e7d72ebfe84aea907a6a1970bda3c9098, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux.upx:                       ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=hIp3g_6zwT-wuNw37nlF/yRjiZIqpozi12VbB8oJg/fRrbEbZVH9QJQMBksiSk/w4gYyyzZ6vlSGvnqL3Ss, statically linked, no section header
./tailscale/tailscaled_mipsle_Linux:                         ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=udum8PtV1yvwUysATtoN/wP5a5UMFfYNGEo4qPn16/2XIm6wdLYYMsOp98P-kD/sZf9UZwTI_akfiSnFq1-, BuildID[sha1]=97b213b28c652a41fb2ac4be9a7f4ae1a1c4f08b, with debug_info, not stripped
./tailscale/tailscaled_mipsle_Linux.upx:                     ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=udum8PtV1yvwUysATtoN/wP5a5UMFfYNGEo4qPn16/2XIm6wdLYYMsOp98P-kD/sZf9UZwTI_akfiSnFq1-, statically linked, no section header
./tailscale/tailscaled_powerpc64_ppc64_Linux:                ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64_ppc64_Linux.upx:            ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_powerpc64le_ppc64le_Linux:            ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx:        ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_riscv64_Linux:                        ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, Go BuildID=XndUe88W4TNV4CA5UuVP/u0UheuhWQ9EqFQoQjyfu/GK7AVt6toUqIwtLBKypP/7W_JRDAdG2QpiQe_2R_j, BuildID[sha1]=d57ad4ce41b70962a6d959a7ecc3ad6e7fd5c559, with debug_info, not stripped
./tailscale/tailscaled_s390x_Linux:                          ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped

--> SHA256SUM
a14b94589c2630eb68ba7f7651ede226d2976708760ef3460556a00cf1aa4bab  ./tailscale/tailscale_aarch64_arm64_Linux
f302ca95db4f4600a70ad1e126756bf14f5f63114ef7b86606408d84f2511dde  ./tailscale/tailscale_aarch64_arm64_Linux.upx
5a3b9f93955f46e052312cbf67db6866b09d5b96c34a6656598b9aa13fdfead2  ./tailscale/tailscale_aarch64_arm64_Windows.msi
758bd296723a348a70f5274b294baeb4053abd2e2ce58e2220e210946b618c6f  ./tailscale/tailscale_aarch64_arm64_macOS
1f6a079b2dbf44d6a214b492e672824f55817c980e129342a192557711c294c9  ./tailscale/tailscale_amd_geode_Linux
9025b5e5a0512b572d644ff652c3ad4b4118f82a89277475d4303102dd726ece  ./tailscale/tailscale_amd_geode_Linux.upx
c82a5f9ba2975e61e754c61c9f0262898d2a5e2e91f7bc01543cfc70caade512  ./tailscale/tailscale_amd_x86_64_Linux
46b322591fc8ac3819f9999651733289f5018d3a4724a69bad97ff94323767d3  ./tailscale/tailscale_amd_x86_64_Linux.upx
03ac8183c6e3ce276e9b44281ebe7e4c02aef28a971034ca170c4b665df42dce  ./tailscale/tailscale_amd_x86_64_Windows.msi
248b7930c0c4c650f988bcb90a968da042066e0b826bf58efd8fe3a69fad8e7f  ./tailscale/tailscale_amd_x86_64_macOS
9b2aa24340d813d3eeb52344548239d71e54b82f68fbb0ef172ae16819b4944f  ./tailscale/tailscale_arm_abi_Linux
bdc2d36766ce4886d275b086399e8292e1ac252eacbea32dd337750f7ab8be66  ./tailscale/tailscale_arm_abi_Linux.upx
ea534e9421b29b84195e83dad389c47e5d29045e4f227e9ecf2ef127b94a4de5  ./tailscale/tailscale_i386_Linux
b26da40d8f131b71f427b31ffcd899e4e7813bd47a82ab10f72d77bb83826489  ./tailscale/tailscale_i386_Linux.upx
1babc56c0ed37690b013cf092dee02edeca8670bbf0d498c85c96c1cfca9a7e8  ./tailscale/tailscale_ipn_setup_Windows.exe
eacade23c7c01fb523c3a5a432d224e9e78b214b2441bcc1b3ea4b3051313a75  ./tailscale/tailscale_merged_aarch64_arm64_Linux
bfddf1e7ef31e0451f6ce37d7c07286c9196bdb61bc1566f7f591700f8b48122  ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
68728bde1313493eb44dbd3be2e989eb00f60f4938d0d2845df9d45e32c25df7  ./tailscale/tailscale_merged_aarch64_arm64_macOS
51501e6c258856493dc721e22ae8362f78b1d4fb592cc19e615c1ed03a750407  ./tailscale/tailscale_merged_amd_x86_64_Linux
2037b6a84e36a91fb2e66161631c6e7e85eff4f791461cc5545af3b2374ceab9  ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
267bebcfe539dd8353add30caf55a042bf996f8e688aae7910b9ecf61714f3f8  ./tailscale/tailscale_merged_amd_x86_64_macOS
179527e7739b396769f4b4ffcde315eaa6cf94de41c5eb33310f61c9516ef83c  ./tailscale/tailscale_merged_arm_Linux
45fc3a565227cbc54d15ad9cf965f86edc377e75526fefb683deb9ec325485c3  ./tailscale/tailscale_merged_arm_Linux.upx
49b7f11977ae464a63f6b34604a7c582eb1df7da76291ef6affcf0df55f4f596  ./tailscale/tailscale_merged_i386_Linux
be8adecdaf79c02ee4a4bbd11caa38cca5c8dd10d18c05815dbb3fee0b0de6fd  ./tailscale/tailscale_merged_i386_Linux.upx
eade70940fbf1395a309809d8ff2975bbebe7e0622e900d3813720edab887230  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux
f6ef6675cba33e1d44ee35353dd168835921ec7d133d5b600ff704be6bec4c13  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
1e897b8a6d29b402e231b7ce2cce45981e9c9b1a3e6fa68db4ce6f9d8098f62d  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux
f4dcc7efa61beaa64b44fcd1a86f60f6dd019fbf8485b0eeddfe8460a5f793c4  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
eceb4cde665d5fed7dbfffa0355969d366a98791efca5c522cc1269017a91e2d  ./tailscale/tailscale_merged_s390x_Linux
19c220fc00d7c0441bbe02bebdb388e018052d00df1ebdf34c868b411c3d9bc8  ./tailscale/tailscale_mips64_Linux
6c15cd79e64b22ff7cd5306836ce3bbf647a471b879fb776ca21d50aba725522  ./tailscale/tailscale_mips64le_Linux
bf2ab3e31e859c76fba64e06a51236d3e2f6457b8c098628e47f1c110d6e5a11  ./tailscale/tailscale_mips_Linux
16bd7a97a95f75a139fb83d4d360a9d173be0dfe7e5b5d1627fd07669bf4ebc3  ./tailscale/tailscale_mips_Linux.upx
50466b96658f962c41fd7fe51815386d44a6753add6ad5d04eca94ebea6540a4  ./tailscale/tailscale_mipsle_Linux
7c362badf69cbca5f41affa578aa954952dd952830806ad9c0d967ba9d2d0e58  ./tailscale/tailscale_mipsle_Linux.upx
a8c2f8571adad1a7d185213f0eb067db4a188b7565d9e7471c892d4b1a336bac  ./tailscale/tailscale_powerpc64_ppc64_Linux
c7025ba7d669dcb507e2d93aa146c127fedb27cdf09405d2ca0f6530da3380d8  ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
ede655c94ca71af8aa758b17b5edc85ecb918194212ac3afa6f73ef69ae0ec5f  ./tailscale/tailscale_powerpc64le_ppc64le_Linux
51ac0f44ca38aa7fbd28dc206a0c5486c9fe3e16810af771c2072162a61b0d3f  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
883083bccedc3ff9159e9723508cd76f56185419b2cc173441de811afb15543a  ./tailscale/tailscale_riscv64_Linux
4063039a64c2b5f195c82854bb53237337b6ac12a9d53ff418255ef01e1376ec  ./tailscale/tailscale_s390x_Linux
64a8ad28cbb67a6171236abe39f75a039a761a0e1aacdef75b26781887cef9a8  ./tailscale/tailscale_setup_Windows.exe
2a46e10f818991ca1476b2947badb6ea5556541061b5b51c02a39682de10df53  ./tailscale/tailscale_x86_Windows.msi
dda710b5bed9fbf87efc0126b614ed8f0e9f4a43b2265486bc6ad7eb0570f226  ./tailscale/tailscaled_aarch64_arm64_Linux
9aa08c7624f785693cbb1d3428c4c93a4ec9ffe3cc632c15ab05bf33ab0ca4c6  ./tailscale/tailscaled_aarch64_arm64_Linux.upx
3045786fe6191b3d64ae9d2b03b5fffcf080e3cb3073a3c2e8e69e57ea05e2cf  ./tailscale/tailscaled_aarch64_arm64_macOS
66750cb303c52f6fcb7d6d4134942c3d1ab49f33c25b8b528f821f5af0f8c420  ./tailscale/tailscaled_amd_geode_Linux
c775ab856f8a7fe8c1fcacc831cb4ec90b8cb08bf8b6d7e275afed2622bd04d6  ./tailscale/tailscaled_amd_geode_Linux.upx
69af01f9ec2bec980a02300b8567f348cc103e5cfefa2349e5956b0c7470cbee  ./tailscale/tailscaled_amd_x86_64_Linux
1aab6bae7a62cc90e287ec3e4168b2ae2630d9de5c2c0172020d3a9834b2ab18  ./tailscale/tailscaled_amd_x86_64_Linux.upx
b5304b43985998d94d5c2c94e0eeb9e160a76906fa0ecb224af45c3b878e684d  ./tailscale/tailscaled_amd_x86_64_macOS
f093488dcb7a2204787de2e0ab12882e2e3caf44f87024a101df04e8753f9eed  ./tailscale/tailscaled_arm_abi_Linux
324da15b0ea2c6e2fa7714742f8a79fdc078d8641600c79d18b592aa1b59c49e  ./tailscale/tailscaled_arm_abi_Linux.upx
b8cd7499bc56c4afbb7592141c4f291b9358a5c83622e24126bda013c52343b8  ./tailscale/tailscaled_i386_Linux
689240ca5ee50eb76db844ec14ebd77faf437960021c8419971ff935717fdff6  ./tailscale/tailscaled_i386_Linux.upx
25c410f97242a90471f75748c3f34428a551eb790a088545c12bb3c7d432234c  ./tailscale/tailscaled_mips64_Linux
99f82c9b1a316bc1abbe79b5fbd72b457208598f9c1ebc2f64116842da74605e  ./tailscale/tailscaled_mips64le_Linux
2b8119b11c7ae1421ee3c2a20b97cd8029677a56a08e3a1f51a4c462dae8ad24  ./tailscale/tailscaled_mips_Linux
d8b0e4be6586079c77212d5a5766975ccaee9a6acb74c52cf7136b3efaddc09e  ./tailscale/tailscaled_mips_Linux.upx
f4f81add0e792690179a05b53353be28069facf685de37da5c7628d0bd9d75ac  ./tailscale/tailscaled_mipsle_Linux
3cc1110836e1992aabaf92a19016f780164b28086b85bfd4a943bb7c48fc6445  ./tailscale/tailscaled_mipsle_Linux.upx
1e12620b904221e49d9583fb5384d800305512b43516efb1510f37792c418e9a  ./tailscale/tailscaled_powerpc64_ppc64_Linux
593658e159857ff3cfb4769d4658d35ddfb57c9b61d476cca417dab4b6a0991e  ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
9e02324cae5f55db971b5fb267422962fcd9b1cde6ee62a9f1ee52da2ee6cafe  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux
b18b9c259754b215cde43d96abf9a3a5a92580b3fc95c03342be5f23ca4a7670  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
8f40058668b361d7021605e50cea898c104d62896954e0131e8ae1f16b16cc59  ./tailscale/tailscaled_riscv64_Linux
2a4cffb42996697a0a35a0c5a1f294588b793dd949259e098ff3ae6db7058887  ./tailscale/tailscaled_s390x_Linux
```


---

- #### Sizes

```console
30M   ./tailscale/tailscale_aarch64_arm64_Linux
13M   ./tailscale/tailscale_aarch64_arm64_Linux.upx
35M   ./tailscale/tailscale_aarch64_arm64_Windows.msi
11M   ./tailscale/tailscale_aarch64_arm64_macOS
21M   ./tailscale/tailscale_amd_geode_Linux
5.8M  ./tailscale/tailscale_amd_geode_Linux.upx
23M   ./tailscale/tailscale_amd_x86_64_Linux
6.2M  ./tailscale/tailscale_amd_x86_64_Linux.upx
37M   ./tailscale/tailscale_amd_x86_64_Windows.msi
11M   ./tailscale/tailscale_amd_x86_64_macOS
30M   ./tailscale/tailscale_arm_abi_Linux
12M   ./tailscale/tailscale_arm_abi_Linux.upx
21M   ./tailscale/tailscale_i386_Linux
5.8M  ./tailscale/tailscale_i386_Linux.upx
70K   ./tailscale/tailscale_ipn_setup_Windows.exe
35M   ./tailscale/tailscale_merged_aarch64_arm64_Linux
8.1M  ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
20M   ./tailscale/tailscale_merged_aarch64_arm64_macOS
37M   ./tailscale/tailscale_merged_amd_x86_64_Linux
9.8M  ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
20M   ./tailscale/tailscale_merged_amd_x86_64_macOS
35M   ./tailscale/tailscale_merged_arm_Linux
7.9M  ./tailscale/tailscale_merged_arm_Linux.upx
35M   ./tailscale/tailscale_merged_i386_Linux
9.2M  ./tailscale/tailscale_merged_i386_Linux.upx
37M   ./tailscale/tailscale_merged_powerpc64_ppc64_Linux
8.0M  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
37M   ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux
8.3M  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
38M   ./tailscale/tailscale_merged_s390x_Linux
33M   ./tailscale/tailscale_mips64_Linux
33M   ./tailscale/tailscale_mips64le_Linux
33M   ./tailscale/tailscale_mips_Linux
12M   ./tailscale/tailscale_mips_Linux.upx
33M   ./tailscale/tailscale_mipsle_Linux
12M   ./tailscale/tailscale_mipsle_Linux.upx
22M   ./tailscale/tailscale_powerpc64_ppc64_Linux
5.0M  ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
22M   ./tailscale/tailscale_powerpc64le_ppc64le_Linux
5.2M  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
30M   ./tailscale/tailscale_riscv64_Linux
23M   ./tailscale/tailscale_s390x_Linux
51M   ./tailscale/tailscale_setup_Windows.exe
36M   ./tailscale/tailscale_x86_Windows.msi
39M   ./tailscale/tailscaled_aarch64_arm64_Linux
16M   ./tailscale/tailscaled_aarch64_arm64_Linux.upx
19M   ./tailscale/tailscaled_aarch64_arm64_macOS
25M   ./tailscale/tailscaled_amd_geode_Linux
7.1M  ./tailscale/tailscaled_amd_geode_Linux.upx
29M   ./tailscale/tailscaled_amd_x86_64_Linux
8.0M  ./tailscale/tailscaled_amd_x86_64_Linux.upx
19M   ./tailscale/tailscaled_amd_x86_64_macOS
35M   ./tailscale/tailscaled_arm_abi_Linux
15M   ./tailscale/tailscaled_arm_abi_Linux.upx
25M   ./tailscale/tailscaled_i386_Linux
7.1M  ./tailscale/tailscaled_i386_Linux.upx
40M   ./tailscale/tailscaled_mips64_Linux
40M   ./tailscale/tailscaled_mips64le_Linux
39M   ./tailscale/tailscaled_mips_Linux
15M   ./tailscale/tailscaled_mips_Linux.upx
39M   ./tailscale/tailscaled_mipsle_Linux
15M   ./tailscale/tailscaled_mipsle_Linux.upx
26M   ./tailscale/tailscaled_powerpc64_ppc64_Linux
6.2M  ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
26M   ./tailscale/tailscaled_powerpc64le_ppc64le_Linux
6.4M  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
36M   ./tailscale/tailscaled_riscv64_Linux
27M   ./tailscale/tailscaled_s390x_Linux
```

---

- #### UPX
```console

testing ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx [OK]
  26935422 ->   6406196   23.78%   linux/ppc64   ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx [OK]
  22544510 ->   5433296   24.10%  linux/ppc64le  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_arm_abi_Linux.upx [OK]
  30568384 ->  12372808   40.48%    linux/arm    ./tailscale/tailscale_arm_abi_Linux.upx
testing ./tailscale/tailscaled_mips_Linux.upx [OK]
  40781670 ->  15327456   37.58%   linux/mips    ./tailscale/tailscaled_mips_Linux.upx
testing ./tailscale/tailscaled_i386_Linux.upx [OK]
  25760204 ->   7373296   28.62%   linux/i386    ./tailscale/tailscaled_i386_Linux.upx
testing ./tailscale/tailscale_merged_arm_Linux.upx [OK]
  35717246 ->   8218228   23.01%    linux/arm    ./tailscale/tailscale_merged_arm_Linux.upx
testing ./tailscale/tailscale_mips_Linux.upx [OK]
  33764882 ->  12469844   36.93%   linux/mips    ./tailscale/tailscale_mips_Linux.upx
testing ./tailscale/tailscale_merged_i386_Linux.upx [OK]
  36192382 ->   9588080   26.49%   linux/i386    ./tailscale/tailscale_merged_i386_Linux.upx
testing ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx [OK]
  26935422 ->   6645252   24.67%  linux/ppc64le  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscaled_mipsle_Linux.upx [OK]
  40612846 ->  15305908   37.69%  linux/mipsel   ./tailscale/tailscaled_mipsle_Linux.upx
testing ./tailscale/tailscale_amd_x86_64_Linux.upx [OK]
  23159496 ->   6459816   27.89%   linux/amd64   ./tailscale/tailscale_amd_x86_64_Linux.upx
testing ./tailscale/tailscaled_aarch64_arm64_Linux.upx [OK]
  40133368 ->  16489076   41.09%   linux/arm64   ./tailscale/tailscaled_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_aarch64_arm64_Linux.upx [OK]
  30825755 ->  12602448   40.88%   linux/arm64   ./tailscale/tailscale_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_merged_amd_x86_64_Linux.upx [OK]
  38592638 ->  10248272   26.55%   linux/amd64   ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx [OK]
  37814398 ->   8661012   22.90%  linux/ppc64le  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_amd_geode_Linux.upx [OK]
  21667876 ->   6036020   27.86%   linux/i386    ./tailscale/tailscale_amd_geode_Linux.upx
testing ./tailscale/tailscaled_arm_abi_Linux.upx [OK]
  36574429 ->  15152688   41.43%    linux/arm    ./tailscale/tailscaled_arm_abi_Linux.upx
testing ./tailscale/tailscaled_amd_x86_64_Linux.upx [OK]
  29806680 ->   8334340   27.96%   linux/amd64   ./tailscale/tailscaled_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_mipsle_Linux.upx [OK]
  33617810 ->  12446628   37.02%  linux/mipsel   ./tailscale/tailscale_mipsle_Linux.upx
testing ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx [OK]
  35848318 ->   8405276   23.45%   linux/arm64   ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_i386_Linux.upx [OK]
  21614596 ->   6026040   27.88%   linux/i386    ./tailscale/tailscale_i386_Linux.upx
testing ./tailscale/tailscale_powerpc64_ppc64_Linux.upx [OK]
  22544510 ->   5213588   23.13%   linux/ppc64   ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscaled_amd_geode_Linux.upx [OK]
  25792972 ->   7378620   28.61%   linux/i386    ./tailscale/tailscaled_amd_geode_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx [OK]
  37814398 ->   8359152   22.11%   linux/ppc64   ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx

```

---

- #### Version
```console
$ ./tailscale/tailscale_amd_x86_64_Linux --version
1.102.3
  tailscale commit: 9329c3677031109ff6d0b80abee0cddc8f35ff6f
  long version: 1.102.3-t9329c3677-ga522f65e9
  other commit: a522f65e92d54b594fe72e842afc9572bd9cf0b8
  go version: go1.26.6 (tailscale/go 7275f792d4)

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
1.102.3
  tailscale commit: 9329c3677031109ff6d0b80abee0cddc8f35ff6f
  long version: 1.102.3-t9329c3677-ga522f65e9
  other commit: a522f65e92d54b594fe72e842afc9572bd9cf0b8
  go version: go1.26.6 (tailscale/go 7275f792d4)

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



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
./tailscale/tailscale_aarch64_arm64_Linux:                   ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=4yTN3oi6uKyl7zs24NdB/bgc8Ubke6f2_ig_lIQ26/vamdvZvMbW6s4Laeeceg/pQRSt2Y-ebEzU1avJ_53, with debug_info, not stripped
./tailscale/tailscale_aarch64_arm64_Linux.upx:               ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_aarch64_arm64_Windows.msi:             Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard.WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Arm64;1033, Revision Number: {358F6D16-80FE-43C9-866F-1D282BAD22E0}, Create Time/Date: Mon Aug 19 17:39:44 2024, Last Saved Time/Date: Mon Aug 19 17:39:44 2024, Number of Pages: 500, Number of Words: 2, Name of Creating Application: Windows Installer XML Toolset (), Security: 2
./tailscale/tailscale_aarch64_arm64_macOS:                   Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_amd_geode_Linux:                       ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=slJlci6ErN5bFz_-sppY/DbecF64_q1v5PPL5oroI/BQbo3VxrNQEt3g859uPw/w5dRbeDD2X2mPlVqEHNr, stripped
./tailscale/tailscale_amd_geode_Linux.upx:                   ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), statically linked, no section header
./tailscale/tailscale_amd_x86_64_Linux:                      ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=tNMEQ_tP_OxYc6ssop0U/3qkN0zgMSgAQO2zMdW1S/klLQHhMq11mN2LNdioJA/l7sPMr81Ygvi66TY7y9S, stripped
./tailscale/tailscale_amd_x86_64_Linux.upx:                  ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_amd_x86_64_Windows.msi:                Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard.WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: x64;1033, Revision Number: {046C2E84-00D9-44D5-9D93-E5A8DB54B654}, Create Time/Date: Mon Aug 19 17:39:16 2024, Last Saved Time/Date: Mon Aug 19 17:39:16 2024, Number of Pages: 500, Number of Words: 2, Name of Creating Application: Windows Installer XML Toolset (), Security: 2
./tailscale/tailscale_amd_x86_64_macOS:                      Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_arm_abi_Linux:                         ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=LCkSVovb9l0iddXmjNkN/2PSH3rUFHjwvbl0Ztj_Z/WjJVqrXnXBGPDEhEvNga/sYJdV0wUoUCxcwAWQrvo, with debug_info, not stripped
./tailscale/tailscale_arm_abi_Linux.upx:                     ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), statically linked, no section header
./tailscale/tailscale_i386_Linux:                            ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=mIbEZJ8Eb5BAwWjs_liK/f_4H8pjUUp7w7-9MJlc2/L-2RtdHexOxzEC0S5rj1/b7_5s3dNzf8yODBsVp7S, stripped
./tailscale/tailscale_i386_Linux.upx:                        ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), statically linked, no section header
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
./tailscale/tailscale_mips64_Linux:                          ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=KLImeNeLIn5kW9ge2Qtl/2iIDDRoj-esGeofujI3D/H1d0_9__1PKb0Rcp1T7A/R3Dsx9lECGdRQf3rB2L0, with debug_info, not stripped
./tailscale/tailscale_mips64le_Linux:                        ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=G7tN9bhCOYrIPmGe7KKC/A57ZZYbB4HKGGp_Vh6xz/sdXa744tXPJkl-CcehZg/GIIuO4hTztdH5gUGd9re, with debug_info, not stripped
./tailscale/tailscale_mips_Linux:                            ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=uN3o92Z3Vc5OJ3wb96t5/osTIeHqGzrFzMdkUxlVM/H6MZ26eOtTJ2t4rZj9Vr/SZNETxhC-jYjxZ1vuN2N, with debug_info, not stripped
./tailscale/tailscale_mips_Linux.upx:                        ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_mipsle_Linux:                          ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=eRsCFWc_nq2YFF44vUts/pecJiIhESqqR0T9ZYHm-/Ko6m9vZpAar5yEkceD95/MrB05-Tl00sJihmUjdEl, with debug_info, not stripped
./tailscale/tailscale_mipsle_Linux.upx:                      ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_powerpc64_ppc64_Linux:                 ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64_ppc64_Linux.upx:             ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_powerpc64le_ppc64le_Linux:             ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx:         ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_riscv64_Linux:                         ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, Go BuildID=OY8TTuDYKQSQ3s1l-lLW/adjqpagTnpPDrX-zLl-Z/oR1A-SnuOOsqF3Wu2Lww/pw5YINW-Wo2TvWWkdpDe, with debug_info, not stripped
./tailscale/tailscale_s390x_Linux:                           ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_setup_Windows.exe:                     PE32 executable (GUI) Intel 80386, for MS Windows
./tailscale/tailscale_x86_Windows.msi:                       Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard.WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Intel;1033, Revision Number: {05D83A77-B3DD-4462-A325-06DA08C2B3B4}, Create Time/Date: Mon Aug 19 17:39:44 2024, Last Saved Time/Date: Mon Aug 19 17:39:44 2024, Number of Pages: 500, Number of Words: 2, Name of Creating Application: Windows Installer XML Toolset (), Security: 2
./tailscale/tailscaled_aarch64_arm64_Linux:                  ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=AXeNkWxMhNfiQ6vl59CX/C9y0_aEJdR3C6LYgcqFG/wJf2Tx2nig1E3AkNZAAg/k0fzP2RtQqZM-i6MCTe8, with debug_info, not stripped
./tailscale/tailscaled_aarch64_arm64_Linux.upx:              ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_aarch64_arm64_macOS:                  Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_amd_geode_Linux:                      ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=uBGvSA3bw-HslZaNaj6T/Z3-lJersWAc0pxMqCYil/Mn3UOI1X5lFFOzWfgoUA/svwMZP-IHX87JzAS4YKG, stripped
./tailscale/tailscaled_amd_geode_Linux.upx:                  ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), statically linked, no section header
./tailscale/tailscaled_amd_x86_64_Linux:                     ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=6rbMxtG1M7pnVtUEcq5J/MQt6XUAuVIsubkl7-YxT/CQkTQqLyip-WsRVTR7iy/rcQgw26LUSkT_poWQxeP, stripped
./tailscale/tailscaled_amd_x86_64_Linux.upx:                 ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_amd_x86_64_macOS:                     Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_arm_abi_Linux:                        ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=CjRxB1XxLFf-Klq0s1kr/r5jnzyUnq2lLN5UCiI73/LgED2S-7MLUYhRTxO0NB/IsqNk9Xy26ixHIf55iqY, with debug_info, not stripped
./tailscale/tailscaled_arm_abi_Linux.upx:                    ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), statically linked, no section header
./tailscale/tailscaled_i386_Linux:                           ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=iVoNjt23s_bmd97P9n7i/LlwqAzAStgUeT7jG8kaH/tHYD4ubp9PTfshw_3OlF/fWETAjI9hMFG7pP2YLZA, stripped
./tailscale/tailscaled_i386_Linux.upx:                       ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), statically linked, no section header
./tailscale/tailscaled_mips64_Linux:                         ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=OG7MJOHSnHXLbwp5z9iZ/1XdkzP_OaFRfQE8Y9SFz/U8tBi1ldF0NIEBzZbtRG/mgYxDsvWowniVmkdiBrg, with debug_info, not stripped
./tailscale/tailscaled_mips64le_Linux:                       ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=-G4d-g5sdWmeAao_-VMK/_xIuCnYUPeTau8Is4lqR/Db54eQfzyLwrLYGKLzGG/OdzFLSk1wRcg8JOKnPmi, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux:                           ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=Qqhhx9vloyvXiWpafoMk/kLhExjNj_wf6R_UdWd8V/TOm15dkdE1UcXTtsqcIk/K7Zcb_VF_9qsNOVftxdU, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux.upx:                       ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_mipsle_Linux:                         ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=xGrHxjH34zCuBcODWb0P/BuYRztqsHjsWxPkrZiWi/iZ9OfGFWmH3M43UeRb9J/hxJlG151DJuZefgIRys3, with debug_info, not stripped
./tailscale/tailscaled_mipsle_Linux.upx:                     ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_powerpc64_ppc64_Linux:                ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64_ppc64_Linux.upx:            ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_powerpc64le_ppc64le_Linux:            ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx:        ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_riscv64_Linux:                        ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, Go BuildID=3SbaEpVuzGQfQ2X6kAf-/9WErEdC3buh1Fac-ogDh/nAjARyqEqbMYfMNfWx0R/4zt_U9FTQVSFXbV8vji0, with debug_info, not stripped
./tailscale/tailscaled_s390x_Linux:                          ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped

--> SHA256SUM
11a755c87d14c869b5056b8e0f5d0443f4bff8d18ae5271629783e736f9c4b38  ./tailscale/tailscale_aarch64_arm64_Linux
f93b634fb20602d5248a6fbe4e9d5c2137b97f0f2f2b81d80cb339596004a250  ./tailscale/tailscale_aarch64_arm64_Linux.upx
d939e63be7eca3d90df84f1fdc629767fb0b7df1c7e78eb37ce434152ae3093a  ./tailscale/tailscale_aarch64_arm64_Windows.msi
758bd296723a348a70f5274b294baeb4053abd2e2ce58e2220e210946b618c6f  ./tailscale/tailscale_aarch64_arm64_macOS
4444c728c79c79abac4c3bc66a0bd6f5048a5b3bad8d801fa1923f00f2195b1d  ./tailscale/tailscale_amd_geode_Linux
7ad6a1b34e40b9c1daf68831db42cbbf81d3baaa4c585daffbec14472b959db5  ./tailscale/tailscale_amd_geode_Linux.upx
8af0fdad5a5045c6f17d307831ee6b85541cddd0ca44bb8635cf63e7cbaeec6e  ./tailscale/tailscale_amd_x86_64_Linux
2bf452db22a6172acc98bafe836023053ebfd2878a4c7c78b0bddeece464dc67  ./tailscale/tailscale_amd_x86_64_Linux.upx
ed11a0dd7fa4a55ec23672131db0527e9100100a9a8dad1cc9cdfa34a4edfb44  ./tailscale/tailscale_amd_x86_64_Windows.msi
248b7930c0c4c650f988bcb90a968da042066e0b826bf58efd8fe3a69fad8e7f  ./tailscale/tailscale_amd_x86_64_macOS
6601a9ee5cbef6d0cef0aa3360edd49669d81e9f280298c4d4e06004b3774c6a  ./tailscale/tailscale_arm_abi_Linux
e3fa4477f0211503d16c97006ec457c9513e24c2a1d87ffee0f96dbf770032ae  ./tailscale/tailscale_arm_abi_Linux.upx
78adddf34c064072bb50085c47e39944147a8fc2a9c097572d96d28325c37c3a  ./tailscale/tailscale_i386_Linux
c2a9dd280f0d6581a90538b4f169e198fb73404c225399fa0daebb24fcef4f4b  ./tailscale/tailscale_i386_Linux.upx
d43bb773a1f91fc2e902fa749c41b29ee4410d7bd9579a571fe659ff9e1beaeb  ./tailscale/tailscale_ipn_setup_Windows.exe
6beb17c2781d8af6c858c988975f3771a4895564f6a047d8d48f2c1b09151afd  ./tailscale/tailscale_merged_aarch64_arm64_Linux
0df205e19d9de664ab9b5d64ebf61feb1b640518b8486f8017f70ddbeee21bda  ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
68728bde1313493eb44dbd3be2e989eb00f60f4938d0d2845df9d45e32c25df7  ./tailscale/tailscale_merged_aarch64_arm64_macOS
00b4e7f1a1d2bed4ef9f6b9f2a71b306ed1138c261b2c2634853f8bf6ec971ff  ./tailscale/tailscale_merged_amd_x86_64_Linux
b28efed63c55a67ca25e47409a2223c279c22fef91b41d9d0ad7765361dbf970  ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
267bebcfe539dd8353add30caf55a042bf996f8e688aae7910b9ecf61714f3f8  ./tailscale/tailscale_merged_amd_x86_64_macOS
d663f4dcb7ae5caa69eb099d0a9f75ac9abf2cb0a223498bae53dc46c293e5b1  ./tailscale/tailscale_merged_arm_Linux
c61cb4235ba899a505ac1d81beca891ac61dd4cb9af281a2770c7e1d5673f2c8  ./tailscale/tailscale_merged_arm_Linux.upx
a36cf94f4e52109e56ed972842e4612e5448e3ef63442bed3bb2f3ec959d01b3  ./tailscale/tailscale_merged_i386_Linux
ea22ee08db8768328bd2eb905834aa647f457edbb4bf80febc5b1466d4dd99ad  ./tailscale/tailscale_merged_i386_Linux.upx
8faec94a706b03ac977d44ef158d5a22d3a19ee69a6578e39aed0f878a6dfeeb  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux
94cc58bfb08faad394da0abc5613441ccf0377750e9322d8b6431967144119b4  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
c16db8d61463b72538b97fa994c8f70b78ea9093677466dfab2deaae8e20536e  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux
0a1705a7f182037d2ace3838b45f6c247a0b9106c24120c46ae0c5f4404ffc39  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
0d7298498eb1148b46e7f22cbd512a561209decd25aba8d6d5779eeb9e4ee16e  ./tailscale/tailscale_merged_s390x_Linux
34d08718d20a59c4791a021f683377411e0c8bd5af123e723ce843ef7f168d97  ./tailscale/tailscale_mips64_Linux
e4ff06ae5d575c01648d3b783f05ba85d56dccdd843d2b21ee069010ab8214cf  ./tailscale/tailscale_mips64le_Linux
b5f46524915cb056e1293e83aa8d03b5bf4f3ff50363594351f258622b1c00ac  ./tailscale/tailscale_mips_Linux
abb072a8c629f1c5f1e402064a9e360864f68cd32761252a869a2d7707ce808e  ./tailscale/tailscale_mips_Linux.upx
739577aca0ab8fa489582c69a2328f5efa967310b8a2d3f141237f8619f4394c  ./tailscale/tailscale_mipsle_Linux
e2ebe39302c519b1bca51258d32502bf205a983d115938de25de035fd6162980  ./tailscale/tailscale_mipsle_Linux.upx
4d360af4a88112d91f7e75f42753790b125d1841849e7d0abe4f5ad6c3d0e779  ./tailscale/tailscale_powerpc64_ppc64_Linux
2e7f6e7250fada4a084b83433369e24c8d98b8c182605824295f330f603677b4  ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
05b4ae9a873efeb59b4b4c7e5d80c5e2ea844bf1effb30005642bf28e8183c9e  ./tailscale/tailscale_powerpc64le_ppc64le_Linux
e625f0f2d72e7bafdefea69fba481f8663636830493ac7175d9f3f7e04c05650  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
8ef4ef86ee585eb655f200387fb383333717b4ae3976b8c992686b4ff924def3  ./tailscale/tailscale_riscv64_Linux
6999bdca1f0c0009dd5477d51c6cdcf0c3a63dc07e9c9803ba7711c79cc795f9  ./tailscale/tailscale_s390x_Linux
64a8ad28cbb67a6171236abe39f75a039a761a0e1aacdef75b26781887cef9a8  ./tailscale/tailscale_setup_Windows.exe
e8cd569eb64296cd496e7265044f6c14e5180bfe341894551c1e23b3c1562e69  ./tailscale/tailscale_x86_Windows.msi
4f9b160e6f4bc775a1b567a418701d5025bd4ee75c7e759100725867f45dcf0f  ./tailscale/tailscaled_aarch64_arm64_Linux
5b0f9c587b77a7b29d75ba9a58bca1bbbcb1a311045e01e857e713d001db2513  ./tailscale/tailscaled_aarch64_arm64_Linux.upx
3045786fe6191b3d64ae9d2b03b5fffcf080e3cb3073a3c2e8e69e57ea05e2cf  ./tailscale/tailscaled_aarch64_arm64_macOS
4279e5385a8c54d28238c114ca82c3c15c9ec8a634ac2071da7c0a72b9c657c2  ./tailscale/tailscaled_amd_geode_Linux
47fe6f9563a6724e00f799abda74b18ca5fb2a42de8e5c94376be1e6a42bec13  ./tailscale/tailscaled_amd_geode_Linux.upx
a935328af703923610dc38d868c33fa53496ea07db595ddf761677ba52c6b857  ./tailscale/tailscaled_amd_x86_64_Linux
ecedda13d45a0782dbed45a41e71c097727e60f5bfa5a067913ed8df79af02aa  ./tailscale/tailscaled_amd_x86_64_Linux.upx
b5304b43985998d94d5c2c94e0eeb9e160a76906fa0ecb224af45c3b878e684d  ./tailscale/tailscaled_amd_x86_64_macOS
99ee82e171ac9f151bc5117987f03fbc5f500899d90301f12c8b03ec78e06e4b  ./tailscale/tailscaled_arm_abi_Linux
c7b4c5b9492b6c096b5b41220e2af556181b92211d5277a06906694daabd795f  ./tailscale/tailscaled_arm_abi_Linux.upx
943da66194bfadaeaaad0c68f3786867f5405887d82f11da69c24d5bf7672c49  ./tailscale/tailscaled_i386_Linux
4e6a4a64ca38ee215e9ae923c8bfeae896d690665c329b171daddf49122d6a84  ./tailscale/tailscaled_i386_Linux.upx
3c765d5824c3b98492c6af506223f03b0214bebed368dafcc5f2d9e101fc4cf2  ./tailscale/tailscaled_mips64_Linux
e644e7c441c040bd20520d7778b92c8344ddff1c7aa86c1b065caba14caeab75  ./tailscale/tailscaled_mips64le_Linux
aa4188500c17d9ef2a58adcb0b6901f977acc570b87d8043cc88606f9eb46abf  ./tailscale/tailscaled_mips_Linux
bb8f8a8721159d9d0cafb65441b5a5c45e8765404e3743521ea8e7c67f993572  ./tailscale/tailscaled_mips_Linux.upx
c9995606116b4845ff695420955ded19e134f04f0c005dad1116d1b1de9b405c  ./tailscale/tailscaled_mipsle_Linux
aed152948e8387d40ca29b793ac66aea9d03ef3778caf9ba8e0a0973eec8e95d  ./tailscale/tailscaled_mipsle_Linux.upx
dbc74927af76064600b9b99b9f46dfa7b2d4ba8b6fe06ce1867f6805ae01d794  ./tailscale/tailscaled_powerpc64_ppc64_Linux
7b8d3014bde44f338c88ca1e0bc9d4c925bfd08ad81e99de4121cb332e4e74e8  ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
15dc112200163adf99362398ce01f641317c141bffb4ea7164dad12ec02995b0  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux
52650e3a7d69192b46f1b672fb895bd29118fc05afbb643dc46024152bd6e707  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
d15cfb6f34679c0855565ec784e9fc67dd6bc543fece107fc288bcaf0e00e1dd  ./tailscale/tailscaled_riscv64_Linux
438829e24b46ef7c5f8a2c51534fa569cdf427f3d25feb49e54a7a82582898cd  ./tailscale/tailscaled_s390x_Linux
```


---

- #### Sizes

```console
17M   ./tailscale/tailscale_aarch64_arm64_Linux
7.3M  ./tailscale/tailscale_aarch64_arm64_Linux.upx
25M   ./tailscale/tailscale_aarch64_arm64_Windows.msi
11M   ./tailscale/tailscale_aarch64_arm64_macOS
11M   ./tailscale/tailscale_amd_geode_Linux
3.4M  ./tailscale/tailscale_amd_geode_Linux.upx
12M   ./tailscale/tailscale_amd_x86_64_Linux
3.7M  ./tailscale/tailscale_amd_x86_64_Linux.upx
27M   ./tailscale/tailscale_amd_x86_64_Windows.msi
11M   ./tailscale/tailscale_amd_x86_64_macOS
16M   ./tailscale/tailscale_arm_abi_Linux
7.0M  ./tailscale/tailscale_arm_abi_Linux.upx
11M   ./tailscale/tailscale_i386_Linux
3.1M  ./tailscale/tailscale_i386_Linux.upx
42K   ./tailscale/tailscale_ipn_setup_Windows.exe
22M   ./tailscale/tailscale_merged_aarch64_arm64_Linux
5.5M  ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
20M   ./tailscale/tailscale_merged_aarch64_arm64_macOS
23M   ./tailscale/tailscale_merged_amd_x86_64_Linux
6.6M  ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
20M   ./tailscale/tailscale_merged_amd_x86_64_macOS
21M   ./tailscale/tailscale_merged_arm_Linux
5.3M  ./tailscale/tailscale_merged_arm_Linux.upx
21M   ./tailscale/tailscale_merged_i386_Linux
6.1M  ./tailscale/tailscale_merged_i386_Linux.upx
22M   ./tailscale/tailscale_merged_powerpc64_ppc64_Linux
5.3M  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
22M   ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux
5.6M  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
24M   ./tailscale/tailscale_merged_s390x_Linux
18M   ./tailscale/tailscale_mips64_Linux
18M   ./tailscale/tailscale_mips64le_Linux
18M   ./tailscale/tailscale_mips_Linux
7.1M  ./tailscale/tailscale_mips_Linux.upx
18M   ./tailscale/tailscale_mipsle_Linux
7.0M  ./tailscale/tailscale_mipsle_Linux.upx
12M   ./tailscale/tailscale_powerpc64_ppc64_Linux
3.0M  ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
12M   ./tailscale/tailscale_powerpc64le_ppc64le_Linux
3.2M  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
16M   ./tailscale/tailscale_riscv64_Linux
13M   ./tailscale/tailscale_s390x_Linux
51M   ./tailscale/tailscale_setup_Windows.exe
26M   ./tailscale/tailscale_x86_Windows.msi
32M   ./tailscale/tailscaled_aarch64_arm64_Linux
14M   ./tailscale/tailscaled_aarch64_arm64_Linux.upx
19M   ./tailscale/tailscaled_aarch64_arm64_macOS
20M   ./tailscale/tailscaled_amd_geode_Linux
5.8M  ./tailscale/tailscaled_amd_geode_Linux.upx
23M   ./tailscale/tailscaled_amd_x86_64_Linux
6.6M  ./tailscale/tailscaled_amd_x86_64_Linux.upx
19M   ./tailscale/tailscaled_amd_x86_64_macOS
29M   ./tailscale/tailscaled_arm_abi_Linux
12M   ./tailscale/tailscaled_arm_abi_Linux.upx
20M   ./tailscale/tailscaled_i386_Linux
5.8M  ./tailscale/tailscaled_i386_Linux.upx
33M   ./tailscale/tailscaled_mips64_Linux
33M   ./tailscale/tailscaled_mips64le_Linux
32M   ./tailscale/tailscaled_mips_Linux
13M   ./tailscale/tailscaled_mips_Linux.upx
32M   ./tailscale/tailscaled_mipsle_Linux
13M   ./tailscale/tailscaled_mipsle_Linux.upx
21M   ./tailscale/tailscaled_powerpc64_ppc64_Linux
5.1M  ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
22M   ./tailscale/tailscaled_powerpc64le_ppc64le_Linux
5.4M  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
30M   ./tailscale/tailscaled_riscv64_Linux
23M   ./tailscale/tailscaled_s390x_Linux
```

---

- #### UPX
```console

testing ./tailscale/tailscale_merged_arm_Linux.upx [OK]
  21758087 ->   5457332   25.08%    linux/arm    ./tailscale/tailscale_merged_arm_Linux.upx
testing ./tailscale/tailscaled_arm_abi_Linux.upx [OK]
  29768079 ->  12549596   42.16%    linux/arm    ./tailscale/tailscaled_arm_abi_Linux.upx
testing ./tailscale/tailscale_powerpc64_ppc64_Linux.upx [OK]
  12124295 ->   3064524   25.28%   linux/ppc64   ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscaled_amd_geode_Linux.upx [OK]
  20667996 ->   6007308   29.07%   linux/i386    ./tailscale/tailscaled_amd_geode_Linux.upx
testing ./tailscale/tailscale_mipsle_Linux.upx [OK]
  18029379 ->   7333856   40.68%  linux/mipsel   ./tailscale/tailscale_mipsle_Linux.upx
testing ./tailscale/tailscale_merged_i386_Linux.upx [OK]
  21852295 ->   6340960   29.02%   linux/i386    ./tailscale/tailscale_merged_i386_Linux.upx
testing ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx [OK]
  22347911 ->   5739464   25.68%   linux/arm64   ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_arm_abi_Linux.upx [OK]
  16480630 ->   7319844   44.41%    linux/arm    ./tailscale/tailscale_arm_abi_Linux.upx
testing ./tailscale/tailscaled_i386_Linux.upx [OK]
  20631132 ->   5998708   29.08%   linux/i386    ./tailscale/tailscaled_i386_Linux.upx
testing ./tailscale/tailscaled_mipsle_Linux.upx [OK]
  32953245 ->  12693376   38.52%  linux/mipsel   ./tailscale/tailscaled_mipsle_Linux.upx
testing ./tailscale/tailscale_merged_amd_x86_64_Linux.upx [OK]
  23285895 ->   6884496   29.57%   linux/amd64   ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
testing ./tailscale/tailscaled_mips_Linux.upx [OK]
  33183831 ->  12759916   38.45%   linux/mips    ./tailscale/tailscaled_mips_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx [OK]
  22872199 ->   5834856   25.51%  linux/ppc64le  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx [OK]
  22020231 ->   5585176   25.36%  linux/ppc64le  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_i386_Linux.upx [OK]
  11354804 ->   3234952   28.49%   linux/i386    ./tailscale/tailscale_i386_Linux.upx
testing ./tailscale/tailscaled_amd_x86_64_Linux.upx [OK]
  23678136 ->   6879332   29.05%   linux/amd64   ./tailscale/tailscaled_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx [OK]
  22741127 ->   5506520   24.21%   linux/ppc64   ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx [OK]
  21889159 ->   5264484   24.05%   linux/ppc64   ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_amd_geode_Linux.upx [OK]
  11387572 ->   3494848   30.69%   linux/i386    ./tailscale/tailscale_amd_geode_Linux.upx
testing ./tailscale/tailscaled_aarch64_arm64_Linux.upx [OK]
  33353025 ->  14133960   42.38%   linux/arm64   ./tailscale/tailscaled_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_mips_Linux.upx [OK]
  18126145 ->   7383428   40.73%   linux/mips    ./tailscale/tailscale_mips_Linux.upx
testing ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx [OK]
  12255367 ->   3325696   27.14%  linux/ppc64le  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_aarch64_arm64_Linux.upx [OK]
  16799968 ->   7633484   45.44%   linux/arm64   ./tailscale/tailscale_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_amd_x86_64_Linux.upx [OK]
  12013288 ->   3808836   31.71%   linux/amd64   ./tailscale/tailscale_amd_x86_64_Linux.upx

```

---

- #### Version
```console
$ ./tailscale/tailscale_amd_x86_64_Linux --version
1.72.1
  tailscale commit: c02a1524467844f5a7e93edceb29226fe9fa089a
  other commit: 5c00d019b93a860bd4fb088181c4064a8ec85c8f
  go version: go1.22.5

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
  switch      Switches to a different Tailscale account
  configure   [ALPHA] Configure the host to enable more Tailscale features
  netcheck    Print an analysis of local network conditions
  ip          Show Tailscale IP addresses
  status      Show state of tailscaled and its connections
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
1.72.1
  tailscale commit: c02a1524467844f5a7e93edceb29226fe9fa089a
  other commit: 5c00d019b93a860bd4fb088181c4064a8ec85c8f
  go version: go1.22.5

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


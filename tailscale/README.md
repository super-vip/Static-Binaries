
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
./tailscale/tailscale_aarch64_arm64_Linux:                   ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=yUyDntmwOElwJmaCpaJ0/kLUKm2ckGx6gsPjMLcyc/UhrdlvPLw51CANotqe6e/QtYgnkHI16jkiUIywUYo, BuildID[sha1]=2323cf48302a072187b2e63fbcb64c68129607a9, with debug_info, not stripped
./tailscale/tailscale_aarch64_arm64_Linux.upx:               ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=yUyDntmwOElwJmaCpaJ0/kLUKm2ckGx6gsPjMLcyc/UhrdlvPLw51CANotqe6e/QtYgnkHI16jkiUIywUYo, statically linked, no section header
./tailscale/tailscale_aarch64_arm64_Windows.msi:             Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Arm64;1033, Revision Number: {0E7AD7B3-461A-4A36-A677-D41B9623B443}, Create Time/Date: Tue Aug  4 23:01:47 2026, Last Saved Time/Date: Tue Aug  4 23:01:47 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscale_aarch64_arm64_macOS:                   Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_amd_geode_Linux:                       ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=jYjms5Yp1zvWc-ghI_6e/t7pS3nnrt1PK29P88Rol/78ERjrieGGP9pZqEG2bc/9eeN67j8c1ANXxeb_coF, BuildID[sha1]=52d7c0ed49054e854cc41bafe94444509fe68374, stripped
./tailscale/tailscale_amd_geode_Linux.upx:                   ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=jYjms5Yp1zvWc-ghI_6e/t7pS3nnrt1PK29P88Rol/78ERjrieGGP9pZqEG2bc/9eeN67j8c1ANXxeb_coF, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Linux:                      ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=HkKGglZJpKI58GHpRsQJ/zpIFIz9YKkCgBSOJ3rZA/KxT2iKDUBpfSiK4QzDBN/nHOTF8h8gv9ZXvbO20sK, BuildID[sha1]=a50c6ae3cbc3c5000812cb697833f930e199ae2d, stripped
./tailscale/tailscale_amd_x86_64_Linux.upx:                  ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=HkKGglZJpKI58GHpRsQJ/zpIFIz9YKkCgBSOJ3rZA/KxT2iKDUBpfSiK4QzDBN/nHOTF8h8gv9ZXvbO20sK, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Windows.msi:                Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: x64;1033, Revision Number: {FD437159-2298-499A-A0FF-A861F7616D0C}, Create Time/Date: Tue Aug  4 23:02:09 2026, Last Saved Time/Date: Tue Aug  4 23:02:09 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscale_amd_x86_64_macOS:                      Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_arm_abi_Linux:                         ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=n_CqIsj95vZid6lDh2fx/RcJzCCxkfMG_YSN4bqcp/2RmEbrehA2z8VVqBCDEC/FbHWkh6Z_nfBmn6-S7QG, BuildID[sha1]=9ffd6d724669b2c13077076e8c33d8e100eb63bb, with debug_info, not stripped
./tailscale/tailscale_arm_abi_Linux.upx:                     ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=n_CqIsj95vZid6lDh2fx/RcJzCCxkfMG_YSN4bqcp/2RmEbrehA2z8VVqBCDEC/FbHWkh6Z_nfBmn6-S7QG, statically linked, no section header
./tailscale/tailscale_i386_Linux:                            ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=nxI5rIap14UCvXK3Ze4B/jhkvaLLwtEoysJhpASGT/we-p-zru6nM6FNJT6Nfm/HNt3Xea5deiKOlxisMQR, BuildID[sha1]=947f7d27148c99608e1030a9622fa3eedb1071a0, stripped
./tailscale/tailscale_i386_Linux.upx:                        ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=nxI5rIap14UCvXK3Ze4B/jhkvaLLwtEoysJhpASGT/we-p-zru6nM6FNJT6Nfm/HNt3Xea5deiKOlxisMQR, statically linked, no section header
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
./tailscale/tailscale_mips64_Linux:                          ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=JLKAstwsSO1UDYrku-DE/CDvjLeYfxCI-Waf9ElqP/65tl5F2MolZ3C340TbCf/QgX170Zxad3Brs22E8E7, BuildID[sha1]=7729e037f9c7ef1a23edcc9e07d75e2042aed707, with debug_info, not stripped
./tailscale/tailscale_mips64le_Linux:                        ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=B9Yq59Mey-q0MJTnlZYo/B0ISUEcqdppCBVG9525x/nn3HYLcZzdVbZ2MYNh5_/j7RXZ6pQR0yWPZUE9CRi, BuildID[sha1]=22877a73290f7018040becddc2a27a10893cfc32, with debug_info, not stripped
./tailscale/tailscale_mips_Linux:                            ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=D2NIypC0S8kQMiXQNb_y/kIDIQR4f8_QiSYEdcELw/IoI_uBAqYKjI4vHqoutC/Ypazzpgj208P629g3UVn, BuildID[sha1]=622dc6c43c907ed3a48f3e115dded141dbb7d7c6, with debug_info, not stripped
./tailscale/tailscale_mips_Linux.upx:                        ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=D2NIypC0S8kQMiXQNb_y/kIDIQR4f8_QiSYEdcELw/IoI_uBAqYKjI4vHqoutC/Ypazzpgj208P629g3UVn, statically linked, no section header
./tailscale/tailscale_mipsle_Linux:                          ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=NxTYhFFhltJUn_E9oZuG/WwTV0nk-c7u4VWJ1Fyz5/o51muBKGHsgZdNBkL_yU/ApX62ADkUaF_R5mP7brG, BuildID[sha1]=34b04a0bf79b3cd7d6cc469de65567fb63cebc4d, with debug_info, not stripped
./tailscale/tailscale_mipsle_Linux.upx:                      ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=NxTYhFFhltJUn_E9oZuG/WwTV0nk-c7u4VWJ1Fyz5/o51muBKGHsgZdNBkL_yU/ApX62ADkUaF_R5mP7brG, statically linked, no section header
./tailscale/tailscale_powerpc64_ppc64_Linux:                 ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64_ppc64_Linux.upx:             ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_powerpc64le_ppc64le_Linux:             ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx:         ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_riscv64_Linux:                         ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, Go BuildID=QTpRtSMu9OPQKOvZK_DB/E61toJkJxyuRDugJt1tc/3bHdVtYxEUCPzR86ByvN/wbJXmMQLcnVL23IZs0sJ, BuildID[sha1]=aea2b5e5fac11f359423b61abb01a4203f002059, with debug_info, not stripped
./tailscale/tailscale_s390x_Linux:                           ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_setup_Windows.exe:                     PE32 executable (GUI) Intel 80386, for MS Windows, 6 sections
./tailscale/tailscale_x86_Windows.msi:                       Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Intel;1033, Revision Number: {90655B0F-B17A-4A21-8A9B-2BCB59525A2C}, Create Time/Date: Tue Aug  4 23:01:47 2026, Last Saved Time/Date: Tue Aug  4 23:01:47 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscaled_aarch64_arm64_Linux:                  ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=Vxt5Zk-XIuIkes_UdBVh/0mU0RCVRtn4VJHy4zzDw/HY9euPgVMDMOczbF-KiU/v1VqVRKbWyVO0qs9Fpjj, BuildID[sha1]=7c08f39006f245a2c5193ba8f38865e83bf072d4, with debug_info, not stripped
./tailscale/tailscaled_aarch64_arm64_Linux.upx:              ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=Vxt5Zk-XIuIkes_UdBVh/0mU0RCVRtn4VJHy4zzDw/HY9euPgVMDMOczbF-KiU/v1VqVRKbWyVO0qs9Fpjj, statically linked, no section header
./tailscale/tailscaled_aarch64_arm64_macOS:                  Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_amd_geode_Linux:                      ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=7SEuukMCij6hEHsJICcL/ePxJGNg-jMyB9DKz1gnR/ZFW4UVRddGxWSBgSqYAR/j8ONo8f_7qx91G6jJ8om, BuildID[sha1]=45b708d15b90ccd1d54081d00da0631fc15f07f5, stripped
./tailscale/tailscaled_amd_geode_Linux.upx:                  ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=7SEuukMCij6hEHsJICcL/ePxJGNg-jMyB9DKz1gnR/ZFW4UVRddGxWSBgSqYAR/j8ONo8f_7qx91G6jJ8om, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_Linux:                     ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=WkCutXzv6dlyujKdbNVr/pZIso_cyp-rzkVTK_2-C/-0Q4JBM4Gm7W80FKQX6A/OFAE7B4ZbDVt788Mo1Mw, BuildID[sha1]=a9c96189ccf557713d07196ea1d2c2418c45b312, stripped
./tailscale/tailscaled_amd_x86_64_Linux.upx:                 ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=WkCutXzv6dlyujKdbNVr/pZIso_cyp-rzkVTK_2-C/-0Q4JBM4Gm7W80FKQX6A/OFAE7B4ZbDVt788Mo1Mw, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_macOS:                     Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_arm_abi_Linux:                        ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=o9Sl6kZEGQVBMMsYOD74/GHqC4qIa99-yj7mlFjoW/CK6TTV9GIEWHttHhRVHH/qF3rrs7KXNH2VNfvrvQH, BuildID[sha1]=7430f29ca8f2fcf391326d17941ad80f4d6adac2, with debug_info, not stripped
./tailscale/tailscaled_arm_abi_Linux.upx:                    ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=o9Sl6kZEGQVBMMsYOD74/GHqC4qIa99-yj7mlFjoW/CK6TTV9GIEWHttHhRVHH/qF3rrs7KXNH2VNfvrvQH, statically linked, no section header
./tailscale/tailscaled_i386_Linux:                           ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=trhrtkFjGv49c1lGwJ57/mbVxx3PogNrz-HxFmRCY/uGvR1vVYU7jPh-T6_s_V/DcXYdIJE5UlcjXyoPnXI, BuildID[sha1]=92e41d7c27b2fb0e1e5811b73cdb4b8b08afe3c6, stripped
./tailscale/tailscaled_i386_Linux.upx:                       ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=trhrtkFjGv49c1lGwJ57/mbVxx3PogNrz-HxFmRCY/uGvR1vVYU7jPh-T6_s_V/DcXYdIJE5UlcjXyoPnXI, statically linked, no section header
./tailscale/tailscaled_mips64_Linux:                         ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=0c1uq54OWjnLOpEoVxoA/b0W90rfyjgFQGYjjgAej/bEFUOX5Weqk1LO6MTzrJ/Nb54c1_GTe4001k6L34t, BuildID[sha1]=89094cd97427536c89c3ff9c9c6d87a4a319829f, with debug_info, not stripped
./tailscale/tailscaled_mips64le_Linux:                       ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=c93WDaXpjjjFWPiaQTYV/WRnfE-FJJcWs8jj-O0vu/1JiukJUs4ymvfawQ1tOP/IbeNO-ADh2PcDrqYsdx4, BuildID[sha1]=85d95e9fdb207485cbfe378cf60916681f2310c8, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux:                           ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=-jheiAX_32_kicfUV028/60jqJtWISP3XuwyLkW5-/MjAh5EE14sVx9Ryxiz47/fzISRNXFzG-q0edY5FMg, BuildID[sha1]=ef654a8d9ec51ced6d0c5231cc1fac937f29eba1, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux.upx:                       ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=-jheiAX_32_kicfUV028/60jqJtWISP3XuwyLkW5-/MjAh5EE14sVx9Ryxiz47/fzISRNXFzG-q0edY5FMg, statically linked, no section header
./tailscale/tailscaled_mipsle_Linux:                         ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=evGSg0UtvcEVSv5SRiPh/86_r0Upz5dxEUd1foyCd/51D5HE59PHpCGbOOlLLA/9f1BfYza_hv2cC03eDyC, BuildID[sha1]=37e8506f6186c9404944f20fa9937d2a11f188fa, with debug_info, not stripped
./tailscale/tailscaled_mipsle_Linux.upx:                     ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=evGSg0UtvcEVSv5SRiPh/86_r0Upz5dxEUd1foyCd/51D5HE59PHpCGbOOlLLA/9f1BfYza_hv2cC03eDyC, statically linked, no section header
./tailscale/tailscaled_powerpc64_ppc64_Linux:                ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64_ppc64_Linux.upx:            ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_powerpc64le_ppc64le_Linux:            ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx:        ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_riscv64_Linux:                        ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, Go BuildID=qg-xE-QZ5seqeuoScbG1/lL_br6ELsGS79_sVCD4A/tgSFdgFcLmJEQjEugZ-K/rwV0exkKtytznQQvamhw, BuildID[sha1]=23f6c2208d67913f0e09ff56eb8724b7fd6d5487, with debug_info, not stripped
./tailscale/tailscaled_s390x_Linux:                          ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped

--> SHA256SUM
95fcc3e02d149e92f8b9139000e73e1e4cac84de421ee8b49218144b0b4aaceb  ./tailscale/tailscale_aarch64_arm64_Linux
ec5b31f6f7be6251e47239bfe27f802be265beb101e533a508180bfb5f799b6d  ./tailscale/tailscale_aarch64_arm64_Linux.upx
80be3b1c902a5914ef164052258df80eb2acb1daa5a7c9fd2c1041f7903cf407  ./tailscale/tailscale_aarch64_arm64_Windows.msi
758bd296723a348a70f5274b294baeb4053abd2e2ce58e2220e210946b618c6f  ./tailscale/tailscale_aarch64_arm64_macOS
9e26af35e0e3c14ceddb09fd90b94f6a10ec5efba96b8d9baa42a67736e40ccf  ./tailscale/tailscale_amd_geode_Linux
eebf225404220c1946598546352d5727408a139b7e08f05c6dd1edc8246edadb  ./tailscale/tailscale_amd_geode_Linux.upx
395c46563c1280c9b1f78120fcd632f1956f941aae7287a07af32adcb316b90f  ./tailscale/tailscale_amd_x86_64_Linux
02af6cd6b5761c23e8715eab7b822382db9449cda7291612b6a560eff03d43a2  ./tailscale/tailscale_amd_x86_64_Linux.upx
d2eb69e103b08a5b77de9d7cb8555541aa99f7dfc6048850b2286a1048c885f9  ./tailscale/tailscale_amd_x86_64_Windows.msi
248b7930c0c4c650f988bcb90a968da042066e0b826bf58efd8fe3a69fad8e7f  ./tailscale/tailscale_amd_x86_64_macOS
0a95771b8a0db62a83f49ac9b75440f19b440a200a05034309ac358d680b14dd  ./tailscale/tailscale_arm_abi_Linux
c478e7a2d2295b86b17a976f0109135a994784209669a09a3f2d4f857c0d4dae  ./tailscale/tailscale_arm_abi_Linux.upx
46a0934ce4fca167fa1cac3fa8149ce01d6e78cfb08fb44c70ccc1f22010f937  ./tailscale/tailscale_i386_Linux
522e54cc08ebe6d2ca0965a75219879d954f566a4e97b0bf0945e1a5e8fcfef3  ./tailscale/tailscale_i386_Linux.upx
8a5ae53c76968d5810af928057a161ee931a261fa84b88353c707d783b8d0edc  ./tailscale/tailscale_ipn_setup_Windows.exe
f2bf88f21aefe55eac6705b82c0f488e6a9451bd8d4aae193490ea50b4f95585  ./tailscale/tailscale_merged_aarch64_arm64_Linux
508e2d687b96b300c074be0a5cb19f36ac9d06a244080b7ba093c21f8eb2cd82  ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
68728bde1313493eb44dbd3be2e989eb00f60f4938d0d2845df9d45e32c25df7  ./tailscale/tailscale_merged_aarch64_arm64_macOS
e0f1a1a13ed63b61b5a0d0d526e35e980b56aac34d0633480b0982ea1a2dc9ae  ./tailscale/tailscale_merged_amd_x86_64_Linux
b838c46545cc311ac10075628734178700f7e29a04d5a7444ada8e31dc7513fb  ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
267bebcfe539dd8353add30caf55a042bf996f8e688aae7910b9ecf61714f3f8  ./tailscale/tailscale_merged_amd_x86_64_macOS
c00fcfd58412ed34ada8ea983983f7d6af0c25a17485dc3a27bced9a67d99d8d  ./tailscale/tailscale_merged_arm_Linux
ebb00735265d0ced0f81a975ff978cae29ad9beb10f9ac4ad7bdaceb51b3ac75  ./tailscale/tailscale_merged_arm_Linux.upx
c3fffbe9e1dfd5275334859bb4d24921a5a7db34f188fe1f61e82dd5eb601ca3  ./tailscale/tailscale_merged_i386_Linux
1c779fe50b4ce1ffd89a6ac5001cee45ef223923142106c229f133348308d5ae  ./tailscale/tailscale_merged_i386_Linux.upx
1d2e3a96894c633967d9a50d3e2107f80515caa80a355a0bcf5b4d17c39fff01  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux
f5ff217e8e2211c7eb36c264e1218505c719d6f26779b1d19775fa217a102d91  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
cb68d8c546a1eeca45209639f7f4a3c3d99be3e1e1d2d43cab69d9083339f8a9  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux
223d4547acb34f74cdc7eb7b6ac660e18a332016ff9ce3e9c427e5c045e8fa46  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
77dcecdb06ea0ba53c061d976eb2a45719053d0d37bc22e6834dcbaf2b4cb7e8  ./tailscale/tailscale_merged_s390x_Linux
4699873d9560ad3644e00b01f226928d3c98794b655efc3dc35dc3939288ac70  ./tailscale/tailscale_mips64_Linux
e14236a4ecf61c528bd567a0c858af83cb1c71063e1750aeb095b84443777073  ./tailscale/tailscale_mips64le_Linux
2650ece34cf21d579687d568403fabcd3590b12e5429167a57a0c16083346c47  ./tailscale/tailscale_mips_Linux
fdd556d2709bf24c3d3bd254706e853252e835caf0804c99fb8c90b65641ba26  ./tailscale/tailscale_mips_Linux.upx
ec68fb0b7bce8a180d50cb8099e97fa6679231bb48fd530e293ace33dc8c3625  ./tailscale/tailscale_mipsle_Linux
5b33298ae9440a51a431a529f5eafb393f0c854a5613b0619f84b8aff3aac1b2  ./tailscale/tailscale_mipsle_Linux.upx
2d8174d28ff4f6852e72964fcf4d2ae533186149cf814cfa9c1d547bc28dce24  ./tailscale/tailscale_powerpc64_ppc64_Linux
d3c2aac7a6220634ceb2255a3c144548c574e319bd342ceb21f8aa7c023908eb  ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
97a750d868239a3c6bcfdf03243ad7fea59f253f991e944de45308ef6b3e18c7  ./tailscale/tailscale_powerpc64le_ppc64le_Linux
7f8c074713db8669d7a93669fda3f6d5ad61641afbf9368f4132263d979eb665  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
b076c15c39c903db3076bbb8d436fa99db112d1f63f0a2b212202d02c7a35fb8  ./tailscale/tailscale_riscv64_Linux
5b7025ed53cb585aa59e26bd20a770c1e36499f14672d27a7e8602f670ba5163  ./tailscale/tailscale_s390x_Linux
64a8ad28cbb67a6171236abe39f75a039a761a0e1aacdef75b26781887cef9a8  ./tailscale/tailscale_setup_Windows.exe
c628a6ea3bb435e568dee22bc1a627f8d29b9d20d9b94b832323a53a24321e6e  ./tailscale/tailscale_x86_Windows.msi
b05057b0cd33ce0b989d11ef015295ba150e469c4f21b07f355f390e9ed011d5  ./tailscale/tailscaled_aarch64_arm64_Linux
ae371da38b74eb76d7fa53671faa0d2b9a7558816ebfac38ee754fb5ab3fec0e  ./tailscale/tailscaled_aarch64_arm64_Linux.upx
3045786fe6191b3d64ae9d2b03b5fffcf080e3cb3073a3c2e8e69e57ea05e2cf  ./tailscale/tailscaled_aarch64_arm64_macOS
d111036d678d38eda4eb4af33ef629706136aef892623d777f84c4b4c2413527  ./tailscale/tailscaled_amd_geode_Linux
f1b987bcef62ec0044ff21fe0ae4fc4a69b773c004eb6ba6df4930123877776a  ./tailscale/tailscaled_amd_geode_Linux.upx
e3d9ade73b5b69a9220551b43475dcc99ecf9e9d27a4a135d70e2faeb6f736ca  ./tailscale/tailscaled_amd_x86_64_Linux
2c2e202660c53baf9a4558862616f65421f377b56f807b75cdc7b85ad9d48018  ./tailscale/tailscaled_amd_x86_64_Linux.upx
b5304b43985998d94d5c2c94e0eeb9e160a76906fa0ecb224af45c3b878e684d  ./tailscale/tailscaled_amd_x86_64_macOS
5f9e666064f3f2a8e944eff0495f087636f173cfc46a348c05f98ba332645bb3  ./tailscale/tailscaled_arm_abi_Linux
ff762bf3382e87e5debad6e6009348817a0e2b3934ac0c77ca7aceb76b85d5fe  ./tailscale/tailscaled_arm_abi_Linux.upx
816daf66651cb122d8f8c2889ccdd33022f53b2610832fe760bafb6c871d720c  ./tailscale/tailscaled_i386_Linux
b4cd98697cf3549e2513f707a345dc95e63a6abd766ba9790b931272354fd137  ./tailscale/tailscaled_i386_Linux.upx
45ab335b1c1826c0d964d25c70fcb1867435620647245540d26a6bdb3d822f5d  ./tailscale/tailscaled_mips64_Linux
d75509464179bd1ab522d836a8d118c127209024ae720f5d15c463e2992e00c8  ./tailscale/tailscaled_mips64le_Linux
5d211f7df4732b4fa3f75ca206560685e54598927f08876ad123e1124c368dde  ./tailscale/tailscaled_mips_Linux
829bc6014a7b343e05c9d92bb3f5ee799f525ae7b76a897f8de89e4349e7557c  ./tailscale/tailscaled_mips_Linux.upx
d75473e4b2b68536df5d7b2c40ca71f901f4bc8a21eaf97e74b6267fff0ee673  ./tailscale/tailscaled_mipsle_Linux
b9d7782211fc562f8edcb4f8299b64e47202d925a04f62363c8db28bdf32b841  ./tailscale/tailscaled_mipsle_Linux.upx
e76fef5ae8bf287b4fee4ed0c0e94dd0704d92495197e73e9f9ce519b9460976  ./tailscale/tailscaled_powerpc64_ppc64_Linux
0a1f66a4dd94ccb7d0038ffb2d04917a0ea5c6afe79a839a848ea0cda84d726d  ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
d574f23fc3fb383a63e710f55e33f51ce9e8dec7dbcfe5c5a4bcfbb259d645d7  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux
7b9d0ba1f4a32cfdf07afe010405b06de37feae67e6e16051721297b23c8794e  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
00fe427a27f0a85593d85658e64fb0a9d2ba382e59de74470f16d6ba8fb15094  ./tailscale/tailscaled_riscv64_Linux
a750c39d8f900024dd26a40ccb61d98a0b2fa8c6a5cd6182dfc1899671ea0b51  ./tailscale/tailscaled_s390x_Linux
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
  26935422 ->   6404040   23.78%   linux/ppc64   ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_amd_geode_Linux.upx [OK]
  21651428 ->   6031100   27.86%   linux/i386    ./tailscale/tailscale_amd_geode_Linux.upx
testing ./tailscale/tailscaled_mipsle_Linux.upx [OK]
  40600769 ->  15277280   37.63%  linux/mipsel   ./tailscale/tailscaled_mipsle_Linux.upx
testing ./tailscale/tailscale_amd_x86_64_Linux.upx [OK]
  23155272 ->   6460116   27.90%   linux/amd64   ./tailscale/tailscale_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_merged_i386_Linux.upx [OK]
  36155518 ->   9576436   26.49%   linux/i386    ./tailscale/tailscale_merged_i386_Linux.upx
testing ./tailscale/tailscale_merged_amd_x86_64_Linux.upx [OK]
  38572158 ->  10241972   26.55%   linux/amd64   ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
testing ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx [OK]
  26869886 ->   6642724   24.72%  linux/ppc64le  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_powerpc64_ppc64_Linux.upx [OK]
  22544510 ->   5210512   23.11%   linux/ppc64   ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscaled_i386_Linux.upx [OK]
  25731468 ->   7364444   28.62%   linux/i386    ./tailscale/tailscaled_i386_Linux.upx
testing ./tailscale/tailscaled_amd_x86_64_Linux.upx [OK]
  29790168 ->   8325428   27.95%   linux/amd64   ./tailscale/tailscaled_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx [OK]
  37748862 ->   8349144   22.12%   linux/ppc64   ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscaled_aarch64_arm64_Linux.upx [OK]
  40127347 ->  16483132   41.08%   linux/arm64   ./tailscale/tailscaled_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_aarch64_arm64_Linux.upx [OK]
  30823196 ->  12597064   40.87%   linux/arm64   ./tailscale/tailscale_aarch64_arm64_Linux.upx
testing ./tailscale/tailscaled_mips_Linux.upx [OK]
  40776101 ->  15308064   37.54%   linux/mips    ./tailscale/tailscaled_mips_Linux.upx
testing ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx [OK]
  35848318 ->   8399972   23.43%   linux/arm64   ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_arm_abi_Linux.upx [OK]
  30567373 ->  12365856   40.45%    linux/arm    ./tailscale/tailscale_arm_abi_Linux.upx
testing ./tailscale/tailscale_mipsle_Linux.upx [OK]
  33613227 ->  12431976   36.99%  linux/mipsel   ./tailscale/tailscale_mipsle_Linux.upx
testing ./tailscale/tailscaled_amd_geode_Linux.upx [OK]
  25768332 ->   7374040   28.62%   linux/i386    ./tailscale/tailscaled_amd_geode_Linux.upx
testing ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx [OK]
  22544510 ->   5429040   24.08%  linux/ppc64le  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_merged_arm_Linux.upx [OK]
  35651710 ->   8205236   23.01%    linux/arm    ./tailscale/tailscale_merged_arm_Linux.upx
testing ./tailscale/tailscaled_arm_abi_Linux.upx [OK]
  36568120 ->  15137624   41.40%    linux/arm    ./tailscale/tailscaled_arm_abi_Linux.upx
testing ./tailscale/tailscale_mips_Linux.upx [OK]
  33763951 ->  12461788   36.91%   linux/mips    ./tailscale/tailscale_mips_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx [OK]
  37748862 ->   8649752   22.91%  linux/ppc64le  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_i386_Linux.upx [OK]
  21598148 ->   6020456   27.87%   linux/i386    ./tailscale/tailscale_i386_Linux.upx

```

---

- #### Version
```console
$ ./tailscale/tailscale_amd_x86_64_Linux --version
1.102.2
  tailscale commit: 6cac918179d4d673bfebe2fc74f81183ddd73fea
  long version: 1.102.2-t6cac91817-g6ff0ddc72
  other commit: 6ff0ddc7264e38276f40986706ae4607dbab57d8
  go version: go1.26.5 (tailscale/go 63ae404c82)

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
1.102.2
  tailscale commit: 6cac918179d4d673bfebe2fc74f81183ddd73fea
  long version: 1.102.2-t6cac91817-g6ff0ddc72
  other commit: 6ff0ddc7264e38276f40986706ae4607dbab57d8
  go version: go1.26.5 (tailscale/go 63ae404c82)

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


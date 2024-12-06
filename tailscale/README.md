
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
./tailscale/tailscale_aarch64_arm64_Linux:                   ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=92JgRslrt5DGAHg6i6yf/z2Wo1Kxyx3AkcmRxobNM/EOvL4Cah9gX5udP-5Dd8/rFJDKzDJtR56PrvLY3Ip, with debug_info, not stripped
./tailscale/tailscale_aarch64_arm64_Linux.upx:               ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_aarch64_arm64_Windows.msi:             Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard.WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Arm64;1033, Revision Number: {D0FF3D54-C1B9-48CE-9591-00ADDBF24450}, Create Time/Date: Thu Dec  5 20:50:04 2024, Last Saved Time/Date: Thu Dec  5 20:50:04 2024, Number of Pages: 500, Number of Words: 2, Name of Creating Application: Windows Installer XML Toolset (), Security: 2
./tailscale/tailscale_aarch64_arm64_macOS:                   Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_amd_geode_Linux:                       ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=LZUKe1WTbAtzsKhEH1eG/a1Nf9fr5SeZ-TQmcSbZ7/cCR_jYe6eTdgf4oA_KI5/Mpl701T31O_gKPg517Qc, stripped
./tailscale/tailscale_amd_geode_Linux.upx:                   ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), statically linked, no section header
./tailscale/tailscale_amd_x86_64_Linux:                      ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=BuKd6iQs-XYn6haeNnTj/HXzOQMXqeK84MQieRitQ/pO2rfgAfnkZKzSEq2N4g/02i_T-bALXEWfKf0Krkg, stripped
./tailscale/tailscale_amd_x86_64_Linux.upx:                  ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_amd_x86_64_Windows.msi:                Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard.WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: x64;1033, Revision Number: {351299DC-DBFB-49A3-9143-38EDA711FBC8}, Create Time/Date: Thu Dec  5 20:50:26 2024, Last Saved Time/Date: Thu Dec  5 20:50:26 2024, Number of Pages: 500, Number of Words: 2, Name of Creating Application: Windows Installer XML Toolset (), Security: 2
./tailscale/tailscale_amd_x86_64_macOS:                      Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_arm_abi_Linux:                         ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=OoNryTlFR86V2RWsOmQt/KWYsKhl5yjnk5uW_b2EW/rzkIb9xfNeDeN3OyPPVr/MXotRFPEfEm3oTYSD9PC, with debug_info, not stripped
./tailscale/tailscale_arm_abi_Linux.upx:                     ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), statically linked, no section header
./tailscale/tailscale_i386_Linux:                            ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=NFn7cg2nUXUnKlQSWtPQ/sbkn4etOO5ZZL-R7kd1b/NJDfqu-X3xwu812f4L6_/ai1Oxliartz5m9T6km7j, stripped
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
./tailscale/tailscale_mips64_Linux:                          ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=gI0ycMk-KkgddW04e4Pc/zABGFfYxMcsxc9PLZvUy/gMLYqh9Yr8rt3kdSHxWX/sIfuOwZmQGNQ1kb6oQdh, with debug_info, not stripped
./tailscale/tailscale_mips64le_Linux:                        ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=xHVNwd-5B3iDRg1KntwN/-waXPHK0LPn56v4msGBL/cC2st7ksPfdNuoxDuJan/z1D3qbZUkjrvK5YJRpf-, with debug_info, not stripped
./tailscale/tailscale_mips_Linux:                            ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=KACa5kfcKaypK5GRTDPA/fbDLEh_giK2Wf4mfSxET/z7004LScwxGstkVQ7Kz6/rtIoDBjwm9mq36LdqFkr, with debug_info, not stripped
./tailscale/tailscale_mips_Linux.upx:                        ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_mipsle_Linux:                          ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=XqsYR-OoXf5oRH_bSxhp/XliirISj_pkuYFVjTBrw/wTT4HuhNWQMWtE4AEnj7/L2ko_CoI-zrMK9NWXYYu, with debug_info, not stripped
./tailscale/tailscale_mipsle_Linux.upx:                      ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_powerpc64_ppc64_Linux:                 ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64_ppc64_Linux.upx:             ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_powerpc64le_ppc64le_Linux:             ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx:         ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_riscv64_Linux:                         ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, Go BuildID=wmchEkKJLCNK73u5DXB2/oFvHIy-qDJUlI7AMwcH1/IJEW2E7R13082qkzaYQv/oumEJYTkeL5LEYA8DIOU, with debug_info, not stripped
./tailscale/tailscale_s390x_Linux:                           ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_setup_Windows.exe:                     PE32 executable (GUI) Intel 80386, for MS Windows
./tailscale/tailscale_x86_Windows.msi:                       Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard.WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Intel;1033, Revision Number: {64A2F827-E38F-4414-8817-CC74534391DE}, Create Time/Date: Thu Dec  5 20:50:04 2024, Last Saved Time/Date: Thu Dec  5 20:50:04 2024, Number of Pages: 500, Number of Words: 2, Name of Creating Application: Windows Installer XML Toolset (), Security: 2
./tailscale/tailscaled_aarch64_arm64_Linux:                  ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=6bO4qvPl3J9sAj5bVJud/TCx9hm_LD95-tUp63ftA/hX3orLgw00QftX7oGy4x/BWGAUzSSXz64kWOslj5G, with debug_info, not stripped
./tailscale/tailscaled_aarch64_arm64_Linux.upx:              ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_aarch64_arm64_macOS:                  Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_amd_geode_Linux:                      ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=lY91LGrQ2t0ijDJ6diNH/leNQBzvSVCDinenz_K1I/XdlDgkS1JXn7LRzlPngo/3AxMRPJNjAOzaIogT5-I, stripped
./tailscale/tailscaled_amd_geode_Linux.upx:                  ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), statically linked, no section header
./tailscale/tailscaled_amd_x86_64_Linux:                     ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=KOHKl3m6ZNsmcijj_38X/xCt6kxdO_i0RPt-ZOMyt/AWKElErD1HFLW1ZHBSvb/MPzAVs1eBRkxq5uO3utL, stripped
./tailscale/tailscaled_amd_x86_64_Linux.upx:                 ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_amd_x86_64_macOS:                     Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_arm_abi_Linux:                        ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=kIR2Q72R8Wh8L77pdxeG/Ygs7O4RP_-p3tfy1VH8g/KHG7f02vx9VwHyOdjJfJ/e4aTaEpq9xBa4akdh9py, with debug_info, not stripped
./tailscale/tailscaled_arm_abi_Linux.upx:                    ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), statically linked, no section header
./tailscale/tailscaled_i386_Linux:                           ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=syR_nsBPJZ6NADWjkjLf/EOFXLLZn2ZVbRRQ8X5Ji/TnMVkwGEGrTKiNDQ1Bw4/V-IGmiia26F_3EOE8dUK, stripped
./tailscale/tailscaled_i386_Linux.upx:                       ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), statically linked, no section header
./tailscale/tailscaled_mips64_Linux:                         ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=QjzExnDrO7-7IpFeNVAu/SLQj2iz1ZKrkbZcJO01O/dNXBAfHvm69XrUBP53Tm/F-mbYsASYoSGCif_tm0i, with debug_info, not stripped
./tailscale/tailscaled_mips64le_Linux:                       ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=m1ikrlacWCwMI0mOXY_K/O5LAC0N2qHwMlb__OtBO/x8N2rbMT4mGgTMQt2MA2/ABDCuuhvLQZ_X3uch0-u, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux:                           ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=b8mYEXOoQdIjrp7ksffZ/io7z4pnzLH7iIMgfZeFw/g_-MyqzYxL1-8SNFrcrn/Xg8VXbrCRnML3WcoeI1g, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux.upx:                       ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_mipsle_Linux:                         ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=qAneZsfF5BbrVqCUKEAR/B38Pn6-3JQTddcUdJC98/RqaIqK7MkjyWDcqIfJN-/uboov5NN7ou7vHMkXD3V, with debug_info, not stripped
./tailscale/tailscaled_mipsle_Linux.upx:                     ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_powerpc64_ppc64_Linux:                ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64_ppc64_Linux.upx:            ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_powerpc64le_ppc64le_Linux:            ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx:        ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_riscv64_Linux:                        ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, Go BuildID=7M2CIWbxxPCcDJyzLxc8/uWB5MglV6Dhwih3SqdH3/eC8iCH3CAG9XSrdTy8T3/nv1YjUp92dnrlkPYomPk, with debug_info, not stripped
./tailscale/tailscaled_s390x_Linux:                          ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped

--> SHA256SUM
8be2e1f216fbf464308c623d8b8efe016b12f845ba1a14c22f71d7e1ae23e6c8  ./tailscale/tailscale_aarch64_arm64_Linux
29e1a544b8059eadcd090f91ec7d697be459e46145836b27e0da6cdecf978748  ./tailscale/tailscale_aarch64_arm64_Linux.upx
7884be361acabf17bcdc4c8677852e8b5f26be97095b4eb1d82c96582873075d  ./tailscale/tailscale_aarch64_arm64_Windows.msi
758bd296723a348a70f5274b294baeb4053abd2e2ce58e2220e210946b618c6f  ./tailscale/tailscale_aarch64_arm64_macOS
eb7ba6df2ee3feacb2ccfa0e5b9609ec2544de79fe0b1025688f2b067116e573  ./tailscale/tailscale_amd_geode_Linux
81014af9724420c416c054957a46b9171e43b6315e1daf3e0ab97e573748edfc  ./tailscale/tailscale_amd_geode_Linux.upx
1064c3d39a3cd37d8fb36a6524abd8c1225e28cb30db9e759d2d827a3302e59c  ./tailscale/tailscale_amd_x86_64_Linux
74deffbd2b47536147b669b3c6ea5884073660c981a69f15af4cee3f4710c263  ./tailscale/tailscale_amd_x86_64_Linux.upx
dffa2ec6f62438572123090f37225381eb5c4848d879a5832badd7ebbab25aab  ./tailscale/tailscale_amd_x86_64_Windows.msi
248b7930c0c4c650f988bcb90a968da042066e0b826bf58efd8fe3a69fad8e7f  ./tailscale/tailscale_amd_x86_64_macOS
544d1775ca0773dd60811437fc2c8c1f9903f79f4936b26e42fa7a3f2f60cac7  ./tailscale/tailscale_arm_abi_Linux
bd7f3e2f3dfe8323a01ee06b6c42945b853cba175e5366a23536168ad08e883a  ./tailscale/tailscale_arm_abi_Linux.upx
1d9785081248c01dfe4db84693ac1c3c08c03f25bcfd0eab20c7984428211adf  ./tailscale/tailscale_i386_Linux
72c0b0a5376bed117e7fc444d87028086e5210ecc38d2ef2c5350acd54d5b457  ./tailscale/tailscale_i386_Linux.upx
ef8e1615aa23a3a9de5db28089838c7479ca3c3fb157696bcb1819f5c38345b4  ./tailscale/tailscale_ipn_setup_Windows.exe
f20658a5eabcc925d5bb1f500423bbbf8c22b72a9fd99dbb24390ebc2bca0c83  ./tailscale/tailscale_merged_aarch64_arm64_Linux
ef02e3a6821a8ed228c6b3fd8be3c608d570ab8953c157b4e05973cd25f0bae0  ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
68728bde1313493eb44dbd3be2e989eb00f60f4938d0d2845df9d45e32c25df7  ./tailscale/tailscale_merged_aarch64_arm64_macOS
370a2651a565bff644b718212ef113586b864eb81046334fac7bd4bfc3b5ee0e  ./tailscale/tailscale_merged_amd_x86_64_Linux
4c8268d65b6897a1d04c915e5484b17ccb74cc0b0d577e6c4540ceb9f8686d9f  ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
267bebcfe539dd8353add30caf55a042bf996f8e688aae7910b9ecf61714f3f8  ./tailscale/tailscale_merged_amd_x86_64_macOS
5a6cbf59765eb7f853cb6828f2b0692ef46b1fc663b84f8202c42dde2481f406  ./tailscale/tailscale_merged_arm_Linux
163aa017d082ab2bb3a7ade7c52461f236168df75c96da318fa889312e2c5dac  ./tailscale/tailscale_merged_arm_Linux.upx
0146630822a4e365b36fdd7c5b9c1a5a0beefac2c8d8702f3dda3b243485aba1  ./tailscale/tailscale_merged_i386_Linux
763100c9c93455e01c6d9463019b800f7eb7dd59dca64e32e6aab8e14d6859f2  ./tailscale/tailscale_merged_i386_Linux.upx
147fabc702aaac66976a3d0e8186e8545dc749a01e04c6eecb76aba9ae28129b  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux
9ac901371db1941429d58f559bf336ff8882876d9360e481b3420894f4f121c6  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
a0bb8ab686d7d77ca537ff67b2a5a25282eeeb7aa13cb792bb787f9d443bd021  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux
2c53eba50024a65fa76445a1bd8e2c404304a70f0be40b01078f911e546f58e7  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
660f36d6182dd977633cd0406914fd74104f53d2b5ba79f27ff33898b532500b  ./tailscale/tailscale_merged_s390x_Linux
096158ef2bd65ed68be2e318297b4f9bdd91ff7c5d09f2ea6d2d01cd788e98f6  ./tailscale/tailscale_mips64_Linux
202abb4a4fa2a79da03e571c2331f3e7935ca2fcbec9835123dfc71f31103d6c  ./tailscale/tailscale_mips64le_Linux
6ae80dc0824ae250525fc9e0ae8b14eda69536a6ebd554153bd473432a56b58d  ./tailscale/tailscale_mips_Linux
27745469280d934becd8d1baca8769684635f192d046c91116db4a33a5d84443  ./tailscale/tailscale_mips_Linux.upx
18b203d42586a51bd1cc5d8ada14e1bd5ac2d6a020167c800d41f2ab4be2fd05  ./tailscale/tailscale_mipsle_Linux
741dfee4c19e12c088148d630ae27db5f7f8c516e13ad5ede45f9471819daca9  ./tailscale/tailscale_mipsle_Linux.upx
6ce0ab9bc4962ac21d4ba42832ba8eace88c2768df76ee7313f9105856d9bcff  ./tailscale/tailscale_powerpc64_ppc64_Linux
083fca618b87bab036612cda1b3c9a018845ec4cb5e07c84f7054f6acbcda617  ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
e40d6fa82f97e8757482f2f6fc23cd79cff75ef6181bb79f1c000bb9ac97770a  ./tailscale/tailscale_powerpc64le_ppc64le_Linux
f400859fcdd2f4cfd9e68b2369138ad0d042baa17e23897dbb2945fddbcbb607  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
dc8f8e83de2d23ba89e378327f1c46881a507cf05e00d71e9cfd361139a9b1d2  ./tailscale/tailscale_riscv64_Linux
edff26aa58728405b9a7aace7f12d9817e752ce4c4bbf7ac9643354c9a9b120e  ./tailscale/tailscale_s390x_Linux
64a8ad28cbb67a6171236abe39f75a039a761a0e1aacdef75b26781887cef9a8  ./tailscale/tailscale_setup_Windows.exe
99379db8b57a13dc7af16bb775595d4626e85b7a30df33e23a00689c9bdcbac5  ./tailscale/tailscale_x86_Windows.msi
e213cdac978b1d6ca854e19c34f525cbf23a3d40a83285acce81cf59ea217ef9  ./tailscale/tailscaled_aarch64_arm64_Linux
fd0b2949941952c1b2a3c3baf0c3a6066e40832ca308d810222a0779761f30a0  ./tailscale/tailscaled_aarch64_arm64_Linux.upx
3045786fe6191b3d64ae9d2b03b5fffcf080e3cb3073a3c2e8e69e57ea05e2cf  ./tailscale/tailscaled_aarch64_arm64_macOS
bafb7f22702e5a02cc9f2031b45f366e2430e4c9b15a68b395486103279d27f3  ./tailscale/tailscaled_amd_geode_Linux
af6dfad7fddbe0eb5bf1dc16a203f3301eea5d30cf9cca1c4302f9fa03bc1dc5  ./tailscale/tailscaled_amd_geode_Linux.upx
7877e19589d04a80e0f4b727847aee94a4a2b073035f742b2f4473dba09cdb8c  ./tailscale/tailscaled_amd_x86_64_Linux
1cc790e703ea592dbe27075e1603fbae00946ad2ab0ee70d204b800916eaa59e  ./tailscale/tailscaled_amd_x86_64_Linux.upx
b5304b43985998d94d5c2c94e0eeb9e160a76906fa0ecb224af45c3b878e684d  ./tailscale/tailscaled_amd_x86_64_macOS
7b884c6d94c4e42018d1d5617a28f744aea239e11944e002a7440f07aeeec3f2  ./tailscale/tailscaled_arm_abi_Linux
8608a7cc23b08a021b4b8f4f63d6ff512f01c3d1370248ed6fc1086f6a6738ca  ./tailscale/tailscaled_arm_abi_Linux.upx
052d93190b12120a893d1e4d6c33b2264086968aefe0f6a8acc0f39d130142f2  ./tailscale/tailscaled_i386_Linux
a581d58caa8f8001c134b41006dfc32696cebf4e51848e85bc2787ced03a1eb8  ./tailscale/tailscaled_i386_Linux.upx
c6d8b5bc9b8702db929772281c3f2d768e1f065b109385bdb3f56ef17ec26dac  ./tailscale/tailscaled_mips64_Linux
e6a26e2f5df70dd3f6c6e31cb54bb34edb6608d054d55f6adf3a7c0fd7b384a6  ./tailscale/tailscaled_mips64le_Linux
e58969f4880cd96f0b72c4a31220e92921f49bee1a62320ec397333bbeeb00de  ./tailscale/tailscaled_mips_Linux
b7b01b493d9c923bf33fec0915c0a7305cf210d7520c8ec05fec854199d57fd9  ./tailscale/tailscaled_mips_Linux.upx
8e650124712b2d97f00c32fcc5df2eb553236928cbc558426e0054c383b7efb6  ./tailscale/tailscaled_mipsle_Linux
64469e4f415e49feee2a9141bfe8e5b79c96e8b0139f89b2ece5355a2755a855  ./tailscale/tailscaled_mipsle_Linux.upx
13f45a42820595a34ea29dc9f6a668bc7ef1eaa9d17f54a6bce41eb8ccf68dab  ./tailscale/tailscaled_powerpc64_ppc64_Linux
a3fb510b3519c2d0fdca27f70a72cf374f6898c0b51a581a2a372c73f3f373f1  ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
5b3adbc703eae9192d4034dc783455b2051e101e9129fe9868c02500aaed42da  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux
3e34a36cdef6e5b159a5e42eb0d9a6bbbe74ac7622e4aa63d71f3b597f90b528  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
1275e0700d759bc62c3c7757996c7f6525dbf9b7a84615454270b6a40015452b  ./tailscale/tailscaled_riscv64_Linux
bfb3e29e425e36f976b0a400c138ce1b6600a89bae16e21386243b85e406cec3  ./tailscale/tailscaled_s390x_Linux
```


---

- #### Sizes

```console
18M   ./tailscale/tailscale_aarch64_arm64_Linux
8.0M  ./tailscale/tailscale_aarch64_arm64_Linux.upx
28M   ./tailscale/tailscale_aarch64_arm64_Windows.msi
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
43K   ./tailscale/tailscale_ipn_setup_Windows.exe
23M   ./tailscale/tailscale_merged_aarch64_arm64_Linux
5.7M  ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
20M   ./tailscale/tailscale_merged_aarch64_arm64_macOS
24M   ./tailscale/tailscale_merged_amd_x86_64_Linux
6.8M  ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
20M   ./tailscale/tailscale_merged_amd_x86_64_macOS
22M   ./tailscale/tailscale_merged_arm_Linux
5.4M  ./tailscale/tailscale_merged_arm_Linux.upx
22M   ./tailscale/tailscale_merged_i386_Linux
6.3M  ./tailscale/tailscale_merged_i386_Linux.upx
23M   ./tailscale/tailscale_merged_powerpc64_ppc64_Linux
5.5M  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
23M   ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux
5.8M  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
25M   ./tailscale/tailscale_merged_s390x_Linux
20M   ./tailscale/tailscale_mips64_Linux
20M   ./tailscale/tailscale_mips64le_Linux
19M   ./tailscale/tailscale_mips_Linux
7.7M  ./tailscale/tailscale_mips_Linux.upx
19M   ./tailscale/tailscale_mipsle_Linux
7.7M  ./tailscale/tailscale_mipsle_Linux.upx
13M   ./tailscale/tailscale_powerpc64_ppc64_Linux
3.1M  ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
13M   ./tailscale/tailscale_powerpc64le_ppc64le_Linux
3.4M  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
18M   ./tailscale/tailscale_riscv64_Linux
14M   ./tailscale/tailscale_s390x_Linux
51M   ./tailscale/tailscale_setup_Windows.exe
29M   ./tailscale/tailscale_x86_Windows.msi
34M   ./tailscale/tailscaled_aarch64_arm64_Linux
15M   ./tailscale/tailscaled_aarch64_arm64_Linux.upx
19M   ./tailscale/tailscaled_aarch64_arm64_macOS
21M   ./tailscale/tailscaled_amd_geode_Linux
6.0M  ./tailscale/tailscaled_amd_geode_Linux.upx
24M   ./tailscale/tailscaled_amd_x86_64_Linux
6.9M  ./tailscale/tailscaled_amd_x86_64_Linux.upx
19M   ./tailscale/tailscaled_amd_x86_64_macOS
30M   ./tailscale/tailscaled_arm_abi_Linux
13M   ./tailscale/tailscaled_arm_abi_Linux.upx
21M   ./tailscale/tailscaled_i386_Linux
6.0M  ./tailscale/tailscaled_i386_Linux.upx
34M   ./tailscale/tailscaled_mips64_Linux
34M   ./tailscale/tailscaled_mips64le_Linux
34M   ./tailscale/tailscaled_mips_Linux
13M   ./tailscale/tailscaled_mips_Linux.upx
33M   ./tailscale/tailscaled_mipsle_Linux
13M   ./tailscale/tailscaled_mipsle_Linux.upx
22M   ./tailscale/tailscaled_powerpc64_ppc64_Linux
5.2M  ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
22M   ./tailscale/tailscaled_powerpc64le_ppc64le_Linux
5.5M  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
32M   ./tailscale/tailscaled_riscv64_Linux
24M   ./tailscale/tailscaled_s390x_Linux
```

---

- #### UPX
```console

testing ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx [OK]
  23724167 ->   6019440   25.37%  linux/ppc64le  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx [OK]
  23593095 ->   5688128   24.11%   linux/ppc64   ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_mipsle_Linux.upx [OK]
  19714556 ->   7971364   40.43%  linux/mipsel   ./tailscale/tailscale_mipsle_Linux.upx
testing ./tailscale/tailscale_arm_abi_Linux.upx [OK]
  17976272 ->   7970192   44.34%    linux/arm    ./tailscale/tailscale_arm_abi_Linux.upx
testing ./tailscale/tailscale_amd_x86_64_Linux.upx [OK]
  13179912 ->   4126380   31.31%   linux/amd64   ./tailscale/tailscale_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_aarch64_arm64_Linux.upx [OK]
  18473657 ->   8327556   45.08%   linux/arm64   ./tailscale/tailscale_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_merged_arm_Linux.upx [OK]
  22610055 ->   5635096   24.92%    linux/arm    ./tailscale/tailscale_merged_arm_Linux.upx
testing ./tailscale/tailscaled_i386_Linux.upx [OK]
  21626780 ->   6265472   28.97%   linux/i386    ./tailscale/tailscaled_i386_Linux.upx
testing ./tailscale/tailscaled_mipsle_Linux.upx [OK]
  34599032 ->  13307408   38.46%  linux/mipsel   ./tailscale/tailscaled_mipsle_Linux.upx
testing ./tailscale/tailscaled_amd_x86_64_Linux.upx [OK]
  24939800 ->   7187296   28.82%   linux/amd64   ./tailscale/tailscaled_amd_x86_64_Linux.upx
testing ./tailscale/tailscaled_amd_geode_Linux.upx [OK]
  21667740 ->   6268028   28.93%   linux/i386    ./tailscale/tailscaled_amd_geode_Linux.upx
testing ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx [OK]
  22741127 ->   5749468   25.28%  linux/ppc64le  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx [OK]
  12910727 ->   3492876   27.05%  linux/ppc64le  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_mips_Linux.upx [OK]
  19821400 ->   8029968   40.51%   linux/mips    ./tailscale/tailscale_mips_Linux.upx
testing ./tailscale/tailscaled_mips_Linux.upx [OK]
  34774268 ->  13384596   38.49%   linux/mips    ./tailscale/tailscaled_mips_Linux.upx
testing ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx [OK]
  23134343 ->   5919568   25.59%   linux/arm64   ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_powerpc64_ppc64_Linux.upx [OK]
  12779655 ->   3227676   25.26%   linux/ppc64   ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_amd_geode_Linux.upx [OK]
  12401524 ->   3505140   28.26%   linux/i386    ./tailscale/tailscale_amd_geode_Linux.upx
testing ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx [OK]
  22610055 ->   5428532   24.01%   linux/ppc64   ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_merged_i386_Linux.upx [OK]
  22655111 ->   6552568   28.92%   linux/i386    ./tailscale/tailscale_merged_i386_Linux.upx
testing ./tailscale/tailscale_i386_Linux.upx [OK]
  12376948 ->   3500340   28.28%   linux/i386    ./tailscale/tailscale_i386_Linux.upx
testing ./tailscale/tailscaled_arm_abi_Linux.upx [OK]
  31233464 ->  13170804   42.17%    linux/arm    ./tailscale/tailscaled_arm_abi_Linux.upx
testing ./tailscale/tailscale_merged_amd_x86_64_Linux.upx [OK]
  24150151 ->   7114204   29.46%   linux/amd64   ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
testing ./tailscale/tailscaled_aarch64_arm64_Linux.upx [OK]
  35092366 ->  14866948   42.37%   linux/arm64   ./tailscale/tailscaled_aarch64_arm64_Linux.upx

```

---

- #### Version
```console
$ ./tailscale/tailscale_amd_x86_64_Linux --version
1.78.0
  tailscale commit: b06ec2696b87e2a237ab4abbdec937a39ddadc73
  other commit: b240d233fedf302da2bd6c3822e7a7390d944f24
  go version: go1.23.3

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
1.78.0
  tailscale commit: b06ec2696b87e2a237ab4abbdec937a39ddadc73
  other commit: b240d233fedf302da2bd6c3822e7a7390d944f24
  go version: go1.23.3

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



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
./tailscale/tailscale_aarch64_arm64_Linux:                   ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, BuildID[sha1]=aad6ee8c4d202111ac6fc6a30c433d1ba3374d06, with debug_info, not stripped
./tailscale/tailscale_aarch64_arm64_Linux.upx:               ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=lH6LGsfFJ3nTJDe6A6WN/bwQtMTNFk8CG_cfgtEA3/xfZ52qyFo5HPJonM8Tcc/Nn4AJXTE-Z8ya2CDZV4c, statically linked, no section header
./tailscale/tailscale_aarch64_arm64_Windows.msi:             Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Arm64;1033, Revision Number: {B413AC5F-8F9C-459B-AB2E-4C92DDC0FBC5}, Create Time/Date: Mon Jun  9 23:23:32 2025, Last Saved Time/Date: Mon Jun  9 23:23:32 2025, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscale_aarch64_arm64_macOS:                   Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_amd_geode_Linux:                       ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, BuildID[sha1]=55e5a1b2944adfc76d0305578c7e77370f099596, stripped
./tailscale/tailscale_amd_geode_Linux.upx:                   ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=3uyWlFPUt-vDOf_ysigi/aevbyzfrnFqXusnD_wCf/W-f08gIMl2G2F3m5npqz/xOVHUtsTVEDTN92NdXaa, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Linux:                      ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, BuildID[sha1]=b3742553f2d472594fd8ad5a860cd6c98279117d, stripped
./tailscale/tailscale_amd_x86_64_Linux.upx:                  ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=MYbHWSU83kppPGK2CHe9/lyme81l9FQIV2-QXGdX4/o7WMpzx_5isbP8eNS_SN/iEzrMfHUqGxrC3NloD4n, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Windows.msi:                Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: x64;1033, Revision Number: {0F9DB0E4-4522-4DA2-8A62-898675933D24}, Create Time/Date: Mon Jun  9 23:23:32 2025, Last Saved Time/Date: Mon Jun  9 23:23:32 2025, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscale_amd_x86_64_macOS:                      Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_arm_abi_Linux:                         ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, BuildID[sha1]=24f13f9a39d683e05c4558d205886ea387e75d3d, with debug_info, not stripped
./tailscale/tailscale_arm_abi_Linux.upx:                     ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=_3GQhPkJ-F9dtErtZcTI/n8x8lg9mrk3choNrKHuZ/vDbu7UPtcir39aRu3RVP/Ywy4sXpA5lItbi01R0Vd, statically linked, no section header
./tailscale/tailscale_i386_Linux:                            ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, BuildID[sha1]=b1dc02d5c5c65562ed55a13dc0c73043606a574c, stripped
./tailscale/tailscale_i386_Linux.upx:                        ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=Zc0luqZRaYsutwisaWd1/G_9AH4Oz5sdhJlYkyRZ2/UV1H8mYSZs12OMDf9fax/3piwyjM_HfiLYYIfp_pJ, statically linked, no section header
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
./tailscale/tailscale_mips64_Linux:                          ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, BuildID[sha1]=adbe15d21b50786b9eec38f264eb2aa75f4af9da, with debug_info, not stripped
./tailscale/tailscale_mips64le_Linux:                        ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, BuildID[sha1]=77dea094ca1d67949370b6fd950554b153972733, with debug_info, not stripped
./tailscale/tailscale_mips_Linux:                            ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, BuildID[sha1]=f453e31b5998ddc97ee8950833335c51086a8071, with debug_info, not stripped
./tailscale/tailscale_mips_Linux.upx:                        ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=3DDoWORzgO3IyBLu8X_2/8xotTpXBmYKpRz3g22cG/Oj_ls3khbdliS9mNZbbA/XNkiAozVyC-9PemiPqHP, statically linked, no section header
./tailscale/tailscale_mipsle_Linux:                          ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, BuildID[sha1]=b44fc84bfd011ff0ce062e9b48caeb98d39b8e21, with debug_info, not stripped
./tailscale/tailscale_mipsle_Linux.upx:                      ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=Y1d0uM2oOdkByHf6pXFL/sTIf4OX3b9A19k8feQc1/TMeBJisFmG35P4Z0amFi/O-RWBJsULuMljvxp4DUT, statically linked, no section header
./tailscale/tailscale_powerpc64_ppc64_Linux:                 ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64_ppc64_Linux.upx:             ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_powerpc64le_ppc64le_Linux:             ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx:         ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_riscv64_Linux:                         ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, BuildID[sha1]=2a7f8660d576f0e67cd0f43ab2d1a52ad5ee33e2, with debug_info, not stripped
./tailscale/tailscale_s390x_Linux:                           ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_setup_Windows.exe:                     PE32 executable (GUI) Intel 80386, for MS Windows, 6 sections
./tailscale/tailscale_x86_Windows.msi:                       Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Intel;1033, Revision Number: {9A0A4B81-CD00-4A7E-82A3-79492BBDC54A}, Create Time/Date: Mon Jun  9 23:23:32 2025, Last Saved Time/Date: Mon Jun  9 23:23:32 2025, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscaled_aarch64_arm64_Linux:                  ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, BuildID[sha1]=32e6fe4fec02e6c0630c8d1c5e0aea5b404bc243, with debug_info, not stripped
./tailscale/tailscaled_aarch64_arm64_Linux.upx:              ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=a9_qhT7DdZ43xKFlQF8v/OR7R5gAw5hct7yVUncMs/ZXfjDPoKfjum095AupA0/QblHKPgGBs72y9N6zMtx, statically linked, no section header
./tailscale/tailscaled_aarch64_arm64_macOS:                  Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_amd_geode_Linux:                      ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, BuildID[sha1]=c29a96cafe7c33b303db214baa4a929f8d9a9550, stripped
./tailscale/tailscaled_amd_geode_Linux.upx:                  ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=Vvk7-DzEvfzctLnJTDJJ/osthfBXCpVlRwozk_xcm/Jre8H_bQsA85jF63FuY5/AJxXFC7LgCmxSudTvZri, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_Linux:                     ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, BuildID[sha1]=e9de6824826c40dc9567b26d51db25d7c8d7feb4, stripped
./tailscale/tailscaled_amd_x86_64_Linux.upx:                 ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=RbzAHk9YwW8BW_o12i43/HGVhlBQqPDYeoYd0q6iu/NfYl6C_547Mh3CANhn2x/DIaHrIByNY5qtNi4SyQI, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_macOS:                     Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_arm_abi_Linux:                        ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, BuildID[sha1]=3102e98753e5c40c712756847ef3135ae7fb7518, with debug_info, not stripped
./tailscale/tailscaled_arm_abi_Linux.upx:                    ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=UpgO27uxlrNG_wNLeJnW/Qkuf6mpSU-3eoonXERXd/bb_QN8Smy6qlOHR1pNie/fEWUX_NcWCmm8rgX3CLc, statically linked, no section header
./tailscale/tailscaled_i386_Linux:                           ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, BuildID[sha1]=47653a6ec22c01ca88a1d4591395e8045544532d, stripped
./tailscale/tailscaled_i386_Linux.upx:                       ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=iFogNsRQB1xbW0JJxnKt/i0cGi7yEdSn6PE9K_dgA/g3krnzof-_JmBOp0LHZN/3olZxml3ZFPrNRQQAOZV, statically linked, no section header
./tailscale/tailscaled_mips64_Linux:                         ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, BuildID[sha1]=81871742f4f5e0199fa96143a7f97ab1c390c017, with debug_info, not stripped
./tailscale/tailscaled_mips64le_Linux:                       ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, BuildID[sha1]=a44e2a1d7b6a9499ff27a2fec91e8b58e9094c0a, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux:                           ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, BuildID[sha1]=494a8f17294a8d7c611e3a07beb7f659c9f860dd, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux.upx:                       ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=M28A3VmqC1CGZEfJ5b1y/eABr5HYH8OCLi2UrUkf8/PhDRHC61pxCjfTpR_3LT/wL8JhelcIoIh8TfH7pXr, statically linked, no section header
./tailscale/tailscaled_mipsle_Linux:                         ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, BuildID[sha1]=a25a7297e4ddd3ab95eb57dbd504325bed946e6b, with debug_info, not stripped
./tailscale/tailscaled_mipsle_Linux.upx:                     ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=dtQz_PFW6o6TkExzQ97E/1oUKYbDbOywC33pr38Tr/9MiLhr8DSZ8RNXqYIMKH/gt-i719SR9_Vv0EZsOAK, statically linked, no section header
./tailscale/tailscaled_powerpc64_ppc64_Linux:                ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64_ppc64_Linux.upx:            ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_powerpc64le_ppc64le_Linux:            ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx:        ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_riscv64_Linux:                        ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, BuildID[sha1]=c45e0263acd75074a3f5b2db6314f91cfae4b56f, with debug_info, not stripped
./tailscale/tailscaled_s390x_Linux:                          ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped

--> SHA256SUM
6d2fb1fb464b0008af02086d473d3f5e4a6c73ce7391748894e644e197cdbbae  ./tailscale/tailscale_aarch64_arm64_Linux
ecf63c5c11ea36531c12d3d22a28d07292461c7700a95f2ea516294b599d8572  ./tailscale/tailscale_aarch64_arm64_Linux.upx
8edbe72a22230a95dce176d2a1eb2f9270a6d672c42bd6deb56b10865e570e3a  ./tailscale/tailscale_aarch64_arm64_Windows.msi
758bd296723a348a70f5274b294baeb4053abd2e2ce58e2220e210946b618c6f  ./tailscale/tailscale_aarch64_arm64_macOS
00dabaeedfe9ecc704abb7ebc8657a5564acb990cb8bc1ab44341ccf0ddf4a62  ./tailscale/tailscale_amd_geode_Linux
beeaeafd8bcc811ac10f8a8780f2e93d1398c7d7870f986011aefb9601d8b431  ./tailscale/tailscale_amd_geode_Linux.upx
49c7da93f549635d56945c2138cddb708467b5fe6ce761179317f034c18206d7  ./tailscale/tailscale_amd_x86_64_Linux
d05710e558af279afc8906fdb4df4f03f84eb0f4c6232f7b1ab8cb9000b3f40b  ./tailscale/tailscale_amd_x86_64_Linux.upx
ca28055e39566cfe1bcf6e3033a43cb9bafcad6b118d0e04c412bc656c23b230  ./tailscale/tailscale_amd_x86_64_Windows.msi
248b7930c0c4c650f988bcb90a968da042066e0b826bf58efd8fe3a69fad8e7f  ./tailscale/tailscale_amd_x86_64_macOS
5aa06efa877de6840140faaafda0d4a13dc78cf419a1ecde26726b7156f8e54d  ./tailscale/tailscale_arm_abi_Linux
05a91b5425302bc74bad1415604b76121e6bddcc418e3a8216a99e928a93addc  ./tailscale/tailscale_arm_abi_Linux.upx
47cbe74286db0b5e114a32d6f5ee38334503ab1c7df7a6d8e1fbab2e68fe3414  ./tailscale/tailscale_i386_Linux
194f5fb363fa86501ddebfd842ebf2d050b424608dc2c8a441489cb55903614e  ./tailscale/tailscale_i386_Linux.upx
2c67db0984d2172ab5359e864d7292181e9704dc1bb71c95d4423a52ce91af66  ./tailscale/tailscale_ipn_setup_Windows.exe
d9f6e11ea386c30e093caf8cb95e78b5e3ab7f2510baebc34d567f4f156b1892  ./tailscale/tailscale_merged_aarch64_arm64_Linux
c07d34c9232893ad6a8c5dd649ee60b165d4f6921eb0a1d8bdb417370317277a  ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
68728bde1313493eb44dbd3be2e989eb00f60f4938d0d2845df9d45e32c25df7  ./tailscale/tailscale_merged_aarch64_arm64_macOS
673a71f1ad597e6677096e1577b77fd59ef850520c6e234f0527d7a393649b6b  ./tailscale/tailscale_merged_amd_x86_64_Linux
ee1a93754ad49cb7cf5783946a83fa0d86f814d0a34b4b9d713644cbbf9d1ff9  ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
267bebcfe539dd8353add30caf55a042bf996f8e688aae7910b9ecf61714f3f8  ./tailscale/tailscale_merged_amd_x86_64_macOS
21b1713cf9e55b3e86e17d7c97f61ccf39beec2279ae4f7863d52ef9b2606bcc  ./tailscale/tailscale_merged_arm_Linux
1e64ab97eb7d916104e77d28399fc958690381a0f21a92f217aa1caad831a77d  ./tailscale/tailscale_merged_arm_Linux.upx
c71dbc4f74079ffcf4ffcbcb6ad07b21bda66370c5ce370fe64d36efe0017dd4  ./tailscale/tailscale_merged_i386_Linux
15c5c62096091970fc12a9ab831f7fadbca866c3658a4d78af25c5465eb072e0  ./tailscale/tailscale_merged_i386_Linux.upx
f66a324c1c5fad2fb270a05c56f17afe80502af62a9cef91753d60d6f48b78ab  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux
046f036f5ad4e4475893472940aede4ef6353f6fb63b2da0b3267a94d20c2bce  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
772c4ba38a64fb1b2d0bb6ecabed24da2ee520cdab9b38acb29b6264a21f7612  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux
261856f6a582623ad7138224cded4d99dab71358d58e14ade9ca9d5c8ee410d4  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
20d527ab4b6b9e619e84e9f1f5570fbe2a8562447ff1947d6424d2aad75822fb  ./tailscale/tailscale_merged_s390x_Linux
f15d36f71531c489b47eb564e1f6d7494333c1878d365257821b0bcdd052913f  ./tailscale/tailscale_mips64_Linux
d46fb821eb77fc0b96e55c54c8365ada14c7eecb772b121eb471e71878d274c5  ./tailscale/tailscale_mips64le_Linux
02c14a0792303c0551329b05b6d717800ae95d0b5183f8e67b240d6e937b644e  ./tailscale/tailscale_mips_Linux
1aa9ac03d40986c1e0e6c85707a0317d26dece0ef689464435684b193b44a629  ./tailscale/tailscale_mips_Linux.upx
606f54fdc92c9370a22b2fd79e52301056251787d0d295ada14f559a080910af  ./tailscale/tailscale_mipsle_Linux
93a7bc942f0c2caff876d574795979c68849a5c08136c3c91447391c75eba7c5  ./tailscale/tailscale_mipsle_Linux.upx
c30ef76ff8c2324b6536ef59a8a683a50670fa0eecb718e121c3c6b4b89b6319  ./tailscale/tailscale_powerpc64_ppc64_Linux
40bfedef8f33c82275f72110ae361a7e7b4e81f1402f3797f3bf1a6fe850b081  ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
f421e56955157275f4f9de116fbdf9e73ff1b8f0799e6a2248a69ca439fb400b  ./tailscale/tailscale_powerpc64le_ppc64le_Linux
9acafa7388626680cea05c525529d6c46a1b9f77da2f850864ec7339c381af97  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
347d8c667f68b36292a6e4dc3942bf28c4d13f3fbf64233077880c2948078146  ./tailscale/tailscale_riscv64_Linux
d6e8242d9c2659be9ca880b7ef723b1bb3acf5bee7155d158572746813a70547  ./tailscale/tailscale_s390x_Linux
64a8ad28cbb67a6171236abe39f75a039a761a0e1aacdef75b26781887cef9a8  ./tailscale/tailscale_setup_Windows.exe
1c39d27ec797ef6108ac371b5bf5696e7586f04558702525804cfa925e5e6a21  ./tailscale/tailscale_x86_Windows.msi
ee56a95fae3b81bf77a374b346e68df4fc19f04771dd9055d81bc1dd2ba86126  ./tailscale/tailscaled_aarch64_arm64_Linux
647ab5b841d2282293545f762fb67bae6cb6a7284e945f1445ac578d9a423c0b  ./tailscale/tailscaled_aarch64_arm64_Linux.upx
3045786fe6191b3d64ae9d2b03b5fffcf080e3cb3073a3c2e8e69e57ea05e2cf  ./tailscale/tailscaled_aarch64_arm64_macOS
cd36015582e445cc5bda197b239a1c3354c6c2af1fdba6775ab00da3593f54d5  ./tailscale/tailscaled_amd_geode_Linux
64e24c6eb01afe4b225941ba2ba20c5df7a5947cb53013742377cc99648991ae  ./tailscale/tailscaled_amd_geode_Linux.upx
f9baa3432350d71d2030f86e7eb00d6f14952309087ec72b68a987616e0e2112  ./tailscale/tailscaled_amd_x86_64_Linux
a8a6ae5d506e19580b7dd7656b773931cb3f6a423f7098cb93e30a8ae27d5486  ./tailscale/tailscaled_amd_x86_64_Linux.upx
b5304b43985998d94d5c2c94e0eeb9e160a76906fa0ecb224af45c3b878e684d  ./tailscale/tailscaled_amd_x86_64_macOS
77bfc5236fa02222163d59da37da5343fb30fb6fbd213dcfc8c5f32309c345dd  ./tailscale/tailscaled_arm_abi_Linux
a5dae95df0ac40db567f5335b75daaf53b58c1ef748538352ad40516ec07dc95  ./tailscale/tailscaled_arm_abi_Linux.upx
204b5cc94fc2435e7091766f546c04b3f22cc6cfbf9ee4fe6b0d3daef7874102  ./tailscale/tailscaled_i386_Linux
637bcda43abddbbef68a24e1a836d35b6ba9727848263edcc9fe580f05c2ea88  ./tailscale/tailscaled_i386_Linux.upx
7227104350b5639eb3ce0ebfe97a390502b32582c4aab1d4fcb76abb33a41e6e  ./tailscale/tailscaled_mips64_Linux
d441fc3b412e259f96c413346d07fd85672dc50423766e816eadc175e038bd44  ./tailscale/tailscaled_mips64le_Linux
645d62738a1fdaf14c2c6d8919a6a147a11b71096e924fed01401a251ea35cd9  ./tailscale/tailscaled_mips_Linux
46b0f9ba51df1fbc234b0cef0ec6765a85715aec194741fd1cf34928e5221e0a  ./tailscale/tailscaled_mips_Linux.upx
72c4983612e9374e2c3353776a0280af4efd903c0c8b97881b80c2946681f922  ./tailscale/tailscaled_mipsle_Linux
ff6de7dcdf9effbc76139f4c9805cfab21e2606b89643845902df4365df591dd  ./tailscale/tailscaled_mipsle_Linux.upx
639ff1ddd6838d04b5bda0a702c87a167d341a3e7dc0cb6c2c3021717bd06aa7  ./tailscale/tailscaled_powerpc64_ppc64_Linux
423e8e626b7f916eed93081a45e535906c9afd4348dde1fa73110c109301fbba  ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
c05e04153ee55c04d5daea1858a07bf494e3e07dc26b034c89b25a3433612fa6  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux
f497b123d3ee31323dfe15eb05ef1c8d65058bf5b9fa6fcca371f36fb09039bf  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
3492c9599153c060592e857ed4cb085421c70bee96b57974ef30556bb554e1d9  ./tailscale/tailscaled_riscv64_Linux
c11d273f95954527dc7f77219d762ba58b0209cf8ef1cc327526d09c1f48080a  ./tailscale/tailscaled_s390x_Linux
```


---

- #### Sizes

```console
20M   ./tailscale/tailscale_aarch64_arm64_Linux
8.8M  ./tailscale/tailscale_aarch64_arm64_Linux.upx
32M   ./tailscale/tailscale_aarch64_arm64_Windows.msi
11M   ./tailscale/tailscale_aarch64_arm64_macOS
14M   ./tailscale/tailscale_amd_geode_Linux
4.1M  ./tailscale/tailscale_amd_geode_Linux.upx
15M   ./tailscale/tailscale_amd_x86_64_Linux
4.4M  ./tailscale/tailscale_amd_x86_64_Linux.upx
34M   ./tailscale/tailscale_amd_x86_64_Windows.msi
11M   ./tailscale/tailscale_amd_x86_64_macOS
20M   ./tailscale/tailscale_arm_abi_Linux
8.6M  ./tailscale/tailscale_arm_abi_Linux.upx
14M   ./tailscale/tailscale_i386_Linux
4.1M  ./tailscale/tailscale_i386_Linux.upx
44K   ./tailscale/tailscale_ipn_setup_Windows.exe
24M   ./tailscale/tailscale_merged_aarch64_arm64_Linux
6.0M  ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
20M   ./tailscale/tailscale_merged_aarch64_arm64_macOS
26M   ./tailscale/tailscale_merged_amd_x86_64_Linux
7.3M  ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
20M   ./tailscale/tailscale_merged_amd_x86_64_macOS
24M   ./tailscale/tailscale_merged_arm_Linux
5.9M  ./tailscale/tailscale_merged_arm_Linux.upx
24M   ./tailscale/tailscale_merged_i386_Linux
6.8M  ./tailscale/tailscale_merged_i386_Linux.upx
25M   ./tailscale/tailscale_merged_powerpc64_ppc64_Linux
5.9M  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
25M   ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux
6.2M  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
27M   ./tailscale/tailscale_merged_s390x_Linux
22M   ./tailscale/tailscale_mips64_Linux
22M   ./tailscale/tailscale_mips64le_Linux
22M   ./tailscale/tailscale_mips_Linux
8.6M  ./tailscale/tailscale_mips_Linux.upx
22M   ./tailscale/tailscale_mipsle_Linux
8.6M  ./tailscale/tailscale_mipsle_Linux.upx
14M   ./tailscale/tailscale_powerpc64_ppc64_Linux
3.5M  ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
14M   ./tailscale/tailscale_powerpc64le_ppc64le_Linux
3.6M  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
20M   ./tailscale/tailscale_riscv64_Linux
15M   ./tailscale/tailscale_s390x_Linux
51M   ./tailscale/tailscale_setup_Windows.exe
33M   ./tailscale/tailscale_x86_Windows.msi
37M   ./tailscale/tailscaled_aarch64_arm64_Linux
16M   ./tailscale/tailscaled_aarch64_arm64_Linux.upx
19M   ./tailscale/tailscaled_aarch64_arm64_macOS
23M   ./tailscale/tailscaled_amd_geode_Linux
6.5M  ./tailscale/tailscaled_amd_geode_Linux.upx
26M   ./tailscale/tailscaled_amd_x86_64_Linux
7.3M  ./tailscale/tailscaled_amd_x86_64_Linux.upx
19M   ./tailscale/tailscaled_amd_x86_64_macOS
33M   ./tailscale/tailscaled_arm_abi_Linux
14M   ./tailscale/tailscaled_arm_abi_Linux.upx
23M   ./tailscale/tailscaled_i386_Linux
6.5M  ./tailscale/tailscaled_i386_Linux.upx
37M   ./tailscale/tailscaled_mips64_Linux
37M   ./tailscale/tailscaled_mips64le_Linux
37M   ./tailscale/tailscaled_mips_Linux
14M   ./tailscale/tailscaled_mips_Linux.upx
36M   ./tailscale/tailscaled_mipsle_Linux
14M   ./tailscale/tailscaled_mipsle_Linux.upx
24M   ./tailscale/tailscaled_powerpc64_ppc64_Linux
5.7M  ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
24M   ./tailscale/tailscaled_powerpc64le_ppc64le_Linux
5.9M  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
34M   ./tailscale/tailscaled_riscv64_Linux
26M   ./tailscale/tailscaled_s390x_Linux
```

---

- #### UPX
```console

testing ./tailscale/tailscale_merged_amd_x86_64_Linux.upx [OK]
  26312852 ->   7577308   28.80%   linux/amd64   ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
testing ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx [OK]
  24772756 ->   5891388   23.78%   linux/ppc64   ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_mipsle_Linux.upx [OK]
  22027820 ->   8919396   40.49%  linux/mipsel   ./tailscale/tailscale_mipsle_Linux.upx
testing ./tailscale/tailscale_powerpc64_ppc64_Linux.upx [OK]
  14090388 ->   3582884   25.43%   linux/ppc64   ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_i386_Linux.upx [OK]
  13900356 ->   4229528   30.43%   linux/i386    ./tailscale/tailscale_i386_Linux.upx
testing ./tailscale/tailscale_aarch64_arm64_Linux.upx [OK]
  20405014 ->   9178688   44.98%   linux/arm64   ./tailscale/tailscale_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_amd_x86_64_Linux.upx [OK]
  14727400 ->   4509640   30.62%   linux/amd64   ./tailscale/tailscale_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx [OK]
  25755796 ->   6402512   24.86%  linux/ppc64le  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_amd_geode_Linux.upx [OK]
  13929028 ->   4235784   30.41%   linux/i386    ./tailscale/tailscale_amd_geode_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx [OK]
  25690260 ->   6158660   23.97%   linux/ppc64   ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscaled_mipsle_Linux.upx [OK]
  37623992 ->  14429776   38.35%  linux/mipsel   ./tailscale/tailscaled_mipsle_Linux.upx
testing ./tailscale/tailscaled_i386_Linux.upx [OK]
  23559972 ->   6759980   28.69%   linux/i386    ./tailscale/tailscaled_i386_Linux.upx
testing ./tailscale/tailscale_merged_arm_Linux.upx [OK]
  24641684 ->   6100948   24.76%    linux/arm    ./tailscale/tailscale_merged_arm_Linux.upx
testing ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx [OK]
  24838292 ->   6134988   24.70%  linux/ppc64le  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscaled_arm_abi_Linux.upx [OK]
  34037740 ->  14349352   42.16%    linux/arm    ./tailscale/tailscaled_arm_abi_Linux.upx
testing ./tailscale/tailscaled_mips_Linux.upx [OK]
  37818368 ->  14508224   38.36%   linux/mips    ./tailscale/tailscaled_mips_Linux.upx
testing ./tailscale/tailscale_arm_abi_Linux.upx [OK]
  20228801 ->   8933440   44.16%    linux/arm    ./tailscale/tailscale_arm_abi_Linux.upx
testing ./tailscale/tailscale_mips_Linux.upx [OK]
  22149032 ->   8979388   40.54%   linux/mips    ./tailscale/tailscale_mips_Linux.upx
testing ./tailscale/tailscale_merged_i386_Linux.upx [OK]
  24780948 ->   7085456   28.59%   linux/i386    ./tailscale/tailscale_merged_i386_Linux.upx
testing ./tailscale/tailscaled_aarch64_arm64_Linux.upx [OK]
  37802083 ->  15949400   42.19%   linux/arm64   ./tailscale/tailscaled_aarch64_arm64_Linux.upx
testing ./tailscale/tailscaled_amd_geode_Linux.upx [OK]
  23600932 ->   6763860   28.66%   linux/i386    ./tailscale/tailscaled_amd_geode_Linux.upx
testing ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx [OK]
  14090388 ->   3753040   26.64%  linux/ppc64le  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscaled_amd_x86_64_Linux.upx [OK]
  27063272 ->   7651292   28.27%   linux/amd64   ./tailscale/tailscaled_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx [OK]
  24903828 ->   6279752   25.22%   linux/arm64   ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx

```

---

- #### Version
```console
$ ./tailscale/tailscale_amd_x86_64_Linux --version
1.84.0
  tailscale commit: 160c11f37850a7e0a50f5efec48cacc333e69a00
  other commit: bf604245899ff9c164ad9236bd52faab03a60faa
  go version: go1.24.2

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
1.84.0
  tailscale commit: 160c11f37850a7e0a50f5efec48cacc333e69a00
  other commit: bf604245899ff9c164ad9236bd52faab03a60faa
  go version: go1.24.2

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


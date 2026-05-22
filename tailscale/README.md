
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
./tailscale/tailscale_aarch64_arm64_Linux:                   ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=9hFQYnq9YhTPPmgwOAK2/mTw46AnYHXZjDx_UK9rz/f55H5bj3y5MW8F-a8e8T/BbgdjNDRPtvP_W3p1eGG, BuildID[sha1]=f16bc7d2e2269a0cfa8b42fe8428d2edb0e48840, with debug_info, not stripped
./tailscale/tailscale_aarch64_arm64_Linux.upx:               ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=9hFQYnq9YhTPPmgwOAK2/mTw46AnYHXZjDx_UK9rz/f55H5bj3y5MW8F-a8e8T/BbgdjNDRPtvP_W3p1eGG, statically linked, no section header
./tailscale/tailscale_aarch64_arm64_Windows.msi:             Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Arm64;1033, Revision Number: {054740BD-16FD-47E7-A9EF-1D0EEC5D0982}, Create Time/Date: Thu May 14 17:21:43 2026, Last Saved Time/Date: Thu May 14 17:21:43 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscale_aarch64_arm64_macOS:                   Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_amd_geode_Linux:                       ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=mEoyWu11XWyJpF_jRsck/-gWAvrS-eQsCAkuRC5W_/1pH8PlgBkg11DMKTQE3r/ozIDP4Z5AKngh6SOF_LT, BuildID[sha1]=3f7824c225cbb9544176f9dee129c6f41874879b, stripped
./tailscale/tailscale_amd_geode_Linux.upx:                   ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=mEoyWu11XWyJpF_jRsck/-gWAvrS-eQsCAkuRC5W_/1pH8PlgBkg11DMKTQE3r/ozIDP4Z5AKngh6SOF_LT, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Linux:                      ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=NDLMMWsXkBwlbihvIuKU/wjSlv2kTalDihlgI_6PJ/b5BArmQHULwSWa5CZoQU/riMtQ9QNAxo8k38fTYht, BuildID[sha1]=ecd1ea82d5788f3c95afbc1a35f1e007fbc1f1a3, stripped
./tailscale/tailscale_amd_x86_64_Linux.upx:                  ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=NDLMMWsXkBwlbihvIuKU/wjSlv2kTalDihlgI_6PJ/b5BArmQHULwSWa5CZoQU/riMtQ9QNAxo8k38fTYht, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Windows.msi:                Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: x64;1033, Revision Number: {3315BB15-3DEC-41E8-BA73-0035FEB2E885}, Create Time/Date: Thu May 14 17:22:15 2026, Last Saved Time/Date: Thu May 14 17:22:15 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscale_amd_x86_64_macOS:                      Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_arm_abi_Linux:                         ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=F3Fcret5caiwzL5dv7vu/FTcj979jAFg_ohJz1NqJ/9_H89IqQGjHpL1Q07U-t/9ZjMT0vgKywZjy4FazZm, BuildID[sha1]=66366f194df97ebed35e3f54422216dc0798cbcf, with debug_info, not stripped
./tailscale/tailscale_arm_abi_Linux.upx:                     ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=F3Fcret5caiwzL5dv7vu/FTcj979jAFg_ohJz1NqJ/9_H89IqQGjHpL1Q07U-t/9ZjMT0vgKywZjy4FazZm, statically linked, no section header
./tailscale/tailscale_i386_Linux:                            ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=yQgq6kZYa2uSb2EN1vnC/YXj0F_Jr1mbCRdz4Dc8Y/pdVSctUnv7tFTogrWv3b/MLWr-rQohULuk-_RYaw7, BuildID[sha1]=d7f9ec6ec982b1edb80931e528dda6af4e0d5a7d, stripped
./tailscale/tailscale_i386_Linux.upx:                        ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=yQgq6kZYa2uSb2EN1vnC/YXj0F_Jr1mbCRdz4Dc8Y/pdVSctUnv7tFTogrWv3b/MLWr-rQohULuk-_RYaw7, statically linked, no section header
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
./tailscale/tailscale_mips64_Linux:                          ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=p5uJ5JD_sLUP7R8UzDtJ/no_wHokjNlLBGYnMWF1I/eiUnZd9MpmpaCtKDoxSU/5MbOiIOzF1i6vzps_Dgs, BuildID[sha1]=af393632aa978a10ac014cbbca45f4207c619b9d, with debug_info, not stripped
./tailscale/tailscale_mips64le_Linux:                        ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=xgj-d1sA3YieuOlFWv7A/Ne1jyrO3ojxpG-vs0fOz/eBmYzFOxrHBcvYXUAiWz/iy8Pa2Lle8aEkrmFN6JC, BuildID[sha1]=34b0f5d29ce70b91d53810560bad0baea3efae0b, with debug_info, not stripped
./tailscale/tailscale_mips_Linux:                            ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=fdT-BL0mPlGWjMtLO_7W/G3W19NtliX2fR7_AZmh_/G3iqTc8kb--zhfocZhAp/YdSzlfvLyx1DOC02t56M, BuildID[sha1]=8e6feb407cfa7257bec4462529ab19315d532bc0, with debug_info, not stripped
./tailscale/tailscale_mips_Linux.upx:                        ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=fdT-BL0mPlGWjMtLO_7W/G3W19NtliX2fR7_AZmh_/G3iqTc8kb--zhfocZhAp/YdSzlfvLyx1DOC02t56M, statically linked, no section header
./tailscale/tailscale_mipsle_Linux:                          ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=3Q88FblDR-Uwija358f3/F0fJpkjifm2zXxKyJZo9/6_1CQRy7QGQC5OlovDIj/cKv-iCEGNQ6NcIUdtdio, BuildID[sha1]=224ae8d8f2750d25fdfa97699767a9885df53a8f, with debug_info, not stripped
./tailscale/tailscale_mipsle_Linux.upx:                      ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=3Q88FblDR-Uwija358f3/F0fJpkjifm2zXxKyJZo9/6_1CQRy7QGQC5OlovDIj/cKv-iCEGNQ6NcIUdtdio, statically linked, no section header
./tailscale/tailscale_powerpc64_ppc64_Linux:                 ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64_ppc64_Linux.upx:             ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_powerpc64le_ppc64le_Linux:             ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx:         ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_riscv64_Linux:                         ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, Go BuildID=-CdJVUPWZjPT6p9KJuD3/VY-RhANBK8eyDFHYpfw5/xvPNarEjemM0XYvhpX0R/xDerKu5lSHKV17LuwDqu, BuildID[sha1]=d77d6364c6d884197771487050d9741abb8711cf, with debug_info, not stripped
./tailscale/tailscale_s390x_Linux:                           ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_setup_Windows.exe:                     PE32 executable (GUI) Intel 80386, for MS Windows, 6 sections
./tailscale/tailscale_x86_Windows.msi:                       Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Intel;1033, Revision Number: {5BA1C700-70F6-450F-B5F7-6DCCB312D90E}, Create Time/Date: Thu May 14 17:21:43 2026, Last Saved Time/Date: Thu May 14 17:21:43 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscaled_aarch64_arm64_Linux:                  ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=hd6N1wf9INfbBSm9fs1d/vqSa7xc6s2DKjDnbOHpN/twoul4hGxvifIApw4UXP/q3Vi8Dd6CrEzNOYr0IFt, BuildID[sha1]=dc229785e777e294572e85a0be0095afcc96780a, with debug_info, not stripped
./tailscale/tailscaled_aarch64_arm64_Linux.upx:              ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=hd6N1wf9INfbBSm9fs1d/vqSa7xc6s2DKjDnbOHpN/twoul4hGxvifIApw4UXP/q3Vi8Dd6CrEzNOYr0IFt, statically linked, no section header
./tailscale/tailscaled_aarch64_arm64_macOS:                  Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_amd_geode_Linux:                      ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=ue_DljptM_GX7q5_VDqS/c1wfIZ1j6aC4oIK4599U/kSFHEAdkb97VGhWdQ0sk/Rh76dXZBYzDDPhioKIU0, BuildID[sha1]=4c24864e7e82556d9c5736c7e1edac0acbf8f310, stripped
./tailscale/tailscaled_amd_geode_Linux.upx:                  ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=ue_DljptM_GX7q5_VDqS/c1wfIZ1j6aC4oIK4599U/kSFHEAdkb97VGhWdQ0sk/Rh76dXZBYzDDPhioKIU0, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_Linux:                     ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=SQj8fvHUVarb3MxQrndi/-7TrpSPNOLtyBdbujSJi/pW6hFEljsi6ALqeGkcop/_LG2n96MuQ9a7sAmWwWt, BuildID[sha1]=b1a9dfd43b437a5b4df0d6cf4ba31084f0bd0e12, stripped
./tailscale/tailscaled_amd_x86_64_Linux.upx:                 ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=SQj8fvHUVarb3MxQrndi/-7TrpSPNOLtyBdbujSJi/pW6hFEljsi6ALqeGkcop/_LG2n96MuQ9a7sAmWwWt, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_macOS:                     Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_arm_abi_Linux:                        ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=OkRdTENEXAakqOkz9NTY/iqyVEZBTjRVFTFUohZzb/FcI6NMdE2C-1lqJznHYb/0vzr-N4imMJYrqrPevQv, BuildID[sha1]=3fcef460a57675fc84df972ca96bd5f9300e5380, with debug_info, not stripped
./tailscale/tailscaled_arm_abi_Linux.upx:                    ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=OkRdTENEXAakqOkz9NTY/iqyVEZBTjRVFTFUohZzb/FcI6NMdE2C-1lqJznHYb/0vzr-N4imMJYrqrPevQv, statically linked, no section header
./tailscale/tailscaled_i386_Linux:                           ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=3pVU4DZ37thpExp-hlJ3/D2fG_ZdNKZzz_NuPJquk/FBmFZFCAu3CmOcXj6inU/NuhDO9HmNTYc3rjFK4tw, BuildID[sha1]=bf23ce5ce6a10a2bfdb6ff6d5c9b773846771de7, stripped
./tailscale/tailscaled_i386_Linux.upx:                       ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=3pVU4DZ37thpExp-hlJ3/D2fG_ZdNKZzz_NuPJquk/FBmFZFCAu3CmOcXj6inU/NuhDO9HmNTYc3rjFK4tw, statically linked, no section header
./tailscale/tailscaled_mips64_Linux:                         ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=1FXjf595CtbZkvuMEfg0/4sRRCutpZsLZgZkDZL_1/xa324QfHl24DXCjHf6V9/aeFWfjT816JrjEDickp9, BuildID[sha1]=502ce09270bd9fcac5c44f8d636f8d2dae64638a, with debug_info, not stripped
./tailscale/tailscaled_mips64le_Linux:                       ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=cs7CSl-V924Hct3C5Yk9/wmCOqkl62pW6iYBfR4QL/BES5nwrSZWlVe5JR55pP/CdAL3rbgXNSedgWlAvku, BuildID[sha1]=3a72f3692e16b5050e77f9ae7523c92ebdef9e73, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux:                           ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=qC0r1F6S59wWAfrvJyp4/MMEsxqetlItT4q18MBVt/fTRmqJpAdDL-h0Yn_eS1/gAWHfwUPr6EsHCrGZ-8o, BuildID[sha1]=6cde002a48d888f7ff06a7a4e78d614f66446184, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux.upx:                       ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=qC0r1F6S59wWAfrvJyp4/MMEsxqetlItT4q18MBVt/fTRmqJpAdDL-h0Yn_eS1/gAWHfwUPr6EsHCrGZ-8o, statically linked, no section header
./tailscale/tailscaled_mipsle_Linux:                         ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=p2d2ijnSi8lWF4QPLs8f/a8eCyQV8S7v5jESsLiTK/IFxRsRsHRkKtmg26jm1k/vqy8vZr-FDNmCciFnyBs, BuildID[sha1]=1468033d3120f27eba5a6488d9e334ecdfb1c5f1, with debug_info, not stripped
./tailscale/tailscaled_mipsle_Linux.upx:                     ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=p2d2ijnSi8lWF4QPLs8f/a8eCyQV8S7v5jESsLiTK/IFxRsRsHRkKtmg26jm1k/vqy8vZr-FDNmCciFnyBs, statically linked, no section header
./tailscale/tailscaled_powerpc64_ppc64_Linux:                ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64_ppc64_Linux.upx:            ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_powerpc64le_ppc64le_Linux:            ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx:        ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_riscv64_Linux:                        ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, Go BuildID=HPhB28n2mhf51Oygn6su/qHhH-wVACO0absJs3_t7/FTnYlI-So5NhNL4ir6pW/cRfmRQT0BeU37rVQ-Gxv, BuildID[sha1]=3f805d80cd0535988e39dd4e2f1537cb3021f93f, with debug_info, not stripped
./tailscale/tailscaled_s390x_Linux:                          ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped

--> SHA256SUM
58e147fea4074b522f655963b31b066aae9bc1aded4c8075d2844db32b4bb20e  ./tailscale/tailscale_aarch64_arm64_Linux
1165c68f6ce34e7551da3414cc884788d5fa65ac0422dc9dde2e4890cab16ecd  ./tailscale/tailscale_aarch64_arm64_Linux.upx
caa77b70367cfe8f99513c72f43a4c768d83255ba1b1408d95b462635eb132e0  ./tailscale/tailscale_aarch64_arm64_Windows.msi
758bd296723a348a70f5274b294baeb4053abd2e2ce58e2220e210946b618c6f  ./tailscale/tailscale_aarch64_arm64_macOS
9a24270810d34753763812037f839f114a3964e220d5bfba079bc99cfbcf9bc6  ./tailscale/tailscale_amd_geode_Linux
22867488d36ba5597fe8a1546cf953e1d4264a7052be2cb6d3ac18ee70ad4d55  ./tailscale/tailscale_amd_geode_Linux.upx
c025f46e1b3c100211dc81773ec6cd1eb6142d46b13f92aad6c6f646c2896691  ./tailscale/tailscale_amd_x86_64_Linux
9c64c1d3f58fb1fbae7e23f7700d917e0f8b146697737c16fb10b055ecbda7da  ./tailscale/tailscale_amd_x86_64_Linux.upx
89eb44e18f1af3e6e4aa998ec161d3996158fe3e0c0b9f1bf745c74eb420f84e  ./tailscale/tailscale_amd_x86_64_Windows.msi
248b7930c0c4c650f988bcb90a968da042066e0b826bf58efd8fe3a69fad8e7f  ./tailscale/tailscale_amd_x86_64_macOS
c39bb52a3732475fd2a8d09b2f7c759d804b6097c02d6d5dac1c0960bba4243f  ./tailscale/tailscale_arm_abi_Linux
2fdb52e909f3d1ab7019648c8be457f70c3e14dac4b6539ec5e74a8626f4854d  ./tailscale/tailscale_arm_abi_Linux.upx
6e22f1c9e393d71d12366b00ced45a91064ae91e41ad49464c2f8c712b5232f3  ./tailscale/tailscale_i386_Linux
d526ed3eb5068b5f4f4968cd9604f2df6616f95084c1acf443342b1ea21502ae  ./tailscale/tailscale_i386_Linux.upx
d522569394a430a6107d793243c5aa31a55cc16cd241d3562bfd2a300e3c5c87  ./tailscale/tailscale_ipn_setup_Windows.exe
341322d176a67c23c9effd7b85dc2fd8b9225c6a7e52b00b69bcfebffa7a66fa  ./tailscale/tailscale_merged_aarch64_arm64_Linux
0577e20c22d38e129c75846398fb3ca96ede0d336f748aaf8de7a596d313a0f9  ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
68728bde1313493eb44dbd3be2e989eb00f60f4938d0d2845df9d45e32c25df7  ./tailscale/tailscale_merged_aarch64_arm64_macOS
9cfd8014489d61d3abe850073b2ac8b05e5f94ca61718ead7b30f7647eabba31  ./tailscale/tailscale_merged_amd_x86_64_Linux
c34ae7ca30df596f2186ad4cf6f3e030e7a0ca83ff8917f3ed2befbf718462fb  ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
267bebcfe539dd8353add30caf55a042bf996f8e688aae7910b9ecf61714f3f8  ./tailscale/tailscale_merged_amd_x86_64_macOS
90b7dd3482d6852c17ff2ebe2cd4d668b432bd6276d6a4c7a58004209618f7c2  ./tailscale/tailscale_merged_arm_Linux
de797443c5d0c81340e17f5d8ac458b0611f0f60d5b8676c00fcb55b09eaf09a  ./tailscale/tailscale_merged_arm_Linux.upx
f824a1b53d946eb32a1df5afa416e127f5f2eb161ab22b3ea80a675dc9384642  ./tailscale/tailscale_merged_i386_Linux
4bd2148c431c9cb140298b6c99a8e9318b1128b7129237a33c0a98a4a029affb  ./tailscale/tailscale_merged_i386_Linux.upx
23b929e23167341727aae7398f00ae5716fa8b33de9e05552b2c7f07f42b974b  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux
85c375f57b7017eb86f8b24b7789deb855520dd4038db2bc8876b11d354fbed2  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
329f09fd5c2b9107b72291ac1e1f34d74b2c94f47f261421a20ff2039f6483f9  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux
479387632fe3d5475cf1151c0ce5531bf7202f0ff6d18a958ebe7e1c8836237f  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
701b9357e50faac8d1c2eff417e48a9758d9100ba7f33dd3d8cf4632503a5cfc  ./tailscale/tailscale_merged_s390x_Linux
497681ebbabac4070fc38950dbe21cb324b587ded8eb6d04e7642d10f98c8fce  ./tailscale/tailscale_mips64_Linux
cff377cb6d51a6c5f62b2d6c4624f968a395da3dec4047f3b444b9e089174da5  ./tailscale/tailscale_mips64le_Linux
b786755ca30d2689b43df0f6721849fbb3ea49c2417b3b01d00e28659f0bf304  ./tailscale/tailscale_mips_Linux
1619cd4b6ba27410084c67d500e36b69b7943cbfe3ceeebd39a2f6358c84d38d  ./tailscale/tailscale_mips_Linux.upx
67efeaa8e0d3f8ddcf01131e629d24fc73518585d1bb6365bd077a9c64effe27  ./tailscale/tailscale_mipsle_Linux
f75ba0b6202db258ac90e9748b1d4a5ee734b08fc3944507af4d72af38549654  ./tailscale/tailscale_mipsle_Linux.upx
1942f80d91485a1c5eb533bcb86cafbfa5f9f12dd85d36d9333ee3677aff3d68  ./tailscale/tailscale_powerpc64_ppc64_Linux
40359e9b3a98d10e7a2a5307732d4beafee802e6029af9440ee2c1052bbc7dae  ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
2d9dc9234fabfabcc88fa9831a4db555711316ace9438ccfe7b187de237d633d  ./tailscale/tailscale_powerpc64le_ppc64le_Linux
90d8aab08d23696c2ef939fdcdb1998063beea5b862ed8e5c4849a69b661612f  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
0d6ded0af1f3f28c0b933d420f04ada83f748aaaf63b8470a6fedd085b0eb68a  ./tailscale/tailscale_riscv64_Linux
a0167ff68b7942f624642469e03fe836da9f7a5265d3d1bf46ce37c3c7c33643  ./tailscale/tailscale_s390x_Linux
64a8ad28cbb67a6171236abe39f75a039a761a0e1aacdef75b26781887cef9a8  ./tailscale/tailscale_setup_Windows.exe
ae94db837124c8f83351a04d31e6ed3de7d5d64f3c5e3641904acf05da6d9600  ./tailscale/tailscale_x86_Windows.msi
468490e44595611952dca026353554f4b03d8c859c940ba6f1810d0421049878  ./tailscale/tailscaled_aarch64_arm64_Linux
b6657e2503109ac92230a19e93d3d2a1bcdfe72277133144b9c5a7d0e0d74c61  ./tailscale/tailscaled_aarch64_arm64_Linux.upx
3045786fe6191b3d64ae9d2b03b5fffcf080e3cb3073a3c2e8e69e57ea05e2cf  ./tailscale/tailscaled_aarch64_arm64_macOS
7bae337be0d1ac0a43d45da0121ff276824948d9ba91c5d36fc657f4658b2d75  ./tailscale/tailscaled_amd_geode_Linux
832550be576c19a407a63ef89bb01945aa469f70b5697a77e2262e8552a7463a  ./tailscale/tailscaled_amd_geode_Linux.upx
377657f38b386b276a1ea16d010b142b0dc95322f1777b0d7afbf828b3e7507d  ./tailscale/tailscaled_amd_x86_64_Linux
01b6d0d1b2c38b16e9192a36d14c06c2dd4698953b590ed1b27407628c9e3d91  ./tailscale/tailscaled_amd_x86_64_Linux.upx
b5304b43985998d94d5c2c94e0eeb9e160a76906fa0ecb224af45c3b878e684d  ./tailscale/tailscaled_amd_x86_64_macOS
a9bc936879ae69fd3a2665349ffc507a598b5022b40c807621105c7bf8fb82d7  ./tailscale/tailscaled_arm_abi_Linux
a4d8ef223bac86ebb38a15803e2b6b3620a0fd21015aec499f3a263777669574  ./tailscale/tailscaled_arm_abi_Linux.upx
e0de9c6641763a56c94106cfb5cf50035c13a42d0c0106f89057e344a1d34305  ./tailscale/tailscaled_i386_Linux
8af0be149eb5d25394c5455186eec4a79364b125d2671c61a89fe14652f43cd1  ./tailscale/tailscaled_i386_Linux.upx
36e7b1bc4fcf720c4ad7593f3e48489a07a512d36c74dfb02da1a2bdccbf5d65  ./tailscale/tailscaled_mips64_Linux
5679156177384e92a951d5858608e823a227543a3594e3ad61d90a47e6b98808  ./tailscale/tailscaled_mips64le_Linux
784ea9328e19a2dd88c5deec4474cdda681a1ce5451bf3bb9f8f4ff27711b0d9  ./tailscale/tailscaled_mips_Linux
fbdd2a866f2bbae3359fa95d60f0c24735afccbc522363b3ac09adb1fa67cd9f  ./tailscale/tailscaled_mips_Linux.upx
47e2cec86039fbe5ce2727f6cc6a93aba14db760edb4d0587eae41074dbe9b40  ./tailscale/tailscaled_mipsle_Linux
9cff2ff77475c82b7920a21c0c48da5637b259235b2e68ed1ec845034bc0b5db  ./tailscale/tailscaled_mipsle_Linux.upx
a21b178ce7fe24b185ba7577b1cbcf95bb6439be56c5095e157c5dd17cdbb475  ./tailscale/tailscaled_powerpc64_ppc64_Linux
c35cd2f88c67bcbae4034daa588efc62089a149ce7bf04d345387e0829f03435  ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
35dae7371e07f7d486cf5c0eaa52dce9590ce4f8845b96a64f9ceda77150bede  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux
3f355adae7ec2131b75cddca25d459679a1bdcc82d85518c0c44c50ab2114da2  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
e83fd05c60920c06e81f42d7ac6fe838d1fa134e1027871c0b56b26bc28e011e  ./tailscale/tailscaled_riscv64_Linux
7b13f2bb8e39ab203b00cb52e1c331469c3357aa68fb78d3fa6268fff0261e38  ./tailscale/tailscaled_s390x_Linux
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
50K   ./tailscale/tailscale_ipn_setup_Windows.exe
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

testing ./tailscale/tailscale_aarch64_arm64_Linux.upx [OK]
  29579196 ->  12088172   40.87%   linux/arm64   ./tailscale/tailscale_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_merged_arm_Linux.upx [OK]
  33882238 ->   7831516   23.11%    linux/arm    ./tailscale/tailscale_merged_arm_Linux.upx
testing ./tailscale/tailscale_mipsle_Linux.upx [OK]
  32243490 ->  11917188   36.96%  linux/mipsel   ./tailscale/tailscale_mipsle_Linux.upx
testing ./tailscale/tailscale_merged_amd_x86_64_Linux.upx [OK]
  36728958 ->   9793772   26.66%   linux/amd64   ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
testing ./tailscale/tailscaled_mips_Linux.upx [OK]
  39035728 ->  14682792   37.61%   linux/mips    ./tailscale/tailscaled_mips_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx [OK]
  35913854 ->   8259868   23.00%  linux/ppc64le  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscaled_amd_geode_Linux.upx [OK]
  24736140 ->   7094420   28.68%   linux/i386    ./tailscale/tailscaled_amd_geode_Linux.upx
testing ./tailscale/tailscaled_mipsle_Linux.upx [OK]
  38868676 ->  14653376   37.70%  linux/mipsel   ./tailscale/tailscaled_mipsle_Linux.upx
testing ./tailscale/tailscaled_aarch64_arm64_Linux.upx [OK]
  38489081 ->  15816080   41.09%   linux/arm64   ./tailscale/tailscaled_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx [OK]
  21364862 ->   5191488   24.30%  linux/ppc64le  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx [OK]
  34078846 ->   8024952   23.55%   linux/arm64   ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_powerpc64_ppc64_Linux.upx [OK]
  21364862 ->   4979796   23.31%   linux/ppc64   ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_amd_geode_Linux.upx [OK]
  20771716 ->   5319508   25.61%   linux/i386    ./tailscale/tailscale_amd_geode_Linux.upx
testing ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx [OK]
  25690238 ->   6390064   24.87%  linux/ppc64le  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_amd_x86_64_Linux.upx [OK]
  22278248 ->   6207044   27.86%   linux/amd64   ./tailscale/tailscale_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_merged_i386_Linux.upx [OK]
  34394238 ->   9143892   26.59%   linux/i386    ./tailscale/tailscale_merged_i386_Linux.upx
testing ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx [OK]
  25690238 ->   6156596   23.96%   linux/ppc64   ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_mips_Linux.upx [OK]
  32392606 ->  11947932   36.88%   linux/mips    ./tailscale/tailscale_mips_Linux.upx
testing ./tailscale/tailscaled_amd_x86_64_Linux.upx [OK]
  28590232 ->   8010320   28.02%   linux/amd64   ./tailscale/tailscaled_amd_x86_64_Linux.upx
testing ./tailscale/tailscaled_arm_abi_Linux.upx [OK]
  35040724 ->  14514172   41.42%    linux/arm    ./tailscale/tailscaled_arm_abi_Linux.upx
testing ./tailscale/tailscaled_i386_Linux.upx [OK]
  24699276 ->   7084868   28.68%   linux/i386    ./tailscale/tailscaled_i386_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx [OK]
  35913854 ->   7970392   22.19%   linux/ppc64   ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_i386_Linux.upx [OK]
  20718468 ->   5776612   27.88%   linux/i386    ./tailscale/tailscale_i386_Linux.upx
testing ./tailscale/tailscale_arm_abi_Linux.upx [OK]
  29259770 ->  11844028   40.48%    linux/arm    ./tailscale/tailscale_arm_abi_Linux.upx

```

---

- #### Version
```console
$ ./tailscale/tailscale_amd_x86_64_Linux --version
1.98.3
  tailscale commit: a16e0f20cff0acd5617fd1b315df32cdad17a8fa
  long version: 1.98.3-ta16e0f20c-ge0c644472
  other commit: e0c6444725a27ff911a18cc4b18575d8700339d5
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
1.98.3
  tailscale commit: a16e0f20cff0acd5617fd1b315df32cdad17a8fa
  long version: 1.98.3-ta16e0f20c-ge0c644472
  other commit: e0c6444725a27ff911a18cc4b18575d8700339d5
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


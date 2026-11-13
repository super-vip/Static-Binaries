
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
./tailscale/tailscale_aarch64_arm64_Linux:                   ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=NQt921QQUZCuYetexeKx/Bs6VmY7yROgu-UWwVxAj/4xYhnGYJV2t7nOokDeT5/K3_5SSz0Kv1Wa7KBBmNS, BuildID[sha1]=a5c76de60d21fe00ae09053c9a150e924d262c0b, with debug_info, not stripped
./tailscale/tailscale_aarch64_arm64_Linux.upx:               ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=NQt921QQUZCuYetexeKx/Bs6VmY7yROgu-UWwVxAj/4xYhnGYJV2t7nOokDeT5/K3_5SSz0Kv1Wa7KBBmNS, statically linked, no section header
./tailscale/tailscale_aarch64_arm64_Windows.msi:             Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Arm64;1033, Revision Number: {EAC1FE75-2D99-4813-BFBE-CE154BC35B99}, Create Time/Date: Thu Nov 12 22:17:39 2026, Last Saved Time/Date: Thu Nov 12 22:17:39 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (6.0.2.0), Security: 2
./tailscale/tailscale_aarch64_arm64_macOS:                   Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_amd_geode_Linux:                       ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=xNCVLoLW-DNu06Ka1Tqa/vLQbaMug7uQS89J7A5YX/_znVVa-z7TMs2quUC5z3/pnY8cnNfo7qzp-i9qXdt, BuildID[sha1]=8879f3d13fdf59f7739b85a3764cc7e9e981d2b9, stripped
./tailscale/tailscale_amd_geode_Linux.upx:                   ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=xNCVLoLW-DNu06Ka1Tqa/vLQbaMug7uQS89J7A5YX/_znVVa-z7TMs2quUC5z3/pnY8cnNfo7qzp-i9qXdt, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Linux:                      ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=BFX5aoEkmdSmQrjzFg8R/v7pQ4TgxFg2wJpy3-EpL/qD3VYcFgdyc3YSaRps8M/g4EtdvfQxEKX2QamEKGP, BuildID[sha1]=a1b5d38390f70b10286ae0faa6d568deff904f5f, stripped
./tailscale/tailscale_amd_x86_64_Linux.upx:                  ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=BFX5aoEkmdSmQrjzFg8R/v7pQ4TgxFg2wJpy3-EpL/qD3VYcFgdyc3YSaRps8M/g4EtdvfQxEKX2QamEKGP, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Windows.msi:                Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: x64;1033, Revision Number: {92B7A47B-DD74-4307-91A7-A7F307010E5D}, Create Time/Date: Thu Nov 12 22:17:39 2026, Last Saved Time/Date: Thu Nov 12 22:17:39 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (6.0.2.0), Security: 2
./tailscale/tailscale_amd_x86_64_macOS:                      Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_arm_abi_Linux:                         ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=c3HhJwAhHnRX_P1Y-4Pu/-DkMemuvxfBQfSRa4Llh/ortaX1mc2CPOuaVnxoEg/aalAzK2KezM-RlvMgi9z, BuildID[sha1]=33a1b5bcf40451cfe9b1ef381b050bdf3d0837d5, with debug_info, not stripped
./tailscale/tailscale_arm_abi_Linux.upx:                     ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=c3HhJwAhHnRX_P1Y-4Pu/-DkMemuvxfBQfSRa4Llh/ortaX1mc2CPOuaVnxoEg/aalAzK2KezM-RlvMgi9z, statically linked, no section header
./tailscale/tailscale_i386_Linux:                            ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=zD3h1s6sQ4LVkKylBtnB/Rj2b-LmckELmwxsXEgwH/0wGki5MdUZj9AXhl2i82/baKGkqemTA3niLMX4k_5, BuildID[sha1]=0130fdbe7c6b5f71b70142ff912e9dabfa8924fb, stripped
./tailscale/tailscale_i386_Linux.upx:                        ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=zD3h1s6sQ4LVkKylBtnB/Rj2b-LmckELmwxsXEgwH/0wGki5MdUZj9AXhl2i82/baKGkqemTA3niLMX4k_5, statically linked, no section header
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
./tailscale/tailscale_merged_powerpc64_ppc64_Linux:          ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx:      ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux:      ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx:  ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_merged_s390x_Linux:                    ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_mips64_Linux:                          ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=me-2Sqz4MO5mxSuumeOa/SBWvgIGQM-nUdXblFo2Y/Mo-pDrSsjTJq5AKYOPdE/VPXURJU2ZLzjIIkXz5la, BuildID[sha1]=5e79c5a73a9a78ece4837e1d7faa926de5650839, with debug_info, not stripped
./tailscale/tailscale_mips64le_Linux:                        ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=xiCtro7_wlayWBrMwBSj/NBIICU0Wh6pU-Q4lUNzI/dRMNFmZFbX27oX2x4r-C/t3nV0a2wKRnPSnL_EW6n, BuildID[sha1]=49efe6bc675ec83d91d8dd9b934fca4939e2d534, with debug_info, not stripped
./tailscale/tailscale_mips_Linux:                            ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=Nhcw4Oo5566hXhgnXcQs/Jy2Lbcn0u0NX88vAHweE/ewZPd7YrVYLFRveCRApS/1vILRPEo3EV7SQrDah0-, BuildID[sha1]=10c821a30c1a7d0db67535ed56cf0b62ef66d7b9, with debug_info, not stripped
./tailscale/tailscale_mips_Linux.upx:                        ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=Nhcw4Oo5566hXhgnXcQs/Jy2Lbcn0u0NX88vAHweE/ewZPd7YrVYLFRveCRApS/1vILRPEo3EV7SQrDah0-, statically linked, no section header
./tailscale/tailscale_mipsle_Linux:                          ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=z3xD2bN0k50RE9dlxK68/QajbeIuq3KVeisVZpvU4/iR_5JAG48NW4-Mi36wRg/WeHJhh2V86G2EdArZ8y0, BuildID[sha1]=e23bca849ae8459eae8704ae500ca423ae55b848, with debug_info, not stripped
./tailscale/tailscale_mipsle_Linux.upx:                      ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=z3xD2bN0k50RE9dlxK68/QajbeIuq3KVeisVZpvU4/iR_5JAG48NW4-Mi36wRg/WeHJhh2V86G2EdArZ8y0, statically linked, no section header
./tailscale/tailscale_powerpc64_ppc64_Linux:                 ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64_ppc64_Linux.upx:             ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_powerpc64le_ppc64le_Linux:             ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx:         ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_riscv64_Linux:                         ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, Go BuildID=eIpTlwEkekunzFhRVHpd/FM_K9vqgOw5S7UwRf2Im/TggRcIF6A4koENR2oE2l/lO_qGGpfVdq49k9Ot9da, BuildID[sha1]=4687787a65286a36b8fe657e7cf994206b7bb22e, with debug_info, not stripped
./tailscale/tailscale_s390x_Linux:                           ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_setup_Windows.exe:                     PE32 executable (GUI) Intel 80386, for MS Windows, 6 sections
./tailscale/tailscale_x86_Windows.msi:                       Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Intel;1033, Revision Number: {E816E5FA-7153-401C-8E63-083703AF08C3}, Create Time/Date: Thu Nov 12 22:17:38 2026, Last Saved Time/Date: Thu Nov 12 22:17:38 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (6.0.2.0), Security: 2
./tailscale/tailscaled_aarch64_arm64_Linux:                  ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=8H5zGe5egFvgCaT21Ygt/uwwA-4dZSHLDkq5v-pd2/15THg3oxaMjPWjgkGsRG/l5CYSVCfYtK2PrAUdBaW, BuildID[sha1]=e7cfee8bd9b9a29fe74fadb0996a772908f1e253, with debug_info, not stripped
./tailscale/tailscaled_aarch64_arm64_Linux.upx:              ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=8H5zGe5egFvgCaT21Ygt/uwwA-4dZSHLDkq5v-pd2/15THg3oxaMjPWjgkGsRG/l5CYSVCfYtK2PrAUdBaW, statically linked, no section header
./tailscale/tailscaled_aarch64_arm64_macOS:                  Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_amd_geode_Linux:                      ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=2HemgZveofYzbt2w6Xnj/YmNxGy3Dn5-KYT-OFmGd/0apa8F9tQPgB7FCtYp9R/Y_ghyaiF92iZEj7ppy4i, BuildID[sha1]=253bd3896d19fae74133804b42e311a502bedcaa, stripped
./tailscale/tailscaled_amd_geode_Linux.upx:                  ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=2HemgZveofYzbt2w6Xnj/YmNxGy3Dn5-KYT-OFmGd/0apa8F9tQPgB7FCtYp9R/Y_ghyaiF92iZEj7ppy4i, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_Linux:                     ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=0_rfRv9jfDIf5e56FAwQ/AS8l_3R-O8AKbWxP20xX/qASUAv2FqVzQK8LwT2fn/7jwQo1mTEkOScpCHIJ4v, BuildID[sha1]=fee675ed52864c1e220a6f1e6ff069bfe9da1b2f, stripped
./tailscale/tailscaled_amd_x86_64_Linux.upx:                 ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=0_rfRv9jfDIf5e56FAwQ/AS8l_3R-O8AKbWxP20xX/qASUAv2FqVzQK8LwT2fn/7jwQo1mTEkOScpCHIJ4v, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_macOS:                     Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_arm_abi_Linux:                        ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=cK8j8y5oSD3n-tn9qAwl/6jr82U8DfsmFHvznYRu1/nTbdu7DNmGV-I6mWdxcw/_J-droN7b0Bq_mnsHKWZ, BuildID[sha1]=56bc2f022667ef048e3884157b4d843476b1ba63, with debug_info, not stripped
./tailscale/tailscaled_arm_abi_Linux.upx:                    ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=cK8j8y5oSD3n-tn9qAwl/6jr82U8DfsmFHvznYRu1/nTbdu7DNmGV-I6mWdxcw/_J-droN7b0Bq_mnsHKWZ, statically linked, no section header
./tailscale/tailscaled_i386_Linux:                           ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=pRgC5x6icw4e156LvT0t/DYbien3yn-_mw7syw5di/YyQAgC01GaF8PufP0aVa/RXsw-oqum0_VhU2xI4eo, BuildID[sha1]=965f6b9f9b78ed5e96a8e232a343ea98cfa7165d, stripped
./tailscale/tailscaled_i386_Linux.upx:                       ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=pRgC5x6icw4e156LvT0t/DYbien3yn-_mw7syw5di/YyQAgC01GaF8PufP0aVa/RXsw-oqum0_VhU2xI4eo, statically linked, no section header
./tailscale/tailscaled_mips64_Linux:                         ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=h0I-EhqNk-lNIEBU8uI9/hdKnz6TnmE6CdNrEKPh8/JOn47lv1Hf9EcVS9z-YY/ljOjxihh5RMBIdkokIgR, BuildID[sha1]=4862a0088371ca3f21b6c3f7741f55738c3c4ff4, with debug_info, not stripped
./tailscale/tailscaled_mips64le_Linux:                       ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=Y75fSJjinpb4USywyo4W/C5YtYJ4Kb_pkQ1i07_qJ/e-GHGpbt1siYLRJvcL4P/Dt1Gml49UGUPqE8HwXHu, BuildID[sha1]=16aae3be434ff8d60ced26b295d0eb8803316f1a, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux:                           ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=LTPSNtXdDUIru752vOKS/_UGZXN2q3tDlGZdsp7WC/lTAjHsVwWSFP8DSr2yZn/fYXVb_xqsQJlB84jxC-Q, BuildID[sha1]=28f1d6cceb9effff57b87563f63b0b4d2c5de945, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux.upx:                       ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=LTPSNtXdDUIru752vOKS/_UGZXN2q3tDlGZdsp7WC/lTAjHsVwWSFP8DSr2yZn/fYXVb_xqsQJlB84jxC-Q, statically linked, no section header
./tailscale/tailscaled_mipsle_Linux:                         ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=dtCvky3v8E93iv4YmJGE/AxQvgfmRvEmf3O4usI6B/XGK8PKjBFLcYKFRbs23Q/hHq42IBCGMvERP_7f_ts, BuildID[sha1]=58bc671ecae2bda6b41009f9f81c63458aa91a78, with debug_info, not stripped
./tailscale/tailscaled_mipsle_Linux.upx:                     ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=dtCvky3v8E93iv4YmJGE/AxQvgfmRvEmf3O4usI6B/XGK8PKjBFLcYKFRbs23Q/hHq42IBCGMvERP_7f_ts, statically linked, no section header
./tailscale/tailscaled_powerpc64_ppc64_Linux:                ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64_ppc64_Linux.upx:            ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_powerpc64le_ppc64le_Linux:            ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx:        ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_riscv64_Linux:                        ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, Go BuildID=U14174X1sm6XLSpy5dP5/RKpNSh9oQj0nLNE0zKkH/ESAPEDzKqd-V3SvFtOxZ/iTVvqiwXv9t_uWxE_q_2, BuildID[sha1]=5af1715855fe9501987f60a777cc83d5604a25b6, with debug_info, not stripped
./tailscale/tailscaled_s390x_Linux:                          ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped

--> SHA256SUM
362426a7417d85879cb76ae767375b1e839996cc63d5d2ebccd5b8bfdc736ec8  ./tailscale/tailscale_aarch64_arm64_Linux
9a51ef3757687dc9a75816c6b992373cc5a2be845b5bf45642c1e0c479f64780  ./tailscale/tailscale_aarch64_arm64_Linux.upx
904c4d877e306d601ac6dc1216091064769be9c942a2a1acc0cd98ffc6ee9191  ./tailscale/tailscale_aarch64_arm64_Windows.msi
758bd296723a348a70f5274b294baeb4053abd2e2ce58e2220e210946b618c6f  ./tailscale/tailscale_aarch64_arm64_macOS
5919b861469d180c784ca4351e3d4642eecb9b0e64d086cb77e144617cbfc148  ./tailscale/tailscale_amd_geode_Linux
f18c2a92d2af4bd87eb7922dd991f372102e33fe33eba1d9db07c2ecc73492dc  ./tailscale/tailscale_amd_geode_Linux.upx
3edbc8de42524fe6ed5c1d8636bdfe34cc8e9095277266496d51f644d54c199c  ./tailscale/tailscale_amd_x86_64_Linux
78b39ddf3e6c6d16e2351b06a5272fbdd9b28933f15db8482ffda0db26808a65  ./tailscale/tailscale_amd_x86_64_Linux.upx
676b5b32fdd1aeaee90d8e8f38e222635b216fbdfbf877bf01cb1d7cda330ec5  ./tailscale/tailscale_amd_x86_64_Windows.msi
248b7930c0c4c650f988bcb90a968da042066e0b826bf58efd8fe3a69fad8e7f  ./tailscale/tailscale_amd_x86_64_macOS
1c14fb51b91c9d70e24643a905f6046675a3f76d8bea89c9eb11e8e601c2adbb  ./tailscale/tailscale_arm_abi_Linux
76be1f486a1131bd8586af0c647a844261ca7e30a91f336ecbec419bb2a0c64e  ./tailscale/tailscale_arm_abi_Linux.upx
a67c50f40199a7a68118bf4ec262476b25054a4274351286b94edeecc244a285  ./tailscale/tailscale_i386_Linux
0d7e0a9d6af18279732af1a8b4ea8761cb2771652b81d175919a8f3b651bc2de  ./tailscale/tailscale_i386_Linux.upx
6838d8ec367e6024b60bc06a9f7af751dda0b5d59521c93c8b44d80d4ad18884  ./tailscale/tailscale_ipn_setup_Windows.exe
ab29fa3908211f8271be251080b73408b53247aebc62cf8619a3ac4363fe15ea  ./tailscale/tailscale_merged_aarch64_arm64_Linux
c1f3804f6dd2b217d96dd9b0999717b88f4336e79f1442decf67105d178575af  ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
68728bde1313493eb44dbd3be2e989eb00f60f4938d0d2845df9d45e32c25df7  ./tailscale/tailscale_merged_aarch64_arm64_macOS
ed3bb7bbc86c7adf4366e817aef2d38a557b0d85b409084a462f7ab019416bb1  ./tailscale/tailscale_merged_amd_x86_64_Linux
582b12cb0ed1bb788b65b815ace7b7a32954f7cb1230b6c56a47ae59ecf203f1  ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
267bebcfe539dd8353add30caf55a042bf996f8e688aae7910b9ecf61714f3f8  ./tailscale/tailscale_merged_amd_x86_64_macOS
facf7968b0e4c3dbc0cb75a15b4c553836aa961e64608cfad3d430debb6b38b9  ./tailscale/tailscale_merged_arm_Linux
4c28f530d96096b03e3b84602e7d277a37b7700126f7f4d71e7ac8bc361e3a0e  ./tailscale/tailscale_merged_arm_Linux.upx
1ec0077fbecc348406872701ade57d8195d9f086a8f71eef42091aa3b03bc0e4  ./tailscale/tailscale_merged_i386_Linux
c06fbbfeb42b63e71b9c5bbe72c3e639b729677e86d8107d2a2a669ccd9c4095  ./tailscale/tailscale_merged_i386_Linux.upx
092a1bfde1ddc72ac7f794da0b4c2e005deaf481a6ded6df61e999cc200bbc8d  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux
3f6f19b1703d7496ee31cadfc2eda7bdd55828750a3e0aa94766040b04ee258a  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
923b7eddae6598f89fa5eaf2c5ca9dec973466b568d2a77104a6b25bc26d6c06  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux
7a59788b23582df32d5ddb828edd1663477f301430e0476d964f5e242c9949be  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
0e887abf0e899dfb7bc32d1970f369e2490c21ca71f6ae0d13de5de8eadd06c4  ./tailscale/tailscale_merged_s390x_Linux
e290d275f31d1ee6515009e3ee6275053e34c21d9db8fef28f3767d3b0dc4082  ./tailscale/tailscale_mips64_Linux
c77a896edbe911830a510379b23e17a9826388f9046f9ed762bcdb5253d3bdbc  ./tailscale/tailscale_mips64le_Linux
041b363e9b5ef1f297d5d7b906edeaa4c38a545d574d6bed8a028a62bdb341ff  ./tailscale/tailscale_mips_Linux
0a24bb4ab048af098e995b2ddd72ff2645004499838b84f4c420b21a87fdc64f  ./tailscale/tailscale_mips_Linux.upx
c5ee590fa80cf42a7aadd289ee2eeffae8742e6fefde86ddbe00000b5ffa1fa2  ./tailscale/tailscale_mipsle_Linux
7721014fdc4a52691e2e5aff69271534585c0e06c1c00b25e8d757a18658654b  ./tailscale/tailscale_mipsle_Linux.upx
ebb28369f12cedc33e7c1c4727c3707ee3c0dd0ddc03e2da2f446a318d9156a8  ./tailscale/tailscale_powerpc64_ppc64_Linux
bc1440c4e7f15a0b3fe76b9fa76be655a224a579b7ea5b9580892877a12c16f1  ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
665c060ea1e40b44d3ccac889a5ef8b4bd5ccfa5e608f352d3e16c42f223c900  ./tailscale/tailscale_powerpc64le_ppc64le_Linux
fc2faad73dad67d431356a6409b6d821438bf2868884546280eafd291ecb9262  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
59e293a236713283976098e831b3178413637fd0a1e877fc5db6c72818a626e6  ./tailscale/tailscale_riscv64_Linux
10a7d14c9b68fae2dcee5a1fe19206f933e206b8cc04069bc3fe1efdb5476ec1  ./tailscale/tailscale_s390x_Linux
64a8ad28cbb67a6171236abe39f75a039a761a0e1aacdef75b26781887cef9a8  ./tailscale/tailscale_setup_Windows.exe
54e063e08eb8d618c57be7fd3b82cf4e2d3ab3a95a0b366e113ab01f353d99e5  ./tailscale/tailscale_x86_Windows.msi
bd34e19b71fdbb11a6e603ac69af5e4d360ea983d0d9f93ff0a7210afff52ad5  ./tailscale/tailscaled_aarch64_arm64_Linux
14999cc94f103baf0f508522c266cf935c3360b7b6902b7730fb09c6e1544cf3  ./tailscale/tailscaled_aarch64_arm64_Linux.upx
3045786fe6191b3d64ae9d2b03b5fffcf080e3cb3073a3c2e8e69e57ea05e2cf  ./tailscale/tailscaled_aarch64_arm64_macOS
757c5074ec8cbb1fced3d3e5611276e0dc42445c67de2cdc29f7126703aacca1  ./tailscale/tailscaled_amd_geode_Linux
fb4370f406eafe15bae528509e338230085033dce4a32a42330b73ee80794ffb  ./tailscale/tailscaled_amd_geode_Linux.upx
086ad509939f0907699c4e87284f2789232f1098c9154ff74993afdf66cb420f  ./tailscale/tailscaled_amd_x86_64_Linux
f935a89281d71aa809ad19049ad0b88dd4c01c2ba51dbf81a37c1ec31dc2f4c0  ./tailscale/tailscaled_amd_x86_64_Linux.upx
b5304b43985998d94d5c2c94e0eeb9e160a76906fa0ecb224af45c3b878e684d  ./tailscale/tailscaled_amd_x86_64_macOS
7b6e407353575cb4dcd1d95da7a1b197c9e6c0597b9570007d7564d2929a7ae4  ./tailscale/tailscaled_arm_abi_Linux
59e110de669c1ac0b62fc578d80af2fd0b115e0d9f846a8a4fc4aa48531fadd9  ./tailscale/tailscaled_arm_abi_Linux.upx
5e59f04ccec0456c8284104e4e5b1f7bac98b6aaaedcf357937bb4b6bc08618a  ./tailscale/tailscaled_i386_Linux
eeb5b6c3e7fc288236f8b1578b9441d024d5faa5291492f5b0ae6d0bf5eeda59  ./tailscale/tailscaled_i386_Linux.upx
b19769e9ee0d8d3e8933d3cc7578a322cd80878e8fc422356863b34861ab0004  ./tailscale/tailscaled_mips64_Linux
fdc8e85bfd822a6fa6aca97d01021e0d66e36f49876874ed4c05b43b66b76151  ./tailscale/tailscaled_mips64le_Linux
7060200de8ae95f35b38f41ab956c71c867f9b092444b4e351149a014d78a67b  ./tailscale/tailscaled_mips_Linux
29c4ec9abcfc2ae055a1fb58ef3db7013e701fc24f57f3a29c82652031f04732  ./tailscale/tailscaled_mips_Linux.upx
80b89c4073934d6f687222e40cf5a0f3741c73c9936718891c49e4106a0fa83c  ./tailscale/tailscaled_mipsle_Linux
fdb70af1a56fe07e74a2818bccefcc75d5c3fb1c6e6a385058cf27a3186a4c11  ./tailscale/tailscaled_mipsle_Linux.upx
71a8008e57e681bed6b034f214393564a11099649e16683c4c07bb01c8c454f4  ./tailscale/tailscaled_powerpc64_ppc64_Linux
a8b3bf9f3ce5cb6520ed722051c0fa094927b37a35aff08c3258496cad375ecc  ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
b544d500e2a0d33fe420294a82354c02f715f29492b81c37a522b8b3a551bdaf  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux
935ad9c8d8b4899521d8a40cb49d34bdcfe0b76fc43a6bfd957c73a3d9d34f59  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
06fd4e86b258442b148cf4d7f17e294b29fd27e19f9e80c4bc2a16ad773e2003  ./tailscale/tailscaled_riscv64_Linux
4a064377bffe394d57df47bd5622e699df48cac1f5c212a3cb918f3a300e9fc3  ./tailscale/tailscaled_s390x_Linux
```


---

- #### Sizes

```console
31M   ./tailscale/tailscale_aarch64_arm64_Linux
13M   ./tailscale/tailscale_aarch64_arm64_Linux.upx
35M   ./tailscale/tailscale_aarch64_arm64_Windows.msi
11M   ./tailscale/tailscale_aarch64_arm64_macOS
22M   ./tailscale/tailscale_amd_geode_Linux
6.1M  ./tailscale/tailscale_amd_geode_Linux.upx
23M   ./tailscale/tailscale_amd_x86_64_Linux
6.4M  ./tailscale/tailscale_amd_x86_64_Linux.upx
37M   ./tailscale/tailscale_amd_x86_64_Windows.msi
11M   ./tailscale/tailscale_amd_x86_64_macOS
31M   ./tailscale/tailscale_arm_abi_Linux
13M   ./tailscale/tailscale_arm_abi_Linux.upx
22M   ./tailscale/tailscale_i386_Linux
6.1M  ./tailscale/tailscale_i386_Linux.upx
70K   ./tailscale/tailscale_ipn_setup_Windows.exe
35M   ./tailscale/tailscale_merged_aarch64_arm64_Linux
8.3M  ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
20M   ./tailscale/tailscale_merged_aarch64_arm64_macOS
38M   ./tailscale/tailscale_merged_amd_x86_64_Linux
11M   ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
20M   ./tailscale/tailscale_merged_amd_x86_64_macOS
36M   ./tailscale/tailscale_merged_arm_Linux
8.1M  ./tailscale/tailscale_merged_arm_Linux.upx
36M   ./tailscale/tailscale_merged_i386_Linux
9.4M  ./tailscale/tailscale_merged_i386_Linux.upx
37M   ./tailscale/tailscale_merged_powerpc64_ppc64_Linux
8.2M  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
37M   ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux
8.5M  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
39M   ./tailscale/tailscale_merged_s390x_Linux
35M   ./tailscale/tailscale_mips64_Linux
35M   ./tailscale/tailscale_mips64le_Linux
34M   ./tailscale/tailscale_mips_Linux
13M   ./tailscale/tailscale_mips_Linux.upx
34M   ./tailscale/tailscale_mipsle_Linux
13M   ./tailscale/tailscale_mipsle_Linux.upx
23M   ./tailscale/tailscale_powerpc64_ppc64_Linux
5.2M  ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
23M   ./tailscale/tailscale_powerpc64le_ppc64le_Linux
5.4M  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
30M   ./tailscale/tailscale_riscv64_Linux
24M   ./tailscale/tailscale_s390x_Linux
51M   ./tailscale/tailscale_setup_Windows.exe
37M   ./tailscale/tailscale_x86_Windows.msi
40M   ./tailscale/tailscaled_aarch64_arm64_Linux
17M   ./tailscale/tailscaled_aarch64_arm64_Linux.upx
19M   ./tailscale/tailscaled_aarch64_arm64_macOS
26M   ./tailscale/tailscaled_amd_geode_Linux
7.3M  ./tailscale/tailscaled_amd_geode_Linux.upx
29M   ./tailscale/tailscaled_amd_x86_64_Linux
8.2M  ./tailscale/tailscaled_amd_x86_64_Linux.upx
19M   ./tailscale/tailscaled_amd_x86_64_macOS
37M   ./tailscale/tailscaled_arm_abi_Linux
16M   ./tailscale/tailscaled_arm_abi_Linux.upx
25M   ./tailscale/tailscaled_i386_Linux
7.3M  ./tailscale/tailscaled_i386_Linux.upx
41M   ./tailscale/tailscaled_mips64_Linux
41M   ./tailscale/tailscaled_mips64le_Linux
40M   ./tailscale/tailscaled_mips_Linux
16M   ./tailscale/tailscaled_mips_Linux.upx
40M   ./tailscale/tailscaled_mipsle_Linux
16M   ./tailscale/tailscaled_mipsle_Linux.upx
27M   ./tailscale/tailscaled_powerpc64_ppc64_Linux
6.3M  ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
27M   ./tailscale/tailscaled_powerpc64le_ppc64le_Linux
6.5M  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
36M   ./tailscale/tailscaled_riscv64_Linux
28M   ./tailscale/tailscaled_s390x_Linux
```

---

- #### UPX
```console

testing ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx [OK]
  27263100 ->   6806372   24.97%  linux/ppc64le  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscaled_arm_abi_Linux.upx [OK]
  37986984 ->  15959868   42.01%    linux/arm    ./tailscale/tailscaled_arm_abi_Linux.upx
testing ./tailscale/tailscale_mips_Linux.upx [OK]
  34928488 ->  13143372   37.63%   linux/mips    ./tailscale/tailscale_mips_Linux.upx
testing ./tailscale/tailscale_merged_amd_x86_64_Linux.upx [OK]
  39194748 ->  10508704   26.81%   linux/amd64   ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx [OK]
  36307068 ->   8605552   23.70%   linux/arm64   ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
testing ./tailscale/tailscaled_amd_x86_64_Linux.upx [OK]
  30225784 ->   8549696   28.29%   linux/amd64   ./tailscale/tailscaled_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_mipsle_Linux.upx [OK]
  34921392 ->  13269444   38.00%  linux/mipsel   ./tailscale/tailscale_mipsle_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx [OK]
  38273148 ->   8850408   23.12%  linux/ppc64le  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_merged_i386_Linux.upx [OK]
  36765820 ->   9829800   26.74%   linux/i386    ./tailscale/tailscale_merged_i386_Linux.upx
testing ./tailscale/tailscaled_amd_geode_Linux.upx [OK]
  26232460 ->   7588328   28.93%   linux/i386    ./tailscale/tailscaled_amd_geode_Linux.upx
testing ./tailscale/tailscale_amd_geode_Linux.upx [OK]
  22340780 ->   6304976   28.22%   linux/i386    ./tailscale/tailscale_amd_geode_Linux.upx
testing ./tailscale/tailscale_merged_arm_Linux.upx [OK]
  36831356 ->   8438140   22.91%    linux/arm    ./tailscale/tailscale_merged_arm_Linux.upx
testing ./tailscale/tailscaled_mips_Linux.upx [OK]
  41695902 ->  15951976   38.26%   linux/mips    ./tailscale/tailscaled_mips_Linux.upx
testing ./tailscale/tailscale_powerpc64_ppc64_Linux.upx [OK]
  23068796 ->   5409012   23.45%   linux/ppc64   ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscaled_mipsle_Linux.upx [OK]
  41691366 ->  16099352   38.62%  linux/mipsel   ./tailscale/tailscaled_mipsle_Linux.upx
testing ./tailscale/tailscaled_i386_Linux.upx [OK]
  26195596 ->   7578788   28.93%   linux/i386    ./tailscale/tailscaled_i386_Linux.upx
testing ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx [OK]
  27263100 ->   6566524   24.09%   linux/ppc64   ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx [OK]
  38338684 ->   8549064   22.30%   linux/ppc64   ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_aarch64_arm64_Linux.upx [OK]
  31913193 ->  13438712   42.11%   linux/arm64   ./tailscale/tailscale_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_arm_abi_Linux.upx [OK]
  32010813 ->  13204112   41.25%    linux/arm    ./tailscale/tailscale_arm_abi_Linux.upx
testing ./tailscale/tailscale_i386_Linux.upx [OK]
  22287532 ->   6293132   28.24%   linux/i386    ./tailscale/tailscale_i386_Linux.upx
testing ./tailscale/tailscale_amd_x86_64_Linux.upx [OK]
  23739672 ->   6697112   28.21%   linux/amd64   ./tailscale/tailscale_amd_x86_64_Linux.upx
testing ./tailscale/tailscaled_aarch64_arm64_Linux.upx [OK]
  40986698 ->  17383388   42.41%   linux/arm64   ./tailscale/tailscaled_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx [OK]
  23068796 ->   5615696   24.34%  linux/ppc64le  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx

```

---

- #### Version
```console
$ ./tailscale/tailscale_amd_x86_64_Linux --version
1.104.7
  tailscale commit: fb3b9b2964ace04490fbd65d4f26a0eaf362131f
  long version: 1.104.7-tfb3b9b296-g0651cc45e
  other commit: 0651cc45e79e308b0b3b808f4b42e7f3a1a8c221
  go version: go1.27.4 (tailscale/go 1635316a95)

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
1.104.7
  tailscale commit: fb3b9b2964ace04490fbd65d4f26a0eaf362131f
  long version: 1.104.7-tfb3b9b296-g0651cc45e
  other commit: 0651cc45e79e308b0b3b808f4b42e7f3a1a8c221
  go version: go1.27.4 (tailscale/go 1635316a95)

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


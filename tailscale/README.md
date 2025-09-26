
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
./tailscale/tailscale_aarch64_arm64_Linux:                   ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, BuildID[sha1]=f1a2123e555ef494eada7113dc791061e73f6735, with debug_info, not stripped
./tailscale/tailscale_aarch64_arm64_Linux.upx:               ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=OxY-JRAtZQVie3Q1MCZV/YU4G4TPQW2eDWOQXqmf_/KgNBiWmSdsUisG4Ic24M/21th6gwGdl9v99t5tm8h, statically linked, no section header
./tailscale/tailscale_aarch64_arm64_Windows.msi:             Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Arm64;1033, Revision Number: {5F61D0C3-1E64-45EB-A02B-DDD24DEB4C25}, Create Time/Date: Thu Sep 25 14:50:19 2025, Last Saved Time/Date: Thu Sep 25 14:50:19 2025, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscale_aarch64_arm64_macOS:                   Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_amd_geode_Linux:                       ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, BuildID[sha1]=db034045d9c8e27c162c1f11c51b9674bd38b5b3, stripped
./tailscale/tailscale_amd_geode_Linux.upx:                   ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=OJChEfY1E77bgdGyLct3/eUB8SFRiIaa4YQFlc1ji/3piY4mhpp1WCYfVvd6vU/lozcz_QJdxU3uRlQ0REM, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Linux:                      ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, BuildID[sha1]=1fce7b95b42711af51c23664ddc6adadf81314f3, stripped
./tailscale/tailscale_amd_x86_64_Linux.upx:                  ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=CTzVBIbR9DhzlMdaRKOU/RMDIO01fKHy_hAk1x3fg/Z4gQIeaziZ4X0EMibVFR/t9SxE2iyKxG0ZahLiMDs, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Windows.msi:                Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: x64;1033, Revision Number: {9EA1EF12-4ECA-4157-91AF-D4326F80FED4}, Create Time/Date: Thu Sep 25 14:50:00 2025, Last Saved Time/Date: Thu Sep 25 14:50:00 2025, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscale_amd_x86_64_macOS:                      Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_arm_abi_Linux:                         ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, BuildID[sha1]=e500651c28b222b695461fd55ab2856b53bcfbac, with debug_info, not stripped
./tailscale/tailscale_arm_abi_Linux.upx:                     ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=hb7LZR_hzJOtv9YyXAha/pM6zh5yWg_GIkCttVGG7/Ijak6LfCsdOyc7vkgj90/C-N-QiJRf6UcsxEShTSp, statically linked, no section header
./tailscale/tailscale_i386_Linux:                            ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, BuildID[sha1]=b0957239cb06cbd33f7fa8224e3c6d14c93b83e5, stripped
./tailscale/tailscale_i386_Linux.upx:                        ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=oVrDx3mOicKv3Uo63nDg/n-mvYsDcCMZAaQ_Fw3wH/VN-YFz6ubYy2uadihP9U/ag64fsEoqCe9F5ii-S46, statically linked, no section header
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
./tailscale/tailscale_mips64_Linux:                          ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, BuildID[sha1]=8adb2bcf0318fa9fbde38af3ad72b1e68f2a7177, with debug_info, not stripped
./tailscale/tailscale_mips64le_Linux:                        ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, BuildID[sha1]=f23d30813a20d0d2a871fcaac8c7b5e40dbabe8d, with debug_info, not stripped
./tailscale/tailscale_mips_Linux:                            ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, BuildID[sha1]=0dd6a68dffca2c5d0bfb76011681818efd40e56f, with debug_info, not stripped
./tailscale/tailscale_mips_Linux.upx:                        ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=sygUdjDm5fsDvortch4J/qpSg6a0nTiBhq87GOi0R/-Poq0hNcqb7xWmbGBCOf/yc4VL-xRUST9rELGPFai, statically linked, no section header
./tailscale/tailscale_mipsle_Linux:                          ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, BuildID[sha1]=fa616ac1370a6c8b82a96c4db01a19cfe99da7e0, with debug_info, not stripped
./tailscale/tailscale_mipsle_Linux.upx:                      ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=5qBBO_vGBV4xzfq1Kt13/wJkdTlesERpUQ5rtiQOr/l96dujwWdnnpO47AZH-2/-ET7Nc5xXB6FEZyDWvW6, statically linked, no section header
./tailscale/tailscale_powerpc64_ppc64_Linux:                 ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64_ppc64_Linux.upx:             ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_powerpc64le_ppc64le_Linux:             ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx:         ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_riscv64_Linux:                         ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, BuildID[sha1]=53c590692a5ee2da3515a80fee38755abf5c1683, with debug_info, not stripped
./tailscale/tailscale_s390x_Linux:                           ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_setup_Windows.exe:                     PE32 executable (GUI) Intel 80386, for MS Windows, 6 sections
./tailscale/tailscale_x86_Windows.msi:                       Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Intel;1033, Revision Number: {C7B30867-24F8-447E-A987-06F34BEDDB0E}, Create Time/Date: Thu Sep 25 14:50:19 2025, Last Saved Time/Date: Thu Sep 25 14:50:19 2025, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscaled_aarch64_arm64_Linux:                  ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, BuildID[sha1]=c27d8cd93d873ded88779b1aa7138a8ac4e46dbd, with debug_info, not stripped
./tailscale/tailscaled_aarch64_arm64_Linux.upx:              ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=14RlGfRhOFfHu9WIxbB8/6iNOdjZDe2vCudlbPo_1/XJIej2Xcji0ibqs2bxdY/MkLgDLwJZ1H72lq95WNg, statically linked, no section header
./tailscale/tailscaled_aarch64_arm64_macOS:                  Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_amd_geode_Linux:                      ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, BuildID[sha1]=1634907efd181ecb899afce1dc16afd54f511149, stripped
./tailscale/tailscaled_amd_geode_Linux.upx:                  ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=0npQk95ezr2bB3q0xmH8/UNevsHRGbEGpdyhMbzjw/YTxSB2wGqmf_EyW1j-6m/HVMHyo_NgkyYRTAa1wsy, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_Linux:                     ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, BuildID[sha1]=c1817f9f615dd918f3a2c33feb3540a2f2229525, stripped
./tailscale/tailscaled_amd_x86_64_Linux.upx:                 ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=gIcnZmQAohwyXUc7Sa3x/JNlsBSrf8lur-sNAfVEK/uYGTJqG9QSz_MTQyUB2H/mkMU1FxmDlSVMSYzdBxH, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_macOS:                     Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_arm_abi_Linux:                        ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, BuildID[sha1]=858a1a9615ffe861463d0549cb8e63698db447de, with debug_info, not stripped
./tailscale/tailscaled_arm_abi_Linux.upx:                    ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=Y5dNrP_8JvczotjVJK5_/sHLe0eyKxRrxScqR70hl/b2V1mK_q44BiycF73dRD/vtP9ZHyeKpdVewtuPZNy, statically linked, no section header
./tailscale/tailscaled_i386_Linux:                           ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, BuildID[sha1]=8a2e1b3482a53d15655e5adace280180f9da0cb1, stripped
./tailscale/tailscaled_i386_Linux.upx:                       ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=UBEfemqEKNPz_1MwreBC/WZOIIEQNj6tLiKA2HFwE/8jjfp_guLXXR4hpRkMbZ/cslF9cKBz6lJSp1eMySX, statically linked, no section header
./tailscale/tailscaled_mips64_Linux:                         ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, BuildID[sha1]=4b4533ab184a4a4e0010c30d60a04bf9f0a0c513, with debug_info, not stripped
./tailscale/tailscaled_mips64le_Linux:                       ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, BuildID[sha1]=c37c3db91a929a6cf4293d10c55e6a5ab56b7044, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux:                           ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, BuildID[sha1]=49c05645fac30fd845e506b008c6bc8904a4bd7e, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux.upx:                       ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=wnFpYJOJ0tNhHUvqjTGq/6NHH6mSZ8pTz15oQf0Dw/21YkHhvWCzD1o_OPew_S/3SXXiXqEgE7Bs2CqDfTA, statically linked, no section header
./tailscale/tailscaled_mipsle_Linux:                         ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, BuildID[sha1]=33d26bebfe210f96e6dbe606c1ed1be8ffb93d76, with debug_info, not stripped
./tailscale/tailscaled_mipsle_Linux.upx:                     ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=-FID3BklwIMy1P7Drbfk/O9zghkgKAc5FCg3S4vO5/m07-Kg-N-t5vfdeIXKPw/9J03xa9BzPnWFDZiPz4F, statically linked, no section header
./tailscale/tailscaled_powerpc64_ppc64_Linux:                ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64_ppc64_Linux.upx:            ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_powerpc64le_ppc64le_Linux:            ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx:        ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_riscv64_Linux:                        ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, BuildID[sha1]=47b5be158f1325f0343d897fb76353b4dd72c96f, with debug_info, not stripped
./tailscale/tailscaled_s390x_Linux:                          ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped

--> SHA256SUM
ff8092ae12acba2d240d314abc5ac025ed22a6a9569f0c4994c29d80b0eb01bb  ./tailscale/tailscale_aarch64_arm64_Linux
8c7e4c6d9d232ac1d0e2f867f49b46e1c917b2539443c0f8f2ef066dff166b35  ./tailscale/tailscale_aarch64_arm64_Linux.upx
3423db4c365a9b034b08c43e766ee81a01577f2a2634f612f242d9f06e055de4  ./tailscale/tailscale_aarch64_arm64_Windows.msi
758bd296723a348a70f5274b294baeb4053abd2e2ce58e2220e210946b618c6f  ./tailscale/tailscale_aarch64_arm64_macOS
abf5728bf982128ec638363fb547503d1beeda1fbe5943e41d2fb48928b63049  ./tailscale/tailscale_amd_geode_Linux
109da268ac0baf6099bd0bcd112fca1d6afda397f2ba97b0b396f7a82719d087  ./tailscale/tailscale_amd_geode_Linux.upx
8ed842262f21cf02f8fd091de1354487ed592229a28cf2ee7f0249de30180b16  ./tailscale/tailscale_amd_x86_64_Linux
2dd8f8cc681f626e36b71a32501cc7a9a0105d461431c85f932e6a038eb71f49  ./tailscale/tailscale_amd_x86_64_Linux.upx
b7ba47d32e336e8b58a3ce528d8726e0067494c7216aa86c35ca3076364272c5  ./tailscale/tailscale_amd_x86_64_Windows.msi
248b7930c0c4c650f988bcb90a968da042066e0b826bf58efd8fe3a69fad8e7f  ./tailscale/tailscale_amd_x86_64_macOS
80c0f7995633c886b8605ee431df09682efe052ff48d6a20f6244019eb6088f7  ./tailscale/tailscale_arm_abi_Linux
7551e82b3d4723577841b90f229ffc0be273f0882629f1d20b8fe5dbb1d4f3f0  ./tailscale/tailscale_arm_abi_Linux.upx
9cbf2c1f29d961be05c3481b49c44e6121254719ae7a08c1a00f1ae7c8182067  ./tailscale/tailscale_i386_Linux
a2f26a52022ea042e2f8b06f634213a10052b795c68eab1fa3d550439bfdbf55  ./tailscale/tailscale_i386_Linux.upx
d63925f5d02a356d4a5ba6535a5ce445724c7d1e1631f8e8c147fd608239217f  ./tailscale/tailscale_ipn_setup_Windows.exe
aca6a34ccb20a9ceed6796a27513a435da3cfdb2ccf8193be42f204f6afdf780  ./tailscale/tailscale_merged_aarch64_arm64_Linux
e97fe2b7cc10b5e5979e9933ccdb56790d580295a5febfa906a01f18ba0477e1  ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
68728bde1313493eb44dbd3be2e989eb00f60f4938d0d2845df9d45e32c25df7  ./tailscale/tailscale_merged_aarch64_arm64_macOS
8e14fe43c5c429b61b657ba530bae0b92688fe6472cfc4cf8c861733cdd1a6cf  ./tailscale/tailscale_merged_amd_x86_64_Linux
9b25118c5c46d2d6a3f264112e94c1a966660f36081a96f66c243ec74583d4cf  ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
267bebcfe539dd8353add30caf55a042bf996f8e688aae7910b9ecf61714f3f8  ./tailscale/tailscale_merged_amd_x86_64_macOS
eaee205920ca9fb17a11364d3394301dad666155ebeecf7527e89d0021384eec  ./tailscale/tailscale_merged_arm_Linux
eefe9c61a705bf6a3a60686fc45ff5733fedefe162f3c8e3c357492af0d214ea  ./tailscale/tailscale_merged_arm_Linux.upx
27d12720d26207495000af0728be899dd715ad89aef70baa6395fe109f13808e  ./tailscale/tailscale_merged_i386_Linux
6f4290ae36a82f6e294a65976c28f599e23fe52e76ecfabb4b1a89b7f01a22af  ./tailscale/tailscale_merged_i386_Linux.upx
abb23f98e3ea3f86eee44b96bba818a78775ef947846acf0a0b5a40bd7156556  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux
310da59d7b6a8d8e2e87f2ad3365e5095d15e6eae2403b7c2448ab6638d28003  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
817d123f28c2987fd64eead5ce51c47e67429ded00c221fdda1f95b60a285069  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux
674404ebc368a2334b9e884266d7e7caca028947d149d4c71722517c2f3be865  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
0190bfb395d5b77d0aa4481ec20498831b0514ba8b956774a0f40f2186f45fdc  ./tailscale/tailscale_merged_s390x_Linux
a367d160857fdfd61c08470c7754403acc3929bbce27ee5b84d5841e05fe44b6  ./tailscale/tailscale_mips64_Linux
217d89b269b47467c7f63f9874ed77df2473d0257496add0da76477699bb01c1  ./tailscale/tailscale_mips64le_Linux
bcd43b984e8afe59d371c23b3c9941a5bcb654d7e8d3e50e69fe036eff48469d  ./tailscale/tailscale_mips_Linux
ff921838972544565acc87a22e36df55bf6607ee8096e1168c63aa3225472f65  ./tailscale/tailscale_mips_Linux.upx
83b88e8efa5223d0a2746849566705c5c36ef5e9befe8ec71c4b9484dea677ee  ./tailscale/tailscale_mipsle_Linux
fb6919eaa7b96d1314b6907ce95938c59cc657692acf06d2d1adbb628874eb47  ./tailscale/tailscale_mipsle_Linux.upx
aa064905bca93b6628f929803f0e7729d2ee79b00bb53cf9b5ec9cfcbf8f9997  ./tailscale/tailscale_powerpc64_ppc64_Linux
dbbfbf9c336b7efc615ac2ca0d0f08230719f3ee82709773cd3f67378b544436  ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
453ebb69741c922caf41e5589c5ab8a47e1bfe4a18c5acd207e29d9a9b577468  ./tailscale/tailscale_powerpc64le_ppc64le_Linux
3abad20a35cd4c969abb5a3032d718ea7353b133a5cb2db949d4f013584bebc8  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
72ff08d8c87a167a200b2468b59d10ca13d9aa45145ca859cbc5b0582e87055f  ./tailscale/tailscale_riscv64_Linux
b186cf4b499ac5aa5c67abc9d7d967d99cc9ca22a83a215f5385bdd7c5c7eeb0  ./tailscale/tailscale_s390x_Linux
64a8ad28cbb67a6171236abe39f75a039a761a0e1aacdef75b26781887cef9a8  ./tailscale/tailscale_setup_Windows.exe
029b25037a03c7db1fdc68c8aa5a495283a0e34aec9d20563896e4e6e2421698  ./tailscale/tailscale_x86_Windows.msi
d9e38bcf4e254513a4be9f570bb22ef84333ce6e942a7c199f601c10d74a48c0  ./tailscale/tailscaled_aarch64_arm64_Linux
f27ec705dd6505dc6fa35bb04252d0d2de6dbb7cbd328f0aae25e67104f531ce  ./tailscale/tailscaled_aarch64_arm64_Linux.upx
3045786fe6191b3d64ae9d2b03b5fffcf080e3cb3073a3c2e8e69e57ea05e2cf  ./tailscale/tailscaled_aarch64_arm64_macOS
3a6ed90109e211e5bfcc4704a0af67f07be3ae1900dfbdd680dee60b14cc19c5  ./tailscale/tailscaled_amd_geode_Linux
53a8887547f0bf91c6593b6e76dc730b2423f2b8cfe76c9787df1f219134b3cb  ./tailscale/tailscaled_amd_geode_Linux.upx
af658c0b85253a4d9ec966653a074bd697a7d5a4f4f834def6e32b8bf3ea77ea  ./tailscale/tailscaled_amd_x86_64_Linux
6e5c08f8e9cfe8019eef618bc55e7f4f21d726651205b9deaa5e8a7ec58ecdd5  ./tailscale/tailscaled_amd_x86_64_Linux.upx
b5304b43985998d94d5c2c94e0eeb9e160a76906fa0ecb224af45c3b878e684d  ./tailscale/tailscaled_amd_x86_64_macOS
b4d456e54f4d9418399f6d6f936bb1bd33f27cad3a79c432e94e339709d16e4c  ./tailscale/tailscaled_arm_abi_Linux
f92d6822fa0295efab990c4f5f54ae94d3b63d1e3be5b99d3d2b7573d8e7c29b  ./tailscale/tailscaled_arm_abi_Linux.upx
442c001ff721aa8a40dfd34eeef5396d1c8775bb01922ab3fc7ada426ecf7c1f  ./tailscale/tailscaled_i386_Linux
22954a7aa52b8a36f1bda3088f882001fa60472a41409041b4ee951252b6005c  ./tailscale/tailscaled_i386_Linux.upx
34a3f893a097ee72034bc55c58c3d807b7fcc8d07627dde4e875397b06d6d32f  ./tailscale/tailscaled_mips64_Linux
c424e83697992ab2c9983353de59d1ff864b8c73cc6342177f286f4175f8d7a4  ./tailscale/tailscaled_mips64le_Linux
dc5c37c19b139e9f146d905ec40517a50339deab76d19ee1f5f504f1a73512ed  ./tailscale/tailscaled_mips_Linux
f539dd6ffe92c497a901135bfa70f7831b9130e40abddd8d49eee371c624da51  ./tailscale/tailscaled_mips_Linux.upx
5ca2fd5fa878338dcd28fad7fcf3be6369f31d1fe12f53270a68614daa58a94e  ./tailscale/tailscaled_mipsle_Linux
a3a4ad566d01fe017c4a41e066fec1206c08d855235163c5bc3770fc4befb77f  ./tailscale/tailscaled_mipsle_Linux.upx
405f126756fc0c4fa26ccc5487e5b40f53e258b0e87702ab0ba4abad125f353d  ./tailscale/tailscaled_powerpc64_ppc64_Linux
3d411949d1eaf0e65a6675ed116a03f7d852854207bf459d2b944229c791fd13  ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
0501e64f8f6fd29760fb3193daaf0a0d26bbd9e6dceb3f53827668652697fed7  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux
228d7b55a66cea638178ab61fc7dd77f90a8a60e34564b2780abfbf761fe5756  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
005345bf5599802da2690766f82b47f81e125183046b463975db4fc85720b4b8  ./tailscale/tailscaled_riscv64_Linux
f721195bf4ff7e5da8c3739f0f7d5bbf22ed1899ae4d4b59be09baa2b20ef4cd  ./tailscale/tailscaled_s390x_Linux
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
4.6M  ./tailscale/tailscale_i386_Linux.upx
46K   ./tailscale/tailscale_ipn_setup_Windows.exe
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

testing ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx [OK]
  25100436 ->   5981072   23.83%   linux/ppc64   ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_merged_arm_Linux.upx [OK]
  30408852 ->   7146608   23.50%    linux/arm    ./tailscale/tailscale_merged_arm_Linux.upx
testing ./tailscale/tailscaled_arm_abi_Linux.upx [OK]
  34213771 ->  14109220   41.24%    linux/arm    ./tailscale/tailscaled_arm_abi_Linux.upx
testing ./tailscale/tailscaled_i386_Linux.upx [OK]
  24019748 ->   6861416   28.57%   linux/i386    ./tailscale/tailscaled_i386_Linux.upx
testing ./tailscale/tailscaled_mips_Linux.upx [OK]
  38049787 ->  14241592   37.43%   linux/mips    ./tailscale/tailscaled_mips_Linux.upx
testing ./tailscale/tailscale_merged_amd_x86_64_Linux.upx [OK]
  32497812 ->   8929104   27.48%   linux/amd64   ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_merged_i386_Linux.upx [OK]
  30572692 ->   8350844   27.31%   linux/i386    ./tailscale/tailscale_merged_i386_Linux.upx
testing ./tailscale/tailscale_amd_geode_Linux.upx [OK]
  17776132 ->   5154012   28.99%   linux/i386    ./tailscale/tailscale_amd_geode_Linux.upx
testing ./tailscale/tailscale_mipsle_Linux.upx [OK]
  27815980 ->  10557048   37.95%  linux/mipsel   ./tailscale/tailscale_mipsle_Linux.upx
testing ./tailscale/tailscale_amd_x86_64_Linux.upx [OK]
  18773128 ->   5477928   29.18%   linux/amd64   ./tailscale/tailscale_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx [OK]
  30539924 ->   7358752   24.10%   linux/arm64   ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx [OK]
  18546836 ->   4643328   25.04%  linux/ppc64le  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscaled_aarch64_arm64_Linux.upx [OK]
  36995387 ->  15156576   40.97%   linux/arm64   ./tailscale/tailscaled_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_aarch64_arm64_Linux.upx [OK]
  25276200 ->  10573212   41.83%   linux/arm64   ./tailscale/tailscale_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx [OK]
  32112788 ->   7300616   22.73%   linux/ppc64   ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_arm_abi_Linux.upx [OK]
  25326901 ->  10540160   41.62%    linux/arm    ./tailscale/tailscale_arm_abi_Linux.upx
testing ./tailscale/tailscale_i386_Linux.upx [OK]
  17726980 ->   4749248   26.79%   linux/i386    ./tailscale/tailscale_i386_Linux.upx
testing ./tailscale/tailscale_powerpc64_ppc64_Linux.upx [OK]
  18546836 ->   4456692   24.03%   linux/ppc64   ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_mips_Linux.upx [OK]
  27939584 ->  10589060   37.90%   linux/mips    ./tailscale/tailscale_mips_Linux.upx
testing ./tailscale/tailscaled_mipsle_Linux.upx [OK]
  37826635 ->  14212788   37.57%  linux/mipsel   ./tailscale/tailscaled_mipsle_Linux.upx
testing ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx [OK]
  25100436 ->   6208648   24.74%  linux/ppc64le  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx [OK]
  32112788 ->   7558816   23.54%  linux/ppc64le  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscaled_amd_x86_64_Linux.upx [OK]
  27483432 ->   7742796   28.17%   linux/amd64   ./tailscale/tailscaled_amd_x86_64_Linux.upx
testing ./tailscale/tailscaled_amd_geode_Linux.upx [OK]
  24056612 ->   6872328   28.57%   linux/i386    ./tailscale/tailscaled_amd_geode_Linux.upx

```

---

- #### Version
```console
$ ./tailscale/tailscale_amd_x86_64_Linux --version
1.88.3
  tailscale commit: f453b350e4ac2b690498137e3a07894437831730
  long version: 1.88.3-tf453b350e-g6ebb4c936
  other commit: 6ebb4c936d785481a61603ecd7d361020b44ecff
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
1.88.3
  tailscale commit: f453b350e4ac2b690498137e3a07894437831730
  long version: 1.88.3-tf453b350e-g6ebb4c936
  other commit: 6ebb4c936d785481a61603ecd7d361020b44ecff
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


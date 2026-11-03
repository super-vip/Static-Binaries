
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
./tailscale/tailscale_aarch64_arm64_Linux:                   ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=lqh2hfG4WNbjJyo1pqGr/xw13fiifVJUh-6dSPcbV/ZnR2_4lwgZzD5w6inpfQ/H01qOdH1WrrGQVvJVFDW, BuildID[sha1]=ea24b2f21f1285799d6621bb42e8f2823d53d163, with debug_info, not stripped
./tailscale/tailscale_aarch64_arm64_Linux.upx:               ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=lqh2hfG4WNbjJyo1pqGr/xw13fiifVJUh-6dSPcbV/ZnR2_4lwgZzD5w6inpfQ/H01qOdH1WrrGQVvJVFDW, statically linked, no section header
./tailscale/tailscale_aarch64_arm64_Windows.msi:             Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Arm64;1033, Revision Number: {641B091A-A8F7-48E5-9E3B-D9DCE9020280}, Create Time/Date: Mon Nov  2 23:58:55 2026, Last Saved Time/Date: Mon Nov  2 23:58:55 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (6.0.2.0), Security: 2
./tailscale/tailscale_aarch64_arm64_macOS:                   Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_amd_geode_Linux:                       ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=m6m6UsVm4gFmMGn8q4xg/_iSBg0IPt7ofL2Qr8OYA/Gly-kTj0PUuE3zvQTZpd/X8LaHb_i_5konpJNjVsP, BuildID[sha1]=40fcd536a41e25cb90d9717abc7cbad12ca60e2d, stripped
./tailscale/tailscale_amd_geode_Linux.upx:                   ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=m6m6UsVm4gFmMGn8q4xg/_iSBg0IPt7ofL2Qr8OYA/Gly-kTj0PUuE3zvQTZpd/X8LaHb_i_5konpJNjVsP, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Linux:                      ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=IA_8mM_x6RMOmR9gKR7O/Ik2D5fzD0DA6eJUaf2ZS/Pg8kSG954vSIQYPem3Gt/oeQAmG2pM5YvjTHLuroT, BuildID[sha1]=8cfd183fafd30d8de84d4c4fda6cdb78ac8a764d, stripped
./tailscale/tailscale_amd_x86_64_Linux.upx:                  ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=IA_8mM_x6RMOmR9gKR7O/Ik2D5fzD0DA6eJUaf2ZS/Pg8kSG954vSIQYPem3Gt/oeQAmG2pM5YvjTHLuroT, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Windows.msi:                Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: x64;1033, Revision Number: {8C996FD2-B289-4CCF-A000-E96F02A4389D}, Create Time/Date: Mon Nov  2 23:57:28 2026, Last Saved Time/Date: Mon Nov  2 23:57:28 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (6.0.2.0), Security: 2
./tailscale/tailscale_amd_x86_64_macOS:                      Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_arm_abi_Linux:                         ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=3Dyyy_wBglu1rqbTVipp/9VObdnmfEwaDVow_yWZO/FcpOFTtCtOuaAXnRunm1/B9oeUybD2jun3Ic48YHk, BuildID[sha1]=19b6e2e66412d8e2e4f30fccf23eedba88815a9e, with debug_info, not stripped
./tailscale/tailscale_arm_abi_Linux.upx:                     ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=3Dyyy_wBglu1rqbTVipp/9VObdnmfEwaDVow_yWZO/FcpOFTtCtOuaAXnRunm1/B9oeUybD2jun3Ic48YHk, statically linked, no section header
./tailscale/tailscale_i386_Linux:                            ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=YUP1KfsK2ozZ2DZWJQQ6/Mpyu1ilMq4pq8IVTBbaL/rVwGYLdJKHWt4c8SSG1_/aE-mgWIMHkQlBHiOGCo7, BuildID[sha1]=5deb45b3a2a0f4a506f8c0da2fbaec0263ffd753, stripped
./tailscale/tailscale_i386_Linux.upx:                        ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=YUP1KfsK2ozZ2DZWJQQ6/Mpyu1ilMq4pq8IVTBbaL/rVwGYLdJKHWt4c8SSG1_/aE-mgWIMHkQlBHiOGCo7, statically linked, no section header
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
./tailscale/tailscale_mips64_Linux:                          ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=J3i-7W8zV1dBUq-t-MZB/FQPamajuIgQCiJm7_PXj/lQtxlrciPUDt77hIlX5d/tLp6bEqT8ljEOYg_2rh0, BuildID[sha1]=00afbe0937741588a5560166095c21f48c839d22, with debug_info, not stripped
./tailscale/tailscale_mips64le_Linux:                        ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=HIaOI_1ym37cgLxdiW2H/2pXXVgqtVRVCDlDictxl/MpcVaXYDxwwcf3vCxJSA/cCOSsE2wZ--LHNF7R-hC, BuildID[sha1]=5b3251b07e1c2fc79a4779d9e348e844bda67413, with debug_info, not stripped
./tailscale/tailscale_mips_Linux:                            ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=X34IYWK77c_P-nu1kdmv/PBNaeQbLFudU-ZMtMZfz/yV19T3plNNKjb-6YPXYb/SYV2aVcMQDRA9XPRiaHl, BuildID[sha1]=988dd5797b09a73a78bde0d6c5120b5735669873, with debug_info, not stripped
./tailscale/tailscale_mips_Linux.upx:                        ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=X34IYWK77c_P-nu1kdmv/PBNaeQbLFudU-ZMtMZfz/yV19T3plNNKjb-6YPXYb/SYV2aVcMQDRA9XPRiaHl, statically linked, no section header
./tailscale/tailscale_mipsle_Linux:                          ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=WGdqe452cnvfWbiGKpjf/l1853FiZOyQu9zg3HqwG/OBzxgAlDQkxeNHbaPW26/2AwJm4e82XcGqwElFnqG, BuildID[sha1]=e0b020467ce9c34f376ad753b7e9ebf7feaaed30, with debug_info, not stripped
./tailscale/tailscale_mipsle_Linux.upx:                      ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=WGdqe452cnvfWbiGKpjf/l1853FiZOyQu9zg3HqwG/OBzxgAlDQkxeNHbaPW26/2AwJm4e82XcGqwElFnqG, statically linked, no section header
./tailscale/tailscale_powerpc64_ppc64_Linux:                 ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64_ppc64_Linux.upx:             ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_powerpc64le_ppc64le_Linux:             ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx:         ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_riscv64_Linux:                         ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, Go BuildID=11vbLQgEtM5OQmiLCVRT/WjhiLdi424n9jr8huDYh/WxHUs6f7q9UFU8BSjuJ2/YzxFfJqW4R15hmRXiPIM, BuildID[sha1]=41fe3254ed9d1959005bc203abd89ad7397aef3d, with debug_info, not stripped
./tailscale/tailscale_s390x_Linux:                           ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_setup_Windows.exe:                     PE32 executable (GUI) Intel 80386, for MS Windows, 6 sections
./tailscale/tailscale_x86_Windows.msi:                       Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Intel;1033, Revision Number: {0260EECA-2E75-40D6-9217-0FD8B6289D44}, Create Time/Date: Mon Nov  2 23:58:31 2026, Last Saved Time/Date: Mon Nov  2 23:58:31 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (6.0.2.0), Security: 2
./tailscale/tailscaled_aarch64_arm64_Linux:                  ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=olybXObmP0Dmx3e7OyLQ/0PYaX8W6Evwlp0fzI76z/ja-SihMlZUNf6MUW7NHU/N-CZH7y_QjvKx6IEAER-, BuildID[sha1]=b66ebb9ed6ebba74c58ea18ebdda78d247308517, with debug_info, not stripped
./tailscale/tailscaled_aarch64_arm64_Linux.upx:              ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=olybXObmP0Dmx3e7OyLQ/0PYaX8W6Evwlp0fzI76z/ja-SihMlZUNf6MUW7NHU/N-CZH7y_QjvKx6IEAER-, statically linked, no section header
./tailscale/tailscaled_aarch64_arm64_macOS:                  Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_amd_geode_Linux:                      ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=pAgR88vcvJoZMGG1Ftxj/nAvh7kOjbusbTbslXub_/MOQVJfzEFehDebZaQr8V/qzffeWLEAfsbvmGZfov1, BuildID[sha1]=eba70acc61123aa8e177cf6759832a963e9d82d3, stripped
./tailscale/tailscaled_amd_geode_Linux.upx:                  ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=pAgR88vcvJoZMGG1Ftxj/nAvh7kOjbusbTbslXub_/MOQVJfzEFehDebZaQr8V/qzffeWLEAfsbvmGZfov1, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_Linux:                     ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=qPTaY29WRgIfj6JIgM0F/Ime9JKG1V7owSwLsnup5/3r_URuiZhifofACyvNlT/G54F1ys17N-HZ6zF32hn, BuildID[sha1]=f4b9756e8269f4cda2915f0d7009e0111c4a6228, stripped
./tailscale/tailscaled_amd_x86_64_Linux.upx:                 ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=qPTaY29WRgIfj6JIgM0F/Ime9JKG1V7owSwLsnup5/3r_URuiZhifofACyvNlT/G54F1ys17N-HZ6zF32hn, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_macOS:                     Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_arm_abi_Linux:                        ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=s6dxgK-NcPP03W3kpgKo/2A9eOQ5HF_P-h9Z40a4s/xp0npcxaW1AM9IqLHr1w/0y85IaU_1xaaq_hff9ep, BuildID[sha1]=6b774a76078d5c4d990983c07bb73a367cf71239, with debug_info, not stripped
./tailscale/tailscaled_arm_abi_Linux.upx:                    ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=s6dxgK-NcPP03W3kpgKo/2A9eOQ5HF_P-h9Z40a4s/xp0npcxaW1AM9IqLHr1w/0y85IaU_1xaaq_hff9ep, statically linked, no section header
./tailscale/tailscaled_i386_Linux:                           ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=SIGz9hHcH9j8miV6yG00/0V_NZF2rmSU5MY9iDtik/ibtvjvTEHePwSuIozALn/Z8-ekBPujAu4jIm46lu8, BuildID[sha1]=1798b6df987965d1d2171b2eab4b6559f2d34115, stripped
./tailscale/tailscaled_i386_Linux.upx:                       ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=SIGz9hHcH9j8miV6yG00/0V_NZF2rmSU5MY9iDtik/ibtvjvTEHePwSuIozALn/Z8-ekBPujAu4jIm46lu8, statically linked, no section header
./tailscale/tailscaled_mips64_Linux:                         ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=I2F6MIqhH9cdef6Jdnyo/8UpPr_LOL3byk6UhpkRz/cFhYJEiRqS2AdujPPv5J/xKysUa-rx74frfU4pPwi, BuildID[sha1]=fc30c73bd070323248dcb776286d36b2f8eaa5db, with debug_info, not stripped
./tailscale/tailscaled_mips64le_Linux:                       ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=rU9h5MFSAtD6Q55MvBsx/lAxulzIDOZ6B9VW-Kb8O/8cNb7Jj_q_BE0oztWsoU/Q8DMgwNrSpUCbdMeRGs9, BuildID[sha1]=a2140b79f3afcd86584f72f28d9f1e5ff3c915de, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux:                           ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=4nNSg-nf-vIUdHCfCJMD/XcUXsarZPEnfWCg6hZdf/R0vMZJ8o9FmwDGibcVCu/euvCndL0WZSL8-C4TQtk, BuildID[sha1]=beec76ad6190b19838e0cc2a0d6b40ba5d078486, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux.upx:                       ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=4nNSg-nf-vIUdHCfCJMD/XcUXsarZPEnfWCg6hZdf/R0vMZJ8o9FmwDGibcVCu/euvCndL0WZSL8-C4TQtk, statically linked, no section header
./tailscale/tailscaled_mipsle_Linux:                         ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=OlQ0bokyq7FRQbwe5Cas/LvT8p4LFWVSZqflL0n_x/57T2p6VKfb-80EwK46E5/voP-qxkeJgsgMXEcJ52Y, BuildID[sha1]=cc473646a659e4d14c3b875b2410c5e94ca3439a, with debug_info, not stripped
./tailscale/tailscaled_mipsle_Linux.upx:                     ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=OlQ0bokyq7FRQbwe5Cas/LvT8p4LFWVSZqflL0n_x/57T2p6VKfb-80EwK46E5/voP-qxkeJgsgMXEcJ52Y, statically linked, no section header
./tailscale/tailscaled_powerpc64_ppc64_Linux:                ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64_ppc64_Linux.upx:            ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_powerpc64le_ppc64le_Linux:            ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx:        ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_riscv64_Linux:                        ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, Go BuildID=n3P8nbq7XuOk1IakLR8Y/fIJebqMBxKgwNP1CqaHJ/aLpG8kN153ZVUzzDgy3K/p9vcrAEtSzSqgbnX-GgE, BuildID[sha1]=1dd94bfc11f3594e37a6b0e8a64e5ca97e5db60a, with debug_info, not stripped
./tailscale/tailscaled_s390x_Linux:                          ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped

--> SHA256SUM
a000d3ee4734531da8e0b2874453e01c6f841e6fea9edae8621f4b2e4e45ab48  ./tailscale/tailscale_aarch64_arm64_Linux
f4287b26ac2af27f00f38c5c7ae67d9eef6a695e2aab103ba0919a0f102ca860  ./tailscale/tailscale_aarch64_arm64_Linux.upx
609982de4dfe70b67a02e2a93c9c5c1dfa20addceb33a7d3b144f1d34d98f5fc  ./tailscale/tailscale_aarch64_arm64_Windows.msi
758bd296723a348a70f5274b294baeb4053abd2e2ce58e2220e210946b618c6f  ./tailscale/tailscale_aarch64_arm64_macOS
df46db83c0fd8219e2f4efb8de474f545acae722f39113a0718b2d19eed33b29  ./tailscale/tailscale_amd_geode_Linux
062e4edae930148f591e1ac9c197aca4b16fe9caf160c8689201636306e5a0c0  ./tailscale/tailscale_amd_geode_Linux.upx
77a995ceb3c0ac24dab06dce7e749347b0df7bae46b02f0d603249b08d15f95f  ./tailscale/tailscale_amd_x86_64_Linux
633ff0301515c92a1426bb9da266deea491e0c540357ac604be058e2f0c7d056  ./tailscale/tailscale_amd_x86_64_Linux.upx
3c41318c83c5d95d0b017b1baa08ba7c99fd5334166122bbb1931e55af99839c  ./tailscale/tailscale_amd_x86_64_Windows.msi
248b7930c0c4c650f988bcb90a968da042066e0b826bf58efd8fe3a69fad8e7f  ./tailscale/tailscale_amd_x86_64_macOS
f406b27e222a802cc8d89a8004cc567ad055e4cc18664c18f4136876b544861d  ./tailscale/tailscale_arm_abi_Linux
ef833629ae84877b691e2f8b6e67c601916510e9efafd67ffa051312ec83d56f  ./tailscale/tailscale_arm_abi_Linux.upx
2b9d3ae42f6528edf735d3ca286e4cc76ed0c368a24d3dfde7ec2baca59e0f56  ./tailscale/tailscale_i386_Linux
434c207b6cbcf701814c90b490648ccfe6a7ff844bec06920e720b455319198a  ./tailscale/tailscale_i386_Linux.upx
e41b8c492199f8af4efda04ee6a74cb02815d9afe579f97172621aa3f0cf62f3  ./tailscale/tailscale_ipn_setup_Windows.exe
492a2562da71e59037966888f8490c3604f5061811c61ce244d60cdf8265012b  ./tailscale/tailscale_merged_aarch64_arm64_Linux
56a1be40f661530fe589a508d39b54f077ea32d1c72271e3623858bcf94cd4cc  ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
68728bde1313493eb44dbd3be2e989eb00f60f4938d0d2845df9d45e32c25df7  ./tailscale/tailscale_merged_aarch64_arm64_macOS
b98593469f1b3a620a04addf7ee428985c5917cd9b6d182764d1c1b91e876601  ./tailscale/tailscale_merged_amd_x86_64_Linux
9252c28584ef8ede7090d98b3043c0f7c20a3265534bf087f94241b004a61347  ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
267bebcfe539dd8353add30caf55a042bf996f8e688aae7910b9ecf61714f3f8  ./tailscale/tailscale_merged_amd_x86_64_macOS
d926a92822a16398ff823289002d68c6440d319d56bfeee0c491c407732262aa  ./tailscale/tailscale_merged_arm_Linux
8b2b970c7197464f375eef8103a18df4741c6907dce3b2d0aafb9887d41e8389  ./tailscale/tailscale_merged_arm_Linux.upx
c8b170fea27af5ce43a7cf68d726617652b9d87538ba664c51ded39c7aca59aa  ./tailscale/tailscale_merged_i386_Linux
588929c4bdf4a1ea887a9bc83c7079877a70891e310eaa32292eb2f69942f1da  ./tailscale/tailscale_merged_i386_Linux.upx
f830caf901ba3d76101cc3a83579f9f6a0bf2a9e5eb4f8a2a109bb55a89fe974  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux
ee8433247742825efb8a9999352d6457857b966ec3fc7ed87a812d41909441ea  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
1e4efcceb2953327beb68e092f00beb3307ad0e28278020f4e2f39caaca158e2  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux
acca3bb02897415ac47165d7699601073550a877e9087d54b773271d28d67b43  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
9330c6496775773c367a5553bc24aff8cf28287721b72351aa86fa6c36c5972d  ./tailscale/tailscale_merged_s390x_Linux
4341e060fb8641d69e56ad8b1edf7cd19e1d86b5ff6b483932e7a00de97082b0  ./tailscale/tailscale_mips64_Linux
bce472b695e146f382f3576f7d54fa1bc2d74f1a59c9a491fb4d7e06494d648d  ./tailscale/tailscale_mips64le_Linux
7ca4e0d7a2fb5f8cd711b0b7451f03ccde97538480e4e68fa5ef8104ef7812f1  ./tailscale/tailscale_mips_Linux
4e6b34c03233d19d10745550c8816419743902154800a71b733a879ea157d4ae  ./tailscale/tailscale_mips_Linux.upx
c48aad84fc1f15a030659af803dfe01e73c8424ab0889823d7eec290e04823e9  ./tailscale/tailscale_mipsle_Linux
364e02ddd9e70b0c65bbae2a98ff228f5543cffd9188ab3cf36b111ca7e7d736  ./tailscale/tailscale_mipsle_Linux.upx
677c8a22c319224fb94c3c0730f7775b5cd96491e00bcd4056ec2fdf94ef87ae  ./tailscale/tailscale_powerpc64_ppc64_Linux
5daefad6ae2922a20aba8e7d35569e90557c909be67360df454af7fdbce4713a  ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
13df247a3b1ef2a7a464fecc3f2d4afd5083a4d2bd7e2a72c4e4e1f1d43b016a  ./tailscale/tailscale_powerpc64le_ppc64le_Linux
49adea253ae1cc5bf5d7485470cc866dc36d031a2b05274f1011cb9f9daecd12  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
a5d35529cdc9fd309e7e927a0f2950340a75f23dfa51cb3b9d02f4c3e19b520c  ./tailscale/tailscale_riscv64_Linux
fb952b787478347b6f47b2c187081bc25cdd7a44858c0237eb012021b5cdc394  ./tailscale/tailscale_s390x_Linux
64a8ad28cbb67a6171236abe39f75a039a761a0e1aacdef75b26781887cef9a8  ./tailscale/tailscale_setup_Windows.exe
078edb90cdab6a4fc67f79721cb2d2b48828b108cf5d656a3d9fd94b859a54d2  ./tailscale/tailscale_x86_Windows.msi
d1532cdbbe9c9a86275939b9130e837da8bb7223d2647996b7b1fabf48bc8359  ./tailscale/tailscaled_aarch64_arm64_Linux
06c3c45bb8ad50ade65b468d0528d3011217c2bfa85c52662bc89c169ac75878  ./tailscale/tailscaled_aarch64_arm64_Linux.upx
3045786fe6191b3d64ae9d2b03b5fffcf080e3cb3073a3c2e8e69e57ea05e2cf  ./tailscale/tailscaled_aarch64_arm64_macOS
c4bcdea0982009833978a312096023a8b50994fdb158e899ec295880473df53a  ./tailscale/tailscaled_amd_geode_Linux
424c1814c5096e85dccae59ebbff00a91aad63a524cbdf94099ba628763546f3  ./tailscale/tailscaled_amd_geode_Linux.upx
0bd67f24bad165f9f002f62b305aa186260121232247e43f53fe590e39091f02  ./tailscale/tailscaled_amd_x86_64_Linux
940199f6639b3145c62880eef87055fced921bc36d6b3f08a00aaa4703b6cf13  ./tailscale/tailscaled_amd_x86_64_Linux.upx
b5304b43985998d94d5c2c94e0eeb9e160a76906fa0ecb224af45c3b878e684d  ./tailscale/tailscaled_amd_x86_64_macOS
197a2c3f2ae97b33a73c27a6497d0259869a14d02c9c9193155c3cfdde9026a3  ./tailscale/tailscaled_arm_abi_Linux
00144756841206aab0356e5a5a60f48476bf9d11ab06bdf811979029f5060341  ./tailscale/tailscaled_arm_abi_Linux.upx
41335c834507d95ee71b2050b533b2cca90cf2a6874bd672820a799e7d9a67c3  ./tailscale/tailscaled_i386_Linux
5a890ca3bfce114c5e496f1ad7d27305af4c7c026cfb63b14013ed8b8412ddbb  ./tailscale/tailscaled_i386_Linux.upx
1f3adc9906155cc5b3208bea4e30082ac30cdb497fca3eda3fc6913383c980bd  ./tailscale/tailscaled_mips64_Linux
dacf8e3d22e12fa4f6d6324eabca65ff2441affecef45b9ebbb9d7faa02aec7c  ./tailscale/tailscaled_mips64le_Linux
4616b161500d65b435b8bc42676e093f22b5dc5073c4d9d720f4373347a9127e  ./tailscale/tailscaled_mips_Linux
dd508c0377224562cd93ce5f58d8ed403561b02e0d62bf0b5eaf35e52a1a8a69  ./tailscale/tailscaled_mips_Linux.upx
76930d33a36604901a57bee6a50c5b32f80382812278cda30927bfa51ff83fa5  ./tailscale/tailscaled_mipsle_Linux
da805ce01fdab08ab0f45595dc9832819eed54a028022a69dcfb8e704368d902  ./tailscale/tailscaled_mipsle_Linux.upx
1ef2a4a2b75dffcc55e1cf4568d7fc212b5f1d11a81cd4bfd88745ee4a4227f3  ./tailscale/tailscaled_powerpc64_ppc64_Linux
61e237ae0a09a6f679559a917f9dc3dd1bcf40f8732539d57f4bf0df55bcd244  ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
39f05bfbac0c0b96f57d1469258aaea5fbdece7aeea445e2708aa3948fabcbcb  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux
7cd6fa9f1fe9438772af46732016d1d287aebac648e22071c252ba79877d2a01  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
dbf9bd22149f3654f28623f24f2117da0056f6589a13cf9252b75409881cc68b  ./tailscale/tailscaled_riscv64_Linux
c6da8df4e2e68c40f77ee3e98179f99a6b2dc071d0428a14d7db800c03153acb  ./tailscale/tailscaled_s390x_Linux
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
38M   ./tailscale/tailscale_amd_x86_64_Windows.msi
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
  27263100 ->   6799624   24.94%  linux/ppc64le  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscaled_arm_abi_Linux.upx [OK]
  37984380 ->  15953548   42.00%    linux/arm    ./tailscale/tailscaled_arm_abi_Linux.upx
testing ./tailscale/tailscale_mips_Linux.upx [OK]
  34927322 ->  13140904   37.62%   linux/mips    ./tailscale/tailscale_mips_Linux.upx
testing ./tailscale/tailscale_merged_amd_x86_64_Linux.upx [OK]
  39182460 ->  10506208   26.81%   linux/amd64   ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx [OK]
  36307068 ->   8605708   23.70%   linux/arm64   ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
testing ./tailscale/tailscaled_amd_x86_64_Linux.upx [OK]
  30217592 ->   8545076   28.28%   linux/amd64   ./tailscale/tailscaled_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_mipsle_Linux.upx [OK]
  34918902 ->  13264984   37.99%  linux/mipsel   ./tailscale/tailscale_mipsle_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx [OK]
  38273148 ->   8852000   23.13%  linux/ppc64le  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_merged_i386_Linux.upx [OK]
  36753532 ->   9827024   26.74%   linux/i386    ./tailscale/tailscale_merged_i386_Linux.upx
testing ./tailscale/tailscaled_amd_geode_Linux.upx [OK]
  26224268 ->   7584168   28.92%   linux/i386    ./tailscale/tailscaled_amd_geode_Linux.upx
testing ./tailscale/tailscale_amd_geode_Linux.upx [OK]
  22340780 ->   6303812   28.22%   linux/i386    ./tailscale/tailscale_amd_geode_Linux.upx
testing ./tailscale/tailscale_merged_arm_Linux.upx [OK]
  36831356 ->   8436768   22.91%    linux/arm    ./tailscale/tailscale_merged_arm_Linux.upx
testing ./tailscale/tailscaled_mips_Linux.upx [OK]
  41626914 ->  15945608   38.31%   linux/mips    ./tailscale/tailscaled_mips_Linux.upx
testing ./tailscale/tailscale_powerpc64_ppc64_Linux.upx [OK]
  23068796 ->   5410856   23.46%   linux/ppc64   ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscaled_mipsle_Linux.upx [OK]
  41557186 ->  16093604   38.73%  linux/mipsel   ./tailscale/tailscaled_mipsle_Linux.upx
testing ./tailscale/tailscaled_i386_Linux.upx [OK]
  26187404 ->   7577788   28.94%   linux/i386    ./tailscale/tailscaled_i386_Linux.upx
testing ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx [OK]
  27263100 ->   6564056   24.08%   linux/ppc64   ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx [OK]
  38273148 ->   8544968   22.33%   linux/ppc64   ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_aarch64_arm64_Linux.upx [OK]
  31910639 ->  13434836   42.10%   linux/arm64   ./tailscale/tailscale_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_arm_abi_Linux.upx [OK]
  32009887 ->  13204828   41.25%    linux/arm    ./tailscale/tailscale_arm_abi_Linux.upx
testing ./tailscale/tailscale_i386_Linux.upx [OK]
  22283436 ->   6292964   28.24%   linux/i386    ./tailscale/tailscale_i386_Linux.upx
testing ./tailscale/tailscale_amd_x86_64_Linux.upx [OK]
  23739672 ->   6697988   28.21%   linux/amd64   ./tailscale/tailscale_amd_x86_64_Linux.upx
testing ./tailscale/tailscaled_aarch64_arm64_Linux.upx [OK]
  40980262 ->  17372240   42.39%   linux/arm64   ./tailscale/tailscaled_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx [OK]
  23068796 ->   5617112   24.35%  linux/ppc64le  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx

```

---

- #### Version
```console
$ ./tailscale/tailscale_amd_x86_64_Linux --version
1.104.5
  tailscale commit: 78838476328d1a97dc05400ad23086a9dbe616da
  long version: 1.104.5-t788384763-gd9218e278
  other commit: d9218e278237adcb8bfc039e82a4ad1912554b4f
  go version: go1.27.3 (tailscale/go 7ef7b40364)

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
1.104.5
  tailscale commit: 78838476328d1a97dc05400ad23086a9dbe616da
  long version: 1.104.5-t788384763-gd9218e278
  other commit: d9218e278237adcb8bfc039e82a4ad1912554b4f
  go version: go1.27.3 (tailscale/go 7ef7b40364)

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


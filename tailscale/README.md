
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
./tailscale/tailscale_aarch64_arm64_Linux:                   ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=LEZKa-AQraSfwY_UVqZO/xhE8jZbU2XsqEERdZMgM/5UIA8dZfED44oT3nVE8z/CsuBxdrNPHwpmsK4rLp5, BuildID[sha1]=dde4a212ae657d06d1b14f6d76f7af91719e4edd, with debug_info, not stripped
./tailscale/tailscale_aarch64_arm64_Linux.upx:               ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=LEZKa-AQraSfwY_UVqZO/xhE8jZbU2XsqEERdZMgM/5UIA8dZfED44oT3nVE8z/CsuBxdrNPHwpmsK4rLp5, statically linked, no section header
./tailscale/tailscale_aarch64_arm64_Windows.msi:             Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Arm64;1033, Revision Number: {79FA0BB0-2EF6-4D1F-AF75-50C9BBB8FA86}, Create Time/Date: Tue Jun 30 17:43:52 2026, Last Saved Time/Date: Tue Jun 30 17:43:52 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscale_aarch64_arm64_macOS:                   Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_amd_geode_Linux:                       ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=8CKte8fBAE0cgeU9L4y5/Li0x09yEsdShHJmz6ZvX/RhJ7Z-rz7qwPtjy5c21n/twOviS90Qwwp7_TX9IMs, BuildID[sha1]=4d2d59c65435bd4f57938ef30d7aeb815c33b86f, stripped
./tailscale/tailscale_amd_geode_Linux.upx:                   ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=8CKte8fBAE0cgeU9L4y5/Li0x09yEsdShHJmz6ZvX/RhJ7Z-rz7qwPtjy5c21n/twOviS90Qwwp7_TX9IMs, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Linux:                      ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=h7-8gZJq1AyH17gO-A4d/xnZ1wD7ZN6zQhtGy1ftZ/vGPY7beJ0d5G12M4qp9O/xRSYOCfqrt3R5MqWOM9A, BuildID[sha1]=4ff3dffd8a90b9a6f2183fb9a8b8083c6031bfdd, stripped
./tailscale/tailscale_amd_x86_64_Linux.upx:                  ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=h7-8gZJq1AyH17gO-A4d/xnZ1wD7ZN6zQhtGy1ftZ/vGPY7beJ0d5G12M4qp9O/xRSYOCfqrt3R5MqWOM9A, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Windows.msi:                Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: x64;1033, Revision Number: {1208F1A6-6962-45F9-B439-EE9DD702EB78}, Create Time/Date: Tue Jun 30 17:45:33 2026, Last Saved Time/Date: Tue Jun 30 17:45:33 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscale_amd_x86_64_macOS:                      Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_arm_abi_Linux:                         ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=VMiUDX8YVbwhsYjTG9s7/1Z0zeITibCGLRhh0xA9X/ecWHj-rwlVqN2hPDYVDr/axEsFYD7VuORcT7oEyhs, BuildID[sha1]=56ef1a21074d3ee2f7b5384ef12434acdaf1c392, with debug_info, not stripped
./tailscale/tailscale_arm_abi_Linux.upx:                     ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=VMiUDX8YVbwhsYjTG9s7/1Z0zeITibCGLRhh0xA9X/ecWHj-rwlVqN2hPDYVDr/axEsFYD7VuORcT7oEyhs, statically linked, no section header
./tailscale/tailscale_i386_Linux:                            ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=zXJ907zOhUhX9ks57a-t/wh63WlWjhEg0ir-c_Idi/tuar9ed74kdjQHJ9ZzGl/duz2Do7kSJEKoEpijh5i, BuildID[sha1]=0180bbfd1d4fd4fa61742eceb0ee1455d0e1fd3c, stripped
./tailscale/tailscale_i386_Linux.upx:                        ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=zXJ907zOhUhX9ks57a-t/wh63WlWjhEg0ir-c_Idi/tuar9ed74kdjQHJ9ZzGl/duz2Do7kSJEKoEpijh5i, statically linked, no section header
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
./tailscale/tailscale_mips64_Linux:                          ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=H8lfw9_ADnTK5N2NoSee/akgwBr01Xz1KdjvTUr5i/d_0WuFl7g19nwHULLqeh/kPeemPvBps_zEWWncqQk, BuildID[sha1]=ccd548233a9c3a55c615e9878643f2d9ce078012, with debug_info, not stripped
./tailscale/tailscale_mips64le_Linux:                        ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=VrvQPZMYAmuo4txea7Vd/LhchgFf3Aubnkm02Piot/SdSi7NaF2855GBAcP1CK/3LESiffbvwDdYz7h-o8s, BuildID[sha1]=7b137718c111ed1f60cba4b12a0442c789c5f6d9, with debug_info, not stripped
./tailscale/tailscale_mips_Linux:                            ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=ZM78AB_sBOr0WPbzzG8n/cSAMYmsdDs0zQcYac_ax/qKqBJn98eq5lTvCb5vPP/kpxlyAxZYS4OI4TzCq17, BuildID[sha1]=f647e1140c78e792f2dff6e28e56c9c07827eecc, with debug_info, not stripped
./tailscale/tailscale_mips_Linux.upx:                        ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=ZM78AB_sBOr0WPbzzG8n/cSAMYmsdDs0zQcYac_ax/qKqBJn98eq5lTvCb5vPP/kpxlyAxZYS4OI4TzCq17, statically linked, no section header
./tailscale/tailscale_mipsle_Linux:                          ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=vwzNA5r3RpAUNRDHMvH1/UhgfWF9jCwcTDZZAPqZj/1XMjVChT4b4i6mR2oyJt/gU1GWDPImn9lX9qN03EG, BuildID[sha1]=d26514e454f09f61c07dbeb86bedc0822bf3f8fc, with debug_info, not stripped
./tailscale/tailscale_mipsle_Linux.upx:                      ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=vwzNA5r3RpAUNRDHMvH1/UhgfWF9jCwcTDZZAPqZj/1XMjVChT4b4i6mR2oyJt/gU1GWDPImn9lX9qN03EG, statically linked, no section header
./tailscale/tailscale_powerpc64_ppc64_Linux:                 ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64_ppc64_Linux.upx:             ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_powerpc64le_ppc64le_Linux:             ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx:         ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_riscv64_Linux:                         ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, Go BuildID=scyDYKethfs28iF5vMFf/OwlJmkiIOzmYXaH0gQCT/CQPM5CRAIlqtC8U7N985/ZviF0B6GzePXB41R7hc8, BuildID[sha1]=2dec378e196cc49576df8d5724dfd94b08f791d7, with debug_info, not stripped
./tailscale/tailscale_s390x_Linux:                           ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_setup_Windows.exe:                     PE32 executable (GUI) Intel 80386, for MS Windows, 6 sections
./tailscale/tailscale_x86_Windows.msi:                       Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Intel;1033, Revision Number: {AD5AFF2D-FCF8-4189-978F-619601B4AD0C}, Create Time/Date: Tue Jun 30 17:43:52 2026, Last Saved Time/Date: Tue Jun 30 17:43:52 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscaled_aarch64_arm64_Linux:                  ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=jlCjX-e08YkmF3gkb4vV/tEQ5TSvNMo_v9W1hGrH0/ecS95L6Kt7_V-lLmgJro/luJ0Ng2QvZ0G4F4hx1nw, BuildID[sha1]=6da18a75d3d1348759d66d27189932fdeab08bb2, with debug_info, not stripped
./tailscale/tailscaled_aarch64_arm64_Linux.upx:              ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=jlCjX-e08YkmF3gkb4vV/tEQ5TSvNMo_v9W1hGrH0/ecS95L6Kt7_V-lLmgJro/luJ0Ng2QvZ0G4F4hx1nw, statically linked, no section header
./tailscale/tailscaled_aarch64_arm64_macOS:                  Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_amd_geode_Linux:                      ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=7D1vj4EtCkOLbWEZiKzM/SEwR2TtAO5o0JwajFFrp/br4zYAmpvb2fm1coENaH/fE6f7dME1UTBWdCCETxQ, BuildID[sha1]=8180f1edbdb7cc883bc0a06913953b50d3662f57, stripped
./tailscale/tailscaled_amd_geode_Linux.upx:                  ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=7D1vj4EtCkOLbWEZiKzM/SEwR2TtAO5o0JwajFFrp/br4zYAmpvb2fm1coENaH/fE6f7dME1UTBWdCCETxQ, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_Linux:                     ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=C5AZI_10Ftrjew2BB0qc/jY8nEBpyGDu-z_w5lKin/jZkPX8-3SKlwj4wKaC7l/vxpJtjSD_Si9Va6Eh4PT, BuildID[sha1]=f24fe839ef82c2f20ba36562522755790ae4a637, stripped
./tailscale/tailscaled_amd_x86_64_Linux.upx:                 ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=C5AZI_10Ftrjew2BB0qc/jY8nEBpyGDu-z_w5lKin/jZkPX8-3SKlwj4wKaC7l/vxpJtjSD_Si9Va6Eh4PT, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_macOS:                     Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_arm_abi_Linux:                        ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=KN7Bu85esadcp50Ncvv5/Eeo1dJLucuprdd9Ldian/03gu4pkRpoKJGTrq-Byo/8gGakoGczAYszaqqiT0v, BuildID[sha1]=de97b86efa2c89ae68130046442b6e92dee98683, with debug_info, not stripped
./tailscale/tailscaled_arm_abi_Linux.upx:                    ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=KN7Bu85esadcp50Ncvv5/Eeo1dJLucuprdd9Ldian/03gu4pkRpoKJGTrq-Byo/8gGakoGczAYszaqqiT0v, statically linked, no section header
./tailscale/tailscaled_i386_Linux:                           ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=5gDi0xQACP-ImyaLqiKm/1zGbUCtFukba29lN9TVD/LwcXWvNSviQY8GkcVmDg/-dCU56Ajwo9sEBQ0o1j4, BuildID[sha1]=702f1e79547df2948d274e84d08b2bff514f5815, stripped
./tailscale/tailscaled_i386_Linux.upx:                       ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=5gDi0xQACP-ImyaLqiKm/1zGbUCtFukba29lN9TVD/LwcXWvNSviQY8GkcVmDg/-dCU56Ajwo9sEBQ0o1j4, statically linked, no section header
./tailscale/tailscaled_mips64_Linux:                         ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=z9u--qvUtWRyzj017qYH/sw6TJiOQRZHR28wBhxMa/_K-kQYgYl52A3Bpb9PBE/05FvEzv4YRQR_hnOLFe-, BuildID[sha1]=01122516a229992126d3cfb26c5b30d63485ea9d, with debug_info, not stripped
./tailscale/tailscaled_mips64le_Linux:                       ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=bg5sXysW0PU7pWCBcCQc/2xlTropotKntONgdVSbS/2CsF3V8T7olS-pl0pDKU/S18laRD1Kz9-j2pWgKk8, BuildID[sha1]=a79564ec667f0bc6383cfb18652f39e4d968496f, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux:                           ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=CKZLeexDpj6cgBj2GfZt/mCvuryzYc-oHxBa_xJow/0nSq7IRKQwSEE47cMjtb/cGoY0f5q6LBmTmnTpSzE, BuildID[sha1]=7fc203edabe74266d3efec4d30cb0cd69ee36650, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux.upx:                       ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=CKZLeexDpj6cgBj2GfZt/mCvuryzYc-oHxBa_xJow/0nSq7IRKQwSEE47cMjtb/cGoY0f5q6LBmTmnTpSzE, statically linked, no section header
./tailscale/tailscaled_mipsle_Linux:                         ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=4x-hHvwQ5SmtAhmbvlyD/PTvz9S0qIBG63HnRryCa/WgMHqNdhLjGHig4M_tWW/MzqfBZX9qj69yCz9Hx1g, BuildID[sha1]=379ce7b0f0d61233e4e069b30127f6d9131c111e, with debug_info, not stripped
./tailscale/tailscaled_mipsle_Linux.upx:                     ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=4x-hHvwQ5SmtAhmbvlyD/PTvz9S0qIBG63HnRryCa/WgMHqNdhLjGHig4M_tWW/MzqfBZX9qj69yCz9Hx1g, statically linked, no section header
./tailscale/tailscaled_powerpc64_ppc64_Linux:                ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64_ppc64_Linux.upx:            ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_powerpc64le_ppc64le_Linux:            ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx:        ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_riscv64_Linux:                        ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, Go BuildID=HhJah9NX-NDi-hnVtZql/pClYGk6lYmUnWOzwBCQB/gM42wA2kfnCW7fw3eNEW/FAp70Cw9uJpdLEDdTBpK, BuildID[sha1]=75f8c07e2cf506b08fd3678ac186f8080e6828fb, with debug_info, not stripped
./tailscale/tailscaled_s390x_Linux:                          ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped

--> SHA256SUM
27264e9ab753480d7899796eaefef6eb15b2dfaa88b2f17fdcae71de0224323e  ./tailscale/tailscale_aarch64_arm64_Linux
4fd254dba2780ad2a5305edd500597b94601de77bda6f2df437c2bc72ea40a43  ./tailscale/tailscale_aarch64_arm64_Linux.upx
f81002c5b971fe2de197703606e81107eacc83c6ea40478976fe5de154aed177  ./tailscale/tailscale_aarch64_arm64_Windows.msi
758bd296723a348a70f5274b294baeb4053abd2e2ce58e2220e210946b618c6f  ./tailscale/tailscale_aarch64_arm64_macOS
404fb71e9a307b5e8b4b84e8cc9a684746fc0baddb8f8ab9de30fb378cc1ee63  ./tailscale/tailscale_amd_geode_Linux
d46f00a9c33685f783900ca9fcef913b298f071c1b13018df65fb1fd14648ca0  ./tailscale/tailscale_amd_geode_Linux.upx
87e912646c3adc566e4f34c2bf2915030bcc447f670e37de4cbfcde9ed6a22f4  ./tailscale/tailscale_amd_x86_64_Linux
de19d244c9cdead82b2a021dbbaaf3efc3925a0da5ff1dee357388c931cab536  ./tailscale/tailscale_amd_x86_64_Linux.upx
988a38ab854ad176778955b0c92b27b1af14bf5e0146ea43076d829496d7ac77  ./tailscale/tailscale_amd_x86_64_Windows.msi
248b7930c0c4c650f988bcb90a968da042066e0b826bf58efd8fe3a69fad8e7f  ./tailscale/tailscale_amd_x86_64_macOS
56b5aedbf4ab0d82b839127b0e199149f11cc6a770a5179b86dfd00e29d1f6d9  ./tailscale/tailscale_arm_abi_Linux
8e568db2b472d11a489e5e3a8579dec08edbae0a5591f5aa6ea00b0806d3feb2  ./tailscale/tailscale_arm_abi_Linux.upx
8904fdb7a2ab24a67538d6768b3b04d46b8ab91bbc60527da9aba246fe7943fd  ./tailscale/tailscale_i386_Linux
4b87e2adc485f8e74b2640403397c2b57fa46349654c05411b937b18f62be80c  ./tailscale/tailscale_i386_Linux.upx
3f50565ad6a21562bd21404925b75ae8f16ea788cb7f77382ae6411f3b80e8a7  ./tailscale/tailscale_ipn_setup_Windows.exe
00d4ce7527656bed91be3dca3c9ede1e19558124669effeef9f7ca776c9337d0  ./tailscale/tailscale_merged_aarch64_arm64_Linux
a7118c961fe483497b2d9c8d31498d23ece3b3cd3378cc545576ef4dcd2bc5c1  ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
68728bde1313493eb44dbd3be2e989eb00f60f4938d0d2845df9d45e32c25df7  ./tailscale/tailscale_merged_aarch64_arm64_macOS
a8cc26889ff4cc246c4452b2d165beed7d6c45a1d14eedbaaeb593c923c9c1ad  ./tailscale/tailscale_merged_amd_x86_64_Linux
d82d50300c6dd747c69227800f54c6b31a3bf73b017b9a5c90ca4057b0389010  ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
267bebcfe539dd8353add30caf55a042bf996f8e688aae7910b9ecf61714f3f8  ./tailscale/tailscale_merged_amd_x86_64_macOS
a7a8c95b4fba1fe68a90957618962b2a5d8eafbf076ee03b703973cd5e399c91  ./tailscale/tailscale_merged_arm_Linux
fd193b9bc716741c8da63ecbcaa90d99412de7566e95c4a7b00a5236d4e4f789  ./tailscale/tailscale_merged_arm_Linux.upx
60cf1f8dd698fa5eec11f595517eedb7e77a87e2921cec456341f11e3257b405  ./tailscale/tailscale_merged_i386_Linux
b2a5cd003585f0fa8430d006d8eecb31e930bfd63346a497a461ec15b7428d7a  ./tailscale/tailscale_merged_i386_Linux.upx
e2ea77e52d7a6bc9725eb66c280a646294354cf12221cbef7c76a52edbe970eb  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux
c26139db037233e26aa5ccb563a7b724478a2aee93c98adc7473e88393744dc1  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
44f3cdb79322250516812fb035fbb3eb23c94b7e4567022e8cf498c9a8e3851e  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux
22ce6479147e6fb9c8b353905bfc3d24128e0e60ba94e828f12ba6e860875b86  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
3dca5f3122bfb3d581dd22c565fe66eb5d19b2e792e4ef1a914599b9fdea6a63  ./tailscale/tailscale_merged_s390x_Linux
eb18a8253d91afbf683f0eb084a49f41cc4171e9e3817e27bcaff44118bbdfd0  ./tailscale/tailscale_mips64_Linux
fde6d228555dcfffb973137deeb48afdb070b9101b5e27cc9ddcc9de0ad7385f  ./tailscale/tailscale_mips64le_Linux
cce8825434dfdf303eb29ce3f4a177927d00135823630469e48d02b3a8f1e009  ./tailscale/tailscale_mips_Linux
56f8033a2882c8f30d3dd3b55d8c3eabce35cf507b2434aaaa8a89bb3b0ff458  ./tailscale/tailscale_mips_Linux.upx
835ec700a736f7502c373c8f0810b7dcc6b4b91e9862574616008c0a3206205d  ./tailscale/tailscale_mipsle_Linux
0d82a835653345471ad4c9be8751de4ddbb28356a0bbf0d0ee2631b3b5a3dd72  ./tailscale/tailscale_mipsle_Linux.upx
0712b053111351b333eabc9c8289158923100e818fca2b54daa678a493b53b97  ./tailscale/tailscale_powerpc64_ppc64_Linux
c3488f4ef679f67d5232efae80dd8177da1885470d05d189d53b109fccb5503c  ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
bb88d1351cda933d1be79eeb95d52fe2e024816dafc913e8551d03c039b3a5a4  ./tailscale/tailscale_powerpc64le_ppc64le_Linux
6bb3c19ccf5ccf2925acd7e3d5422e77cdf0ddd72736a7a1100e1069e68f7512  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
2dc5a0f4f689797359165cb398ee54e6e6df9a57cd465b8397e9a2a1718b602a  ./tailscale/tailscale_riscv64_Linux
e773f72f070ddb34d73bfaa51ced2ae0c05610b221057fd14d4be90a8d6f991b  ./tailscale/tailscale_s390x_Linux
64a8ad28cbb67a6171236abe39f75a039a761a0e1aacdef75b26781887cef9a8  ./tailscale/tailscale_setup_Windows.exe
7599c76f8ff0aac49f3c6d4a125bf679c0829dd381f3757988e732c1ce0ede3a  ./tailscale/tailscale_x86_Windows.msi
f2c8cfce618a67094a1e9d103b1031bb134097d97ece1edf43e33514dd1911ad  ./tailscale/tailscaled_aarch64_arm64_Linux
d020b80edc3ec4e78429a1bb43039b61691b81caf1a732cfc1eac4bf1a719ab6  ./tailscale/tailscaled_aarch64_arm64_Linux.upx
3045786fe6191b3d64ae9d2b03b5fffcf080e3cb3073a3c2e8e69e57ea05e2cf  ./tailscale/tailscaled_aarch64_arm64_macOS
2c27f2abebbee8880e4e255add38ca598e400fb319982956e7d3b5b33e9309c9  ./tailscale/tailscaled_amd_geode_Linux
2986ced470a346d41452117e0feb6bd03f3b97e81603c80586c7a4ecc25ad51d  ./tailscale/tailscaled_amd_geode_Linux.upx
d6351077e5059b7513928701422509a112261779a6de94b302ed1c4cc99b7743  ./tailscale/tailscaled_amd_x86_64_Linux
da29f65740429445b9dfbbeab9a6c8c06aba52e362d50d8e43144b76c30ec7db  ./tailscale/tailscaled_amd_x86_64_Linux.upx
b5304b43985998d94d5c2c94e0eeb9e160a76906fa0ecb224af45c3b878e684d  ./tailscale/tailscaled_amd_x86_64_macOS
175d8ee2b1944398f9206339218db00f4915d0f169efae8ae6b3a8c8f5d51dce  ./tailscale/tailscaled_arm_abi_Linux
0b2749a1dfd91312afa969403a0eef9b161908c5c155bc9b49beeedcbaaecdca  ./tailscale/tailscaled_arm_abi_Linux.upx
664f9f87c3c43a8a994b143f5db2a7cc9ec9931e616097009b1be05ca3a60776  ./tailscale/tailscaled_i386_Linux
54b267f64d065d8216d7f7f7700bc9244d205eaeaa59b835f8c6a3f55b8a14db  ./tailscale/tailscaled_i386_Linux.upx
295f83de9e34bf6589262535498a06d8d0fb08aa07a087f5a2a7960e81c2c9d4  ./tailscale/tailscaled_mips64_Linux
9d2a7399c433b852387e173eb5715112c208570fa6cbbecc19eaea9182db51de  ./tailscale/tailscaled_mips64le_Linux
10e7540867883c345da1337f3fff8536651d19a03525f6937bed26759d18801d  ./tailscale/tailscaled_mips_Linux
29d8bb4f54f03360c593a2b8b9f7796187c96b77aac1071daaf95f7952a5b185  ./tailscale/tailscaled_mips_Linux.upx
2ef50ba6dffedfd9475ecaa7d4a1f2317bb8a75d2a7e7d4139e92610ca4b4f24  ./tailscale/tailscaled_mipsle_Linux
d6ca8eaad6361780cb6925089c96a3d82f2a79b38ce6e9ee7ba98d68f506468a  ./tailscale/tailscaled_mipsle_Linux.upx
ed04e2d44d1449a87099eeea8d2da9839c1a4c3a726625284638238690550275  ./tailscale/tailscaled_powerpc64_ppc64_Linux
c16c9e99217c1e78a1b1c0b49bd3686f5ee99d4c53f0bae0394f347ecd4488eb  ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
6e46689fef7b6b41fb89ad6aa49743933acc6e325c7be3815ec50ab8c929ae08  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux
bd254e49246fe60f0b05c4228d5516d9526aacdb1e542a5f5cfb5f69a0e51600  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
f1fb71f50fb1b2906a841c54694741674771c9dd689b87db1b5760296433c932  ./tailscale/tailscaled_riscv64_Linux
3277e591ec2fa8e88367096a24e04adab827b21e52b84ad056ffc8e24303a9c4  ./tailscale/tailscaled_s390x_Linux
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
  26935422 ->   6403032   23.77%   linux/ppc64   ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_amd_geode_Linux.upx [OK]
  21651428 ->   6031364   27.86%   linux/i386    ./tailscale/tailscale_amd_geode_Linux.upx
testing ./tailscale/tailscaled_mipsle_Linux.upx [OK]
  40600441 ->  15277056   37.63%  linux/mipsel   ./tailscale/tailscaled_mipsle_Linux.upx
testing ./tailscale/tailscale_amd_x86_64_Linux.upx [OK]
  23155272 ->   6462116   27.91%   linux/amd64   ./tailscale/tailscale_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_merged_i386_Linux.upx [OK]
  36155518 ->   9576832   26.49%   linux/i386    ./tailscale/tailscale_merged_i386_Linux.upx
testing ./tailscale/tailscale_merged_amd_x86_64_Linux.upx [OK]
  38572158 ->  10240324   26.55%   linux/amd64   ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
testing ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx [OK]
  26869886 ->   6639172   24.71%  linux/ppc64le  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_powerpc64_ppc64_Linux.upx [OK]
  22544510 ->   5210744   23.11%   linux/ppc64   ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscaled_i386_Linux.upx [OK]
  25731468 ->   7365192   28.62%   linux/i386    ./tailscale/tailscaled_i386_Linux.upx
testing ./tailscale/tailscaled_amd_x86_64_Linux.upx [OK]
  29790168 ->   8326000   27.95%   linux/amd64   ./tailscale/tailscaled_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx [OK]
  37748862 ->   8348648   22.12%   linux/ppc64   ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscaled_aarch64_arm64_Linux.upx [OK]
  40127211 ->  16481852   41.07%   linux/arm64   ./tailscale/tailscaled_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_aarch64_arm64_Linux.upx [OK]
  30823188 ->  12597368   40.87%   linux/arm64   ./tailscale/tailscale_aarch64_arm64_Linux.upx
testing ./tailscale/tailscaled_mips_Linux.upx [OK]
  40776029 ->  15307584   37.54%   linux/mips    ./tailscale/tailscaled_mips_Linux.upx
testing ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx [OK]
  35848318 ->   8400516   23.43%   linux/arm64   ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_arm_abi_Linux.upx [OK]
  30567349 ->  12365964   40.45%    linux/arm    ./tailscale/tailscale_arm_abi_Linux.upx
testing ./tailscale/tailscale_mipsle_Linux.upx [OK]
  33613219 ->  12433380   36.99%  linux/mipsel   ./tailscale/tailscale_mipsle_Linux.upx
testing ./tailscale/tailscaled_amd_geode_Linux.upx [OK]
  25764236 ->   7371536   28.61%   linux/i386    ./tailscale/tailscaled_amd_geode_Linux.upx
testing ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx [OK]
  22544510 ->   5429360   24.08%  linux/ppc64le  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_merged_arm_Linux.upx [OK]
  35651710 ->   8204356   23.01%    linux/arm    ./tailscale/tailscale_merged_arm_Linux.upx
testing ./tailscale/tailscaled_arm_abi_Linux.upx [OK]
  36567700 ->  15136660   41.39%    linux/arm    ./tailscale/tailscaled_arm_abi_Linux.upx
testing ./tailscale/tailscale_mips_Linux.upx [OK]
  33763939 ->  12461992   36.91%   linux/mips    ./tailscale/tailscale_mips_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx [OK]
  37748862 ->   8648780   22.91%  linux/ppc64le  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_i386_Linux.upx [OK]
  21598148 ->   6019872   27.87%   linux/i386    ./tailscale/tailscale_i386_Linux.upx

```

---

- #### Version
```console
$ ./tailscale/tailscale_amd_x86_64_Linux --version
1.102.1
  tailscale commit: 8ebe8f7c36d79b792714ed8360ca55dd1b38cc23
  long version: 1.102.1-t8ebe8f7c3-gda6192991
  other commit: da61929913f0135ffb1f0d10f16858700f9652f5
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
1.102.1
  tailscale commit: 8ebe8f7c36d79b792714ed8360ca55dd1b38cc23
  long version: 1.102.1-t8ebe8f7c3-gda6192991
  other commit: da61929913f0135ffb1f0d10f16858700f9652f5
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


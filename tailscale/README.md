
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
./tailscale/tailscale_aarch64_arm64_Linux:                   ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=OqjTAMinTFzVPN2BrO8l/kckR3FCLuTyWvp00I_sm/5M-jYkbV8CpMco_yeSvJ/cpARWngXRmoDtapBmhjV, BuildID[sha1]=e182c0e528b38699fd0a2281e8417a75b78ec522, with debug_info, not stripped
./tailscale/tailscale_aarch64_arm64_Linux.upx:               ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=OqjTAMinTFzVPN2BrO8l/kckR3FCLuTyWvp00I_sm/5M-jYkbV8CpMco_yeSvJ/cpARWngXRmoDtapBmhjV, statically linked, no section header
./tailscale/tailscale_aarch64_arm64_Windows.msi:             Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Arm64;1033, Revision Number: {90D8A9A4-FF9B-4FC2-AB9F-855CBD48A13D}, Create Time/Date: Tue Jul 28 23:32:48 2026, Last Saved Time/Date: Tue Jul 28 23:32:48 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscale_aarch64_arm64_macOS:                   Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_amd_geode_Linux:                       ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=na6GCHhVt2X9DCO-2SCc/qy4lh2RCuVPNCRL6fGKM/xruV9zwB0I-5rBRw9uHV/WNLF9cqyy31i26XYdznQ, BuildID[sha1]=ea3efaf829d3054c9f965785371c0a8b32ab0f33, stripped
./tailscale/tailscale_amd_geode_Linux.upx:                   ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=na6GCHhVt2X9DCO-2SCc/qy4lh2RCuVPNCRL6fGKM/xruV9zwB0I-5rBRw9uHV/WNLF9cqyy31i26XYdznQ, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Linux:                      ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=sObktqxF-EYRsShnkkA0/U4d_cM6_W5K05aiHTmCw/rMT9zGKvSO78jdWhapSs/gJX4S_IC1355DFMIx0BF, BuildID[sha1]=42d0478a01cbe16342b7bb720dbac3fb3b1c7bf1, stripped
./tailscale/tailscale_amd_x86_64_Linux.upx:                  ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=sObktqxF-EYRsShnkkA0/U4d_cM6_W5K05aiHTmCw/rMT9zGKvSO78jdWhapSs/gJX4S_IC1355DFMIx0BF, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Windows.msi:                Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: x64;1033, Revision Number: {F74442CA-B71E-4D8F-83E7-78557B69984B}, Create Time/Date: Tue Jul 28 23:32:48 2026, Last Saved Time/Date: Tue Jul 28 23:32:48 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscale_amd_x86_64_macOS:                      Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_arm_abi_Linux:                         ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=Mpz73lLu7mJIDCBTC3Zw/_toDzTUhnERZvX-dazx3/qXzXYGFpNYQspg1bxqtl/NY49ijQGWHgdVjpCwNQC, BuildID[sha1]=a514c101ccdb113f401e67c6b0892b14b1df7826, with debug_info, not stripped
./tailscale/tailscale_arm_abi_Linux.upx:                     ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=Mpz73lLu7mJIDCBTC3Zw/_toDzTUhnERZvX-dazx3/qXzXYGFpNYQspg1bxqtl/NY49ijQGWHgdVjpCwNQC, statically linked, no section header
./tailscale/tailscale_i386_Linux:                            ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=Zd-mmZ5vz-vWYO_oGVe_/2Y7uVfk0zFiMGrXDgBR5/n6FuVWPW7rpUvlAzOGgW/3GHNFF6U4FAaVPf4mokX, BuildID[sha1]=c02b88b12310f08134837246bd40036c5cefe8a6, stripped
./tailscale/tailscale_i386_Linux.upx:                        ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=Zd-mmZ5vz-vWYO_oGVe_/2Y7uVfk0zFiMGrXDgBR5/n6FuVWPW7rpUvlAzOGgW/3GHNFF6U4FAaVPf4mokX, statically linked, no section header
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
./tailscale/tailscale_mips64_Linux:                          ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=bwaIpN04EEW9iCbzXA7f/WmCQHW3oMKL-CqTA3xo8/ereMJHRErLV-uhr4VYLQ/Ze3NcGpYaQk1au1CvFBv, BuildID[sha1]=cdf6968df3167ec7b3ce54e6f75a752e7ad2fa4d, with debug_info, not stripped
./tailscale/tailscale_mips64le_Linux:                        ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=1AGTZBTOLS2S_wm8Oc5H/43V4D9tU4-MsbV6yvB0D/UBukqWjvIYw_kNXOKAN9/OHihteaIl53bQ8SzXq66, BuildID[sha1]=d59615a70d74614fee21b76e95d931b60a6ac01c, with debug_info, not stripped
./tailscale/tailscale_mips_Linux:                            ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=w7s0c8sNbW5S0KCrjFVd/7-hUxLvxMrMmPGXcm3Zk/b9tZNPmBvYltTroNaexX/8smjE2Ju0Vr8LqmUC1ef, BuildID[sha1]=58bde23434cafd26f6bdc958f99c9462bdca58b5, with debug_info, not stripped
./tailscale/tailscale_mips_Linux.upx:                        ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=w7s0c8sNbW5S0KCrjFVd/7-hUxLvxMrMmPGXcm3Zk/b9tZNPmBvYltTroNaexX/8smjE2Ju0Vr8LqmUC1ef, statically linked, no section header
./tailscale/tailscale_mipsle_Linux:                          ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=4Yfwgch9qvYElzg72zff/hWENZdJGYX0nhUv4lDQn/IgJqqotwHe_ZdRshTX9t/b-DaLhVKVgoMfnJecGA-, BuildID[sha1]=e22bf98aa9ce57da28184312baaf5f1100d02e4c, with debug_info, not stripped
./tailscale/tailscale_mipsle_Linux.upx:                      ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=4Yfwgch9qvYElzg72zff/hWENZdJGYX0nhUv4lDQn/IgJqqotwHe_ZdRshTX9t/b-DaLhVKVgoMfnJecGA-, statically linked, no section header
./tailscale/tailscale_powerpc64_ppc64_Linux:                 ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64_ppc64_Linux.upx:             ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_powerpc64le_ppc64le_Linux:             ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx:         ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_riscv64_Linux:                         ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, Go BuildID=1rjT256n54XuEl6qsUC8/uyhFEI5CmWFgdjS8dJvW/RbsxjI_2NckvTeuip4Fs/c-eYXFc8vQwfsTLKFQ27, BuildID[sha1]=e75ed42976af7cf1fa1888559336a70188cd20ba, with debug_info, not stripped
./tailscale/tailscale_s390x_Linux:                           ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_setup_Windows.exe:                     PE32 executable (GUI) Intel 80386, for MS Windows, 6 sections
./tailscale/tailscale_x86_Windows.msi:                       Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Intel;1033, Revision Number: {654798D0-B66A-4BF2-864F-E5ADBA714D78}, Create Time/Date: Tue Jul 28 23:32:48 2026, Last Saved Time/Date: Tue Jul 28 23:32:48 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscaled_aarch64_arm64_Linux:                  ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=Ve-lWLiBx1gh3_Jws1aM/KPDBRDyRQDL0KrkSPS-H/q9EFQtdKbij02ZuWHy9G/JN3O_QUYDVra59yf9Vox, BuildID[sha1]=4920f74e6643425354758984daf5b1cfb3ac24bd, with debug_info, not stripped
./tailscale/tailscaled_aarch64_arm64_Linux.upx:              ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=Ve-lWLiBx1gh3_Jws1aM/KPDBRDyRQDL0KrkSPS-H/q9EFQtdKbij02ZuWHy9G/JN3O_QUYDVra59yf9Vox, statically linked, no section header
./tailscale/tailscaled_aarch64_arm64_macOS:                  Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_amd_geode_Linux:                      ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=_kMVT0sLsST6PQ9xy7Be/8axM1tYuAotY6SLFHkdE/2nixp0rQlxFBcb_2qtie/9Fqt9BxC1Ey6vZ3XSE5o, BuildID[sha1]=c10bb198c8b23913ed19838a09a9faa99e7df6af, stripped
./tailscale/tailscaled_amd_geode_Linux.upx:                  ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=_kMVT0sLsST6PQ9xy7Be/8axM1tYuAotY6SLFHkdE/2nixp0rQlxFBcb_2qtie/9Fqt9BxC1Ey6vZ3XSE5o, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_Linux:                     ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=HuRBNVtHwM24a4Ht2wJd/qMfrCHBGqBbuGknEzzC6/yvlq0KwH9bC8Yyf9ccwR/KJF9pvplPLrjFvwHYL8p, BuildID[sha1]=fc1bdda782ceb161ce0b18a3490c0fb80199c094, stripped
./tailscale/tailscaled_amd_x86_64_Linux.upx:                 ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=HuRBNVtHwM24a4Ht2wJd/qMfrCHBGqBbuGknEzzC6/yvlq0KwH9bC8Yyf9ccwR/KJF9pvplPLrjFvwHYL8p, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_macOS:                     Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_arm_abi_Linux:                        ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=5kkRdqrGRgmi36SnHBp5/qRNx00amYE1VXaZQcHJy/QdcbuMwZm83SGT0gsZKd/N4PyXgRIQ07kA8IDDfq8, BuildID[sha1]=425e87b263a970dda197eb1ed5b9e4f6d3d980fd, with debug_info, not stripped
./tailscale/tailscaled_arm_abi_Linux.upx:                    ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=5kkRdqrGRgmi36SnHBp5/qRNx00amYE1VXaZQcHJy/QdcbuMwZm83SGT0gsZKd/N4PyXgRIQ07kA8IDDfq8, statically linked, no section header
./tailscale/tailscaled_i386_Linux:                           ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=rbwQccyuaPrtK6QQoaqE/7SZOaIlcTMXLaJVM1GsL/FfRqfLgoNUA87cj1Gknw/2EiHKMsRNmLJZtoXPLOc, BuildID[sha1]=59661a32a5636b576e9e88973be846b932d1c6a4, stripped
./tailscale/tailscaled_i386_Linux.upx:                       ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=rbwQccyuaPrtK6QQoaqE/7SZOaIlcTMXLaJVM1GsL/FfRqfLgoNUA87cj1Gknw/2EiHKMsRNmLJZtoXPLOc, statically linked, no section header
./tailscale/tailscaled_mips64_Linux:                         ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=R3HyQhIjX7Mc4PwWLsCd/Dd4x96ht-Zk9tqHa9Vwn/COGMBx3uTDTY7azlksA6/DxKF9OvjVjQNWMn9R_44, BuildID[sha1]=114ffb1816c4d18741d26d9ead35c355a5c74a25, with debug_info, not stripped
./tailscale/tailscaled_mips64le_Linux:                       ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=0QlxL77JS-Z1hgPI28bf/SWh-YVNdXLbVUGmXTVvG/E5ig13i2jHC1y0cOS87C/xeyGRh4RkADVnf4hrnid, BuildID[sha1]=d94c97a90b8e4d656e259a6482608a27bb6d4fcd, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux:                           ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=FOJNvPvG0Oojubmm5U9h/bO_xngx5Q6hAmvMXmX2u/Oe1fL-3PF-lVNH0CNwAE/DgWyUTSjXJeXXYqriMG8, BuildID[sha1]=04e915063569ad1e1b3ed20300810554a3784284, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux.upx:                       ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=FOJNvPvG0Oojubmm5U9h/bO_xngx5Q6hAmvMXmX2u/Oe1fL-3PF-lVNH0CNwAE/DgWyUTSjXJeXXYqriMG8, statically linked, no section header
./tailscale/tailscaled_mipsle_Linux:                         ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=MghOvOrCNmBM9nDTEzDZ/7oZFqMIcFwg2WaKqaXTR/uyVWE6IOl8X9-xal_1l4/dXp_u68hCZICh_V0kQB5, BuildID[sha1]=6100256bd7e572060137e05d4e3f7d4c50b3a4da, with debug_info, not stripped
./tailscale/tailscaled_mipsle_Linux.upx:                     ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=MghOvOrCNmBM9nDTEzDZ/7oZFqMIcFwg2WaKqaXTR/uyVWE6IOl8X9-xal_1l4/dXp_u68hCZICh_V0kQB5, statically linked, no section header
./tailscale/tailscaled_powerpc64_ppc64_Linux:                ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64_ppc64_Linux.upx:            ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_powerpc64le_ppc64le_Linux:            ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx:        ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_riscv64_Linux:                        ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, Go BuildID=euxNIhz0_bGSQ2N56nCN/Yq6jI7W5jI21oUsv-n1P/zI9GbdeD2Tv4-u1PHhkR/SZ8GGLqmyCfg-Wb1hSpS, BuildID[sha1]=0074db6c76864c6b08f8b298050a3c5a2f6061ab, with debug_info, not stripped
./tailscale/tailscaled_s390x_Linux:                          ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped

--> SHA256SUM
a0704a3d4ae4323bb0f4a31e703f053094c12e900eda32caca4449333306d4fe  ./tailscale/tailscale_aarch64_arm64_Linux
37ac4670d066e7ea82c852563d8841ede6fa1dd8eab591eaa0263641052f0e8f  ./tailscale/tailscale_aarch64_arm64_Linux.upx
38d1d1fb8e6414b4e0522cb3c86976a8eb928b9aac4933bb7ec728dda8d6eb3b  ./tailscale/tailscale_aarch64_arm64_Windows.msi
758bd296723a348a70f5274b294baeb4053abd2e2ce58e2220e210946b618c6f  ./tailscale/tailscale_aarch64_arm64_macOS
49209ccc46737b0f7900f79d32102a8577e31fb3e498845bfaa4812ced6e607e  ./tailscale/tailscale_amd_geode_Linux
c050fe0a52943de11c67606a337d32f7ed44d18a97f199f0d7d680d7f4d045c7  ./tailscale/tailscale_amd_geode_Linux.upx
0d801d75148c795d253d54d36b1a95a9592b44c19576423722d34469dd6d3ea5  ./tailscale/tailscale_amd_x86_64_Linux
6558f88e6faf7939554e72cb516f55eb9cda7a7f44929bebd8fd8e2437f42ebd  ./tailscale/tailscale_amd_x86_64_Linux.upx
a66919f0e4a2008ad47a666ba041db3a986e41692ad00e743237e65c7a1f4fda  ./tailscale/tailscale_amd_x86_64_Windows.msi
248b7930c0c4c650f988bcb90a968da042066e0b826bf58efd8fe3a69fad8e7f  ./tailscale/tailscale_amd_x86_64_macOS
b43d43beb78781d4fac640935731821573be49b184832cc23fea4aefb206dd76  ./tailscale/tailscale_arm_abi_Linux
3d324991cf0b361f5f992751b26dcf3523cedc6415355f79a82677de08f70a6a  ./tailscale/tailscale_arm_abi_Linux.upx
d6f5708d6dc934b89aac50d8835678ccaf66e1a8570240e72b324989d3b9d86e  ./tailscale/tailscale_i386_Linux
c10d10bb84a079a7cfde23fb0364d353b2b93c4f14af2223f9e2cd1544da6655  ./tailscale/tailscale_i386_Linux.upx
c7935601a8608b64322f052404bdda0880895ff9355aa8f5c5740822b3b8113b  ./tailscale/tailscale_ipn_setup_Windows.exe
ac9349bb9020ad02ded30d55ae9401bdeb151eef2265f44756a7ea84a53c774e  ./tailscale/tailscale_merged_aarch64_arm64_Linux
23efafae3d4ef88ef7c3a31c867418c0eea16b29b1b10e78509c2bb28a232b5a  ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
68728bde1313493eb44dbd3be2e989eb00f60f4938d0d2845df9d45e32c25df7  ./tailscale/tailscale_merged_aarch64_arm64_macOS
ebc1786212bf0e8c7c5742874c9bbe48e0f31028f97473649914ff9a64efb017  ./tailscale/tailscale_merged_amd_x86_64_Linux
eac8da37b7f93ed788bbfeae4dd873e7f820dda96b40f2cfd61b3eeba66bfaef  ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
267bebcfe539dd8353add30caf55a042bf996f8e688aae7910b9ecf61714f3f8  ./tailscale/tailscale_merged_amd_x86_64_macOS
8777aea82feb54a9b1189e9b607ead7a47e2803d6f9a4cc12e26136d70fb70f5  ./tailscale/tailscale_merged_arm_Linux
f24b9b90d3f14e2052d397657a73ac9e001cfc3b6adbe3ae4b44b7c63a45d8b5  ./tailscale/tailscale_merged_arm_Linux.upx
6aab3ded279a70ae0b64422cab8c61b2eae90c8a59619dc80941f49bd7100497  ./tailscale/tailscale_merged_i386_Linux
23391eb77e786f823a0eb1e095d5c79754b13557be5df40bd5430b5309b7bf60  ./tailscale/tailscale_merged_i386_Linux.upx
4ed17929bf9bc046fae7d92a0b163be3659c05854096a6edb9bffc03496329be  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux
2a456fa30893b25f65c54dd7445a8e544ed19d2cfcb6a63c71aee5e18425b2ca  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
ce9782ea72a62005c1615abd0509f1ee17e154f1b70358547422fa8d971c16ab  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux
172b0187ef641663b338ff4e5a9416229624f6b55f889d6b99fa08c27460347b  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
336b097e984c0c4e90b740b1977f981269fc645c113a0bf923d789c06d827450  ./tailscale/tailscale_merged_s390x_Linux
0c3e39eea9251854e795658a4f2c4c5dd0ad19c2b0a24a99c143950dbe52d755  ./tailscale/tailscale_mips64_Linux
4a108d882bfddd95d8cce88e9bd942cd4d574f9d0e06bd0e53b89adf8d7dfca4  ./tailscale/tailscale_mips64le_Linux
2eb8031d195205221690785ac0ca187adab71fd4cf22da62b2b0b340cffbb3a5  ./tailscale/tailscale_mips_Linux
8ec95732550664efd5d32b88c231bc01762bdd09ef083d6f06fafba9d9c945f7  ./tailscale/tailscale_mips_Linux.upx
100765fa65ad6e24886e93223a3c415c2856668944c7d687a41540e1e0e2b4f9  ./tailscale/tailscale_mipsle_Linux
e3000a564a61b12cbe836cfb359178d43c56ae43e670b3ded082e9ae3e35844d  ./tailscale/tailscale_mipsle_Linux.upx
ea67ec941f1a61e9a22bfc964de725509ca963aaabc41f1d83603fae4d258fed  ./tailscale/tailscale_powerpc64_ppc64_Linux
568402d4be0fd30146dbd7ee9913cb61ce767c15f1f81262caccb6d075ee2c63  ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
4343e440cd43a5d8526ad9d671456eab5c06cebe12bc5ee1ff15fc1ac56171c7  ./tailscale/tailscale_powerpc64le_ppc64le_Linux
e777d7fbfad4f4a4e3ba4ef3ca9b1eaf33362a432560bd92d2f953af378be4b4  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
a435556089c1ef53faed380010ea6b5dcf2abbb934495a2b1fc2681020bb1101  ./tailscale/tailscale_riscv64_Linux
f2da0250a9c24ce74760692ddae7b231d616ddc38d6e3d60f5cc7625fdcbb45a  ./tailscale/tailscale_s390x_Linux
64a8ad28cbb67a6171236abe39f75a039a761a0e1aacdef75b26781887cef9a8  ./tailscale/tailscale_setup_Windows.exe
9ce8163b038338b617b3641cde8a7b2d7a35236fcade883f3f5d89162417da4e  ./tailscale/tailscale_x86_Windows.msi
e7ccc6a429c7bac219e2f4243b13f8176c033d301cc3c4fc98ec6edc0e570615  ./tailscale/tailscaled_aarch64_arm64_Linux
7d5fc01000aaa320f15ef358b15020c1b8c86604249242f66c04bfe74193c30e  ./tailscale/tailscaled_aarch64_arm64_Linux.upx
3045786fe6191b3d64ae9d2b03b5fffcf080e3cb3073a3c2e8e69e57ea05e2cf  ./tailscale/tailscaled_aarch64_arm64_macOS
981d1393233dc7c829be18c89679fe24052bd9349b50fee99fb63125b51a01bd  ./tailscale/tailscaled_amd_geode_Linux
0566141376553a08d988f24026295bd15e14065287cea7ab68523443f54c2ab9  ./tailscale/tailscaled_amd_geode_Linux.upx
fb6e7824b2f4404f225c4687d642f7271fa3030812818fd7850eb75f13f71e57  ./tailscale/tailscaled_amd_x86_64_Linux
e14938fcf7fb4bb8598d2c81c4478dc220cef85584db28e140fcee1d17db2209  ./tailscale/tailscaled_amd_x86_64_Linux.upx
b5304b43985998d94d5c2c94e0eeb9e160a76906fa0ecb224af45c3b878e684d  ./tailscale/tailscaled_amd_x86_64_macOS
d1de31feb0919f84e525fd72cff5f0354def68353a60136d129fc5947b0764e7  ./tailscale/tailscaled_arm_abi_Linux
5670a89209e25f0e60eaee3767844c2cd9e776b5cf73373d2408554ff167aa68  ./tailscale/tailscaled_arm_abi_Linux.upx
018a166099d57e3dcba42aee9abf307e80182ae90ca8d5888c01e4bab6693cf7  ./tailscale/tailscaled_i386_Linux
0562986a5f2c8cff0317e9213f9abd6794020ca353c08c1c4744ea522aada5c5  ./tailscale/tailscaled_i386_Linux.upx
76497c9b95a4ad54bf4b704b5de75128c1fe4a2d1ad873aefc060974f738b111  ./tailscale/tailscaled_mips64_Linux
1b3829af8c43011e8fd04a16f6654e1d85f0a064df0eccd6eb52f5850017289d  ./tailscale/tailscaled_mips64le_Linux
9c6dd444da608e79142f5af26e764c1843aa0b6292e2d014c9efd258eb88bf90  ./tailscale/tailscaled_mips_Linux
b005800f3eb07e54b1c96229c13c2492409236e76bb0a964d850b161772a1555  ./tailscale/tailscaled_mips_Linux.upx
9a315f21f8e6a614a1386ab74ebd81155ed04df9e7e8dc2ae6489f16b39b3423  ./tailscale/tailscaled_mipsle_Linux
5a903f0b56579e14b2761fa0de7b4ffcbfac414132c8262be802be4255d58a7a  ./tailscale/tailscaled_mipsle_Linux.upx
5aad3ed47c885a4e164353fd29e0a9025b50e9b51bedec50500fc984aebb3e30  ./tailscale/tailscaled_powerpc64_ppc64_Linux
62e5dda37f09fcbc54577d22fb9c0d48353cfa2c52cb502b8c9a19051b6aedb3  ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
bedd5dfbefb9ccc6e40173e98f9041f0c0d6599f39b1556d47bd2eba3ddb774c  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux
0d3738c687436c8394df358d8c8a1c8a812ca7388e92aa0d4096ad3cbd399e61  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
b4c6a4d7e95dddba740414e330a6f35408b92d4c1bab6215db452843d0883527  ./tailscale/tailscaled_riscv64_Linux
0d9b34a7a3bf9b287f5a1c27c179b944ced5af9b64a521478761e0d751c383ab  ./tailscale/tailscaled_s390x_Linux
```


---

- #### Sizes

```console
29M   ./tailscale/tailscale_aarch64_arm64_Linux
12M   ./tailscale/tailscale_aarch64_arm64_Linux.upx
33M   ./tailscale/tailscale_aarch64_arm64_Windows.msi
11M   ./tailscale/tailscale_aarch64_arm64_macOS
20M   ./tailscale/tailscale_amd_geode_Linux
5.6M  ./tailscale/tailscale_amd_geode_Linux.upx
22M   ./tailscale/tailscale_amd_x86_64_Linux
6.0M  ./tailscale/tailscale_amd_x86_64_Linux.upx
35M   ./tailscale/tailscale_amd_x86_64_Windows.msi
11M   ./tailscale/tailscale_amd_x86_64_macOS
28M   ./tailscale/tailscale_arm_abi_Linux
12M   ./tailscale/tailscale_arm_abi_Linux.upx
20M   ./tailscale/tailscale_i386_Linux
5.6M  ./tailscale/tailscale_i386_Linux.upx
70K   ./tailscale/tailscale_ipn_setup_Windows.exe
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
6.2M  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
34M   ./tailscale/tailscaled_riscv64_Linux
26M   ./tailscale/tailscaled_s390x_Linux
```

---

- #### UPX
```console

testing ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx [OK]
  25755774 ->   6166472   23.94%   linux/ppc64   ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_amd_geode_Linux.upx [OK]
  20788164 ->   5794276   27.87%   linux/i386    ./tailscale/tailscale_amd_geode_Linux.upx
testing ./tailscale/tailscaled_mipsle_Linux.upx [OK]
  38880923 ->  14674716   37.74%  linux/mipsel   ./tailscale/tailscaled_mipsle_Linux.upx
testing ./tailscale/tailscale_amd_x86_64_Linux.upx [OK]
  22282408 ->   6210920   27.87%   linux/amd64   ./tailscale/tailscale_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_merged_i386_Linux.upx [OK]
  34427006 ->   9158056   26.60%   linux/i386    ./tailscale/tailscale_merged_i386_Linux.upx
testing ./tailscale/tailscale_merged_amd_x86_64_Linux.upx [OK]
  36757630 ->   9799484   26.66%   linux/amd64   ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
testing ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx [OK]
  25755774 ->   6402044   24.86%  linux/ppc64le  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_powerpc64_ppc64_Linux.upx [OK]
  21364862 ->   4986532   23.34%   linux/ppc64   ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscaled_i386_Linux.upx [OK]
  24723980 ->   7094500   28.69%   linux/i386    ./tailscale/tailscaled_i386_Linux.upx
testing ./tailscale/tailscaled_amd_x86_64_Linux.upx [OK]
  28606840 ->   8022200   28.04%   linux/amd64   ./tailscale/tailscaled_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx [OK]
  35979390 ->   7983960   22.19%   linux/ppc64   ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscaled_aarch64_arm64_Linux.upx [OK]
  38494994 ->  15829116   41.12%   linux/arm64   ./tailscale/tailscaled_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_aarch64_arm64_Linux.upx [OK]
  29583570 ->  12097556   40.89%   linux/arm64   ./tailscale/tailscale_aarch64_arm64_Linux.upx
testing ./tailscale/tailscaled_mips_Linux.upx [OK]
  39047903 ->  14703560   37.66%   linux/mips    ./tailscale/tailscaled_mips_Linux.upx
testing ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx [OK]
  34078846 ->   8033976   23.57%   linux/arm64   ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_arm_abi_Linux.upx [OK]
  29267970 ->  11857612   40.51%    linux/arm    ./tailscale/tailscale_arm_abi_Linux.upx
testing ./tailscale/tailscale_mipsle_Linux.upx [OK]
  32249258 ->  11928640   36.99%  linux/mipsel   ./tailscale/tailscale_mipsle_Linux.upx
testing ./tailscale/tailscaled_amd_geode_Linux.upx [OK]
  24760876 ->   7102964   28.69%   linux/i386    ./tailscale/tailscaled_amd_geode_Linux.upx
testing ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx [OK]
  21430398 ->   5197524   24.25%  linux/ppc64le  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_merged_arm_Linux.upx [OK]
  33882238 ->   7839708   23.14%    linux/arm    ./tailscale/tailscale_merged_arm_Linux.upx
testing ./tailscale/tailscaled_arm_abi_Linux.upx [OK]
  35046710 ->  14526464   41.45%    linux/arm    ./tailscale/tailscaled_arm_abi_Linux.upx
testing ./tailscale/tailscale_mips_Linux.upx [OK]
  32396010 ->  11956004   36.91%   linux/mips    ./tailscale/tailscale_mips_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx [OK]
  35979390 ->   8278848   23.01%  linux/ppc64le  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_i386_Linux.upx [OK]
  20734884 ->   5782532   27.89%   linux/i386    ./tailscale/tailscale_i386_Linux.upx

```

---

- #### Version
```console
$ ./tailscale/tailscale_amd_x86_64_Linux --version
1.98.10
  tailscale commit: 0ee734d3089846b27bc6ebcddd3d6ee5ec13e04d
  long version: 1.98.10-t0ee734d30-g6b4108809
  other commit: 6b4108809f6395c897bc1d4f5eb82ad882133989
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
1.98.10
  tailscale commit: 0ee734d3089846b27bc6ebcddd3d6ee5ec13e04d
  long version: 1.98.10-t0ee734d30-g6b4108809
  other commit: 6b4108809f6395c897bc1d4f5eb82ad882133989
  go version: go1.26.5 (tailscale/go 63ae404c82)

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


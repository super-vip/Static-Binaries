
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
./tailscale/tailscale_aarch64_arm64_Linux:                   ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=RzLWzHk-wK5degJ4rht1/cIZOetqaFr2deLQPqEEI/ZTObV0V2SqoFOcr4hYqm/CB3qa2eDvFkJHF-2AKgA, BuildID[sha1]=5d19600238fb14fb878b276534e6644003bbdac5, with debug_info, not stripped
./tailscale/tailscale_aarch64_arm64_Linux.upx:               ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=RzLWzHk-wK5degJ4rht1/cIZOetqaFr2deLQPqEEI/ZTObV0V2SqoFOcr4hYqm/CB3qa2eDvFkJHF-2AKgA, statically linked, no section header
./tailscale/tailscale_aarch64_arm64_Windows.msi:             Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Arm64;1033, Revision Number: {10FBCB00-3434-40C3-8A4D-AB31248DE0B9}, Create Time/Date: Thu Mar 19 18:16:15 2026, Last Saved Time/Date: Thu Mar 19 18:16:15 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscale_aarch64_arm64_macOS:                   Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_amd_geode_Linux:                       ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=OTbrSCKrFeihjih6RJCw/pBrjVxfmnkY54AGBpgeC/xJIAD4SfGj8qFcPOSDtP/viDS7rP1yfv2StpLtKc9, BuildID[sha1]=2fbe1a001ad1efa4fc3cf8299ffce419898a80a5, stripped
./tailscale/tailscale_amd_geode_Linux.upx:                   ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=OTbrSCKrFeihjih6RJCw/pBrjVxfmnkY54AGBpgeC/xJIAD4SfGj8qFcPOSDtP/viDS7rP1yfv2StpLtKc9, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Linux:                      ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=Frc8czhMPI4TkzPHZLGo/SoqAvNVuRoh1d3027b4h/PwayEUv1R2URpzOWznLI/Hbm-pdUsoQkTLL0ztPat, BuildID[sha1]=afade7a0fdda938c236dbaf9f56bccc905891ba9, stripped
./tailscale/tailscale_amd_x86_64_Linux.upx:                  ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=Frc8czhMPI4TkzPHZLGo/SoqAvNVuRoh1d3027b4h/PwayEUv1R2URpzOWznLI/Hbm-pdUsoQkTLL0ztPat, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Windows.msi:                Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: x64;1033, Revision Number: {5C2F596E-F018-408C-B5EC-1397E0CBC4FA}, Create Time/Date: Thu Mar 19 18:16:04 2026, Last Saved Time/Date: Thu Mar 19 18:16:04 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscale_amd_x86_64_macOS:                      Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_arm_abi_Linux:                         ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=dG4WtBAEuakZ41VnorFM/tz2hd6-gxHNHTJRbzql_/pnpUhFNMiE1OmeNmqyh-/BuwuzbBzKNrWk0E073aK, BuildID[sha1]=7390f192a911ae13847d15feeec25248652a4b34, with debug_info, not stripped
./tailscale/tailscale_arm_abi_Linux.upx:                     ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=dG4WtBAEuakZ41VnorFM/tz2hd6-gxHNHTJRbzql_/pnpUhFNMiE1OmeNmqyh-/BuwuzbBzKNrWk0E073aK, statically linked, no section header
./tailscale/tailscale_i386_Linux:                            ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=nkHnL-hGINc6QxpJfKmY/p6DT4PJPRWKrouRs-6VC/Ve_kOriJEFhny0vbkOtQ/Kb_PSk7GfvuWKr0Dvej9, BuildID[sha1]=14ae5cf8395df58b03828c99a6927f18f1bb3b1b, stripped
./tailscale/tailscale_i386_Linux.upx:                        ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=nkHnL-hGINc6QxpJfKmY/p6DT4PJPRWKrouRs-6VC/Ve_kOriJEFhny0vbkOtQ/Kb_PSk7GfvuWKr0Dvej9, statically linked, no section header
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
./tailscale/tailscale_mips64_Linux:                          ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=vSOMmRuGlGu46_T7qpa2/GR36J8kKVDkNdtAxrvnf/68Mw7Y8WmZPpbZnoaGaX/c7ifWB_yJOi-Onhw5u77, BuildID[sha1]=48b351412f56feb5c52fdba091d8bdcdb87dc760, with debug_info, not stripped
./tailscale/tailscale_mips64le_Linux:                        ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=1bLJ8gmjqaPWgE9ceP1j/LtOkZ7WqKo5LDVrrZKQb/BmwcChWI0PF4VaP9ZG50/If2WSxX97ogPdPxcLysu, BuildID[sha1]=a53688edf22e5978dd25de6f0a5ce759ec7865e1, with debug_info, not stripped
./tailscale/tailscale_mips_Linux:                            ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=yhnZa0SUbMYCwsbOOYHU/d2BD3ibxUMAAdBlaF7Tw/DM-LHiWn9CoHzfKu9dFh/OgN02ESHFpIQuTh0zdm_, BuildID[sha1]=d2a1cc7ae847513d6d15bbd5c1645859c9a82c76, with debug_info, not stripped
./tailscale/tailscale_mips_Linux.upx:                        ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=yhnZa0SUbMYCwsbOOYHU/d2BD3ibxUMAAdBlaF7Tw/DM-LHiWn9CoHzfKu9dFh/OgN02ESHFpIQuTh0zdm_, statically linked, no section header
./tailscale/tailscale_mipsle_Linux:                          ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=X-60y7NmcUPrGQmkehmf/4KbtB0x61dRm5RVUFgbb/GYWsP_aujTSyBk-faq1L/Q2foJU6ZxSVDRiFqHfyg, BuildID[sha1]=96e398950ad927e98269bd62d791b5750945a695, with debug_info, not stripped
./tailscale/tailscale_mipsle_Linux.upx:                      ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=X-60y7NmcUPrGQmkehmf/4KbtB0x61dRm5RVUFgbb/GYWsP_aujTSyBk-faq1L/Q2foJU6ZxSVDRiFqHfyg, statically linked, no section header
./tailscale/tailscale_powerpc64_ppc64_Linux:                 ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64_ppc64_Linux.upx:             ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_powerpc64le_ppc64le_Linux:             ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx:         ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_riscv64_Linux:                         ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, Go BuildID=Qul4ssfo83pmLZ_9SXwo/biHacDqZTWZk1wt0JqJC/W_Wpq6uJJJ1ARetCB--e/EY1Y0ihqljv0WaY_M2_A, BuildID[sha1]=fdd86f3c438df840fe6aafd69b0f481eeff984b7, with debug_info, not stripped
./tailscale/tailscale_s390x_Linux:                           ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_setup_Windows.exe:                     PE32 executable (GUI) Intel 80386, for MS Windows, 6 sections
./tailscale/tailscale_x86_Windows.msi:                       Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Intel;1033, Revision Number: {6C5FE0CA-850D-4395-BA2C-5024C93034F9}, Create Time/Date: Thu Mar 19 18:16:15 2026, Last Saved Time/Date: Thu Mar 19 18:16:15 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscaled_aarch64_arm64_Linux:                  ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=xNgP3qxSXSAaugMalcWt/crYC5tAu4m4NQPDLBDTs/mNqvHR6izwKuOo11CneJ/_B5br5ZRcNhkeLp8uzlV, BuildID[sha1]=ec994370431bb1c3a7ee558da1c6de402fba5e57, with debug_info, not stripped
./tailscale/tailscaled_aarch64_arm64_Linux.upx:              ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=xNgP3qxSXSAaugMalcWt/crYC5tAu4m4NQPDLBDTs/mNqvHR6izwKuOo11CneJ/_B5br5ZRcNhkeLp8uzlV, statically linked, no section header
./tailscale/tailscaled_aarch64_arm64_macOS:                  Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_amd_geode_Linux:                      ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=XTU38dTS_ab9spwTvpoS/tIscW1cEZ4_FYhZT9--s/rnZgQWeXEf8iSO27byEG/NCSGoAu2cVloCgbx3OL6, BuildID[sha1]=94ef5d44b81e7be0892157860100badc06b30cbe, stripped
./tailscale/tailscaled_amd_geode_Linux.upx:                  ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=XTU38dTS_ab9spwTvpoS/tIscW1cEZ4_FYhZT9--s/rnZgQWeXEf8iSO27byEG/NCSGoAu2cVloCgbx3OL6, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_Linux:                     ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=_7aHzSbINt8U-7aal4KV/jio6APNmVYxIeIZkrKRE/lUrKhZFyG0goF2KRA5Ol/yXJqaT22If5OOJtesmxs, BuildID[sha1]=5d88bea66e8933134c77d311b2481e0a206dc523, stripped
./tailscale/tailscaled_amd_x86_64_Linux.upx:                 ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=_7aHzSbINt8U-7aal4KV/jio6APNmVYxIeIZkrKRE/lUrKhZFyG0goF2KRA5Ol/yXJqaT22If5OOJtesmxs, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_macOS:                     Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_arm_abi_Linux:                        ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=V1wLOscCe0H3xeGWGAlm/aKqZrbOsjzDju3BD45mG/VHCZYJv7YsF0J_677BGG/P1jhtHk4vmGsiw5xX2_M, BuildID[sha1]=1bea1bb04da9ceeb5be61e1adb8a146a979cbc24, with debug_info, not stripped
./tailscale/tailscaled_arm_abi_Linux.upx:                    ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=V1wLOscCe0H3xeGWGAlm/aKqZrbOsjzDju3BD45mG/VHCZYJv7YsF0J_677BGG/P1jhtHk4vmGsiw5xX2_M, statically linked, no section header
./tailscale/tailscaled_i386_Linux:                           ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=G7RAHHJ4PcanVZs3b8Du/VaLZplkwrGKoj0DC7eM2/seggFDK1m9XfE0UaH4R4/0q_67bmUAjox13tta-n2, BuildID[sha1]=47c2ae2e2803ef4ad080356d1f82da4370be6921, stripped
./tailscale/tailscaled_i386_Linux.upx:                       ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=G7RAHHJ4PcanVZs3b8Du/VaLZplkwrGKoj0DC7eM2/seggFDK1m9XfE0UaH4R4/0q_67bmUAjox13tta-n2, statically linked, no section header
./tailscale/tailscaled_mips64_Linux:                         ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=eKfj0kA74a2vNGamd7Gn/Kh5iyXhH8CNe7VsvWA9k/7-MYyRNlAKzKoOP-gUKJ/b-WsHQxA8LsJlbMRB1Jh, BuildID[sha1]=45d8143d154c58dcbc62332765d66fc69b0094dd, with debug_info, not stripped
./tailscale/tailscaled_mips64le_Linux:                       ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=SahvCw_Aed_HG8NZDJ1B/PydZIq6uW-LYqZUS8cRB/DF1AP6traQCx6C_2QDNC/X2bAE8jWJ41ZhGc_QCO5, BuildID[sha1]=badacb2254b715eb245f98969f18eb10dec4eb16, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux:                           ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=3AYxPExN5gVfBiYvgE-i/nW5-sYHUIOx1GaJmiook/ntSQOjZ9hz0AzC8tMHLv/G_SQfeAs4bGZjgbtZkOh, BuildID[sha1]=d11299e39f9c19f739407f44fee49f06b1631bcb, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux.upx:                       ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=3AYxPExN5gVfBiYvgE-i/nW5-sYHUIOx1GaJmiook/ntSQOjZ9hz0AzC8tMHLv/G_SQfeAs4bGZjgbtZkOh, statically linked, no section header
./tailscale/tailscaled_mipsle_Linux:                         ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=AoW7vlMSnXfMOf8778ir/4p5PY0NhUpviBwnPkIVF/bs5VawhobNFkdOPp8NjK/WokoIeeo1wICWDtrDGWW, BuildID[sha1]=4f8be2b26621cdb564d790117fb08a3ca4ce5df8, with debug_info, not stripped
./tailscale/tailscaled_mipsle_Linux.upx:                     ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=AoW7vlMSnXfMOf8778ir/4p5PY0NhUpviBwnPkIVF/bs5VawhobNFkdOPp8NjK/WokoIeeo1wICWDtrDGWW, statically linked, no section header
./tailscale/tailscaled_powerpc64_ppc64_Linux:                ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64_ppc64_Linux.upx:            ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_powerpc64le_ppc64le_Linux:            ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx:        ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_riscv64_Linux:                        ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, Go BuildID=aqNdyUQFYip3WT5_WLlE/xbeM9yImmTkLInggFPiK/DPH7MJSCa9UoxIlhpxB4/Vas2GG6JhZLlc8el4bQ7, BuildID[sha1]=950b8130ef4d42e6aa6f27fdbe52e8c2c652813c, with debug_info, not stripped
./tailscale/tailscaled_s390x_Linux:                          ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped

--> SHA256SUM
e0878697480a584bd9d87caec62c80585c9bd87cea3267716c1b903a23ac29c7  ./tailscale/tailscale_aarch64_arm64_Linux
47352ae867fac92e8d81234f0b9bb8d4e87673ed422949729571c3a08d790339  ./tailscale/tailscale_aarch64_arm64_Linux.upx
f9103f09d52ea009ec2cd325cc992c9afe9ade60aa3eefadf2df7869e385882a  ./tailscale/tailscale_aarch64_arm64_Windows.msi
758bd296723a348a70f5274b294baeb4053abd2e2ce58e2220e210946b618c6f  ./tailscale/tailscale_aarch64_arm64_macOS
b14f18307dff2af8644a77bb6c2e01d0783c11ea00c4a182bf1146e6c9a24b9f  ./tailscale/tailscale_amd_geode_Linux
4b9e3da548916ce55f6f0fb50c6577f11a6ce995149887dc4aaabdcbebead01f  ./tailscale/tailscale_amd_geode_Linux.upx
5f0433066d14630836a153a72658a43ad8b03491d113ba72fb657e09122bef09  ./tailscale/tailscale_amd_x86_64_Linux
d965c5744aeefd4ff96d55d976738791e264d3852127432147f67784345abb51  ./tailscale/tailscale_amd_x86_64_Linux.upx
b501e3eef74dab81ab1731e759f82c600e77ba227750f9cf26357e0a59e26ed5  ./tailscale/tailscale_amd_x86_64_Windows.msi
248b7930c0c4c650f988bcb90a968da042066e0b826bf58efd8fe3a69fad8e7f  ./tailscale/tailscale_amd_x86_64_macOS
d568e85972c8d6bd126bfc188aa299abf35a8a1a8657641d857a4c5aadf8d48e  ./tailscale/tailscale_arm_abi_Linux
aee41d2faffb74391e8bc289f0f0a57a9a48836bc4322cc97fe4e0337729b5dd  ./tailscale/tailscale_arm_abi_Linux.upx
ea1b1930f400ac48a011f0dba89c24e168867b805724139c6f87570645e268df  ./tailscale/tailscale_i386_Linux
373eb5cf6986baebd6393094ddcf06f2dbce527b5ca1c10b07cc871fdf47faf8  ./tailscale/tailscale_i386_Linux.upx
b9fe0e5ea5fd581744e5554d48a748992fce69fb4fc2b8a8233b7a1db0bb47d5  ./tailscale/tailscale_ipn_setup_Windows.exe
6ae77960447d743344d204f2a02145a471733b313d78acb95d609ec3bc3e94d2  ./tailscale/tailscale_merged_aarch64_arm64_Linux
96a8f56fc95b628281c5f5e7f945d046f41d8036ec408c293f8a3848a618a64d  ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
68728bde1313493eb44dbd3be2e989eb00f60f4938d0d2845df9d45e32c25df7  ./tailscale/tailscale_merged_aarch64_arm64_macOS
dbf1dddd959835f6a1868d82ab0671e0c50f7e92b82562e8a1c2dc11bff471d1  ./tailscale/tailscale_merged_amd_x86_64_Linux
f3c424c428fe2b750b04857fda5fd35ab126ba0d6c8adb273c0da16aebb31128  ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
267bebcfe539dd8353add30caf55a042bf996f8e688aae7910b9ecf61714f3f8  ./tailscale/tailscale_merged_amd_x86_64_macOS
aee91f09fa4d984dfbc9d97d870987061f2aebf0d429b3b758d3dc115a81ce2a  ./tailscale/tailscale_merged_arm_Linux
8939582512d98e2e86e3a2fe532c0cb2e5358c048cc61fcfcfcc0458de12d4f3  ./tailscale/tailscale_merged_arm_Linux.upx
6cc29c115afea3550b24ae7a21a9d4cd1fc4b90892dcef9649b34d0acceb0590  ./tailscale/tailscale_merged_i386_Linux
9fb5a98ae512441776246d097e4fc42f4753628103c0154167a08ac2527fa8b2  ./tailscale/tailscale_merged_i386_Linux.upx
576f43e8ea9e810506a822751d57dc98854e8dc91e41423346cc7cb99d4a0b83  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux
c5485544f3e5031b5cfe013c1841a36e34f5031e296a65731a5d85cc9c03abc4  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
7a2ef02c0b8602230ef2d5318b52bcc19af5fb26162b47b4c02e0538b3e118bd  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux
570828b78cc40f6ef7a6535f888788bcb7e6931fbf6b64b675b442339dd144a3  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
d69f5e7d8b1a78701ea07b7b672faaa0b074309005b1126ebd38397292a3312e  ./tailscale/tailscale_merged_s390x_Linux
b50c35c423cc3c5aa0b44e02aa19629ea1e9605e5a19767b81beeb1cfe165d30  ./tailscale/tailscale_mips64_Linux
904b021955b0e5d17b2a3f7ab81e6d99adb762725efffeccabaf747c0e073f45  ./tailscale/tailscale_mips64le_Linux
e5abdd016f254ada8ef13c2d4ea21e39808d411347d3a5c5b02065a9ed37b0e3  ./tailscale/tailscale_mips_Linux
a53e1244a0c8995c6381b2c46c396f9c40c635d0a075eb7cd5869550147d38ce  ./tailscale/tailscale_mips_Linux.upx
87db6247155a8a3feed1a51d9e0c692497dfcb400e365c2ef096a23e54f0c6ee  ./tailscale/tailscale_mipsle_Linux
6720852d926da4435e0b014bce420e57eb9109f0f87d5f3922ee4559aaa45f08  ./tailscale/tailscale_mipsle_Linux.upx
6419d32c65e42776da8425d561858fc458d4bc6e6937f5cd1ce34c4b72451a56  ./tailscale/tailscale_powerpc64_ppc64_Linux
93148454b3ed39a662df2e2b353bdcb620a259d158eeb264fd1adc2768ade4d8  ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
4c5e21bb78e6f41c0035a88d7a0563e88c6e0416cc30b50817569bf80498961a  ./tailscale/tailscale_powerpc64le_ppc64le_Linux
a25d3951c96d99b37544738460f1b490940eafec8f079f3039c838c0b37177b1  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
b8545b990b770d806c56c778611f5dac8b889c859257b0d3636ab7cb9a1ca5d0  ./tailscale/tailscale_riscv64_Linux
2d87f55466cbd0e123277609eabfcc131c506aa43be4fd25ae5f2206a21679b7  ./tailscale/tailscale_s390x_Linux
64a8ad28cbb67a6171236abe39f75a039a761a0e1aacdef75b26781887cef9a8  ./tailscale/tailscale_setup_Windows.exe
53a5d27da631829eac86195ae61da539d6b5f9c260420ac9b6b1349467063b46  ./tailscale/tailscale_x86_Windows.msi
d49b1b9f0870b453093a92b72519483d946a03726ab72e80650665f99d7c2c6b  ./tailscale/tailscaled_aarch64_arm64_Linux
2aba65571464efa7e2014d93f6cea11f7758a420ee0c527804db1721d889d47f  ./tailscale/tailscaled_aarch64_arm64_Linux.upx
3045786fe6191b3d64ae9d2b03b5fffcf080e3cb3073a3c2e8e69e57ea05e2cf  ./tailscale/tailscaled_aarch64_arm64_macOS
a56c867b7a6f6789d815414c189cdb6217e4f05c09affea86a861086ce71242e  ./tailscale/tailscaled_amd_geode_Linux
bfd8b3b71dc02271b9742f64c102bb7d66155f95edf451beae9a9e48c615d744  ./tailscale/tailscaled_amd_geode_Linux.upx
8ff4072c20f65cdcd07182db8ef9efe140e685459d508f2ee5b86b21942db662  ./tailscale/tailscaled_amd_x86_64_Linux
df42db259f79ffbc092d3bde735c0663e7d0a51188e6246147b74f256a74ab62  ./tailscale/tailscaled_amd_x86_64_Linux.upx
b5304b43985998d94d5c2c94e0eeb9e160a76906fa0ecb224af45c3b878e684d  ./tailscale/tailscaled_amd_x86_64_macOS
5026e496ab712a45ea8d72f4e943db471ad05241c5c48743d53ea4c832e73612  ./tailscale/tailscaled_arm_abi_Linux
e8cbb27ddc0915c6a4c0e6ed5f83774fa93b7134097ffab94a6ffb128bdd7c19  ./tailscale/tailscaled_arm_abi_Linux.upx
26bbd9d05c7f50b2567697648a5210ff9c33fa688480b4dc4ba7d7923c49d52a  ./tailscale/tailscaled_i386_Linux
69ce7d38301a2a81bb5643e98ba00e34ba577a2c887d578d918f8483a720160b  ./tailscale/tailscaled_i386_Linux.upx
8f2861ad3ae31a421bdfa663804f0c95170b4800930211e12be7a356dcb628a1  ./tailscale/tailscaled_mips64_Linux
0897edc6306b0c809e8dbef2e05df35ccbe29e4d5bf5ef9dec76656e8225f675  ./tailscale/tailscaled_mips64le_Linux
309a29c188eb370b34dedd8b6f3f5dafaa4c041f2ccf8590944fa5b13246fa79  ./tailscale/tailscaled_mips_Linux
2e15757c96535c206c3823bcf05d12b3d70a8f0abe44163248d8145decbec827  ./tailscale/tailscaled_mips_Linux.upx
d186b5374259a5f0efb6db19e98dc7a62c11fe9c7789d49cb641ad422c407b7d  ./tailscale/tailscaled_mipsle_Linux
98d0426d55434cc78ef2f5d4effd99a4fbe058524ddf462012f5d7464a17e126  ./tailscale/tailscaled_mipsle_Linux.upx
86dd20b9cb4eafc136d4d78aa6eabe2a3563ba72e6cbd28aa5e57fe3543a845f  ./tailscale/tailscaled_powerpc64_ppc64_Linux
af14336de8b8794f1448251d2c6295b75f01481677dcd86c69aceff97def88c9  ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
d11c23390e08f3f68be42d48668eacba932e67582731ca914854f8b19ae839af  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux
f59da17c1082a66e596809f46ba198ef79ae08be3fab9eff24823aff6825da7a  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
c3825630b690e00b526baec5a2ac23940e77b28ce8ac17d5a3a1f5a72727c5dd  ./tailscale/tailscaled_riscv64_Linux
2463108cc308d84553c75ed1ddbe80f102d7419f5f4b84e84808254ace790868  ./tailscale/tailscaled_s390x_Linux
```


---

- #### Sizes

```console
28M   ./tailscale/tailscale_aarch64_arm64_Linux
12M   ./tailscale/tailscale_aarch64_arm64_Linux.upx
33M   ./tailscale/tailscale_aarch64_arm64_Windows.msi
11M   ./tailscale/tailscale_aarch64_arm64_macOS
20M   ./tailscale/tailscale_amd_geode_Linux
5.1M  ./tailscale/tailscale_amd_geode_Linux.upx
21M   ./tailscale/tailscale_amd_x86_64_Linux
5.9M  ./tailscale/tailscale_amd_x86_64_Linux.upx
35M   ./tailscale/tailscale_amd_x86_64_Windows.msi
11M   ./tailscale/tailscale_amd_x86_64_macOS
28M   ./tailscale/tailscale_arm_abi_Linux
12M   ./tailscale/tailscale_arm_abi_Linux.upx
20M   ./tailscale/tailscale_i386_Linux
5.5M  ./tailscale/tailscale_i386_Linux.upx
50K   ./tailscale/tailscale_ipn_setup_Windows.exe
32M   ./tailscale/tailscale_merged_aarch64_arm64_Linux
7.6M  ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
20M   ./tailscale/tailscale_merged_aarch64_arm64_macOS
35M   ./tailscale/tailscale_merged_amd_x86_64_Linux
9.2M  ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
20M   ./tailscale/tailscale_merged_amd_x86_64_macOS
32M   ./tailscale/tailscale_merged_arm_Linux
7.4M  ./tailscale/tailscale_merged_arm_Linux.upx
33M   ./tailscale/tailscale_merged_i386_Linux
8.6M  ./tailscale/tailscale_merged_i386_Linux.upx
34M   ./tailscale/tailscale_merged_powerpc64_ppc64_Linux
7.5M  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
34M   ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux
7.8M  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
36M   ./tailscale/tailscale_merged_s390x_Linux
32M   ./tailscale/tailscale_mips64_Linux
31M   ./tailscale/tailscale_mips64le_Linux
31M   ./tailscale/tailscale_mips_Linux
12M   ./tailscale/tailscale_mips_Linux.upx
31M   ./tailscale/tailscale_mipsle_Linux
12M   ./tailscale/tailscale_mipsle_Linux.upx
21M   ./tailscale/tailscale_powerpc64_ppc64_Linux
4.7M  ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
21M   ./tailscale/tailscale_powerpc64le_ppc64le_Linux
4.9M  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
28M   ./tailscale/tailscale_riscv64_Linux
22M   ./tailscale/tailscale_s390x_Linux
51M   ./tailscale/tailscale_setup_Windows.exe
34M   ./tailscale/tailscale_x86_Windows.msi
37M   ./tailscale/tailscaled_aarch64_arm64_Linux
15M   ./tailscale/tailscaled_aarch64_arm64_Linux.upx
19M   ./tailscale/tailscaled_aarch64_arm64_macOS
24M   ./tailscale/tailscaled_amd_geode_Linux
6.7M  ./tailscale/tailscaled_amd_geode_Linux.upx
27M   ./tailscale/tailscaled_amd_x86_64_Linux
7.6M  ./tailscale/tailscaled_amd_x86_64_Linux.upx
19M   ./tailscale/tailscaled_amd_x86_64_macOS
33M   ./tailscale/tailscaled_arm_abi_Linux
14M   ./tailscale/tailscaled_arm_abi_Linux.upx
24M   ./tailscale/tailscaled_i386_Linux
6.7M  ./tailscale/tailscaled_i386_Linux.upx
38M   ./tailscale/tailscaled_mips64_Linux
38M   ./tailscale/tailscaled_mips64le_Linux
37M   ./tailscale/tailscaled_mips_Linux
14M   ./tailscale/tailscaled_mips_Linux.upx
37M   ./tailscale/tailscaled_mipsle_Linux
14M   ./tailscale/tailscaled_mipsle_Linux.upx
25M   ./tailscale/tailscaled_powerpc64_ppc64_Linux
5.8M  ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
25M   ./tailscale/tailscaled_powerpc64le_ppc64le_Linux
6.1M  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
34M   ./tailscale/tailscaled_riscv64_Linux
26M   ./tailscale/tailscaled_s390x_Linux
```

---

- #### UPX
```console

testing ./tailscale/tailscale_i386_Linux.upx [OK]
  20455588 ->   5711096   27.92%   linux/i386    ./tailscale/tailscale_i386_Linux.upx
testing ./tailscale/tailscale_merged_amd_x86_64_Linux.upx [OK]
  35999870 ->   9617832   26.72%   linux/amd64   ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_amd_geode_Linux.upx [OK]
  20508836 ->   5258296   25.64%   linux/i386    ./tailscale/tailscale_amd_geode_Linux.upx
testing ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx [OK]
  33423486 ->   7885616   23.59%   linux/arm64   ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_powerpc64_ppc64_Linux.upx [OK]
  20971646 ->   4910368   23.41%   linux/ppc64   ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_mipsle_Linux.upx [OK]
  31797200 ->  11768800   37.01%  linux/mipsel   ./tailscale/tailscale_mipsle_Linux.upx
testing ./tailscale/tailscale_amd_x86_64_Linux.upx [OK]
  21977800 ->   6133156   27.91%   linux/amd64   ./tailscale/tailscale_amd_x86_64_Linux.upx
testing ./tailscale/tailscaled_mips_Linux.upx [OK]
  38478680 ->  14475280   37.62%   linux/mips    ./tailscale/tailscaled_mips_Linux.upx
testing ./tailscale/tailscaled_aarch64_arm64_Linux.upx [OK]
  37926256 ->  15605456   41.15%   linux/arm64   ./tailscale/tailscaled_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_merged_arm_Linux.upx [OK]
  33292414 ->   7707164   23.15%    linux/arm    ./tailscale/tailscale_merged_arm_Linux.upx
testing ./tailscale/tailscaled_amd_geode_Linux.upx [OK]
  24366476 ->   6999204   28.72%   linux/i386    ./tailscale/tailscaled_amd_geode_Linux.upx
testing ./tailscale/tailscale_arm_abi_Linux.upx [OK]
  28886960 ->  11706128   40.52%    linux/arm    ./tailscale/tailscale_arm_abi_Linux.upx
testing ./tailscale/tailscaled_i386_Linux.upx [OK]
  24333708 ->   6990928   28.73%   linux/i386    ./tailscale/tailscaled_i386_Linux.upx
testing ./tailscale/tailscale_aarch64_arm64_Linux.upx [OK]
  29189938 ->  11932928   40.88%   linux/arm64   ./tailscale/tailscale_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx [OK]
  35192958 ->   8127432   23.09%  linux/ppc64le  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx [OK]
  20971646 ->   5118648   24.41%  linux/ppc64le  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_merged_i386_Linux.upx [OK]
  33726590 ->   8992644   26.66%   linux/i386    ./tailscale/tailscale_merged_i386_Linux.upx
testing ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx [OK]
  25297022 ->   6297884   24.90%  linux/ppc64le  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscaled_amd_x86_64_Linux.upx [OK]
  28170424 ->   7907660   28.07%   linux/amd64   ./tailscale/tailscaled_amd_x86_64_Linux.upx
testing ./tailscale/tailscaled_arm_abi_Linux.upx [OK]
  34557592 ->  14319628   41.44%    linux/arm    ./tailscale/tailscaled_arm_abi_Linux.upx
testing ./tailscale/tailscaled_mipsle_Linux.upx [OK]
  38315032 ->  14447712   37.71%  linux/mipsel   ./tailscale/tailscaled_mipsle_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx [OK]
  35192958 ->   7838356   22.27%   linux/ppc64   ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx [OK]
  25362558 ->   6068300   23.93%   linux/ppc64   ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_mips_Linux.upx [OK]
  32006708 ->  11797384   36.86%   linux/mips    ./tailscale/tailscale_mips_Linux.upx

```

---

- #### Version
```console
$ ./tailscale/tailscale_amd_x86_64_Linux --version
1.96.4
  tailscale commit: 8cf541dfd1e0a97096c01cb775d5e26336f3bc6c
  long version: 1.96.4-t8cf541dfd-g62bc84ce7
  other commit: 62bc84ce7236dafdeb40272171dae03a66502ed1
  go version: go1.26.1

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
1.96.4
  tailscale commit: 8cf541dfd1e0a97096c01cb775d5e26336f3bc6c
  long version: 1.96.4-t8cf541dfd-g62bc84ce7
  other commit: 62bc84ce7236dafdeb40272171dae03a66502ed1
  go version: go1.26.1

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


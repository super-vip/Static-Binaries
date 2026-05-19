
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
./tailscale/tailscale_aarch64_arm64_Linux:                   ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=mAvAAXGZ6eqyOva1ESZU/uIyntp2v3oVHvZx9pd9z/6ZKkzTOgj734FpLD95Rx/GrALdowsdDGtvk-6iqE4, BuildID[sha1]=acba4e936ed79b512130e2ac209d0b515842cc34, with debug_info, not stripped
./tailscale/tailscale_aarch64_arm64_Linux.upx:               ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=mAvAAXGZ6eqyOva1ESZU/uIyntp2v3oVHvZx9pd9z/6ZKkzTOgj734FpLD95Rx/GrALdowsdDGtvk-6iqE4, statically linked, no section header
./tailscale/tailscale_aarch64_arm64_Windows.msi:             Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Arm64;1033, Revision Number: {054740BD-16FD-47E7-A9EF-1D0EEC5D0982}, Create Time/Date: Thu May 14 17:21:43 2026, Last Saved Time/Date: Thu May 14 17:21:43 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscale_aarch64_arm64_macOS:                   Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_amd_geode_Linux:                       ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=qg3O5HZA3w4L4ZQgoskj/u7I3QzmqoIpsfzaWQPj5/8m7J1z8aok8tUcdNWBH4/cuQxEd_Qnrd7msjuceuV, BuildID[sha1]=569e0195c22859276f5f2f1de98bffe91564d70d, stripped
./tailscale/tailscale_amd_geode_Linux.upx:                   ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=qg3O5HZA3w4L4ZQgoskj/u7I3QzmqoIpsfzaWQPj5/8m7J1z8aok8tUcdNWBH4/cuQxEd_Qnrd7msjuceuV, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Linux:                      ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=mPqaeRd7V-DZiKmXTwHj/QauXrd0xWo431Fu6LWjo/kdSun_faNOhWSnXCBpNZ/3EWD1oMlajCBK9rhzTOD, BuildID[sha1]=c24a73d54137ceeca57c05a59a3a9004fe3973f1, stripped
./tailscale/tailscale_amd_x86_64_Linux.upx:                  ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=mPqaeRd7V-DZiKmXTwHj/QauXrd0xWo431Fu6LWjo/kdSun_faNOhWSnXCBpNZ/3EWD1oMlajCBK9rhzTOD, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Windows.msi:                Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: x64;1033, Revision Number: {3315BB15-3DEC-41E8-BA73-0035FEB2E885}, Create Time/Date: Thu May 14 17:22:15 2026, Last Saved Time/Date: Thu May 14 17:22:15 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscale_amd_x86_64_macOS:                      Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_arm_abi_Linux:                         ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=grTnVikgp2q3nUSHYghk/4WxWRAs2sf2f1Gsh4B3K/rd_z-xtZdQBb17O_-oqq/RDOQSs4ZppJJ5NOwhrEl, BuildID[sha1]=8d5948c3ba828569bfb609fd77c6042f3d80eff2, with debug_info, not stripped
./tailscale/tailscale_arm_abi_Linux.upx:                     ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=grTnVikgp2q3nUSHYghk/4WxWRAs2sf2f1Gsh4B3K/rd_z-xtZdQBb17O_-oqq/RDOQSs4ZppJJ5NOwhrEl, statically linked, no section header
./tailscale/tailscale_i386_Linux:                            ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=d08I2ZmdC-1NuTcvFfsG/rrk91tMHdSMnsY7CWkd_/NquiivxZMQnIS_fptfgp/Inns2q1F1JqfXoliypR9, BuildID[sha1]=4ca2ecbc7633ab1e4c9b822112e667044955c722, stripped
./tailscale/tailscale_i386_Linux.upx:                        ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=d08I2ZmdC-1NuTcvFfsG/rrk91tMHdSMnsY7CWkd_/NquiivxZMQnIS_fptfgp/Inns2q1F1JqfXoliypR9, statically linked, no section header
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
./tailscale/tailscale_mips64_Linux:                          ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=pQ0YI_q9FQlCUWiyArSI/lMItwnm4qxFGCvAucB6U/sqAgnWYYDJdU6d5-w749/gaiVGUa_4e5bM7_EBui_, BuildID[sha1]=c8a41edc623e4572fbbf82dc6d9ba7de55b9f127, with debug_info, not stripped
./tailscale/tailscale_mips64le_Linux:                        ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=el2Y0qq8wvxRGuTJImf2/BWY8FYFciqvN_CsKy34H/Jjp2QAzxWv78y0WehN-i/AoMNQKdJjxMHOxBJXEb6, BuildID[sha1]=a3634e2120250d765da18733c4709207dbf6c88f, with debug_info, not stripped
./tailscale/tailscale_mips_Linux:                            ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=kGUUCAjejYViRltE4mSJ/wrcqplJL1q9g3th7xN-A/o9ROBSz1IdowMW43MJQr/g4rbcT6_i98dP0IgK7eV, BuildID[sha1]=50f5398800971bdb2dbc475884a27fa19fa8fb0a, with debug_info, not stripped
./tailscale/tailscale_mips_Linux.upx:                        ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=kGUUCAjejYViRltE4mSJ/wrcqplJL1q9g3th7xN-A/o9ROBSz1IdowMW43MJQr/g4rbcT6_i98dP0IgK7eV, statically linked, no section header
./tailscale/tailscale_mipsle_Linux:                          ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=STsYK9RAIWTreIOQk6VO/kLbxf38NXXmDFspyVesX/C3teTkW32ZpAFGJKBMtF/EpN4nYpXpe_-sg0P8y9f, BuildID[sha1]=9d930c4ca1b67f971078a8a47759ec6971ee54a1, with debug_info, not stripped
./tailscale/tailscale_mipsle_Linux.upx:                      ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=STsYK9RAIWTreIOQk6VO/kLbxf38NXXmDFspyVesX/C3teTkW32ZpAFGJKBMtF/EpN4nYpXpe_-sg0P8y9f, statically linked, no section header
./tailscale/tailscale_powerpc64_ppc64_Linux:                 ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64_ppc64_Linux.upx:             ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_powerpc64le_ppc64le_Linux:             ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx:         ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_riscv64_Linux:                         ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, Go BuildID=Jf0LVtXRt0LBVWrVQIeI/WXpkdQBN8b9Hg_42XAS-/nq0jm1LJgHfr_IITBB2x/YIriKCaBeCs-nAaJKkx7, BuildID[sha1]=a7b38c4303b97f129667dad4613c5cd42d7f5112, with debug_info, not stripped
./tailscale/tailscale_s390x_Linux:                           ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_setup_Windows.exe:                     PE32 executable (GUI) Intel 80386, for MS Windows, 6 sections
./tailscale/tailscale_x86_Windows.msi:                       Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Intel;1033, Revision Number: {5BA1C700-70F6-450F-B5F7-6DCCB312D90E}, Create Time/Date: Thu May 14 17:21:43 2026, Last Saved Time/Date: Thu May 14 17:21:43 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscaled_aarch64_arm64_Linux:                  ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=EUnL5rdfys29dj_QJRsH/JAUJXPrO8sN_Kb06uP74/h4Pgzp_NZiHJOZHVUOYp/m-MANUXOX9FJcg4n_BZi, BuildID[sha1]=0a88c67fe17ddab4a21430bbdef75a7788c31a2d, with debug_info, not stripped
./tailscale/tailscaled_aarch64_arm64_Linux.upx:              ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=EUnL5rdfys29dj_QJRsH/JAUJXPrO8sN_Kb06uP74/h4Pgzp_NZiHJOZHVUOYp/m-MANUXOX9FJcg4n_BZi, statically linked, no section header
./tailscale/tailscaled_aarch64_arm64_macOS:                  Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_amd_geode_Linux:                      ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=YF-4PvGmPyrDT_MUbyG5/SBW8C2m9jc_MHGBz9yqv/qYFC6rxRvzKvFt2Sb71H/sSEf7HRMxvkac0O46W3d, BuildID[sha1]=dfc0c73dd1a07efd583197058ab136082ec1e98b, stripped
./tailscale/tailscaled_amd_geode_Linux.upx:                  ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=YF-4PvGmPyrDT_MUbyG5/SBW8C2m9jc_MHGBz9yqv/qYFC6rxRvzKvFt2Sb71H/sSEf7HRMxvkac0O46W3d, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_Linux:                     ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=2S-x6WuShPrknBnxzATz/AzzYEO_ttzqtO-5_lw_A/SOz-b-Ye2x42h0uubU4W/zgkUpLXKLzCUcw2LB2zZ, BuildID[sha1]=cefac17aff0f625f456d9cdb73435f81d34bb629, stripped
./tailscale/tailscaled_amd_x86_64_Linux.upx:                 ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=2S-x6WuShPrknBnxzATz/AzzYEO_ttzqtO-5_lw_A/SOz-b-Ye2x42h0uubU4W/zgkUpLXKLzCUcw2LB2zZ, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_macOS:                     Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_arm_abi_Linux:                        ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=WFC_aBRcqtBG677X0qBz/NidWQojWtRjEN3RqLBgy/Qxh7FUIuza7NsccKaNsk/PnWejnIVNYiSfaAyl9LM, BuildID[sha1]=4555fd8f7bf2373761d4c48201e87ded35bf94f7, with debug_info, not stripped
./tailscale/tailscaled_arm_abi_Linux.upx:                    ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=WFC_aBRcqtBG677X0qBz/NidWQojWtRjEN3RqLBgy/Qxh7FUIuza7NsccKaNsk/PnWejnIVNYiSfaAyl9LM, statically linked, no section header
./tailscale/tailscaled_i386_Linux:                           ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=erLWT_8Ujp6ukpxt0Nfs/MXBmojc7eTK8rF8jLhwv/-SB98eeEbwJ3BA0V-4_W/4CytS14AMGbXRbMw11R0, BuildID[sha1]=dd381e99518d2cf5498d5b257a1109aa4db31adf, stripped
./tailscale/tailscaled_i386_Linux.upx:                       ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=erLWT_8Ujp6ukpxt0Nfs/MXBmojc7eTK8rF8jLhwv/-SB98eeEbwJ3BA0V-4_W/4CytS14AMGbXRbMw11R0, statically linked, no section header
./tailscale/tailscaled_mips64_Linux:                         ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=3JXqzFXMeXh4Alx3zrng/7QCrdWBgZncgQ3n5-i-h/2DHVIadkdTh3CXtSqpq9/FQA7BO45tlqYf0v0eC5w, BuildID[sha1]=b734e3da477c958f40d0fd437c47cba4d38ce650, with debug_info, not stripped
./tailscale/tailscaled_mips64le_Linux:                       ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=KrKfCJ9EJO3Urzh96KBv/HqTRJGnZeNo_wzCZ77C9/WtnyCnvlhDZgTI54CNMq/JhwULANf-6D27NYpoIEa, BuildID[sha1]=b3cc6b93398ba07220b3909176d2a36d777207b6, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux:                           ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=pJ-quLiqc3XPzT4Ds5qP/7azY-noAuitYerdXMAcR/wWgyoPsV_x48UE58IsvA/H3plqmZfKAc6i7QHNQ9u, BuildID[sha1]=51504b017b6c6026ee2418f3c16b19c6e752cd71, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux.upx:                       ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=pJ-quLiqc3XPzT4Ds5qP/7azY-noAuitYerdXMAcR/wWgyoPsV_x48UE58IsvA/H3plqmZfKAc6i7QHNQ9u, statically linked, no section header
./tailscale/tailscaled_mipsle_Linux:                         ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=o4xlVjBi91CXR8aPSwz9/QhVFThQZeD6po8fiW-se/KlfJDAEq9fTtuTvvEdtB/yJGjp4-dmZ48Iqa47k3X, BuildID[sha1]=45c195e7572a12cc3aa629e010b30975227016e8, with debug_info, not stripped
./tailscale/tailscaled_mipsle_Linux.upx:                     ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=o4xlVjBi91CXR8aPSwz9/QhVFThQZeD6po8fiW-se/KlfJDAEq9fTtuTvvEdtB/yJGjp4-dmZ48Iqa47k3X, statically linked, no section header
./tailscale/tailscaled_powerpc64_ppc64_Linux:                ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64_ppc64_Linux.upx:            ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_powerpc64le_ppc64le_Linux:            ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx:        ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_riscv64_Linux:                        ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, Go BuildID=d_dScwf7PN3ZdvbcfF1M/NWthy0XoIpCfIbs3oYRl/8RHPUR8xz3c5a8VIAkoE/IyRuD_y2rJ_3Pb5M92S6, BuildID[sha1]=627b1302e200260a1924c781e5173ee2b9a3939c, with debug_info, not stripped
./tailscale/tailscaled_s390x_Linux:                          ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped

--> SHA256SUM
dce9f04cf4c416c2156b7667ec60057e7ee9da484b4b7c3c820fbf9a72b6e67b  ./tailscale/tailscale_aarch64_arm64_Linux
fe7031ba0732e918aabc126f2e5bd164afaafeef734db97b1ad46254e1686e23  ./tailscale/tailscale_aarch64_arm64_Linux.upx
caa77b70367cfe8f99513c72f43a4c768d83255ba1b1408d95b462635eb132e0  ./tailscale/tailscale_aarch64_arm64_Windows.msi
758bd296723a348a70f5274b294baeb4053abd2e2ce58e2220e210946b618c6f  ./tailscale/tailscale_aarch64_arm64_macOS
65c191f8de557dcf603ecd3d2e932a05bbda8d6e41f62429a36b36ba66535f37  ./tailscale/tailscale_amd_geode_Linux
710aa79f64d16cdcd70504d48995b45a0d79008a08be092de26ad38f6020062f  ./tailscale/tailscale_amd_geode_Linux.upx
0be3adace0f54a2cc2c68513f0a45d5989bc65b8a869c63e1fe2e1e9356b8c49  ./tailscale/tailscale_amd_x86_64_Linux
00e894568220f092eaf02cebc67b4115df011d05b5a0e8eb9951ea8c561b508e  ./tailscale/tailscale_amd_x86_64_Linux.upx
89eb44e18f1af3e6e4aa998ec161d3996158fe3e0c0b9f1bf745c74eb420f84e  ./tailscale/tailscale_amd_x86_64_Windows.msi
248b7930c0c4c650f988bcb90a968da042066e0b826bf58efd8fe3a69fad8e7f  ./tailscale/tailscale_amd_x86_64_macOS
245ebbb38244e71c4dfac0ec0d9ca5de65334b9e86ba3d8685f6bde611a2827d  ./tailscale/tailscale_arm_abi_Linux
afb8100673d127a20a90f68215727992b8a33c1f1ed8b84d4f1ba359dcb6ffa8  ./tailscale/tailscale_arm_abi_Linux.upx
46e61367e9d966eb8e3d8d256532aa65ac05a629895d7e82863e98cd606bcda1  ./tailscale/tailscale_i386_Linux
6119753053f6c2b7e0dc368e30999c9323dd417b484b477be1b497d2b4dbb5c2  ./tailscale/tailscale_i386_Linux.upx
982fecdb01b031bb94010f39eb7dc432ff55fff4b0b7642090b25682f81a3412  ./tailscale/tailscale_ipn_setup_Windows.exe
356c706db5cab0ba77ce6d68452d4f2ab2d81afb474b6ddd527e7ce473a92262  ./tailscale/tailscale_merged_aarch64_arm64_Linux
024c69e179696469718c9882158c0b9709bddd174c201acfc8418bb68910a843  ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
68728bde1313493eb44dbd3be2e989eb00f60f4938d0d2845df9d45e32c25df7  ./tailscale/tailscale_merged_aarch64_arm64_macOS
79766f75ed4565ef7ac137b3138180d5e26b598da8871785d7f9138951b03253  ./tailscale/tailscale_merged_amd_x86_64_Linux
ab7dcb159fc9c8a465c06b7cbef1519086e388c5172104efcb5bdfd00f578959  ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
267bebcfe539dd8353add30caf55a042bf996f8e688aae7910b9ecf61714f3f8  ./tailscale/tailscale_merged_amd_x86_64_macOS
ca2d4abadbd50d454232e28f4c796cc52bfb78eda420eccf516053afe1a7e5e6  ./tailscale/tailscale_merged_arm_Linux
ea6873d0fd47f0028f8022482ff5be89c2e1bb7b9790fb065ac36662d6e6b0f1  ./tailscale/tailscale_merged_arm_Linux.upx
2609b0667f15e2782e72fe8a5dfbb104c1ef738e249102f065fe3b2b8e057f01  ./tailscale/tailscale_merged_i386_Linux
17f6b010d6b0936988938d797001674d8e1f9cded4a4f255e7ac284329370502  ./tailscale/tailscale_merged_i386_Linux.upx
bd0dc1310731dd45eb5ef932d5814e08b1be620d42fea8c13a057b7ac4d11a5e  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux
2338ae80488b45285b159b64f69893374cd666a762d6e288321710f9aee8ece1  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
94411d9cc4740ec6c64ae246eca0ae7d3c98e7d3fa92f1e5748912fb71497065  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux
db0f054d52eb0b98f73c5eebd5d50588515f9e579a28287c94127514f6ed548c  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
7193f8357cc584fbfdd9bfb7e29a448f909bfdb4230d8d255a5aab6955267045  ./tailscale/tailscale_merged_s390x_Linux
0bbb8d4b771de88d1ffc47be527baac8d6f7909f69f6a0533cf9a37dee50eaff  ./tailscale/tailscale_mips64_Linux
c296d41acf23822db656d04a7127bcbf3b0f0414e6745dd13f9c4a053abffedf  ./tailscale/tailscale_mips64le_Linux
1bce3099091af18d84c60896bea0d6ac194cc7e27552a6875377d58c7c91b63f  ./tailscale/tailscale_mips_Linux
12eb01824fc80fb510f86d177b9312979ceed98978f6bb98fa4a6071bc52cc71  ./tailscale/tailscale_mips_Linux.upx
70322f9538a8c642372f76ff8c346734650e88e44dd47181f3d2636df272ebdd  ./tailscale/tailscale_mipsle_Linux
f148aadd91b64563c2908933299fbcd1e0d9d090afe680e889adc874d3c36094  ./tailscale/tailscale_mipsle_Linux.upx
66ba34ad1af96ef9bbf493b61a2f839b5d4e1006b03b0bffa71093153a425c2b  ./tailscale/tailscale_powerpc64_ppc64_Linux
afa27a6faf0009921b59e2edbc06dcb697340b1c6c8e2fdce7f0e9906474dedc  ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
f3759585836dd11ea9e79d9a5da9362c6445c71423db894a6264d41dbab15649  ./tailscale/tailscale_powerpc64le_ppc64le_Linux
ca8b87ef8e4ba2c6b14dec3c525ccd4b1b26e06e7699501f35bd750bb33eb566  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
64f91dcc66be6575614946bef7c41012fba185730e4056bd669bfd94f20ee3a5  ./tailscale/tailscale_riscv64_Linux
5a1de4f1d451a6646ec1750144e9555328cf548362f1a328dd19959781bebbe9  ./tailscale/tailscale_s390x_Linux
64a8ad28cbb67a6171236abe39f75a039a761a0e1aacdef75b26781887cef9a8  ./tailscale/tailscale_setup_Windows.exe
ae94db837124c8f83351a04d31e6ed3de7d5d64f3c5e3641904acf05da6d9600  ./tailscale/tailscale_x86_Windows.msi
a2bb27de94d9e933c063427d1379fc0d5c0a4727e4d8afb0a2eec120d266e7d4  ./tailscale/tailscaled_aarch64_arm64_Linux
bb79a79ca8d87a15cf6cb68eb9e64aeb2e07e6d076fe7a50a66d6feb3354d502  ./tailscale/tailscaled_aarch64_arm64_Linux.upx
3045786fe6191b3d64ae9d2b03b5fffcf080e3cb3073a3c2e8e69e57ea05e2cf  ./tailscale/tailscaled_aarch64_arm64_macOS
8964e1bdcf1ecd8c76b47060f89a3fd3d622f3c93ce14d168173e87eadab0f31  ./tailscale/tailscaled_amd_geode_Linux
31477f429b69f7aa9abafe71dded806eadb51b2e75b7baed32dd60039e0922a7  ./tailscale/tailscaled_amd_geode_Linux.upx
44737ad41a5d9584f846c74ab8d8c348e522b15b915eb2b2675b5cecaa748a22  ./tailscale/tailscaled_amd_x86_64_Linux
ae9f49aa273674a72644408fb01e7cf98e62757c680313c99b7aca5ae41d47bb  ./tailscale/tailscaled_amd_x86_64_Linux.upx
b5304b43985998d94d5c2c94e0eeb9e160a76906fa0ecb224af45c3b878e684d  ./tailscale/tailscaled_amd_x86_64_macOS
3c7d1bd1d378a243be8c143172fa74bc1c14c330b3bf68980263adcfff0791ce  ./tailscale/tailscaled_arm_abi_Linux
3d534b28dafd2596f433453c4a0ff102c0bfa702275bdd88146bffb55e740c7c  ./tailscale/tailscaled_arm_abi_Linux.upx
1eeaf7d71177cca8e80602f5459ce6e7b45c10ce24d9348cd8dfe652e3d3c96d  ./tailscale/tailscaled_i386_Linux
41542fc9b20dccb81714277377d997f8a86ca514edbae067d57ff7690285f385  ./tailscale/tailscaled_i386_Linux.upx
c0b846a1f7f046bc319dcab157a84938dabb512339cb8a84015c77a494243a82  ./tailscale/tailscaled_mips64_Linux
62e85b97fe29531f56bb92d273d53c52e75aad43d2a2473198382da640db1dab  ./tailscale/tailscaled_mips64le_Linux
f7bede1c335b1767eca71768210b9d2739022c2c53a807ccc256d4cd2105e7d7  ./tailscale/tailscaled_mips_Linux
9077d38071182bc617b5a3777b1daf22a65e4331364e57489af8e804cf84b33b  ./tailscale/tailscaled_mips_Linux.upx
48ab212f68a05eaca06cf8c0f25bec5a81c66f2cab001d9e7266c78ae349f992  ./tailscale/tailscaled_mipsle_Linux
34180f4b4794521c16854bd4943b991f905afcd377ca48b542d2f4aedea009ec  ./tailscale/tailscaled_mipsle_Linux.upx
97475a78a4fef97befdefec44956742072cc88400471633ae39f20b6e6b4cc2f  ./tailscale/tailscaled_powerpc64_ppc64_Linux
f732b5510e2d13ff0add518b5d943aeaecff77e3483d77ff1f0976cf7b2fb5e2  ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
67e340811784f11102416896ed440a3874b1d5a7c305a042a6b597ce109cb551  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux
dd14ec2e010f0043b6e11960d0b54a6f41e33b86918ccfd5356e6c6798bd5671  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
dd5e7fd0672c1cb6d648e0c0b406847034e598ae4652c38b0f28ec9282931bd9  ./tailscale/tailscaled_riscv64_Linux
1a60ec89e18d20daf64b6d6d970b1ad6cd27100658be0bd3e7b151d81a2288a7  ./tailscale/tailscaled_s390x_Linux
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
  29579212 ->  12088028   40.87%   linux/arm64   ./tailscale/tailscale_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_merged_arm_Linux.upx [OK]
  33882238 ->   7831364   23.11%    linux/arm    ./tailscale/tailscale_merged_arm_Linux.upx
testing ./tailscale/tailscale_mipsle_Linux.upx [OK]
  32243494 ->  11917012   36.96%  linux/mipsel   ./tailscale/tailscale_mipsle_Linux.upx
testing ./tailscale/tailscale_merged_amd_x86_64_Linux.upx [OK]
  36728958 ->   9791484   26.66%   linux/amd64   ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
testing ./tailscale/tailscaled_mips_Linux.upx [OK]
  39035620 ->  14683200   37.61%   linux/mips    ./tailscale/tailscaled_mips_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx [OK]
  35913854 ->   8262232   23.01%  linux/ppc64le  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscaled_amd_geode_Linux.upx [OK]
  24736140 ->   7094640   28.68%   linux/i386    ./tailscale/tailscaled_amd_geode_Linux.upx
testing ./tailscale/tailscaled_mipsle_Linux.upx [OK]
  38868796 ->  14655076   37.70%  linux/mipsel   ./tailscale/tailscaled_mipsle_Linux.upx
testing ./tailscale/tailscaled_aarch64_arm64_Linux.upx [OK]
  38489097 ->  15815896   41.09%   linux/arm64   ./tailscale/tailscaled_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx [OK]
  21364862 ->   5189648   24.29%  linux/ppc64le  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx [OK]
  34078846 ->   8024632   23.55%   linux/arm64   ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_powerpc64_ppc64_Linux.upx [OK]
  21364862 ->   4980316   23.31%   linux/ppc64   ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_amd_geode_Linux.upx [OK]
  20771716 ->   5319572   25.61%   linux/i386    ./tailscale/tailscale_amd_geode_Linux.upx
testing ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx [OK]
  25690238 ->   6393432   24.89%  linux/ppc64le  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_amd_x86_64_Linux.upx [OK]
  22278248 ->   6207300   27.86%   linux/amd64   ./tailscale/tailscale_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_merged_i386_Linux.upx [OK]
  34394238 ->   9144828   26.59%   linux/i386    ./tailscale/tailscale_merged_i386_Linux.upx
testing ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx [OK]
  25690238 ->   6157484   23.97%   linux/ppc64   ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_mips_Linux.upx [OK]
  32392610 ->  11951792   36.90%   linux/mips    ./tailscale/tailscale_mips_Linux.upx
testing ./tailscale/tailscaled_amd_x86_64_Linux.upx [OK]
  28590232 ->   8009336   28.01%   linux/amd64   ./tailscale/tailscaled_amd_x86_64_Linux.upx
testing ./tailscale/tailscaled_arm_abi_Linux.upx [OK]
  35040728 ->  14513452   41.42%    linux/arm    ./tailscale/tailscaled_arm_abi_Linux.upx
testing ./tailscale/tailscaled_i386_Linux.upx [OK]
  24699276 ->   7086012   28.69%   linux/i386    ./tailscale/tailscaled_i386_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx [OK]
  35913854 ->   7970200   22.19%   linux/ppc64   ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_i386_Linux.upx [OK]
  20718468 ->   5777396   27.89%   linux/i386    ./tailscale/tailscale_i386_Linux.upx
testing ./tailscale/tailscale_arm_abi_Linux.upx [OK]
  29259786 ->  11844448   40.48%    linux/arm    ./tailscale/tailscale_arm_abi_Linux.upx

```

---

- #### Version
```console
$ ./tailscale/tailscale_amd_x86_64_Linux --version
1.98.2
  tailscale commit: aaf7caef13becf6989e9e81f66412f3edc564c38
  long version: 1.98.2-taaf7caef1-gc4a37aed9
  other commit: c4a37aed97b8b6dcc3fb32d87281c069fd2359d7
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
1.98.2
  tailscale commit: aaf7caef13becf6989e9e81f66412f3edc564c38
  long version: 1.98.2-taaf7caef1-gc4a37aed9
  other commit: c4a37aed97b8b6dcc3fb32d87281c069fd2359d7
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


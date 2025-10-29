
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
./tailscale/tailscale_aarch64_arm64_Linux:                   ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, BuildID[sha1]=ac90a879cd6332b4b1a45c008db9057b9ae12995, with debug_info, not stripped
./tailscale/tailscale_aarch64_arm64_Linux.upx:               ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=VL5WAcvRbGZDkY9mjUCi/NAEj0JQoYq64WQf188p0/9YjKZsqDL0SgHaKAvJZe/va-iwVze7dXLs9Fh0KI8, statically linked, no section header
./tailscale/tailscale_aarch64_arm64_Windows.msi:             Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Arm64;1033, Revision Number: {5BF9D0CD-5F7F-4F74-A562-52F814D85DC0}, Create Time/Date: Tue Oct 28 19:51:05 2025, Last Saved Time/Date: Tue Oct 28 19:51:05 2025, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscale_aarch64_arm64_macOS:                   Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_amd_geode_Linux:                       ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, BuildID[sha1]=a6f89a8f1c3833fa0bfe5871d453fb3bf10d0eaa, stripped
./tailscale/tailscale_amd_geode_Linux.upx:                   ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=ZVEghU0K8t2qK64IBFNZ/ZWScLUHTer3zZVDHKH9j/3bIT878WraeMZyUzBBAS/Dhz6anU-Ar3qYuQuFx4w, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Linux:                      ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, BuildID[sha1]=688bc92b942a8abf621fe18ecf98329d4b71cc39, stripped
./tailscale/tailscale_amd_x86_64_Linux.upx:                  ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=eO2IX-HsnfAG8iLeXiwl/X8m5hdRGzC7H0zh8rpNI/o4HWgRRR0EEGKUkpG_CB/VZMiPeX7kuHE4VQL9K-i, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Windows.msi:                Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: x64;1033, Revision Number: {2D3D2669-7D19-4FDB-BF22-03D7F71FB592}, Create Time/Date: Tue Oct 28 19:51:33 2025, Last Saved Time/Date: Tue Oct 28 19:51:33 2025, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscale_amd_x86_64_macOS:                      Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_arm_abi_Linux:                         ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, BuildID[sha1]=c375bfc1bc7dbddf839319560c308a85a94390e6, with debug_info, not stripped
./tailscale/tailscale_arm_abi_Linux.upx:                     ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=5ebY5TqDp_zLukrC7bZ4/UvB7qaprQt0VAHWeOU3l/2mjqstHQdVvze_uCfwZ9/uPLALa4o3d7NIVPMKBWq, statically linked, no section header
./tailscale/tailscale_i386_Linux:                            ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, BuildID[sha1]=2185bc50a3d665c686eff7c7fc8a7a575bdc8077, stripped
./tailscale/tailscale_i386_Linux.upx:                        ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=fOlCDkBgxq2Dm-t5G4R2/VDcdJMevZmdwIPyzeSU4/SYgqZRBiH90zJ5Gr6zG4/T74xbikB1XdekeVncq_l, statically linked, no section header
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
./tailscale/tailscale_mips64_Linux:                          ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, BuildID[sha1]=acd8afd2e1c2ba4d3c7de788302c870c8337573b, with debug_info, not stripped
./tailscale/tailscale_mips64le_Linux:                        ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, BuildID[sha1]=04cfd73bca842c118fbb4b087edc23ae4382fc51, with debug_info, not stripped
./tailscale/tailscale_mips_Linux:                            ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, BuildID[sha1]=2cf1a0ee3b3fa30053dc439b9f52976bdafd755b, with debug_info, not stripped
./tailscale/tailscale_mips_Linux.upx:                        ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=yWHPYeJBFCYn-dDe-aGT/WU6V2su6U247pAkAxMCw/t8TwZsC6Ns_CZHz1Ea4v/feJXY0nvmtbO7GwHIf58, statically linked, no section header
./tailscale/tailscale_mipsle_Linux:                          ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, BuildID[sha1]=25cbb2f0c7bafec59ec997c6296833120f48c83a, with debug_info, not stripped
./tailscale/tailscale_mipsle_Linux.upx:                      ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=gsj1Wk2eY9ffgQ_rNr2u/GQ6xoNzGAPWnEu0u-Fix/KnExzT6pwI3uT74q_vrW/LPm-8lhl_EhY0W6zGFnq, statically linked, no section header
./tailscale/tailscale_powerpc64_ppc64_Linux:                 ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64_ppc64_Linux.upx:             ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_powerpc64le_ppc64le_Linux:             ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx:         ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_riscv64_Linux:                         ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, BuildID[sha1]=4cc8026c45b262e0dcc389d42487a4d2b7850fd1, with debug_info, not stripped
./tailscale/tailscale_s390x_Linux:                           ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_setup_Windows.exe:                     PE32 executable (GUI) Intel 80386, for MS Windows, 6 sections
./tailscale/tailscale_x86_Windows.msi:                       Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Intel;1033, Revision Number: {8A46FDD2-8FCA-4DCB-9CD4-B56CA49FEC40}, Create Time/Date: Tue Oct 28 19:51:05 2025, Last Saved Time/Date: Tue Oct 28 19:51:05 2025, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscaled_aarch64_arm64_Linux:                  ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, BuildID[sha1]=49961ae23ef73c026d897177c708a8be513cebe4, with debug_info, not stripped
./tailscale/tailscaled_aarch64_arm64_Linux.upx:              ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=0bjXF-UI2zA9K30kK3PN/y8b1VMuGOmeNCYw8c1KS/sby9ZdkyBJNjje-dMHy3/1C5KqE927YukTNvzkPCv, statically linked, no section header
./tailscale/tailscaled_aarch64_arm64_macOS:                  Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_amd_geode_Linux:                      ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, BuildID[sha1]=67ddf8523236b8d78dc1db846b0e7542e3b8370a, stripped
./tailscale/tailscaled_amd_geode_Linux.upx:                  ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=y9AMQAYGhDbN6RQamleY/gF0yJsWSjmwJXi_DzZj3/qXxNX5jbXDStoxo5n9m7/EhBSM9k_N6H6e-0Sk8kN, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_Linux:                     ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, BuildID[sha1]=56d0c4411f4783147e4eda4d923870785f85ea9b, stripped
./tailscale/tailscaled_amd_x86_64_Linux.upx:                 ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=Kaisk53gQLTxrRJwEgmx/NIbY9XaiQlB5sKyxSth6/SV9jOwVDJbGy_qV_G_AR/LrKuBXY2M3DBAHohyg4g, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_macOS:                     Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_arm_abi_Linux:                        ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, BuildID[sha1]=6f4ed1f3e4e2974079a9b997ecfb5dfb55915b0b, with debug_info, not stripped
./tailscale/tailscaled_arm_abi_Linux.upx:                    ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=_5fwTqyJlcpgM_FFv9jl/wDaH79MU9TevkHlzWxXC/Sk3pnxPFE_NM7XGaMOxR/lYXKOYcloTkZbndx_rfo, statically linked, no section header
./tailscale/tailscaled_i386_Linux:                           ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, BuildID[sha1]=eac2de3006f17cdb2ad8e7e9d30e035a058a52e0, stripped
./tailscale/tailscaled_i386_Linux.upx:                       ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=r-OZVIKrG04GuFDFMcWI/64aHFpd-joqq1pXVrtUj/P1h3G2fz47chm08vj6MI/WbOl9_HSVygIwRYS1AlS, statically linked, no section header
./tailscale/tailscaled_mips64_Linux:                         ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, BuildID[sha1]=05a00a7a00f5059661d8d7a4daa3f45ee5e19edb, with debug_info, not stripped
./tailscale/tailscaled_mips64le_Linux:                       ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, BuildID[sha1]=7483e7b1e4737daaed75f7c18531de9a7297bb4c, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux:                           ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, BuildID[sha1]=ab76a7711b52b9cf54e245bcc962754a43e7a6bd, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux.upx:                       ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=B3jLW8b23HMMrSQlLuBD/qcQ4XDIzsOjqlYsKMqKj/po_OkczFTsFKqvvf5GBY/TQ5M4l79utCR_Aoi3MoG, statically linked, no section header
./tailscale/tailscaled_mipsle_Linux:                         ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, BuildID[sha1]=92d7370b2acb94942ce6cdb0454ceac936295c83, with debug_info, not stripped
./tailscale/tailscaled_mipsle_Linux.upx:                     ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=JIf45Zi4zwUZ7EyBRYoG/jYrYOfeu-o7nazYDW25G/H1rzVETQcErjvVMuzBUK/8DZEU8CYQ37oltJB8p-r, statically linked, no section header
./tailscale/tailscaled_powerpc64_ppc64_Linux:                ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64_ppc64_Linux.upx:            ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_powerpc64le_ppc64le_Linux:            ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx:        ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_riscv64_Linux:                        ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, BuildID[sha1]=5d9753bf32ef65a08abe78134ec05025f479adf3, with debug_info, not stripped
./tailscale/tailscaled_s390x_Linux:                          ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped

--> SHA256SUM
8d320b6f3f94c3a0d5c234a8b8c0b175422cd774c53614841ccf5b0c307bae99  ./tailscale/tailscale_aarch64_arm64_Linux
7d1dbfb2099464c11a31d5f136fa7151688874b4c4ec179c52e3dfc53a8a14f5  ./tailscale/tailscale_aarch64_arm64_Linux.upx
b649a349ebd7e27a1d0a9fb836c3f662d3d985d3586684a820949cb5a87db479  ./tailscale/tailscale_aarch64_arm64_Windows.msi
758bd296723a348a70f5274b294baeb4053abd2e2ce58e2220e210946b618c6f  ./tailscale/tailscale_aarch64_arm64_macOS
fdae3c658efdbeb0f36169d03ec256e6faa9d36459416796c7487a847b81683b  ./tailscale/tailscale_amd_geode_Linux
638d8b40db917e63c80458c246876f122dc198fad129fd69e46853a67d9fe023  ./tailscale/tailscale_amd_geode_Linux.upx
691adccb9b98ac18472f6db8814c714198482b87c1e59cafeba1e831822efff2  ./tailscale/tailscale_amd_x86_64_Linux
1c4d9cd07b282c37f80fa96e50a4e84015b43f785d373985137a485448f71b46  ./tailscale/tailscale_amd_x86_64_Linux.upx
0dc65cc01efa31580d5b26f7ec07dbdfe9ff60d4d6a1881c7f4453a54a8b766b  ./tailscale/tailscale_amd_x86_64_Windows.msi
248b7930c0c4c650f988bcb90a968da042066e0b826bf58efd8fe3a69fad8e7f  ./tailscale/tailscale_amd_x86_64_macOS
e448831eff80d816bc5c491fbb06de2c82240672007f8513ca3542246e2cbdfb  ./tailscale/tailscale_arm_abi_Linux
0cdb7d05af4a79a45e34030ae32693c9caad77c95ed7c4340407126bd96da7fa  ./tailscale/tailscale_arm_abi_Linux.upx
cedd6ae059d79781cee631007e07a0556c2115869db8d0621832962f9d9992cd  ./tailscale/tailscale_i386_Linux
291715dd20f0d44a67f93e4631c3e99dccca6f564b2fa11151ff792ff5639825  ./tailscale/tailscale_i386_Linux.upx
d6aba685ad320414fdc07117fcdf0728faa913ff7558561e9ea7a49c33807ce6  ./tailscale/tailscale_ipn_setup_Windows.exe
91cfd4f9db9db5346084d11b6e12ccc96876e21e7aeb502d0101c0bf7c635ca0  ./tailscale/tailscale_merged_aarch64_arm64_Linux
2ade368bd82773ab2bcfcb7ff7e049451eca15e1dfda0712856bd67eee94a7ad  ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
68728bde1313493eb44dbd3be2e989eb00f60f4938d0d2845df9d45e32c25df7  ./tailscale/tailscale_merged_aarch64_arm64_macOS
e8ebef79fff468bb48331c1da5c3e4d239ca57371774c3176bea25bc5af03224  ./tailscale/tailscale_merged_amd_x86_64_Linux
0597ce8c394414060b12c771a6f192e013003db7a5280f4dc1d765e7e833d3fe  ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
267bebcfe539dd8353add30caf55a042bf996f8e688aae7910b9ecf61714f3f8  ./tailscale/tailscale_merged_amd_x86_64_macOS
2a4b7684f979dd85ff3a3cab3a97a28f0e4a42fa2d084c0e8f424f635a8ade7a  ./tailscale/tailscale_merged_arm_Linux
55012cab4c4561274fc468104a1a78bcf00f3bd32431ad306da20125be9a3ae3  ./tailscale/tailscale_merged_arm_Linux.upx
7d06401a0852b0a292c0d040795b9aa2ca6da6b502f70ff41496d61e940bad9c  ./tailscale/tailscale_merged_i386_Linux
d7622bc00b08556f22500b1b1652dc47ae4290ff34309b6919359bfb6b25fcf1  ./tailscale/tailscale_merged_i386_Linux.upx
a52d4acf1f8c04b3f11993aaee2b6a3828e95d6e2328d679716f41c3120cf4dc  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux
0e84e4ec16563cac5aeb68b6bc9cab71d7b7d2bba7d833217307f94a3e8aa024  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
d8bc6e4fc493695fefc694d2db5cef4f8d10b45e517ed4376230e505d2ad7b6d  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux
03d7e45435370df8b90db02bc70558f824121d8a20766bc08fdd23c2bd09a904  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
1d59126729dff5508e17bd82b8160f6b2aff828415664a99207153e7ffbdf5d3  ./tailscale/tailscale_merged_s390x_Linux
0885b8f30d88fbe0d444c15e5b2944a56ba908676d6308b01bbe1bdb64a0e168  ./tailscale/tailscale_mips64_Linux
cec0d6d6c8b01bd27582f69710fc3c120ba00bdc51b603fba32c7a5013c52fe8  ./tailscale/tailscale_mips64le_Linux
c5eec7037fb71ebb0bd720db69d8532542417e1d2982e972649e7f09b2f0fe07  ./tailscale/tailscale_mips_Linux
b6f59c189f31b84539fbcf10c97ba7a479f343678917b00e53e687f35cd3ae2d  ./tailscale/tailscale_mips_Linux.upx
889c9381f66645c9582b5272158a46b8973987b99d716857b4b319f8b0b705a1  ./tailscale/tailscale_mipsle_Linux
4ebc02c3d60fa8cdeb7fa44f3fa96c8b9364796f33c289472cb05f0cd3492d65  ./tailscale/tailscale_mipsle_Linux.upx
415e9c0d44ab8e8e42084c6d949d644f71874d410e4fb9fa807aa29b4ea5a6f5  ./tailscale/tailscale_powerpc64_ppc64_Linux
417afceb28ec65120468a308f907a41d0d8ade508515284fe7333de121702bde  ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
596a2a2229c573dab184c5e175d1449d83a236cfaaaeabc09c78d83e85105e93  ./tailscale/tailscale_powerpc64le_ppc64le_Linux
9124583795ae015d9fdbf1457304a13dc0766660357cdc7aae7bd3ff7bec3823  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
d6683323d1fc8f7cd0125e8ccea13fea2f0cab9670b407a1079d9bbc4fe3214a  ./tailscale/tailscale_riscv64_Linux
1a5c7dda0ac5bed40c48123047ae94da80df0b11fffbb148c5183e8bd0534638  ./tailscale/tailscale_s390x_Linux
64a8ad28cbb67a6171236abe39f75a039a761a0e1aacdef75b26781887cef9a8  ./tailscale/tailscale_setup_Windows.exe
4ed8eeecc5514ed1fcd8744db68739c4c30685466e53e8ae1b2c27e4d95c70c1  ./tailscale/tailscale_x86_Windows.msi
4557d079b81ed8f0748bfc5cdcfed0ebe42590fc2ae5f2703824368f1aa01119  ./tailscale/tailscaled_aarch64_arm64_Linux
9a20c1355ea34014b1abab2f47f4a9a3516468f172c609a7e453f5337dc25c81  ./tailscale/tailscaled_aarch64_arm64_Linux.upx
3045786fe6191b3d64ae9d2b03b5fffcf080e3cb3073a3c2e8e69e57ea05e2cf  ./tailscale/tailscaled_aarch64_arm64_macOS
1f366ea81caa8902c4411477f160aed18c51ec639a2314f9413e1422f7c26c18  ./tailscale/tailscaled_amd_geode_Linux
069de70ef881ed1b359da7236f1611c21a5163e720aa2201e0bff1532e4ab10d  ./tailscale/tailscaled_amd_geode_Linux.upx
f00bca71f9d13d30d63061b4cfe3a4da5c54a0ad170e7239b6094058370ed7f4  ./tailscale/tailscaled_amd_x86_64_Linux
3f750e520daa5a43c85c596b382c08a083544cf086947842d5812b566565c4cd  ./tailscale/tailscaled_amd_x86_64_Linux.upx
b5304b43985998d94d5c2c94e0eeb9e160a76906fa0ecb224af45c3b878e684d  ./tailscale/tailscaled_amd_x86_64_macOS
0baae90f97277eebd3497e4610c5b591ebc46d2c099b118fa3c1afced3710f8a  ./tailscale/tailscaled_arm_abi_Linux
66de58c719ddd7d4286285adaef03eaed6c1df8dedc3d7a3cdbe5ba8d003ca33  ./tailscale/tailscaled_arm_abi_Linux.upx
c738881a98bff03e1a68aba5910f76d6b537ba7d6dbb652196141d61652a9dd1  ./tailscale/tailscaled_i386_Linux
d218016fe77d042c2721189b282edb114887d1c577605350395a1c11682db850  ./tailscale/tailscaled_i386_Linux.upx
a37de3733fa8b1f77e0e541d0b90cd0fc461c45b6e7189f527aae46a2754e1b6  ./tailscale/tailscaled_mips64_Linux
7e0b11f050188cf13706d16a2edd0f7b3b680d81adf88e4af4db53f25b3d71d1  ./tailscale/tailscaled_mips64le_Linux
f40204ca2d6682687b0bdf347b34abe21f8362f80f77eacb11061f6e76066f89  ./tailscale/tailscaled_mips_Linux
4195e55799dac3864aa6c6ac1afd2c7a9fa2d5b450fc9b9d045b8768afd7d6ec  ./tailscale/tailscaled_mips_Linux.upx
772574af73d8e6e0c5d4858dd759b5f31930fd1725095ccd209eafa37dbf43eb  ./tailscale/tailscaled_mipsle_Linux
952c6835461d651e13d9f6009d5e7c4f9651e6c6f5f5f864be561d9445a5d351  ./tailscale/tailscaled_mipsle_Linux.upx
3af3e76d908d36714a5bfd041b21850d836ba9aa308c3b716c806516c4ffc4ce  ./tailscale/tailscaled_powerpc64_ppc64_Linux
e67d6a35e34b99cf348bf1f8137244db2977f1109406d67655e607bbf6d85331  ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
c2a56dcfe4f45f181ce6c4846b558eea6132cf0a7ee5c63421d737555e42ad47  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux
d2a975042dc9d0b23f4da0814417270706e2ac22db83e374a0a21264ae3bc33f  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
42ca07293bfcac44ca8e70d8e197d1a969ec1bdca12d213e1d5d68cd3921a23f  ./tailscale/tailscaled_riscv64_Linux
56e011667bc92cbcf9d66b0fc876004ee991dd96ea41d869822ee6abbb9e9744  ./tailscale/tailscaled_s390x_Linux
```


---

- #### Sizes

```console
24M   ./tailscale/tailscale_aarch64_arm64_Linux
9.9M  ./tailscale/tailscale_aarch64_arm64_Linux.upx
31M   ./tailscale/tailscale_aarch64_arm64_Windows.msi
11M   ./tailscale/tailscale_aarch64_arm64_macOS
17M   ./tailscale/tailscale_amd_geode_Linux
4.5M  ./tailscale/tailscale_amd_geode_Linux.upx
18M   ./tailscale/tailscale_amd_x86_64_Linux
5.2M  ./tailscale/tailscale_amd_x86_64_Linux.upx
34M   ./tailscale/tailscale_amd_x86_64_Windows.msi
11M   ./tailscale/tailscale_amd_x86_64_macOS
24M   ./tailscale/tailscale_arm_abi_Linux
9.9M  ./tailscale/tailscale_arm_abi_Linux.upx
17M   ./tailscale/tailscale_i386_Linux
4.9M  ./tailscale/tailscale_i386_Linux.upx
47K   ./tailscale/tailscale_ipn_setup_Windows.exe
29M   ./tailscale/tailscale_merged_aarch64_arm64_Linux
7.0M  ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
20M   ./tailscale/tailscale_merged_aarch64_arm64_macOS
31M   ./tailscale/tailscale_merged_amd_x86_64_Linux
8.4M  ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
20M   ./tailscale/tailscale_merged_amd_x86_64_macOS
29M   ./tailscale/tailscale_merged_arm_Linux
6.8M  ./tailscale/tailscale_merged_arm_Linux.upx
29M   ./tailscale/tailscale_merged_i386_Linux
7.9M  ./tailscale/tailscale_merged_i386_Linux.upx
31M   ./tailscale/tailscale_merged_powerpc64_ppc64_Linux
6.9M  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
31M   ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux
7.2M  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
33M   ./tailscale/tailscale_merged_s390x_Linux
27M   ./tailscale/tailscale_mips64_Linux
27M   ./tailscale/tailscale_mips64le_Linux
27M   ./tailscale/tailscale_mips_Linux
9.9M  ./tailscale/tailscale_mips_Linux.upx
26M   ./tailscale/tailscale_mipsle_Linux
9.9M  ./tailscale/tailscale_mipsle_Linux.upx
18M   ./tailscale/tailscale_powerpc64_ppc64_Linux
4.2M  ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
18M   ./tailscale/tailscale_powerpc64le_ppc64le_Linux
4.4M  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
25M   ./tailscale/tailscale_riscv64_Linux
19M   ./tailscale/tailscale_s390x_Linux
51M   ./tailscale/tailscale_setup_Windows.exe
33M   ./tailscale/tailscale_x86_Windows.msi
35M   ./tailscale/tailscaled_aarch64_arm64_Linux
15M   ./tailscale/tailscaled_aarch64_arm64_Linux.upx
19M   ./tailscale/tailscaled_aarch64_arm64_macOS
23M   ./tailscale/tailscaled_amd_geode_Linux
6.5M  ./tailscale/tailscaled_amd_geode_Linux.upx
26M   ./tailscale/tailscaled_amd_x86_64_Linux
7.3M  ./tailscale/tailscaled_amd_x86_64_Linux.upx
19M   ./tailscale/tailscaled_amd_x86_64_macOS
32M   ./tailscale/tailscaled_arm_abi_Linux
14M   ./tailscale/tailscaled_arm_abi_Linux.upx
23M   ./tailscale/tailscaled_i386_Linux
6.5M  ./tailscale/tailscaled_i386_Linux.upx
36M   ./tailscale/tailscaled_mips64_Linux
36M   ./tailscale/tailscaled_mips64le_Linux
36M   ./tailscale/tailscaled_mips_Linux
14M   ./tailscale/tailscaled_mips_Linux.upx
36M   ./tailscale/tailscaled_mipsle_Linux
14M   ./tailscale/tailscaled_mipsle_Linux.upx
24M   ./tailscale/tailscaled_powerpc64_ppc64_Linux
5.7M  ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
24M   ./tailscale/tailscaled_powerpc64le_ppc64le_Linux
5.9M  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
33M   ./tailscale/tailscaled_riscv64_Linux
26M   ./tailscale/tailscaled_s390x_Linux
```

---

- #### UPX
```console

testing ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx [OK]
  24510612 ->   5877676   23.98%   linux/ppc64   ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_merged_arm_Linux.upx [OK]
  29884564 ->   7050608   23.59%    linux/arm    ./tailscale/tailscale_merged_arm_Linux.upx
testing ./tailscale/tailscaled_arm_abi_Linux.upx [OK]
  33337258 ->  13827008   41.48%    linux/arm    ./tailscale/tailscaled_arm_abi_Linux.upx
testing ./tailscale/tailscaled_i386_Linux.upx [OK]
  23425156 ->   6746100   28.80%   linux/i386    ./tailscale/tailscaled_i386_Linux.upx
testing ./tailscale/tailscaled_mips_Linux.upx [OK]
  37098296 ->  13948472   37.60%   linux/mips    ./tailscale/tailscaled_mips_Linux.upx
testing ./tailscale/tailscale_merged_amd_x86_64_Linux.upx [OK]
  31973524 ->   8792024   27.50%   linux/amd64   ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_merged_i386_Linux.upx [OK]
  30072980 ->   8230968   27.37%   linux/i386    ./tailscale/tailscale_merged_i386_Linux.upx
testing ./tailscale/tailscale_amd_geode_Linux.upx [OK]
  17469732 ->   4714780   26.99%   linux/i386    ./tailscale/tailscale_amd_geode_Linux.upx
testing ./tailscale/tailscale_mipsle_Linux.upx [OK]
  27231199 ->  10353084   38.02%  linux/mipsel   ./tailscale/tailscale_mipsle_Linux.upx
testing ./tailscale/tailscale_amd_x86_64_Linux.upx [OK]
  18435048 ->   5415972   29.38%   linux/amd64   ./tailscale/tailscale_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx [OK]
  30015636 ->   7257012   24.18%   linux/arm64   ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx [OK]
  18153620 ->   4590500   25.29%  linux/ppc64le  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscaled_aarch64_arm64_Linux.upx [OK]
  36178203 ->  14863184   41.08%   linux/arm64   ./tailscale/tailscaled_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_aarch64_arm64_Linux.upx [OK]
  24670017 ->  10344616   41.93%   linux/arm64   ./tailscale/tailscale_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx [OK]
  31522964 ->   7183492   22.79%   linux/ppc64   ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_arm_abi_Linux.upx [OK]
  24814363 ->  10342308   41.68%    linux/arm    ./tailscale/tailscale_arm_abi_Linux.upx
testing ./tailscale/tailscale_i386_Linux.upx [OK]
  17416452 ->   5090300   29.23%   linux/i386    ./tailscale/tailscale_i386_Linux.upx
testing ./tailscale/tailscale_powerpc64_ppc64_Linux.upx [OK]
  18153620 ->   4402428   24.25%   linux/ppc64   ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_mips_Linux.upx [OK]
  27348695 ->  10376508   37.94%   linux/mips    ./tailscale/tailscale_mips_Linux.upx
testing ./tailscale/tailscaled_mipsle_Linux.upx [OK]
  36944712 ->  13924112   37.69%  linux/mipsel   ./tailscale/tailscaled_mipsle_Linux.upx
testing ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx [OK]
  24510612 ->   6103328   24.90%  linux/ppc64le  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx [OK]
  31522964 ->   7452576   23.64%  linux/ppc64le  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscaled_amd_x86_64_Linux.upx [OK]
  26849416 ->   7612212   28.35%   linux/amd64   ./tailscale/tailscaled_amd_x86_64_Linux.upx
testing ./tailscale/tailscaled_amd_geode_Linux.upx [OK]
  23466116 ->   6757416   28.80%   linux/i386    ./tailscale/tailscaled_amd_geode_Linux.upx

```

---

- #### Version
```console
$ ./tailscale/tailscale_amd_x86_64_Linux --version
1.90.4
  tailscale commit: 0d72986024458ffb250def1677a1430beb6b1c8b
  long version: 1.90.4-t0d7298602-g1c96c3ed9
  other commit: 1c96c3ed9ecd0d6130ec0f01f9e01091f02967e4
  go version: go1.25.3

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
  completion   Shell tab-completion scripts

FLAGS
  --socket value
    	path to tailscaled socket (default /var/run/tailscale/tailscaled.sock)

$ ./tailscale/tailscaled_amd_x86_64_Linux -version
1.90.4
  tailscale commit: 0d72986024458ffb250def1677a1430beb6b1c8b
  long version: 1.90.4-t0d7298602-g1c96c3ed9
  other commit: 1c96c3ed9ecd0d6130ec0f01f9e01091f02967e4
  go version: go1.25.3

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
    	use hardware-backed keys to bind node identity to this device when supported by the OS and hardware. Uses TPM 2.0 on Linux and Windows; SecureEnclave on macOS and iOS; and Keystore on Android
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


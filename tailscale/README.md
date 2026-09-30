
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
./tailscale/tailscale_aarch64_arm64_Linux:                   ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=vt8E_0PhI7vIPShwTBda/YE2N6_DVkSu6uW7HpFBD/HQ9uMhBUWehJN17teXKh/jWCtXX5XvIm4Y3jQn4yi, BuildID[sha1]=31062082624fefbfbe3cabd4bc5fdad9f572e83c, with debug_info, not stripped
./tailscale/tailscale_aarch64_arm64_Linux.upx:               ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=vt8E_0PhI7vIPShwTBda/YE2N6_DVkSu6uW7HpFBD/HQ9uMhBUWehJN17teXKh/jWCtXX5XvIm4Y3jQn4yi, statically linked, no section header
./tailscale/tailscale_aarch64_arm64_Windows.msi:             Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Arm64;1033, Revision Number: {01D74F77-8E50-4E46-BC68-AD721F1FDEB2}, Create Time/Date: Thu Sep 10 21:55:10 2026, Last Saved Time/Date: Thu Sep 10 21:55:10 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscale_aarch64_arm64_macOS:                   Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_amd_geode_Linux:                       ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=am7xF3iWAPP7wgBGZF7s/JN5BeV9NdBOpa0PNfdWH/rxtNfbL7VBjjwG0D3kBH/5pue2qM1NmqQaMwNxLHt, BuildID[sha1]=bd293c96f091840d031061e037ed01100311bfd9, stripped
./tailscale/tailscale_amd_geode_Linux.upx:                   ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=am7xF3iWAPP7wgBGZF7s/JN5BeV9NdBOpa0PNfdWH/rxtNfbL7VBjjwG0D3kBH/5pue2qM1NmqQaMwNxLHt, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Linux:                      ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=hhR7Dr-I2gAGww7v-iSH/qHBICNIc9rQwS16HSJwA/o_BnkNcotlXgeY5A3vff/PNs-ybo_urKEQUxos43e, BuildID[sha1]=1cd41efa5d6a30a85d4ab305e85724961fb70f09, stripped
./tailscale/tailscale_amd_x86_64_Linux.upx:                  ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=hhR7Dr-I2gAGww7v-iSH/qHBICNIc9rQwS16HSJwA/o_BnkNcotlXgeY5A3vff/PNs-ybo_urKEQUxos43e, statically linked, no section header
./tailscale/tailscale_amd_x86_64_Windows.msi:                Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: x64;1033, Revision Number: {1B991909-5B1A-4D43-8F6E-5B3416DB01F0}, Create Time/Date: Thu Sep 10 21:53:30 2026, Last Saved Time/Date: Thu Sep 10 21:53:30 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscale_amd_x86_64_macOS:                      Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscale_arm_abi_Linux:                         ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=4RBrpm7wxCZAuOtI_hwp/EbtReHB58yOJAp0IhCxc/5YlHD3vZve8ZsU_WbFOc/UobcCc-X_K0GlXGbQLlm, BuildID[sha1]=efea5df7609a237bcdb7100d7cbd552148ed7472, with debug_info, not stripped
./tailscale/tailscale_arm_abi_Linux.upx:                     ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=4RBrpm7wxCZAuOtI_hwp/EbtReHB58yOJAp0IhCxc/5YlHD3vZve8ZsU_WbFOc/UobcCc-X_K0GlXGbQLlm, statically linked, no section header
./tailscale/tailscale_i386_Linux:                            ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=q5i8xodLcYMZSUEken8w/jI3MwzgfkYAbm2B2kkIZ/8Pc3r8XdubPlNdAsuz5m/k2DW-gebMOYVHAMB1rpl, BuildID[sha1]=d6312bdc31b74691979644d4d240597b19cc436f, stripped
./tailscale/tailscale_i386_Linux.upx:                        ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=q5i8xodLcYMZSUEken8w/jI3MwzgfkYAbm2B2kkIZ/8Pc3r8XdubPlNdAsuz5m/k2DW-gebMOYVHAMB1rpl, statically linked, no section header
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
./tailscale/tailscale_mips64_Linux:                          ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=Jn7uZZgXnaBdweudE530/vq2sPGxINoPZoxD8DYI8/aUqIKokmxcwo_Qf_xF_s/7Yw8CBDvMW3i02yt-t5O, BuildID[sha1]=e4902189663a5b7fd4d8775af0476c827ac50112, with debug_info, not stripped
./tailscale/tailscale_mips64le_Linux:                        ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=nnFv1TxSIpvDvcDKDQhK/PFw4jX1ZlXGQY-7WPrWB/cACWSV9NRng1bhOUuifT/R_a3Cbuune9-R1W5YZxf, BuildID[sha1]=94c69397d12557a72dd61a7ef05ae5ab5779c848, with debug_info, not stripped
./tailscale/tailscale_mips_Linux:                            ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=aFLT23EgyzxtNrOyVhrX/syg1PfKHxdPk1M3OhhWd/By2LQmRrOCBJBvcJ3crV/H4Fm0j2-RWQnHZvVuWU3, BuildID[sha1]=3fb071cb715eb9d46d5c88172be84d304d1b0f0f, with debug_info, not stripped
./tailscale/tailscale_mips_Linux.upx:                        ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=aFLT23EgyzxtNrOyVhrX/syg1PfKHxdPk1M3OhhWd/By2LQmRrOCBJBvcJ3crV/H4Fm0j2-RWQnHZvVuWU3, statically linked, no section header
./tailscale/tailscale_mipsle_Linux:                          ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=RSiXBUcbAai9K8kjiceW/Qn9ug_V0eHUWJz55vYi0/DzDDqi-zraktTgp_ORBt/b3bJIzwycddAlzzg9Fda, BuildID[sha1]=2848df84c4681e14915846ebd20787b66dcc103c, with debug_info, not stripped
./tailscale/tailscale_mipsle_Linux.upx:                      ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=RSiXBUcbAai9K8kjiceW/Qn9ug_V0eHUWJz55vYi0/DzDDqi-zraktTgp_ORBt/b3bJIzwycddAlzzg9Fda, statically linked, no section header
./tailscale/tailscale_powerpc64_ppc64_Linux:                 ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64_ppc64_Linux.upx:             ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_powerpc64le_ppc64le_Linux:             ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx:         ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscale_riscv64_Linux:                         ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, Go BuildID=_IH1NvDFh7WdVwf5ISUK/w-6cs-D8xjikzM70lO0a/0bP07ueaINm3_p0OH3GC/QRqjtXePhya6u3qjVPza, BuildID[sha1]=814f58eb21e4543b48652e1527040eb2c482e4fc, with debug_info, not stripped
./tailscale/tailscale_s390x_Linux:                           ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped
./tailscale/tailscale_setup_Windows.exe:                     PE32 executable (GUI) Intel 80386, for MS Windows, 6 sections
./tailscale/tailscale_x86_Windows.msi:                       Composite Document File V2 Document, Little Endian, Os: Windows, Version 5.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: Tailscale is a zero config VPN for building secure networks. Install on any device in minutes. Remote access from any network or physical location. Built on WireGuard. WireGuard is a registered trademark of Jason A. Donenfeld., Author: Tailscale Inc., Keywords: Installer;Tailscale;vpn;security;privacy;wireguard;networking, Comments: This installer database contains the logic and data required to install Tailscale., Template: Intel;1033, Revision Number: {DBCF0178-89E3-445D-9036-484831A697BB}, Create Time/Date: Thu Sep 10 21:54:31 2026, Last Saved Time/Date: Thu Sep 10 21:54:31 2026, Number of Pages: 500, Number of Words: 2, Name of Creating Application: WiX Toolset (5.0.2.0), Security: 2
./tailscale/tailscaled_aarch64_arm64_Linux:                  ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, Go BuildID=UOJc95u58-PfETHR0oIn/P2iaMZaaYD11Ay5tpnQc/h-uWBA0uMvu0g8yW9Fgn/m_IWVQxR5iNX_i1eB90z, BuildID[sha1]=a87e75f404981184244f0e352cd4f36587cd2c32, with debug_info, not stripped
./tailscale/tailscaled_aarch64_arm64_Linux.upx:              ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), Go BuildID=UOJc95u58-PfETHR0oIn/P2iaMZaaYD11Ay5tpnQc/h-uWBA0uMvu0g8yW9Fgn/m_IWVQxR5iNX_i1eB90z, statically linked, no section header
./tailscale/tailscaled_aarch64_arm64_macOS:                  Mach-O 64-bit arm64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_amd_geode_Linux:                      ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=maGyGsRpLV1vbfsYUfPv/JPeRgExJ8EiPnmq_W5QY/P2fAqmwQoouZMhXM2ZAH/0wUP4dEfNcs5df76BRIV, BuildID[sha1]=717849f69d67340d9dfe0fd955ac8a0bfaf86b5e, stripped
./tailscale/tailscaled_amd_geode_Linux.upx:                  ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=maGyGsRpLV1vbfsYUfPv/JPeRgExJ8EiPnmq_W5QY/P2fAqmwQoouZMhXM2ZAH/0wUP4dEfNcs5df76BRIV, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_Linux:                     ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go BuildID=5tc2zRcQe8JCbyw7Toxb/Jsfl8g7M3t5-3UO3qjUK/WcXZGO17QeCEtW5EMDZS/LO57x666_KuNBbqhGEkJ, BuildID[sha1]=92309420122737a02c5e6b3ac0bdecfa6c876e91, stripped
./tailscale/tailscaled_amd_x86_64_Linux.upx:                 ELF 64-bit LSB executable, x86-64, version 1 (SYSV), Go BuildID=5tc2zRcQe8JCbyw7Toxb/Jsfl8g7M3t5-3UO3qjUK/WcXZGO17QeCEtW5EMDZS/LO57x666_KuNBbqhGEkJ, statically linked, no section header
./tailscale/tailscaled_amd_x86_64_macOS:                     Mach-O 64-bit x86_64 executable, flags:<|DYLDLINK|PIE>
./tailscale/tailscaled_arm_abi_Linux:                        ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, Go BuildID=zgldahuDItUkioUuNMZr/VGbYPbixSIAZB5o6vlGh/osjLpoRKIeFGZwPu84eJ/yl0sOfrN2MRGM--CjOex, BuildID[sha1]=0972c48764b628c497354c542e2b2257c258fdfd, with debug_info, not stripped
./tailscale/tailscaled_arm_abi_Linux.upx:                    ELF 32-bit LSB executable, ARM, EABI5 version 1 (GNU/Linux), Go BuildID=zgldahuDItUkioUuNMZr/VGbYPbixSIAZB5o6vlGh/osjLpoRKIeFGZwPu84eJ/yl0sOfrN2MRGM--CjOex, statically linked, no section header
./tailscale/tailscaled_i386_Linux:                           ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, Go BuildID=ewgYvlVUevaV2aodjvVi/OUQ306Bcg2nwkYFy1FCb/YTIKLgDhx8wDG6zpVrmL/38xnofC7rDrnoz4UZ2SM, BuildID[sha1]=4fd5d2482cc1e4edef7eb0fb8ca0697df6dcb37f, stripped
./tailscale/tailscaled_i386_Linux.upx:                       ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), Go BuildID=ewgYvlVUevaV2aodjvVi/OUQ306Bcg2nwkYFy1FCb/YTIKLgDhx8wDG6zpVrmL/38xnofC7rDrnoz4UZ2SM, statically linked, no section header
./tailscale/tailscaled_mips64_Linux:                         ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=l8rA-ExtZSs-QWB8UxXM/eqMg7CVCU0iXNjyHOXT_/iTaPLugMxZmts59nJo12/gJTEVL6uux8wYQEfmseo, BuildID[sha1]=3d4bf6f4bde2ce65cb5f6a1164e2c9f82dfbd781, with debug_info, not stripped
./tailscale/tailscaled_mips64le_Linux:                       ELF 64-bit LSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, Go BuildID=aiWiHl-yyO2BbuXC16mU/SVw5JTr8AAZ-LI6XnPsy/lO_2nDq3jMzh8MCKO6JU/hnGvhXjAvEG9jnHBHRaB, BuildID[sha1]=a2a6bd9b4b2706c2589f5ceac60f4950cb0d6935, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux:                           ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=SeT-E4z9GJA9DOXzl29l/2y6GzUG3bHk1a_fB0-FR/kHawqYu_5jSvwLe179tE/FRp7AiTwNXTU9MY8Ygrc, BuildID[sha1]=b51c20fdd9a94df41642402fa10a848bbe1f7144, with debug_info, not stripped
./tailscale/tailscaled_mips_Linux.upx:                       ELF 32-bit MSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=SeT-E4z9GJA9DOXzl29l/2y6GzUG3bHk1a_fB0-FR/kHawqYu_5jSvwLe179tE/FRp7AiTwNXTU9MY8Ygrc, statically linked, no section header
./tailscale/tailscaled_mipsle_Linux:                         ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), statically linked, Go BuildID=FJmLlfWo52r__PohQGXr/W9Yc0EOwaGWCnSFS-AsJ/Z6sxscmZRt25HagHOQPG/BFIRyPjPPDzwAfOUmiBo, BuildID[sha1]=474f446664c0be4f69e308d71713883d6a6f732b, with debug_info, not stripped
./tailscale/tailscaled_mipsle_Linux.upx:                     ELF 32-bit LSB executable, MIPS, MIPS32 version 1 (SYSV), Go BuildID=FJmLlfWo52r__PohQGXr/W9Yc0EOwaGWCnSFS-AsJ/Z6sxscmZRt25HagHOQPG/BFIRyPjPPDzwAfOUmiBo, statically linked, no section header
./tailscale/tailscaled_powerpc64_ppc64_Linux:                ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64_ppc64_Linux.upx:            ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, Power ELF V1 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_powerpc64le_ppc64le_Linux:            ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx:        ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, no section header
./tailscale/tailscaled_riscv64_Linux:                        ELF 64-bit LSB executable, UCB RISC-V, double-float ABI, version 1 (SYSV), statically linked, Go BuildID=xqcxvdc205kkV__xhesb/4NKRY6KdpeR82MspH4Zs/UwOEr2qmEYtS96j4EhPh/Mj_GOnoIlyuLbfBNkhHN, BuildID[sha1]=f1fb4ad295ff28a20c932c28c78c51b1575bd3e8, with debug_info, not stripped
./tailscale/tailscaled_s390x_Linux:                          ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped

--> SHA256SUM
93c3558f592200133b377dd9f96eac9b278b9057f7ae6b8656b15f4fa05506d0  ./tailscale/tailscale_aarch64_arm64_Linux
5c2b6a348497f86f17e474884bd93868573333e0d6ba9c1d5f20f94d271ca25b  ./tailscale/tailscale_aarch64_arm64_Linux.upx
b7dd1c03bf2e2c430f1fffc4e47ef92829c86d5190febbd9c025dcada5f410b6  ./tailscale/tailscale_aarch64_arm64_Windows.msi
758bd296723a348a70f5274b294baeb4053abd2e2ce58e2220e210946b618c6f  ./tailscale/tailscale_aarch64_arm64_macOS
327009aca2021ccda7e5071da53aae8246cf03b1356fcae32186bcb12d9b6488  ./tailscale/tailscale_amd_geode_Linux
03562e1bd152f5c02f1f16eaf6b81383109c5f517a48d5c853cac4ff5efbb96f  ./tailscale/tailscale_amd_geode_Linux.upx
4ffada3f4c792f905664c0ba485fa97fbeca9a2de003abdd77d67ada4f6ba736  ./tailscale/tailscale_amd_x86_64_Linux
4fbe7f9e91fabdde3e85846d05400bd8856e4e323ef84016002dade5a112df4e  ./tailscale/tailscale_amd_x86_64_Linux.upx
80eb007e39dfebe17299fa1a09c79a8e1d934f76e0246c0817ebe3af675b7ef6  ./tailscale/tailscale_amd_x86_64_Windows.msi
248b7930c0c4c650f988bcb90a968da042066e0b826bf58efd8fe3a69fad8e7f  ./tailscale/tailscale_amd_x86_64_macOS
0fb730c51955b471591d8740f594455e520db332e1cd4ae50e297d4e8b9cf954  ./tailscale/tailscale_arm_abi_Linux
a8dd8cf344603d30b281faa0194324a6fd2d7f97857db7d1d8909859880a1554  ./tailscale/tailscale_arm_abi_Linux.upx
5420128e462d08559ecfdbb976d89f408e085fc4350a84c019dca6006909c80f  ./tailscale/tailscale_i386_Linux
60a179af952f0802a9ff0482597cd090cfa75337a74c74bc5e4b7b84007186dd  ./tailscale/tailscale_i386_Linux.upx
d5997380249ff3a73d3151cabd895b8d272a4592032d79aa5d0273a1eec4d12e  ./tailscale/tailscale_ipn_setup_Windows.exe
973d57cc85f780cf9fdf27dbe4bc4f11b26d2beda16ee1beb38c07ab2958f24f  ./tailscale/tailscale_merged_aarch64_arm64_Linux
5e8101e64d85e63a30ec61bdcb81f0830e78d07406bec9fa12b2d4a9fa18db07  ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
68728bde1313493eb44dbd3be2e989eb00f60f4938d0d2845df9d45e32c25df7  ./tailscale/tailscale_merged_aarch64_arm64_macOS
a899087010a05573a1c459f6c4b8dc2060cd7f213ba7fb64acf726497532bc35  ./tailscale/tailscale_merged_amd_x86_64_Linux
84ab9cd964ba2656d741f1f22ada22fa025d351e7798dbfd6c8a84b468c96b32  ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
267bebcfe539dd8353add30caf55a042bf996f8e688aae7910b9ecf61714f3f8  ./tailscale/tailscale_merged_amd_x86_64_macOS
b5f4698f219429059ab35f44953a1eebd91b5b1c713ea9bbcd486fe141596a46  ./tailscale/tailscale_merged_arm_Linux
635d88cfcc347bbd0483cee30c01b9b9d5f34ed46e2baf7954ba2b4ab117c903  ./tailscale/tailscale_merged_arm_Linux.upx
8c48f27dff445d176a2b32b58cb26ec6f275b1b1a5c8612062eb35c9b0c12c26  ./tailscale/tailscale_merged_i386_Linux
38a1340aca54e7bb4ab56ac44257a78c974b7af44918225b6e81865b1318000c  ./tailscale/tailscale_merged_i386_Linux.upx
3754d614195eee1644456f35445786a6360b8195895ac70f14731de81c51abd4  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux
bc15d2dfb7ce7b508915e5f1dcd6e7bc1884e5d3d9644f00ce83ba4de14625da  ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
f31ce5b310b23171c308837b72684b7a6b0326c1c5d745ed8f6310c139ea16cc  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux
c449d76f7e96165b79f06d8293eb75ef770ecf4b91f4be980498884bc55cbb02  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
3a9a587a70469f33fde93713aebc8edf27773ec3f9fc03382f74f3ce3691fc61  ./tailscale/tailscale_merged_s390x_Linux
89be42d72570f0f2d44e47a3c9acb370f797abbb5ca90376d06fc9e14c86a10b  ./tailscale/tailscale_mips64_Linux
16904b2a2bae2636b1b873086ddd065a11d463269565dcd32163df5f381dbfd7  ./tailscale/tailscale_mips64le_Linux
e33b6256d33d3e1466b8054e25440679b8ee6862a7cf0a3863e209c6dacc46a1  ./tailscale/tailscale_mips_Linux
7d84e7353e211d553c6ce943592e044d4a214d4e91991dfa4e521bf9a179bb64  ./tailscale/tailscale_mips_Linux.upx
fb81a48e74dcef619f670a27993c2a4dc5fc22dbeb4d1dcff58fcf6b1714d9b2  ./tailscale/tailscale_mipsle_Linux
ced6ccd4908ff2d2ac6e19605e99f5d67c7232ae9ad0e1c89f705190f63f516f  ./tailscale/tailscale_mipsle_Linux.upx
af64ea6b3e2fbd1fd407d9a51ad027f07834c9ab1847cea5f977bd2013603790  ./tailscale/tailscale_powerpc64_ppc64_Linux
54d5317dc07431bc73a6b000083cc3e78bc19966585bd585f4fd217baf1451ad  ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
bdeb5e48f6654c395a1f336c78d7ed6475a99b1134eca50cdd3c45c32ff3b36f  ./tailscale/tailscale_powerpc64le_ppc64le_Linux
57e8cb15defc4ed82ba728f4e4fd283ec58567fff4609e100bba9cdf6497ee55  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
fe8fb09bba3b28b4e173a2481494469c8d663e9cdd3e1a90f06e15a9c6734aba  ./tailscale/tailscale_riscv64_Linux
cf734988ce0ebedbf609255cde0308c71fa60d5d24e83be2ab8c8a686a94e155  ./tailscale/tailscale_s390x_Linux
64a8ad28cbb67a6171236abe39f75a039a761a0e1aacdef75b26781887cef9a8  ./tailscale/tailscale_setup_Windows.exe
a8bda9fb254374bb13d46ebf02b6ffba4ed009a739580be511aa7afa8dddd42d  ./tailscale/tailscale_x86_Windows.msi
1ff5174fcbf3abbff85eacc73e6e548b0d094d913a48c1369f60811d1e92eeef  ./tailscale/tailscaled_aarch64_arm64_Linux
a1c7aed378c199a330ff1f4717010c773b501fee5ca806c913ed5d2e8613dd80  ./tailscale/tailscaled_aarch64_arm64_Linux.upx
3045786fe6191b3d64ae9d2b03b5fffcf080e3cb3073a3c2e8e69e57ea05e2cf  ./tailscale/tailscaled_aarch64_arm64_macOS
661adfde85eacd9145ff28643bbe99e171714907f7a7b9e48f41135242fc6898  ./tailscale/tailscaled_amd_geode_Linux
63e96ab194cea8a401ca23e1fccafd5ca29a2c75506426fb121d7e942c10d5c3  ./tailscale/tailscaled_amd_geode_Linux.upx
b1cf69f12de3f9ad88e4113664cee416e512cab22e914235d8c1fb2c8c88a792  ./tailscale/tailscaled_amd_x86_64_Linux
b0f1a25f781fd6e4c1c6623b13f4da3409c0704c56537da47ecc01b92100449f  ./tailscale/tailscaled_amd_x86_64_Linux.upx
b5304b43985998d94d5c2c94e0eeb9e160a76906fa0ecb224af45c3b878e684d  ./tailscale/tailscaled_amd_x86_64_macOS
1a2dfa6b9a68111514d69518aa10f619beecb53246317830cdafb3ea63399edb  ./tailscale/tailscaled_arm_abi_Linux
c637fa02a52302e7c621c5d3c483b34b21af1a7e008c7fe58e904c6c72fdaafe  ./tailscale/tailscaled_arm_abi_Linux.upx
e32e7aaec30789b9603ab2648c7fa872ea230413f46f66d9e5295a513e64f956  ./tailscale/tailscaled_i386_Linux
f10e4101655b2789a4f8025756b6e3a207cf98a5f6e1a0ad27eee99ce3950683  ./tailscale/tailscaled_i386_Linux.upx
2904bfcbed0d6de26b017d1af6b614fe216fcac90ce6856c3a901b75290c8672  ./tailscale/tailscaled_mips64_Linux
9b43ba642eda3ebe8bb2a423af0a0a11b2f4c272d55959ce61287953ccf2c9b9  ./tailscale/tailscaled_mips64le_Linux
60bef627d183965fb4d1132d9bfbc51c20879dc9ba39c96fe1e5c8491f9aa784  ./tailscale/tailscaled_mips_Linux
5356b2cd74ef45af5b5d0c1c3dbccc814b57cab6a020e591df6cfbbd2c819286  ./tailscale/tailscaled_mips_Linux.upx
2d9be3863d1c35a14b55ff59234801f9c9ca2e94bf1bd377b6e4e979dbea4a80  ./tailscale/tailscaled_mipsle_Linux
d97f918b107b495d5b001dad723c1fcf89ff5018eb587ce2821289b413ecc695  ./tailscale/tailscaled_mipsle_Linux.upx
5721929aaefec38bfcabb14f19906f001d148a2e19c992fb1337038cc0dcdb81  ./tailscale/tailscaled_powerpc64_ppc64_Linux
22868848eb76f709d8feb356daab4ad8bce22b3f8d93e4ab920062df013da77b  ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx
861ac9beddbb4ccd842e1681d6650bd330c1cb9de62ba141b9afc0265ab8514a  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux
24cf60fcb904ed84eb0ed0a69e634ee46e58f9baa899d9689748559e8f0d8b70  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
780cb77efcae2d59162e38a4ab7084a2d5da5fbb0073fc4c267a1ac78e2c48b8  ./tailscale/tailscaled_riscv64_Linux
6ef286e36924a022d8f5fd54ab6623ac6bbd69e1981487365063075424bf8898  ./tailscale/tailscaled_s390x_Linux
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

testing ./tailscale/tailscaled_amd_x86_64_Linux.upx [OK]
  29810776 ->   8336588   27.97%   linux/amd64   ./tailscale/tailscaled_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx [OK]
  37814398 ->   8359824   22.11%   linux/ppc64   ./tailscale/tailscale_merged_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_powerpc64_ppc64_Linux.upx [OK]
  22544510 ->   5214004   23.13%   linux/ppc64   ./tailscale/tailscale_powerpc64_ppc64_Linux.upx
testing ./tailscale/tailscale_merged_i386_Linux.upx [OK]
  36200574 ->   9586416   26.48%   linux/i386    ./tailscale/tailscale_merged_i386_Linux.upx
testing ./tailscale/tailscaled_mipsle_Linux.upx [OK]
  40615397 ->  15307900   37.69%  linux/mipsel   ./tailscale/tailscaled_mipsle_Linux.upx
testing ./tailscale/tailscale_mips_Linux.upx [OK]
  33765022 ->  12468608   36.93%   linux/mips    ./tailscale/tailscale_mips_Linux.upx
testing ./tailscale/tailscale_merged_amd_x86_64_Linux.upx [OK]
  38592638 ->  10248312   26.56%   linux/amd64   ./tailscale/tailscale_merged_amd_x86_64_Linux.upx
testing ./tailscale/tailscale_mipsle_Linux.upx [OK]
  33617930 ->  12446672   37.02%  linux/mipsel   ./tailscale/tailscale_mipsle_Linux.upx
testing ./tailscale/tailscaled_i386_Linux.upx [OK]
  25764300 ->   7374184   28.62%   linux/i386    ./tailscale/tailscaled_i386_Linux.upx
testing ./tailscale/tailscaled_mips_Linux.upx [OK]
  40783557 ->  15331216   37.59%   linux/mips    ./tailscale/tailscaled_mips_Linux.upx
testing ./tailscale/tailscaled_arm_abi_Linux.upx [OK]
  36576672 ->  15154848   41.43%    linux/arm    ./tailscale/tailscaled_arm_abi_Linux.upx
testing ./tailscale/tailscale_aarch64_arm64_Linux.upx [OK]
  30826067 ->  12603544   40.89%   linux/arm64   ./tailscale/tailscale_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_arm_abi_Linux.upx [OK]
  30568548 ->  12372828   40.48%    linux/arm    ./tailscale/tailscale_arm_abi_Linux.upx
testing ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx [OK]
  37814398 ->   8663704   22.91%  linux/ppc64le  ./tailscale/tailscale_merged_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx [OK]
  26935422 ->   6649176   24.69%  linux/ppc64le  ./tailscale/tailscaled_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscale_merged_arm_Linux.upx [OK]
  35717246 ->   8220184   23.01%    linux/arm    ./tailscale/tailscale_merged_arm_Linux.upx
testing ./tailscale/tailscale_amd_x86_64_Linux.upx [OK]
  23159496 ->   6463340   27.91%   linux/amd64   ./tailscale/tailscale_amd_x86_64_Linux.upx
testing ./tailscale/tailscaled_aarch64_arm64_Linux.upx [OK]
  40135967 ->  16492464   41.09%   linux/arm64   ./tailscale/tailscaled_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx [OK]
  22544510 ->   5432660   24.10%  linux/ppc64le  ./tailscale/tailscale_powerpc64le_ppc64le_Linux.upx
testing ./tailscale/tailscaled_amd_geode_Linux.upx [OK]
  25797068 ->   7383112   28.62%   linux/i386    ./tailscale/tailscaled_amd_geode_Linux.upx
testing ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx [OK]
  35848318 ->   8407480   23.45%   linux/arm64   ./tailscale/tailscale_merged_aarch64_arm64_Linux.upx
testing ./tailscale/tailscale_i386_Linux.upx [OK]
  21614596 ->   6025788   27.88%   linux/i386    ./tailscale/tailscale_i386_Linux.upx
testing ./tailscale/tailscale_amd_geode_Linux.upx [OK]
  21667876 ->   6036140   27.86%   linux/i386    ./tailscale/tailscale_amd_geode_Linux.upx
testing ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx [OK]
  26935422 ->   6407940   23.79%   linux/ppc64   ./tailscale/tailscaled_powerpc64_ppc64_Linux.upx

```

---

- #### Version
```console
$ ./tailscale/tailscale_amd_x86_64_Linux --version
1.102.4
  tailscale commit: 3caf7d9e7dcaba589cfc58beda596929733e4fea
  long version: 1.102.4-t3caf7d9e7-g084ee3b64
  other commit: 084ee3b64537a1276e56fc38cdf0a711da9f4936
  go version: go1.26.6 (tailscale/go 7275f792d4)

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
1.102.4
  tailscale commit: 3caf7d9e7dcaba589cfc58beda596929733e4fea
  long version: 1.102.4-t3caf7d9e7-g084ee3b64
  other commit: 084ee3b64537a1276e56fc38cdf0a711da9f4936
  go version: go1.26.6 (tailscale/go 7275f792d4)

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


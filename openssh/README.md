
---
- #### Download [openssh](https://www.openssh.com/)
> - **Sources**
> > ```bash
> > --> Linux:
> >      - https://github.com/Azathothas/static-toolbox
> > 
> > --> Windows:
> >      - https://github.com/PowerShell/Win32-OpenSSH/ [ Latest Beta Releases ]
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

!#For Linux
--> aarch64 || arm64 [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/openssh/sshd_aarch64_arm64_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/openssh/sshd_config_aarch64_arm64_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/openssh/sftp_server_aarch64_arm64_Linux"
--> Amd x86_64 || x86_64 [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/openssh/sshd_amd_x86_64_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/openssh/sshd_config_amd_x86_64_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/openssh/sftp_server_amd_x86_64_Linux"
--> ARMv7_eabihf [32-bit]
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/openssh/sshd_armv7_eabihf_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/openssh/sshd_config_armv7_eabihf_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/openssh/sftp_server_armv7_eabihf_Linux"

!#For Windows
--> x86
## msi
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/openssh/openssh_amd_x86_Windows.msi"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/openssh/openssh_amd_x86_Windows.zip"
!# Or using powershell
-->  Invoke-WebRequest -Uri "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/openssh/openssh_amd_x86_Windows.msi" -OutFile "openssh.msi"
-->  Invoke-WebRequest -Uri "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/openssh/openssh_amd_x86_Windows.zip" -OutFile "openssh.zip"
--> amd 64 || x86_64
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/openssh/openssh_amd_x86_64_Windows.msi"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/openssh/openssh_amd_x86_64_Windows.zip"
-->  Invoke-WebRequest -Uri "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/openssh/openssh_amd_x86_64_Windows.msi" -OutFile "openssh.msi"
-->  Invoke-WebRequest -Uri "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/openssh/openssh_amd_x86_64_Windows.zip" -OutFile "openssh.zip"
--> aarch || arm
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/openssh/openssh_arm_Windows.zip"
-->  Invoke-WebRequest -Uri "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/openssh/openssh_arm_Windows.zip" -OutFile "openssh.zip"
--> aarch64 || arm64
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/openssh/openssh_aarch64_arm64_Windows.msi"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/openssh/openssh_aarch64_arm64_Windows.zip"
-->  Invoke-WebRequest -Uri "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/openssh/openssh_aarch64_arm64_Windows.msi" -OutFile "openssh.msi"
-->  Invoke-WebRequest -Uri "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/openssh/openssh_aarch64_arm64_Windows.zip" -OutFile "openssh.zip"

```
---
- #### Install openssh
```bash
!# If have conda, then install via conda
 conda install -c conda-forge openssh


--> Linux 
!# Copy downloaded openssh binaries to /usr/bin || /usr/local/bin
!# For $HOME/bin
 mkdir -p "$HOME/bin" && export PATH="$HOME/bin:$PATH"

!# Move Downloaded openssh binaries to that DIR
 mv "$Path_To_sshd_Binary" "/usr/bin/sshd"
 mv "$Path_To_sftp_Binary" "/usr/bin/sftp"

!# For `sshd_config`
 mkdir -p "/etc/ssh/"
 mv "$Path_To_sshd_config" "/etc/ssh/sshd_config"

!# Give Writeable Perms
 chmod +xwr /usr/bin/ssh* && chmod +xwr /usr/bin/sftp*
```
```powershell
--> Windows

!# Using '.msi' [Recommended]
!# Note that | Out-Host makes sure powershell waits for the installer to finish
!# Auto Installs to `C:\Program Files (x86)\OpenSSH` & Starts sshd in the background
msiexec /i openssh.msi
!# For logs 
msiexec /i openssh.msi /l*vx install.log

# Generate Host Keys
  . "C:\Program Files (x86)\OpenSSH\ssh-keygen.exe" -A
#Fix Perms 
#https://github.com/PowerShell/Win32-OpenSSH/wiki/OpenSSH-utility-scripts-to-fix-file-permissions
  . "C:\Program Files (x86)\OpenSSH\FixHostFilePermissions.ps1" -Confirm:$false | Out-Null
  . "C:\Program Files (x86)\OpenSSH\FixUserFilePermissions.ps1" -Confirm:$false | Out-Null

#Add Public SSH Key
  New-Item -Path "$env:USERPROFILE\.ssh" -ItemType Directory -Force
  #Add SSH Keys
  (Invoke-RestMethod -Uri "https://github.com/Azathothas.keys").Split("`n") | ForEach-Object { if (-not [string]::IsNullOrWhiteSpace($_)) { Add-Content -Path "$env:USERPROFILE\.ssh\authorized_keys" -Value $_ } }
#Configure SSH Config
  $filePath = Join-Path $env:ProgramData "ssh\sshd_config"; if (-not (Test-Path $filePath)) { New-Item -Path (Split-Path $filePath) -Name "sshd_config" -ItemType File }; Add-Content -Path $filePath -Value "PasswordAuthentication yes`nAllowTcpForwarding yes`nPubkeyAuthentication yes"
#Configure Firewall
  New-NetFirewallRule -Protocol TCP -LocalPort 22 -Direction Inbound -Action Allow -DisplayName "OpenSSH-Server-In-TCP"
  New-NetFirewallRule -Protocol TCP -LocalPort 22 -Direction Outbound -Action Allow -DisplayName "OpenSSH-Server-Out-TCP"
  New-NetFirewallRule -Protocol TCP -LocalPort 22 -Direction Inbound -Action Allow -DisplayName "OpenSSH-Server-In-TCP-EdgeTraversal" -EdgeTraversalPolicy Allow
  if (!(Get-NetFirewallRule -Name "OpenSSH-Server-In-TCP" -ErrorAction SilentlyContinue | Select-Object Name, Enabled)) {Write-Output "Firewall Rule 'OpenSSH-Server-In-TCP' does not exist, creating it..." New-NetFirewallRule -Name 'OpenSSH-Server-In-TCP' -DisplayName 'OpenSSH Server (sshd)' -Enabled True -Direction Inbound -Protocol TCP -Action Allow -LocalPort 22} else {Write-Output "Firewall rule 'OpenSSH-Server-In-TCP' has been created and exists."}
# Finally Start
Get-Process -Name sshd
Stop-Process -Name sshd -Force 2>$null
Get-Process -Name sshd
Start-Process -Wait -FilePath "C:\Program Files (x86)\OpenSSH\sshd.exe" -WindowStyle Hidden & ; Start-Sleep 5
#--------------------------------------------------------------------------#
!# Check if these work (Skip .zip if these work)
  Add-WindowsCapability -Online -Name OpenSSH.Server*
  choco install openssh -y | Out-Null
#--------------------------------------------------------------------------#
!# Using '.zip' (Only if .msi doesn't work)
!# In PowerShell, To Install
 Expand-Archive -Path .\openssh.zip -Verbose 
 mv openssh C:\Program Files\OpenSSH-Win64

!# To enable & Run
 #Start Service
  . "C:\Program Files\OpenSSH-Win64\install-sshd.ps1"
  . "C:\Program Files\OpenSSH-Win64\ssh-keygen.exe" -A
  Start-Process -Wait -FilePath "C:\Program Files\OpenSSH-Win64\sshd.exe" -WindowStyle Hidden
  Start-Sleep 5
 #Fix Perms 
  #https://github.com/PowerShell/Win32-OpenSSH/wiki/OpenSSH-utility-scripts-to-fix-file-permissions
  . "C:\Program Files\OpenSSH-Win64\FixHostFilePermissions.ps1" -Confirm:$false | Out-Null
  . "C:\Program Files\OpenSSH-Win64\FixUserFilePermissions.ps1" -Confirm:$false | Out-Null
 #Add Public SSH Key
  New-Item -Path "$env:USERPROFILE\.ssh" -ItemType Directory -Force
  #Add SSH Keys
  (Invoke-RestMethod -Uri "https://github.com/Azathothas.keys").Split("`n") | ForEach-Object { if (-not [string]::IsNullOrWhiteSpace($_)) { Add-Content -Path "$env:USERPROFILE\.ssh\authorized_keys" -Value $_ } }
 #Configure SSH Config
  $filePath = Join-Path $env:ProgramData "ssh\sshd_config"; if (-not (Test-Path $filePath)) { New-Item -Path (Split-Path $filePath) -Name "sshd_config" -ItemType File }; Add-Content -Path $filePath -Value "PasswordAuthentication yes`nAllowTcpForwarding yes`nPubkeyAuthentication yes"
 #Configure Firewall
  New-NetFirewallRule -Protocol TCP -LocalPort 22 -Direction Inbound -Action Allow -DisplayName "OpenSSH-Server-In-TCP"
  New-NetFirewallRule -Protocol TCP -LocalPort 22 -Direction Outbound -Action Allow -DisplayName "OpenSSH-Server-Out-TCP"
  New-NetFirewallRule -Protocol TCP -LocalPort 22 -Direction Inbound -Action Allow -DisplayName "OpenSSH-Server-In-TCP-EdgeTraversal" -EdgeTraversalPolicy Allow
  if (!(Get-NetFirewallRule -Name "OpenSSH-Server-In-TCP" -ErrorAction SilentlyContinue | Select-Object Name, Enabled)) {Write-Output "Firewall Rule 'OpenSSH-Server-In-TCP' does not exist, creating it..." New-NetFirewallRule -Name 'OpenSSH-Server-In-TCP' -DisplayName 'OpenSSH Server (sshd)' -Enabled True -Direction Inbound -Protocol TCP -Action Allow -LocalPort 22} else {Write-Output "Firewall rule 'OpenSSH-Server-In-TCP' has been created and exists."}
 # Finally Start
Start-Process -Wait -FilePath "C:\Program Files\OpenSSH-Win64\sshd.exe" -WindowStyle Hidden ; Start-Sleep 5

#--------------------------------------------------------------------------#
!# For Troubleshooting:
!# Restart openssh daemons & Services
Stop-Process -Name sshd -Force 2>$null
Get-Process -Name sshd   
```

---
```console

--> METADATA
./openssh/INFO.md:                           ASCII text, with very long lines (456)
./openssh/README.md:                         ASCII text, with very long lines (456)
./openssh/openssh_aarch64_arm64_Windows.msi: Composite Document File V2 Document, Little Endian, Os: Windows, Version 10.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: OpenSSH, Author: Microsoft Corporation, Keywords: Installer, Comments: This installer database contains the logic and data required to install OpenSSH., Template: Arm64;1033, Revision Number: {E7A17144-5F82-4E23-91E5-5D1EC8F7A12A}, Create Time/Date: Thu Apr 17 20:53:14 2025, Last Saved Time/Date: Thu Apr 17 20:53:14 2025, Number of Pages: 500, Number of Words: 2, Name of Creating Application: Windows Installer XML Toolset (3.14.1.8722), Security: 2
./openssh/openssh_aarch64_arm64_Windows.zip: Zip archive data, at least v2.0 to extract, compression method=store
./openssh/openssh_aarch_arm_Windows.zip:     Zip archive data, at least v2.0 to extract, compression method=store
./openssh/openssh_amd_x86_64_Windows.msi:    Composite Document File V2 Document, Little Endian, Os: Windows, Version 10.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: OpenSSH, Author: Microsoft Corporation, Keywords: Installer, Comments: This installer database contains the logic and data required to install OpenSSH., Template: x64;1033, Revision Number: {6E3F62BF-002C-4999-B87D-7637D4804A11}, Create Time/Date: Thu Apr 17 20:51:48 2025, Last Saved Time/Date: Thu Apr 17 20:51:48 2025, Number of Pages: 200, Number of Words: 2, Name of Creating Application: Windows Installer XML Toolset (3.14.1.8722), Security: 2
./openssh/openssh_amd_x86_64_Windows.zip:    Zip archive data, at least v2.0 to extract, compression method=store
./openssh/openssh_amd_x86_Windows.msi:       Composite Document File V2 Document, Little Endian, Os: Windows, Version 10.0, MSI Installer, Code page: 1252, Title: Installation Database, Subject: OpenSSH, Author: Microsoft Corporation, Keywords: Installer, Comments: This installer database contains the logic and data required to install OpenSSH., Template: Intel;1033, Revision Number: {D74A8E59-D5A6-4A7E-A2E9-FA7894416387}, Create Time/Date: Thu Apr 17 20:48:24 2025, Last Saved Time/Date: Thu Apr 17 20:48:24 2025, Number of Pages: 200, Number of Words: 2, Name of Creating Application: Windows Installer XML Toolset (3.14.1.8722), Security: 2
./openssh/openssh_amd_x86_Windows.zip:       Zip archive data, at least v2.0 to extract, compression method=store
./openssh/sftp_server_aarch64_arm64_Linux:   ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, stripped
./openssh/sftp_server_amd_x86_64_Linux:      ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, stripped
./openssh/sftp_server_armv7_eabihf_Linux:    ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, stripped
./openssh/sshd_aarch64_arm64_Linux:          ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, stripped
./openssh/sshd_amd_x86_64_Linux:             ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, stripped
./openssh/sshd_armv7_eabihf_Linux:           ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, stripped
./openssh/sshd_config_aarch64_arm64_Linux:   ASCII text
./openssh/sshd_config_amd_x86_64_Linux:      ASCII text
./openssh/sshd_config_armv7_eabihf_Linux:    ASCII text

--> SHA256SUM
b199e119075255d47303b9040322ce41a8ad362ca2da8f5da7376bce11cca8f3  ./openssh/INFO.md
ce5a0f6ac35df826c631668c6c2997782ee19d8ba50346d09588f7639d47ba36  ./openssh/README.md
5cbe84935b51402bd5de0e0e00b8f0c7a7ae605a9f1d3d3c1d0172c6343eaebb  ./openssh/openssh_aarch64_arm64_Windows.msi
9c1c2e346ea7c76ddbd7e82e231c014e9e30fd497550c727adcdfdb8ca08642d  ./openssh/openssh_aarch64_arm64_Windows.zip
26c2c3713fbfa960bc101f7a59a2d3ad7bf37a5f5fe73914b158c5d441ded5a6  ./openssh/openssh_aarch_arm_Windows.zip
c8a8c7e21136a099665c2fad9accb41152d129466b719ea71678bab665e03389  ./openssh/openssh_amd_x86_64_Windows.msi
0ca131f3a78f404dc819a6336606caec0db1663a692ccc3af1e90232706ada54  ./openssh/openssh_amd_x86_64_Windows.zip
2b92552423d26b33dbfcef03c60cbd4017b390f967d9c1ecdc53e01856f602c1  ./openssh/openssh_amd_x86_Windows.msi
de65a5cc1c43192bbc7e5fc527ba435c9d1668713f062eaf1298932e28995085  ./openssh/openssh_amd_x86_Windows.zip
f3d275070dc64d7f5fb278795a0bca34df77f4f19280d58a4a18ecca4b5ba1ff  ./openssh/sftp_server_aarch64_arm64_Linux
2cba45068ceccd7f04342f3ee884ccb0534cbba80573dc9f6ff19b6131032b22  ./openssh/sftp_server_amd_x86_64_Linux
e8ed57f7cf1b93e4edb77e7b85b0792c3001a4b2d9da5f2e41f3c59bf21125cc  ./openssh/sftp_server_armv7_eabihf_Linux
a2f739d66edbc1c274b02a5ad63e305bff2974631555aa1771b2dbaddc768acc  ./openssh/sshd_aarch64_arm64_Linux
002d8838ddca9b13e023b1cce1791bbb1ac9ed819c8c0f27bad130b5ae693373  ./openssh/sshd_amd_x86_64_Linux
233092df84777ea62426603fdf1866d12dab151c70ac682786630d6ee06adf56  ./openssh/sshd_armv7_eabihf_Linux
b29a6aafd672f43a35fda7295f2a5360603d90729e6ab717dac0f73754503005  ./openssh/sshd_config_aarch64_arm64_Linux
f6c2fbaffc1fc3f4f426171d38091206ae1bcc2f8a2dff03cefa5f3519e55a72  ./openssh/sshd_config_amd_x86_64_Linux
b29a6aafd672f43a35fda7295f2a5360603d90729e6ab717dac0f73754503005  ./openssh/sshd_config_armv7_eabihf_Linux
```


---

- #### Sizes

```console
9.5K  ./openssh/INFO.md
15K   ./openssh/README.md
5.7M  ./openssh/openssh_aarch64_arm64_Windows.msi
4.3M  ./openssh/openssh_aarch64_arm64_Windows.zip
4.1M  ./openssh/openssh_aarch_arm_Windows.zip
5.9M  ./openssh/openssh_amd_x86_64_Windows.msi
4.9M  ./openssh/openssh_amd_x86_64_Windows.zip
5.3M  ./openssh/openssh_amd_x86_Windows.msi
4.3M  ./openssh/openssh_amd_x86_Windows.zip
275K  ./openssh/sftp_server_aarch64_arm64_Linux
266K  ./openssh/sftp_server_amd_x86_64_Linux
290K  ./openssh/sftp_server_armv7_eabihf_Linux
4.9M  ./openssh/sshd_aarch64_arm64_Linux
4.9M  ./openssh/sshd_amd_x86_64_Linux
5.1M  ./openssh/sshd_armv7_eabihf_Linux
3.1K  ./openssh/sshd_config_aarch64_arm64_Linux
3.1K  ./openssh/sshd_config_amd_x86_64_Linux
3.1K  ./openssh/sshd_config_armv7_eabihf_Linux
```

---

- #### Version
```console

$ ./openssh/sshd_amd_x86_64_Linux -h
./openssh/sshd_amd_x86_64_Linux: option requires an argument: h
OpenSSH_9.7p1, OpenSSL 3.3.0 9 Apr 2024
usage: sshd [-46DdeGiqTtV] [-C connection_spec] [-c host_cert_file]
            [-E log_file] [-f config_file] [-g login_grace_time]
            [-h host_key_file] [-o option] [-p port] [-u len]

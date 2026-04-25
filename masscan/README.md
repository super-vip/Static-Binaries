
---
- #### Download MassScan
> - An effort to compile as many binaries as there are **ARCH** of Systems has been put in, however, there's still no process to compile for the following **Architectures**
> > ```bash
> > 
> >  --> Windows*
> >    - There is much work to be done before dockcross can compile for Windows
> >    - Further, running masscan on Windows is pointless since requests are capped at 300,000 packets/second
> >      !# https://github.com/robertdavidgraham/masscan#transmit-rate-important 
> > 
> > ```
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
--> linux_arm64_aarch64_gcc || arm64 [64-bit] (GNU/Linux)
--> linux_arm64_aarch64_musl || arm64 [64-bit] (GNU/Linux)
--> linux_s390x_gcc || IBM S/390 [64-bit] (GNU/Linux)
--> linux_x86_gcc || x86 [32-bit] (GNU/Linux)
--> linux_x86_64_gcc || x86_64 [64-bit] (GNU/Linux)

!# Export
export MASSCAN_ARCH="$YOUR_CPU_ARCH_FROM_LIST_ABOVE"

!# Download
 curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/masscan/masscan_$MASSCAN_ARCH"
```
---
- #### Install Masscan
```bash
!# Copy downloaded Masscan binary to /usr/bin || /usr/local/bin
 mkdir -p "$HOME/bin" && export PATH="$HOME/bin:$PATH"

!# Move Downloaded Busybox binary to that DIR
 mv "$Path_To_Masscan_Binary" "/usr/bin/masscan"

!# Give Writeable Perms
 chmod +xwr "/usr/bin/masscan"

#! Install libpcap: https://github.com/the-tcpdump-group/libpcap
!# apt
 sudo apt-get install libpcap-dev -y

!# conda
!# To Install:
!# curl -qfSL "https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh" -o /tmp/install_conda.sh && chmod +xwr "/tmp/install_conda.sh" && /tmp/install_conda.sh -b
!# export PATH=$HOME/miniconda3/bin:$PATH
!# export PATH=$HOME/miniconda3/condabin:$PATH

 conda install -c conda-forge libcap --all -y
 conda install -c conda-forge libpcap --all -y

!# dnf
 sudo dnf install libpcap --nogpgcheck

!# pacman
 sudo pacman -S libpcap

!# yum
 sudo dnf install libpcap --nogpgcheck
```

---
```console
$ file ./masscan/masscan_linux_arm64_aarch64_gcc ./masscan/masscan_linux_arm64_aarch64_musl ./masscan/masscan_linux_s390x_gcc ./masscan/masscan_linux_x86_64_gcc ./masscan/masscan_linux_x86_gcc
./masscan/masscan_linux_arm64_aarch64_gcc:  ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, BuildID[sha1]=938a81c1d25f5e10f3b8a39c100aa262c963cbd7, for GNU/Linux 6.1.35, stripped
./masscan/masscan_linux_arm64_aarch64_musl: ELF 64-bit LSB pie executable, ARM aarch64, version 1 (SYSV), static-pie linked, stripped
./masscan/masscan_linux_s390x_gcc:          ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, BuildID[sha1]=2dbfe751ccc301b0637e7475da33a83a43aa9451, for GNU/Linux 5.4.0, stripped
./masscan/masscan_linux_x86_64_gcc:         ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, BuildID[sha1]=272f17cb47e357b65d37efbbca3f05e3fb0e27b1, for GNU/Linux 3.2.0, stripped
./masscan/masscan_linux_x86_gcc:            ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, BuildID[sha1]=a5a904fc5237cd9b9aecb09fdea1979b24c7f96f, for GNU/Linux 3.2.0, stripped

--> SHA256SUM
$ sha256sum ./masscan/masscan_linux_arm64_aarch64_gcc ./masscan/masscan_linux_arm64_aarch64_musl ./masscan/masscan_linux_s390x_gcc ./masscan/masscan_linux_x86_64_gcc ./masscan/masscan_linux_x86_gcc
db779382e4c08892ed11e6c9231274816db7cda5c7ee469e05a1f7f822e796a8  ./masscan/masscan_linux_arm64_aarch64_gcc
50a04b1c98b231ed3cb1b4de1a0d47527f0c8fcc72ba5c64fd92ab9d6276e749  ./masscan/masscan_linux_arm64_aarch64_musl
2eb77348c17cdcf86e1fa756b5811feefc2d6d96b15a44942465033f0e09ac32  ./masscan/masscan_linux_s390x_gcc
ae6929ade79bd02a13bb4ed3bcfb0ea823c64213ddbf196ab7e5f1779636dc17  ./masscan/masscan_linux_x86_64_gcc
70c11da07f969af0504a622d8bf93802b0341bd016b1475865a569aba677ce54  ./masscan/masscan_linux_x86_gcc
```


---

- #### Sizes

```console

2.2K  INFO.md
4.1K  README.md
1.2M  masscan_linux_arm64_aarch64_gcc
550K  masscan_linux_arm64_aarch64_musl
1.4M  masscan_linux_s390x_gcc
1.4M  masscan_linux_x86_64_gcc
1.5M  masscan_linux_x86_gcc
```

---



---
- #### Download MassDNS
> - An effort to compile as many binaries as there are **ARCH** of Systems has been put in, however, there's still no process to compile for the following **Architectures**
> > ```bash
> >  --> 32-bit Only
> >    - Currently all builds of MassDNS against dockcross 32 bit only images fail
> > 
> >  --> Windows*
> >    - There is much work to be done before dockcross can compile for Windows
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
--> linux_x86_64_gcc || x86_64 [64-bit] (GNU/Linux)

!# Export
export MASSDNS_ARCH="$YOUR_CPU_ARCH_FROM_LIST_ABOVE"

!# Download
 curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/massdns/massdns_$MASSDNS_ARCH"
```
---
- #### Install MassDNS
```bash
!# Creae & export $USER writeable $DIR
 mkdir -p "$HOME/bin" && export PATH="$HOME/bin:$PATH"

!# Move Downloaded Busybox binary to that DIR
 mv "$Path_To_MassDNS_Binary" "$HOME/bin/massdns"

!# Give Writeable Perms
 chmod +xwr "$HOME/bin/massdns"

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
$ file ./massdns/massdns_linux_arm64_aarch64_gcc ./massdns/massdns_linux_arm64_aarch64_musl ./massdns/massdns_linux_s390x_gcc ./massdns/massdns_linux_x86_64_gcc
./massdns/massdns_linux_arm64_aarch64_gcc:  ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, BuildID[sha1]=94ff1693d3255f987fbf5973e8963436c2e5fc6c, for GNU/Linux 6.1.35, stripped
./massdns/massdns_linux_arm64_aarch64_musl: ELF 64-bit LSB pie executable, ARM aarch64, version 1 (SYSV), static-pie linked, stripped
./massdns/massdns_linux_s390x_gcc:          ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, BuildID[sha1]=3ee86dbee6d3f203482d0a36a7cb09ffb4a6f1dc, for GNU/Linux 5.4.0, stripped
./massdns/massdns_linux_x86_64_gcc:         ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, BuildID[sha1]=1ce6802eb7d33b2440a97812f77d7e05ffcb1a39, for GNU/Linux 3.2.0, stripped

--> SHA256SUM
$ sha256sum ./massdns/massdns_linux_arm64_aarch64_gcc ./massdns/massdns_linux_arm64_aarch64_musl ./massdns/massdns_linux_s390x_gcc ./massdns/massdns_linux_x86_64_gcc
694f4c2279cae5faf7bcee2cfcbbe1057ec71805464a7f1e3c8d4eb3e86d712a  ./massdns/massdns_linux_arm64_aarch64_gcc
d48a7041513eed13b28e765ce04d10026ad6b57ccf2d327dae428c4f7df9ae14  ./massdns/massdns_linux_arm64_aarch64_musl
393add1bbe1371842a4aa7e76e9f7f7348b1a5f589774a7f96d4f88859f007d2  ./massdns/massdns_linux_s390x_gcc
e36a0a25705932b7675b6eae8dd1e9898cdd120fcc33722193b0fe14198d313d  ./massdns/massdns_linux_x86_64_gcc
```


---

- #### Sizes

```console
2.1K  INFO.md
3.6K  README.md
731K  massdns_linux_arm64_aarch64_gcc
151K  massdns_linux_arm64_aarch64_musl
837K  massdns_linux_s390x_gcc
932K  massdns_linux_x86_64_gcc
```

---


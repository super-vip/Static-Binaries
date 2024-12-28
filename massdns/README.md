
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
./massdns/massdns_linux_arm64_aarch64_gcc:  ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, BuildID[sha1]=af43ad30eb2650abaccdb3167534ae315ad2fc3d, for GNU/Linux 6.1.35, stripped
./massdns/massdns_linux_arm64_aarch64_musl: ELF 64-bit LSB pie executable, ARM aarch64, version 1 (SYSV), static-pie linked, stripped
./massdns/massdns_linux_s390x_gcc:          ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, BuildID[sha1]=5f128b2242210aaf6e9a00ba6608c4414d6613be, for GNU/Linux 5.4.0, stripped
./massdns/massdns_linux_x86_64_gcc:         ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, BuildID[sha1]=9baf3b432b335b4f49b4eae30572bd28be0bd244, for GNU/Linux 3.2.0, stripped

--> SHA256SUM
$ sha256sum ./massdns/massdns_linux_arm64_aarch64_gcc ./massdns/massdns_linux_arm64_aarch64_musl ./massdns/massdns_linux_s390x_gcc ./massdns/massdns_linux_x86_64_gcc
aeeb3b675df4bf17f2aa5f2a2f2f9bdca2d749fdf89d6b1210974d49300b7e65  ./massdns/massdns_linux_arm64_aarch64_gcc
2ba48023d84488ab32652cf8afebb496224e20960ae21b211f6b070ee1abb43d  ./massdns/massdns_linux_arm64_aarch64_musl
79d987dee8c8775dff4295cf0a919d84394de5fb97c042a50e2a8389aaea827c  ./massdns/massdns_linux_s390x_gcc
d378e13e99760ac02bddeaa13d05cc9009b3284a691a1c4cfe5d83bf3ed66f7c  ./massdns/massdns_linux_x86_64_gcc
```


---

- #### Sizes

```console
2.1K  INFO.md
3.6K  README.md
731K  massdns_linux_arm64_aarch64_gcc
147K  massdns_linux_arm64_aarch64_musl
833K  massdns_linux_s390x_gcc
932K  massdns_linux_x86_64_gcc
```

---


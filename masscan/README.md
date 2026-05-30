
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
./masscan/masscan_linux_arm64_aarch64_gcc:  ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, BuildID[sha1]=372d5bbb16772d24efedce802142334621037c46, for GNU/Linux 6.1.35, stripped
./masscan/masscan_linux_arm64_aarch64_musl: ELF 64-bit LSB pie executable, ARM aarch64, version 1 (SYSV), static-pie linked, stripped
./masscan/masscan_linux_s390x_gcc:          ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, BuildID[sha1]=6152a73a03f85eb5a08c135c46476ef93ee3d8c1, for GNU/Linux 5.4.0, stripped
./masscan/masscan_linux_x86_64_gcc:         ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, BuildID[sha1]=0015e699913567482e0e52906e963c91e049db9f, for GNU/Linux 3.2.0, stripped
./masscan/masscan_linux_x86_gcc:            ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, BuildID[sha1]=0d99f60aed8fea42de4d8ad7e84ed5dfea3520ea, for GNU/Linux 3.2.0, stripped

--> SHA256SUM
$ sha256sum ./masscan/masscan_linux_arm64_aarch64_gcc ./masscan/masscan_linux_arm64_aarch64_musl ./masscan/masscan_linux_s390x_gcc ./masscan/masscan_linux_x86_64_gcc ./masscan/masscan_linux_x86_gcc
6c2807851aed261dd79e16e21877b668a7f73c6ecaf14ebfed93153b37a7d12d  ./masscan/masscan_linux_arm64_aarch64_gcc
7fac35437f19f8071592a6b2fae8e7a1dc14053c9c2427f2106871d2c73a5759  ./masscan/masscan_linux_arm64_aarch64_musl
4d2942e2b5b3f23c532bba89a92e537a5837a44e0c4e37c7cfed83df591d790a  ./masscan/masscan_linux_s390x_gcc
a2382e3ac7c6983fef1fad1b23d43583400a83749e55b408ce973b09e54f301f  ./masscan/masscan_linux_x86_64_gcc
850d70a746278909b9a7d354b5cee643861ff6d8bbcdbcf75c2985a3d1acdf67  ./masscan/masscan_linux_x86_gcc
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


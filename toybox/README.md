
---
- #### Download [Toybox](http://landley.net/toybox/) 
> - This is just a mirror of : http://landley.net/toybox/bin/
> - Nothing is rebuilt/re-compiled

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

!# Linux
--> arm64_aarch64 || arm64 [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/toybox/toybox_arm64_aarch64_Linux"
--> AMD || x86_64 || [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/toybox/toybox_amd_x86_64_Linux"
--> armv4l || arm-linux-gnueabi [32-bit] {Hardware Floating-Point Unit (FPU) support : NO} (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/toybox/toybox_armv4l_Linux"
--> armv5l || arm-linux-gnueabi  [32-bit] {Hardware Floating-Point Unit (FPU) support : NO} (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/toybox/toybox_armv5l_Linux"
--> armv7l || (Little-Endian)  [32-bit] {Hardware Floating-Point Unit (FPU) support : NO} (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/toybox/toybox_armv7l_Linux"
--> armv7m || arm-linux-gnueabihf || ARMv7 [32-bit] {Hardware Floating-Point Unit (FPU) support : YES} (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/toybox/toybox_armv7m_Linux"
--> i486 || [32-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/toybox/toybox_i486_Linux"
--> i686 || x86_64 [32-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/toybox/toybox_i686_Linux"
--> microblaze || [32-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/toybox/toybox_m68k_Linux"
--> m68k || Motorola_NXP [32-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/toybox/toybox_microblaze_Linux"
--> mips || MIPS (Big-Endian) [32-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/toybox/toybox_mips_Linux"
--> mipsel || MIPSel (Little-Endian) [32-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/toybox/toybox_mipsel_Linux"
--> mips64 || MIPS (Big-Endian) [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/toybox/toybox_mips64_Linux"
--> powerpc || cisco 4500 [32-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/toybox/toybox_powerpc_Linux"
--> powerpc64 || cisco 7500 || Power ELF V1 ABI [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/toybox/toybox_powerpc64_Linux"
--> powerpc64le || cisco 7500 || OpenPOWER ELF V2 ABI (Little-Endian) [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/toybox/toybox_powerpc64le_Linux"
--> s390x || IBM S/390 [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/toybox/toybox_s390x_Linux"
--> sh4 || UCB RISC-V || RVC [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/toybox/toybox_sh4_Linux"
```
---
- #### Install Toybox
```bash
!# Create a $USER Writeable DIR & export to PATH
 mkdir -p "$HOME/bin" && export PATH="$HOME/bin:$PATH"

!# Move the Downloaded Toybox binary to that DIR
 mv "$Path_To_Toybox_Binary" "$HOME/bin/toybox"

!# Give Writeable Perms
 chmod +xwr "$HOME/bin/toybox" && chmod +xwr $HOME/bin/*

#! Install & Symlink Everything : https://github.com/landley/toybox/issues/155
cd "$HOME/bin" && for i in $($HOME/bin/toybox); do ln -s toybox $i; done; PATH=$PWD:$PATH

```

---
```console

--> METADATA
./toybox/toybox_amd_x86_64_Linux:           ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, stripped
./toybox/toybox_arm64_aarch64_Linux:        ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), statically linked, stripped
./toybox/toybox_armv4l_Linux:               ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, stripped
./toybox/toybox_armv5l_Linux:               ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, stripped
./toybox/toybox_armv7l_Linux:               ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, stripped
./toybox/toybox_armv7m_Linux:               ELF 32-bit LSB pie executable, ARM, EABI5 version 1 (SYSV), static-pie linked, stripped
./toybox/toybox_i486_Linux:                 ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, stripped
./toybox/toybox_i686_Linux:                 ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, stripped
./toybox/toybox_m68k_Linux:                 ELF 32-bit MSB executable, Motorola m68k, 68020, version 1 (SYSV), statically linked, stripped
./toybox/toybox_microblaze_Linux:           ELF 32-bit MSB executable, Xilinx MicroBlaze 32-bit RISC, version 1 (SYSV), statically linked, stripped
./toybox/toybox_mips64_Linux:               ELF 64-bit MSB executable, MIPS, MIPS-III version 1 (SYSV), statically linked, stripped
./toybox/toybox_mips_Linux:                 ELF 32-bit MSB executable, MIPS, MIPS-I version 1 (SYSV), statically linked, stripped
./toybox/toybox_mipsel_Linux:               ELF 32-bit LSB executable, MIPS, MIPS-I version 1 (SYSV), statically linked, stripped
./toybox/toybox_powerpc64_Linux:            ELF 64-bit MSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./toybox/toybox_powerpc64le_Linux:          ELF 64-bit LSB executable, 64-bit PowerPC or cisco 7500, OpenPOWER ELF V2 ABI, version 1 (SYSV), statically linked, stripped
./toybox/toybox_powerpc_Linux:              ELF 32-bit MSB executable, PowerPC or cisco 4500, version 1 (SYSV), statically linked, stripped
./toybox/toybox_s390x_Linux:                ELF 64-bit MSB executable, IBM S/390, version 1 (SYSV), statically linked, stripped
./toybox/toybox_sh4_Linux:                  ELF 32-bit LSB executable, Renesas SH, version 1 (SYSV), statically linked, stripped

--> SHA256SUM
8c98795a15db31ea55c8065fed379db3669766b7a714c46b009d8bfb87b25ffd  ./toybox/toybox_amd_x86_64_Linux
b3508e5f51a0d429c1bda9d500d98d97dc0b86571762eeb099495eb238a8c52a  ./toybox/toybox_arm64_aarch64_Linux
c3ff0963dcd8cdf22c4e681c2946c622ee2e3fa065beeff3bf64004e22e68dcc  ./toybox/toybox_armv4l_Linux
d88dbc731da244539eb2f7569ea7243407aedf7670197953f542fdc261e276f0  ./toybox/toybox_armv5l_Linux
57eb98200b6b15767c79af78316b6975388466146311da5ba0938790667275d4  ./toybox/toybox_armv7l_Linux
5b928ca17ab11c30c3bd037ad228f64976064032f96cda9bfdb8468427cfe242  ./toybox/toybox_armv7m_Linux
5e3067deff3fb88c975dbadc6dc91defaff0a4b4f163c000f0899b838f48634f  ./toybox/toybox_i486_Linux
fa6f6751a95c971f8603cd967a98ccdbbe012f840553c0a2addc89ab0a8dfdf8  ./toybox/toybox_i686_Linux
821ce699dcaae48d13cfe54a5ef1bb23bc601d001a813d6e86140b9661558aea  ./toybox/toybox_m68k_Linux
e716859ea1cb522f6aa17c9124cad08699d9643f5ab5a14e80791987417af341  ./toybox/toybox_microblaze_Linux
a529ea2379de48c4dfc7f24ad3209d2e7a632a9d475a66ad3344a9c719b644c8  ./toybox/toybox_mips64_Linux
1dd0918db9b9677478b6318f19c79b0fa1e9d100a282b311793173fe7c7d3b8a  ./toybox/toybox_mips_Linux
b96d3d267b732f48d43c0909f1e0df05523599cf598aa4770377abdaea964a83  ./toybox/toybox_mipsel_Linux
8c8743cdb65599eb28c995d156d6990701db5396795e433af99ff67f1e048cf9  ./toybox/toybox_powerpc64_Linux
2fe1dc9342592715d5e3f5b583585bfefa9c8b3cdcd38c27554e86b261d5a7d4  ./toybox/toybox_powerpc64le_Linux
ee3455db89db011b9c5bd0ea6f34599f6c527e4e406291574c1b6e60370a805f  ./toybox/toybox_powerpc_Linux
70c0384e635349a167556810736a63d0f123569f0e72036808dd00b66cd40f7a  ./toybox/toybox_s390x_Linux
7749d79174df0128a02e5614f2731575a380721651654e8c21f4e6f5e33af4f6  ./toybox/toybox_sh4_Linux
```


---

- #### Bundled Commands
```console
Toybox 0.8.13 multicall binary (see https://landley.net/toybox)

usage: toybox [--long | --help | --version | [COMMAND] [ARGUMENTS...]]

With no arguments, "toybox" shows available COMMAND names. Add --long
to include suggested install path for each command, see
https://landley.net/toybox/faq.html#install for details.

First argument is name of a COMMAND to run, followed by any ARGUMENTS
to that command. Most toybox commands also understand:

--help		Show command help (only)
--version	Show toybox version (only)

The filename "-" means stdin/stdout, and "--" stops argument parsing.

Numerical arguments accept a single letter suffix for
kilo, mega, giga, tera, peta, and exabytes, plus an additional
"d" to indicate decimal 1000's instead of 1024.

Durations can be decimal fractions and accept minute ("m"), hour ("h"),
or day ("d") suffixes (so 0.1m = 6s).

[ acpi arch ascii base32 base64 basename bash blkdiscard blkid blockdev
bunzip2 bzcat cal cat chattr chgrp chmod chown chroot chrt chvt cksum
clear cmp comm count cp cpio crc32 cut date dd deallocvt devmem df
dirname dmesg dnsdomainname dos2unix du echo egrep eject env expand
factor fallocate false fgrep file find flock fmt fold free freeramdisk
fsfreeze fstype fsync ftpget ftpput getconf getopt gpiodetect gpiofind
gpioget gpioinfo gpioset grep groups gunzip halt hd head help hexedit
host hostname httpd hwclock i2cdetect i2cdump i2cget i2cset i2ctransfer
iconv id ifconfig inotifyd insmod install ionice iorenice iotop kill
killall killall5 link linux32 ln logger login logname losetup ls lsattr
lsmod lspci lsusb makedevs mcookie md5sum memeater microcom mix mkdir
mkfifo mknod mkpasswd mkswap mktemp modinfo mount mountpoint mv nbd-client
nbd-server nc netcat netstat nice nl nohup nologin nproc nsenter od
oneit openvt partprobe paste patch pgrep pidof ping ping6 pivot_root
pkill pmap poweroff printenv printf prlimit ps pwd pwdx pwgen readahead
readelf readlink realpath reboot renice reset rev rfkill rm rmdir
rmmod route rtcwake sed seq setfattr setsid sh sha1sum sha224sum sha256sum
sha384sum sha3sum sha512sum shred shuf sleep sntp sort split stat
strings su swapoff swapon switch_root sync sysctl tac tail tar taskset
tee test time timeout top touch toysh true truncate ts tsort tty tunctl
uclampset ulimit umount uname unicode uniq unix2dos unlink unshare
uptime usleep uudecode uuencode uuidgen vconfig vmstat w watch watchdog
wc wget which who whoami xargs xxd yes zcat 
```

---

- #### Sizes

```console
735K  ./toybox/toybox_amd_x86_64_Linux
815K  ./toybox/toybox_arm64_aarch64_Linux
778K  ./toybox/toybox_armv4l_Linux
770K  ./toybox/toybox_armv5l_Linux
762K  ./toybox/toybox_armv7l_Linux
643K  ./toybox/toybox_armv7m_Linux
741K  ./toybox/toybox_i486_Linux
741K  ./toybox/toybox_i686_Linux
725K  ./toybox/toybox_m68k_Linux
1.1M  ./toybox/toybox_microblaze_Linux
963K  ./toybox/toybox_mips64_Linux
996K  ./toybox/toybox_mips_Linux
998K  ./toybox/toybox_mipsel_Linux
947K  ./toybox/toybox_powerpc64_Linux
947K  ./toybox/toybox_powerpc64le_Linux
878K  ./toybox/toybox_powerpc_Linux
875K  ./toybox/toybox_s390x_Linux
697K  ./toybox/toybox_sh4_Linux

```



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
079f7ee3ed5bbb34d0b317d487a4538a7712a28e4ca28efc5bf6133596b4ac61  ./toybox/toybox_amd_x86_64_Linux
fc459ebbf21c10df85446d63709c8c9b7ed15659d159c8ce4bd194ca04716667  ./toybox/toybox_arm64_aarch64_Linux
749dfafc1f8fd97baadacccd16a73c4a37322504142fa20e65ccebdf54763fef  ./toybox/toybox_armv4l_Linux
43df6a6ca7dcd1e2f49b6e92b3ffea55dd35509df3cae86f0aa52c83f2bd7bed  ./toybox/toybox_armv5l_Linux
a25c858a0dfa217a47ed189090c9b12c00304a8e5a4452cc0e59d936b10e2c2f  ./toybox/toybox_armv7l_Linux
f77bc7b4c49d2324422d6c8b299d213ea7a4be45ecbe6533a20f915ee97080a0  ./toybox/toybox_armv7m_Linux
e6ec79fcedbbb9e171cf5cc4fffae8848917ebca27ed588654d90e32a43258a5  ./toybox/toybox_i486_Linux
0cbf5ec060b04d596639b32711c6da8df62406a7425827f002b92c1a22580ca6  ./toybox/toybox_i686_Linux
dadee06a8a6e05603466f17778a086ba45075c77e979eb875ec238445112f801  ./toybox/toybox_m68k_Linux
4a90980a22b857b665a6bd9310622784cc1eb1cea6591758830e9c83ed55c544  ./toybox/toybox_microblaze_Linux
f6ceb4ae71fe05a47aa3c8e2625f12357319a6bbfef05b67f444a50758a66470  ./toybox/toybox_mips64_Linux
1479f3b9143828b0d7df7835058005a41dfeb6d24009791a76ddbb865aed9974  ./toybox/toybox_mips_Linux
06ee96490f89a0e1218aca2f4adfee2d2222a6ec61e167f4fdc84342557faf95  ./toybox/toybox_mipsel_Linux
2469995a015206b4e6193340e7e0dab6d784d06eef89a12781f3a8c935dd369c  ./toybox/toybox_powerpc64_Linux
81643b6ffb2b53692709309b3990e0749f72b6e172a609eeaadf30a7630e7846  ./toybox/toybox_powerpc64le_Linux
6e2030e9a6ea93c5f039684dee2aa93794c4b8cd5a9d56fe6b911d4055ab3cd8  ./toybox/toybox_powerpc_Linux
1a8c835ec81ade7cd65dc49afad20c81515b19cc74fe5fcf889c795312c81c32  ./toybox/toybox_s390x_Linux
a767e283881a42b954d4615f37a97960615880e66acd8d9db7676f5e3a74ee21  ./toybox/toybox_sh4_Linux
```


---

- #### Bundled Commands
```console
Toybox 0.8.12 multicall binary (see https://landley.net/toybox)

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
gpioget gpioinfo gpioset grep groups gunzip halt head help hexedit
host hostname httpd hwclock i2cdetect i2cdump i2cget i2cset i2ctransfer
iconv id ifconfig inotifyd insmod install ionice iorenice iotop kill
killall killall5 link linux32 ln logger login logname losetup ls lsattr
lsmod lspci lsusb makedevs mcookie md5sum memeater microcom mix mkdir
mkfifo mknod mkpasswd mkswap mktemp modinfo mount mountpoint mv nbd-client
nbd-server nc netcat netstat nice nl nohup nproc nsenter od oneit
openvt partprobe paste patch pgrep pidof ping ping6 pivot_root pkill
pmap poweroff printenv printf prlimit ps pwd pwdx pwgen readahead
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
814K   ./toybox/toybox_amd_x86_64_Linux
898K   ./toybox/toybox_arm64_aarch64_Linux
861K   ./toybox/toybox_armv4l_Linux
853K   ./toybox/toybox_armv5l_Linux
845K   ./toybox/toybox_armv7l_Linux
726K   ./toybox/toybox_armv7m_Linux
825K   ./toybox/toybox_i486_Linux
825K   ./toybox/toybox_i686_Linux
812K   ./toybox/toybox_m68k_Linux
1.2M   ./toybox/toybox_microblaze_Linux
1.1M   ./toybox/toybox_mips64_Linux
1.1M   ./toybox/toybox_mips_Linux
1.1M   ./toybox/toybox_mipsel_Linux
1010K  ./toybox/toybox_powerpc64_Linux
1010K  ./toybox/toybox_powerpc64le_Linux
941K   ./toybox/toybox_powerpc_Linux
954K   ./toybox/toybox_s390x_Linux
780K   ./toybox/toybox_sh4_Linux

```



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
836ba9d6821fb3bcd85f4e2c511115d677930796ef76418799e0df95526d4e65  ./toybox/toybox_amd_x86_64_Linux
223b5ff5929371225d0bc62fb3b99a148692295fb6f85ad86bb924f689a55ea4  ./toybox/toybox_arm64_aarch64_Linux
cbcc324f2d7cb731f34cdae39d8c435766848cc42e6e7b12ce8d1f540d8511b7  ./toybox/toybox_armv4l_Linux
32a31d27786e11e6e38e6a611337bad14cc713271f723cb33b9d735469a3a653  ./toybox/toybox_armv5l_Linux
fab000067d4d1f4a1b070d97f546b94b71740bf6fc31911c1679df45dd1bf950  ./toybox/toybox_armv7l_Linux
0d8a5514111b3db6e9b68d141deae158873bad389d7c58875cbb43db368c9fd5  ./toybox/toybox_armv7m_Linux
8152b939cc7d79619ad45d7f7d5bf564424d736e79539f6dc36199cc4e75ae15  ./toybox/toybox_i486_Linux
5890eb67923bca277b34c9dd030bbe9aaff60bee6938713d7c29dca89ccc1fd9  ./toybox/toybox_i686_Linux
6ee5cdb3ebddaf0492f6d959ab550ce5fc4cc83807e16addea8cc50c47090ffd  ./toybox/toybox_m68k_Linux
b48afa91ae541c21008ef2bdb31120e8ec68675a34071bfe882c9745151774db  ./toybox/toybox_microblaze_Linux
3d804fe0ca0bb3a659a9c248d71336d3d3d7a5334883e0e162ba8323f6963706  ./toybox/toybox_mips64_Linux
3e92331f02f2e04f6bb6a39545b7fede3ef6dc91b44573997453a5ab5c7a3eb1  ./toybox/toybox_mips_Linux
697b251b9a9458add4974e885cc48f2096391265ac2bf8f6efe6a17c0fab5849  ./toybox/toybox_mipsel_Linux
0f540c2c8db21b5fbdcf6a38c38b0a4366b346957d030277aa69fa5dca6a153e  ./toybox/toybox_powerpc64_Linux
630583bc07e6c5fb2429d8d3777b583e3a9920931f995b7696483a6d1fca1724  ./toybox/toybox_powerpc64le_Linux
da5558b50a5c66032f52215ceb8c4273d082e2dec8f56ed39a0efa6a3ce95c2e  ./toybox/toybox_powerpc_Linux
03681ba01e223e1b90803fe0a48a92905d6cb7bc449f77a8a2d7c4e08e0fdb2d  ./toybox/toybox_s390x_Linux
c2dbe220cd80ec85485e50d381e587dd2e57222b2affbd4b0b98336f474330d8  ./toybox/toybox_sh4_Linux
```


---

- #### Bundled Commands
```console
Toybox 0.8.14 multicall binary (see https://landley.net/toybox)

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
747K   ./toybox/toybox_amd_x86_64_Linux
819K   ./toybox/toybox_arm64_aarch64_Linux
782K   ./toybox/toybox_armv4l_Linux
774K   ./toybox/toybox_armv5l_Linux
766K   ./toybox/toybox_armv7l_Linux
647K   ./toybox/toybox_armv7m_Linux
761K   ./toybox/toybox_i486_Linux
761K   ./toybox/toybox_i686_Linux
741K   ./toybox/toybox_m68k_Linux
1.1M   ./toybox/toybox_microblaze_Linux
966K   ./toybox/toybox_mips64_Linux
1002K  ./toybox/toybox_mips_Linux
1004K  ./toybox/toybox_mipsel_Linux
947K   ./toybox/toybox_powerpc64_Linux
947K   ./toybox/toybox_powerpc64le_Linux
878K   ./toybox/toybox_powerpc_Linux
935K   ./toybox/toybox_s390x_Linux
749K   ./toybox/toybox_sh4_Linux

```


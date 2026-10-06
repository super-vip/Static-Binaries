
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
38e03ffd8aead8ca26833e1e5c90a9ea7250f3719c29d779ebff7aa55c9d2dac  ./toybox/toybox_amd_x86_64_Linux
be360e78774c9ad599f2c0a606a2a7579840f9957ffccdc9898b0dd8e3f87e88  ./toybox/toybox_arm64_aarch64_Linux
9d9b89b9a949045a1762ae2421721067dcf5fbe14ff291ed3acb7619f2a96b02  ./toybox/toybox_armv4l_Linux
c1f9fe4c7242e7db16beafd0e3c729ec5954360822c3380f73baec2803ad522d  ./toybox/toybox_armv5l_Linux
c316531d76f57639582028ac9f5fce0408a217319650815f70c0049bd0122003  ./toybox/toybox_armv7l_Linux
1c657408965181fb8cc415e862740e72575347a7dff8a720f2d8c2c055bd75d7  ./toybox/toybox_armv7m_Linux
c6a8deee9f1364067528be703f40ccefa726a84ff18e04deb49a7b66c11a623c  ./toybox/toybox_i486_Linux
a8337bd6415db1b88f392914b971978ccb8201e818b7a2da6f023726ae4f207a  ./toybox/toybox_i686_Linux
6654a48777b1637cfa89095d3987be39ab5646aeae379bcdbebd6e0d39960205  ./toybox/toybox_m68k_Linux
d0aa13ecd73510831734954dcea1d268ae181489fff685a223aa82058ac3861e  ./toybox/toybox_microblaze_Linux
9bac351278f156f26441afcfc3119f66193f9f6fa89f10768f1e43ba43be198a  ./toybox/toybox_mips64_Linux
738ccfdc7a6c69615e35c77aa3ebb73f412c4dd839f47b52fa109be46c62cb5f  ./toybox/toybox_mips_Linux
9d63eec363df5625016795a60f2729dd0bf6a39c26f5434ee7dedd505f728de7  ./toybox/toybox_mipsel_Linux
8aaf0bbe33648fe8420be31e22a1eba2955dc31401be155770acc615111beba3  ./toybox/toybox_powerpc64_Linux
d69ef05ef998068ff7b5b90bd2e92343900e5cf5825a587b58a36538148879de  ./toybox/toybox_powerpc64le_Linux
fd07fdfe2eccb306c95b930bab82d37f797e9c18d5ecc55ec68df826579886a3  ./toybox/toybox_powerpc_Linux
a50daa43249083dcbdb86ba96e259a636a2f269ce7ab8eb599f1793d502c1cfc  ./toybox/toybox_s390x_Linux
15f6a5bd1df200bb507370c2801ef0d147a74991ebf63e8d310c632d53d20258  ./toybox/toybox_sh4_Linux
```


---

- #### Bundled Commands
```console
Toybox 0.8.15 multicall binary (see https://landley.net/toybox)

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
uclampset ucsicontrol ulimit umount uname unicode uniq unix2dos unlink
unshare uptime usleep uudecode uuencode uuidgen vconfig vmstat w watch
watchdog wc wget which who whoami xargs xxd yes zcat 
```

---

- #### Sizes

```console
760K   ./toybox/toybox_amd_x86_64_Linux
884K   ./toybox/toybox_arm64_aarch64_Linux
799K   ./toybox/toybox_armv4l_Linux
787K   ./toybox/toybox_armv5l_Linux
779K   ./toybox/toybox_armv7l_Linux
660K   ./toybox/toybox_armv7m_Linux
779K   ./toybox/toybox_i486_Linux
779K   ./toybox/toybox_i686_Linux
758K   ./toybox/toybox_m68k_Linux
1.1M   ./toybox/toybox_microblaze_Linux
986K   ./toybox/toybox_mips64_Linux
1023K  ./toybox/toybox_mips_Linux
1.0M   ./toybox/toybox_mipsel_Linux
948K   ./toybox/toybox_powerpc64_Linux
948K   ./toybox/toybox_powerpc64le_Linux
879K   ./toybox/toybox_powerpc_Linux
952K   ./toybox/toybox_s390x_Linux
750K   ./toybox/toybox_sh4_Linux

```


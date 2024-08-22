
---
- #### Download [Twingate](https://github.com/schollz/twingate#install)
> - **Sources**
> > ```bash
> > --> Linux:
> >   - All binaries are downloaded using official apt sources inside containers
> >     - 'https://binaries.twingate.com/client/linux/install.sh' !# Client
> >     - 'https://binaries.twingate.com/connector/setup.sh'      !# Connector 
> >   - They are then extracted and optionally made static using 'StaticX' !# https://github.com/JonathonReinhart/staticx
> > 
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

!# Linux
--> aarch64 || arm64 [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/twingate/twingate_client_aarch64_arm64_dynamic_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/twingate/twingate_connector_aarch64_arm64_dynamic_Linux"
--> Amd x86_64 || x86_64 [64-bit] (SYSV)
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/twingate/twingate_client_amd_x86_64_dynamic_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/twingate/twingate_client_amd_x86_64_staticx_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/twingate/twingate_connector_amd_x86_64_dynamic_Linux"
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/twingate/twingate_connector_amd_x86_64_staticx_Linux"
--> ARM_abi|| ARMv4 || ARMv5 || ARMv7 (?) [32-bit]
-->  curl -qfSLO "https://raw.githubusercontent.com/Azathothas/Static-Binaries/main/twingate/twingate_connector_arm32v7_dynamic_Linux"

```
---
- #### Install Twingate
```bash
!# Recommended way to install Twingate is:

!# Linux
--> Client  !# Requires ROOT
 curl -qfsSLO "https://binaries.twingate.com/client/linux/install.sh" && sudo bash "./install.sh"
--> Connector !# Requires ROOT
 curl -qfsSLO "https://binaries.twingate.com/connector/setup.sh" && sudo bash "./setup.sh"

!# Windows
--> Client
  https://api.twingate.com/download/windows
--> Connector
  !# This is just a linux binary being run and passed through multipass (https://multipass.run/install)
  https://www.twingate.com/docs/deploy-connector-on-windows-with-chocolatey

!# Copy downloaded twingate binaries to /usr/bin || /usr/local/bin
!# For $HOME/bin
 mkdir -p "$HOME/bin" && export PATH="$HOME/bin:$PATH"

!# Move Downloaded twingate binaries to that DIR
 mv "$Path_To_twingate_Binary" "/usr/bin/twingate"
 
!# Give Writeable Perms
 chmod +xwr /usr/bin/twingate*
```

---
```console
$ file ./twingate/twingate_client_aarch64_arm64_dynamic_Linux ./twingate/twingate_client_amd_x86_64_dynamic_Linux ./twingate/twingate_client_amd_x86_64_staticx_Linux ./twingate/twingate_connector_aarch64_arm64_dynamic_Linux ./twingate/twingate_connector_amd_x86_64_dynamic_Linux ./twingate/twingate_connector_amd_x86_64_staticx_Linux ./twingate/twingate_connector_arm32v7_dynamic_Linux ./twingate/twingate_connector_version.txt ./twingate/twingate_connectorctl_aarch64_arm64_dynamic_Linux ./twingate/twingate_connectorctl_amd_x86_64_dynamic_Linux ./twingate/twingate_connectorctl_amd_x86_64_staticx_Linux ./twingate/twingate_connectorctl_arm32v7_dynamic_Linux ./twingate/twingate_notifier_aarch64_arm64_dynamic_Linux ./twingate/twingate_notifier_amd_x86_64_dynamic_Linux ./twingate/twingate_notifier_amd_x86_64_staticx_Linux ./twingate/twingate_version.txt
$ grep -v .txt
./twingate/twingate_client_aarch64_arm64_dynamic_Linux:       ELF 64-bit LSB pie executable, ARM aarch64, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux-aarch64.so.1, for GNU/Linux 3.7.0, BuildID[sha1]=09a0cf866f354f1c0aa954b71eb24e973e53d3cc, stripped
./twingate/twingate_client_amd_x86_64_dynamic_Linux:          ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 3.2.0, BuildID[sha1]=600f32d2712f37431886be71d49e018aba67239c, stripped
./twingate/twingate_client_amd_x86_64_staticx_Linux:          ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, stripped
./twingate/twingate_connector_aarch64_arm64_dynamic_Linux:    ELF 64-bit LSB pie executable, ARM aarch64, version 1 (GNU/Linux), dynamically linked, interpreter /lib/ld-linux-aarch64.so.1, BuildID[sha1]=82e99985c92ca7412c3758822dc1e317cdc3a7a8, for GNU/Linux 3.7.0, stripped
./twingate/twingate_connector_amd_x86_64_dynamic_Linux:       ELF 64-bit LSB pie executable, x86-64, version 1 (GNU/Linux), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=22ea850b147fa4f3e80778e5ddf3e000f29ebae5, for GNU/Linux 3.2.0, stripped
./twingate/twingate_connector_amd_x86_64_staticx_Linux:       ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, stripped
./twingate/twingate_connector_arm32v7_dynamic_Linux:          ELF 32-bit LSB pie executable, ARM, EABI5 version 1 (GNU/Linux), dynamically linked, interpreter /lib/ld-linux-armhf.so.3, BuildID[sha1]=8952defa0bb71dce0960228bda9905d2faa0e245, for GNU/Linux 3.2.0, stripped
./twingate/twingate_connectorctl_aarch64_arm64_dynamic_Linux: ELF 64-bit LSB pie executable, ARM aarch64, version 1 (GNU/Linux), dynamically linked, interpreter /lib/ld-linux-aarch64.so.1, BuildID[sha1]=c603470a71310b124aedbc7602d5d163a8942327, for GNU/Linux 3.7.0, stripped
./twingate/twingate_connectorctl_amd_x86_64_dynamic_Linux:    ELF 64-bit LSB pie executable, x86-64, version 1 (GNU/Linux), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=4f3760be02b2dd7eaa78ea5aa62700c1d5a1a467, for GNU/Linux 3.2.0, stripped
./twingate/twingate_connectorctl_amd_x86_64_staticx_Linux:    ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, stripped
./twingate/twingate_connectorctl_arm32v7_dynamic_Linux:       ELF 32-bit LSB pie executable, ARM, EABI5 version 1 (GNU/Linux), dynamically linked, interpreter /lib/ld-linux-armhf.so.3, BuildID[sha1]=c47f9d188f9baed2a3d60fa1472029d5b7b3f517, for GNU/Linux 3.2.0, stripped
./twingate/twingate_notifier_aarch64_arm64_dynamic_Linux:     ELF 64-bit LSB pie executable, ARM aarch64, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux-aarch64.so.1, for GNU/Linux 3.7.0, BuildID[sha1]=24f79daf7a4d312816f4a6dc6bb3c87615cb4098, stripped
./twingate/twingate_notifier_amd_x86_64_dynamic_Linux:        ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 3.2.0, BuildID[sha1]=2d58030e856c66e559c4ef567d3a652ed4f7768c, stripped
./twingate/twingate_notifier_amd_x86_64_staticx_Linux:        ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, stripped

--> SHA256SUM
69ec2dc59c9d82d386c1db256b44398c7b5beae05cece8c0c54a21764142861a  ./twingate/twingate_client_aarch64_arm64_dynamic_Linux
8422a36475f85221fab54841fef40ae2efa56ae4f5596ff0fbd52ef6b9d6a58f  ./twingate/twingate_client_amd_x86_64_dynamic_Linux
44e528e36ac7d73aaf4d355b05da8585fd41f72348d3c911591edc0416529c41  ./twingate/twingate_client_amd_x86_64_staticx_Linux
16ffec8725864dddbdb462424f124383c59e5b388d2e196b94e5e2628bd96cc1  ./twingate/twingate_connector_aarch64_arm64_dynamic_Linux
c6a07597271078cf48cd66dec6abecf154a08eca80dc4564d9d11562dbf76c31  ./twingate/twingate_connector_amd_x86_64_dynamic_Linux
b0cdf9b7c5623272904c9faf0853b4b9cbf2bc86eb4735ef81fabbf7987e1158  ./twingate/twingate_connector_amd_x86_64_staticx_Linux
b0c1d172bd116515fb660ca2c915fd0551c349065498fbe10993eb2a9c4ae85a  ./twingate/twingate_connector_arm32v7_dynamic_Linux
7e2043d8a2e4377ce0747fc5b74c8372cb7b3320e50089c4321cd75fe9608bee  ./twingate/twingate_connectorctl_aarch64_arm64_dynamic_Linux
1d85e4f704b4221be60bbc7d562cc49b79a56e82379a8704c4e40dc27c77d119  ./twingate/twingate_connectorctl_amd_x86_64_dynamic_Linux
1ceac1d0b0e2c1ea07abec7e2444a76eb48d61f22f395ca758914a9a295e396e  ./twingate/twingate_connectorctl_amd_x86_64_staticx_Linux
3c92ea355ea26efae1d06c7187ecf450dabf8720484ecaba1577e0e5e5ba814c  ./twingate/twingate_connectorctl_arm32v7_dynamic_Linux
6dcde2293aa8f08158e268029a3eb63ddc03be58a97541dbae6632a26df75053  ./twingate/twingate_notifier_aarch64_arm64_dynamic_Linux
fe6b6d49a5b6ba12e836b906fb04bbc91760c570c3a04e0899740b2d62956544  ./twingate/twingate_notifier_amd_x86_64_dynamic_Linux
c8778ba10341c6bdcb2a14b06fed96dea5cc089470e71d65acc31a246d3cf5a4  ./twingate/twingate_notifier_amd_x86_64_staticx_Linux
```


---

- #### Versions
```console
$ ./twingate/twingate_client_amd_x86_64_dynamic_Linux --version
Twingate 2024.219.127389 | 0.162.2

Twingate 2024.219.127389 | 0.162.2
Copyright (C) 2024 Twingate

Twingate allows you to connect to private, remote resources as if they were
available locally. Only network traffic intended for your private resources
is routed via Twingate. For more detailed information: https://docs.twingate.com

Usage: twingate_client_amd_x86_64_dynamic_Linux [OPTIONS] <COMMAND>

Commands:
  setup            First-time setup & configuration
  version          Show version information and exit
  start            Connect to your Twingate network
  service-start    Start Twingate daemon
  desktop-restart  Restart UI notifications
  desktop-start    Start UI notifications
  stop             Disconnect from your Twingate network
  service-stop     Stop Twingate daemon
  desktop-stop     Stop UI notifications
  status           Return the status of Twingate network
  resources        Display a list of authorized resources
  auth             Initiate the authentication process for a locked resource
  config           Configure Twingate
  report           Collect diagnostic information
  help             Print this message or the help of the given subcommand(s)

Options:
  -p, --print-commands                Print commands instead of running them
  -d, --disable-colors                Disable colors in command output
  -n, --disable-network-verification  Accept the network value without verification
  -h, --help                          Print help
  -V, --version                       Print version


$ ./twingate/twingate_connector_amd_x86_64_dynamic_Linux --version
1.69.0

The Twingate Connector runs inside your network and connects you to your Resources.

Usage: twingate_connector_amd_x86_64_dynamic_Linux [OPTIONS] <--controller-url <CONTROLLER_URL>|--controller-network <CONTROLLER_NETWORK>|--features>

Options:
  -u, --controller-url <CONTROLLER_URL>
          Twingate Network URL (ex: https://mynetwork.twingate.com) [env: TWINGATE_URL=]
  -n, --controller-network <CONTROLLER_NETWORK>
          Twingate Network name (ex: mynetwork) [env: TWINGATE_NETWORK=]
  -l, --log-level <LOG_LEVEL>
          Log level (-1 to 7: -1 for no logs, 0 - least verbose, 7 - most verbose) [env: TWINGATE_LOG_LEVEL=] [default: 3]
      --log-timestamp-format <LOG_TIMESTAMP_FORMAT>
          Log timestamp format (0 - None, 1 - Relative to start, 2 - Absolute) [env: TWINGATE_TIMESTAMP_FORMAT=] [default: 0]
      --log-analytics <LOG_ANALYTICS>
          Enable local analytics logs in STDOUT [env: TWINGATE_LOG_ANALYTICS=] [possible values: v1, v2]
      --dns <DNS>...
          Custom DNS servers (comma separated) [env: TWINGATE_DNS=]
      --systemd-watchdog
          Enable systemd watchdog
  -h, --help
          Print help
  -V, --version
          Print version
```

---

- #### Sizes

```console
4.8M  ./twingate/twingate_client_aarch64_arm64_dynamic_Linux
5.5M  ./twingate/twingate_client_amd_x86_64_dynamic_Linux
3.6M  ./twingate/twingate_client_amd_x86_64_staticx_Linux
17M   ./twingate/twingate_connector_aarch64_arm64_dynamic_Linux
18M   ./twingate/twingate_connector_amd_x86_64_dynamic_Linux
7.1M  ./twingate/twingate_connector_amd_x86_64_staticx_Linux
12M   ./twingate/twingate_connector_arm32v7_dynamic_Linux
12M   ./twingate/twingate_connectorctl_aarch64_arm64_dynamic_Linux
12M   ./twingate/twingate_connectorctl_amd_x86_64_dynamic_Linux
4.4M  ./twingate/twingate_connectorctl_amd_x86_64_staticx_Linux
6.9M  ./twingate/twingate_connectorctl_arm32v7_dynamic_Linux
4.2M  ./twingate/twingate_notifier_aarch64_arm64_dynamic_Linux
4.8M  ./twingate/twingate_notifier_amd_x86_64_dynamic_Linux
4.0M  ./twingate/twingate_notifier_amd_x86_64_staticx_Linux

```


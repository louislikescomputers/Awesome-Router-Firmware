# Awesome Router Firmware

> A curated list of custom router firmware, the hardware each one supports, and the tools and add-ons that go with them.

Flashing custom firmware can brick your device and void your warranty. Always check the **exact model and hardware revision** (v1, v2, etc.) against the project's official compatibility list before flashing. Compatibility lists change constantly, so the device lists below are representative examples, not exhaustive. The official database linked under each firmware is the source of truth.

## Contents

- [Quick Comparison](#quick-comparison)
- [General-Purpose Firmware](#general-purpose-firmware)
  - [OpenWrt](#openwrt)
  - [DD-WRT](#dd-wrt)
  - [Tomato Family](#tomato-family)
  - [Asuswrt-Merlin](#asuswrt-merlin)
- [OpenWrt-Based Distributions and Forks](#openwrt-based-distributions-and-forks)
- [Other Router Firmware](#other-router-firmware)
- [Firewall and Router Operating Systems (x86/ARM)](#firewall-and-router-operating-systems-x86arm)
- [Historical and Discontinued Firmware](#historical-and-discontinued-firmware)
- [Add-ons, Packages and Tools](#add-ons-packages-and-tools)
- [Choosing Firmware](#choosing-firmware)
- [Before You Flash](#before-you-flash)
- [Communities and Learning](#communities-and-learning)

---

## Quick Comparison

| Firmware | Base | Best For | Hardware Breadth | Package Manager | Status |
|---|---|---|---|---|---|
| [OpenWrt](#openwrt) | Linux | Flexibility, security, everything | Very wide (hundreds of devices) | `opkg` / `apk` | Active |
| [DD-WRT](#dd-wrt) | Linux | Feature-rich UI, older and varied hardware | Wide | Limited (Entware optional) | Active |
| [FreshTomato](#freshtomato) | Linux (Tomato) | Clean UI, QoS, stability on Broadcom | Broadcom-based routers | Entware optional | Active |
| [Tomato64](#tomato64) | Linux (Tomato) | x86_64 PCs and Raspberry Pi | x86_64 and ARM SBCs | Entware optional | Active |
| [Asuswrt-Merlin](#asuswrt-merlin) | ASUS stock + patches | ASUS owners wanting stock-plus | ASUS only | Entware optional | Active |
| [AdvancedTomato](#advancedtomato) | Tomato (Shibby) | Modern Tomato web UI | Broadcom-based routers | Entware optional | Discontinued |
| [Gargoyle](#gargoyle) | OpenWrt | Bandwidth monitoring and quotas | OpenWrt-compatible | `opkg` | Low activity |
| [libreCMC](#librecmc) | OpenWrt | 100% free software | Limited | `opkg` | Low activity |
| [ImmortalWrt](#immortalwrt) | OpenWrt | Extra drivers and packages, wide China-market hardware | Very wide | `opkg` / `apk` | Active |
| [Padavan](#padavan) | Linux | Low-resource MediaTek/Ralink devices | Select MediaTek/Ralink | None | Community |
| [Freetz-NG](#freetz-ng) | AVM stock + patches | FRITZ!Box owners | AVM FRITZ!Box only | Built-in | Community |

---

## General-Purpose Firmware

### OpenWrt

- **Website:** https://openwrt.org
- **Supported hardware:** https://openwrt.org/toh/start (Table of Hardware)
- **Firmware selector:** https://firmware-selector.openwrt.org
- **Source:** https://github.com/openwrt/openwrt

The most flexible and widely supported open-source router operating system. Fully writable filesystem, a large package repository, LuCI web UI, and a strong security track record.

**Highlights:** SQM/CAKE bufferbloat control, WireGuard/OpenVPN, VLANs, multi-WAN (mwan3), mesh (802.11s), `adblock`/`banIP`, Docker on capable hardware, DSA switch support.

**Architectures:** MIPS, ARM/ARM64, x86/x86_64, RISC-V, and others.

**Representative supported devices:**

| Vendor | Example Models |
|---|---|
| OpenWrt (official) | OpenWrt One |
| TP-Link | Archer C7, Archer A7, Archer C6, TL-WR841N, TL-WR1043ND, Archer AX23, Archer AX55 (varies by version) |
| Netgear | R7800 (Nighthawk X4S), WNDR3700, WNDR4300, R7000 (limited), WAX202 |
| Linksys | WRT1200AC, WRT1900ACS, WRT3200ACM, WRT32X, E8450 / Belkin RT3200 |
| GL.iNet | GL-MT300N-V2, GL-AR750S, GL-MT3000 (Beryl AX), GL-MT6000 (Flint 2), GL-AXT1800 |
| Ubiquiti | EdgeRouter X, EdgeRouter 4, UniFi AP AC Lite/LR/Pro |
| ASUS | RT-AC58U, RT-AX53U, RT-AX57, RT-AX89X, ZenWiFi series (limited) |
| Xiaomi | Mi Router 4A Gigabit, Mi Router 3G, Redmi AX6S, AX3200 |
| D-Link | DIR-860L B1, DIR-825, DIR-505 |
| MikroTik | hAP ac2, hAP ac3, RB750Gr3, RB5009 |
| Banana Pi | BPI-R3, BPI-R4, BPI-R64 |
| Dynalink | DL-WRX36 |
| Single-board / PC | Raspberry Pi 3/4/5, NanoPi R4S/R5S, generic x86_64 |

---

### DD-WRT

- **Website:** https://dd-wrt.com
- **Router database:** https://dd-wrt.com/support/router-database/
- **Forum:** https://forum.dd-wrt.com

One of the oldest and best known custom firmwares. Feature-rich web UI with a lot of options in one image, and compatibility with a very wide span of older hardware.

**Highlights:** WDS and repeater modes, VPN (OpenVPN, WireGuard), hotspot support (Chillispot, Sputnik), QoS, Wi-Fi power tuning, SSH/Telnet, JFFS2 storage.

**Chipset families:** Broadcom, Atheros/Qualcomm, Ralink/MediaTek, Intel IXP, x86, and others.

**Representative supported devices:**

| Vendor | Example Models |
|---|---|
| Linksys | WRT54G / GS / GL, WRT160N, WRT310N, WRT610N, E1000, E2000, E3000, E4200, EA6500, WRT1900AC |
| Netgear | R6300v2, R6400, R7000, R7800, R8000, WNDR3700, WNDR4500 |
| ASUS | RT-N12, RT-N16, RT-N66U, RT-AC56U, RT-AC66U, RT-AC68U, RT-AC87U, RT-AC3200 |
| TP-Link | Archer C7, WDR3600, WDR4300, WR1043ND, WR841N |
| Buffalo | WHR-HP-G300N, WZR-HP-G300NH, WZR-HP-AG300H, WZR-1750DHP |
| D-Link | DIR-300, DIR-615, DIR-825, DIR-860L |
| Ubiquiti | NanoStation, Bullet, PicoStation, UniFi AP |
| Others | Belkin, Dell, Cisco, Western Digital, Gateworks, x86 PCs |

> DD-WRT publishes builds at different feature levels (mini, micro, std, mega, big, etc.). Choose the build size that fits your device flash size.

---

### Tomato Family

The Tomato lineage began with the original Tomato firmware by Jonathan Zarate and has been carried forward by multiple forks. Known for a clean, graphical bandwidth monitor and good QoS.

#### FreshTomato

- **Website:** https://freshtomato.org
- **Based on:** TomatoUSB / Tomato by Shibby lineage
- **Status:** Active; the most current maintained Tomato fork

**Highlights:** Real-time bandwidth graphs, QoS, VLAN, OpenVPN/WireGuard, USB storage, IPv6, scripting, Entware support.

**Builds:** Separate MIPS and ARM builds, and a range of image sizes (e.g. Lite, Standard, Max).

**Representative supported devices (Broadcom-based):**

| Vendor | Example Models |
|---|---|
| ASUS | RT-N12, RT-N16, RT-N18U, RT-N66U, RT-AC56U, RT-AC66U, RT-AC68U, RT-AC86U, RT-AC87U, RT-AC88U, RT-AC3100, RT-AC5300 |
| Netgear | WNR3500L, WNDR4000, R6250, R6300v2, R6400, R7000, R7900, R8000 |
| Linksys | WRT54GL, E3000, E4200, EA6200, EA6400, EA6500v2, EA6700, EA6900 |
| D-Link | DIR-868L, DIR-885L, DIR-890L |
| Tenda | AC15, AC18 |
| Others | Huawei WS880, select Buffalo and Belkin models |

#### Tomato64

- **Website:** https://tomato64.org
- **Based on:** FreshTomato codebase ported to modern 64-bit targets
- **Targets:** x86_64 PCs and select ARM single-board computers (including Raspberry Pi); check the project site for the current list.

#### AdvancedTomato

- **Website:** https://advancedtomato.com
- **Status:** Discontinued/archived. Based on Tomato by Shibby with a redesigned, responsive web UI.
- **Hardware:** Broadcom-based routers supported by the Shibby builds (RT-N66U, RT-AC56U, RT-AC66U, RT-AC68U, Netgear R6250/R6300v2/R7000, Linksys E-series, and similar). Prefer FreshTomato for new installs, as it carries the same lineage with ongoing updates.

#### Other Tomato Variants (historical)

| Firmware | Notes |
|---|---|
| Tomato (Polaris/original) | The original by Jonathan Zarate, aimed at Broadcom WRT54G-class devices. |
| TomatoUSB | Added USB and N-class router support. |
| Tomato by Shibby | Widely used for ARM/MIPS Broadcom devices. Discontinued. |
| Tomato-RAF | Feature-expanded fork for a range of MIPS devices. |
| Toastman | Popular for QoS tuning and extras. Discontinued. |
| Victek | Tomato variant with additional hardware and features. |

---

### Asuswrt-Merlin

- **Website:** https://www.asuswrt-merlin.net
- **Source:** https://github.com/RMerl/asuswrt-merlin.ng
- **Fork with newer model support:** https://github.com/gnuton/asuswrt-merlin.ng
- **Supported hardware:** ASUS routers only

Not a replacement for the ASUS firmware but an enhanced version of it. It keeps the stock UI and driver quality while adding features, fixes, and security updates.

**Highlights:** Enhanced VPN client/server support, custom scripts (`/jffs/scripts`), Entware, Diversion/Skynet addons, AiMesh compatibility, tuned Wi-Fi and QoS.

**Representative supported devices:**

| Series | Example Models |
|---|---|
| Wi-Fi 6 / 6E (AX) | RT-AX56U, RT-AX58U, RT-AX68U, RT-AX86U, RT-AX88U, RT-AX86S, RT-AX3000, GT-AX6000, GT-AX11000, GT-AXE11000 |
| Wi-Fi 5 (AC) | RT-AC66U B1, RT-AC68U, RT-AC86U, RT-AC87U, RT-AC88U, RT-AC3100, RT-AC5300 |
| Others | Older RT-N66U, RT-N16, and similar are on legacy branches |

> ASUS retires models and Merlin drops older ones, so check the project's support list for your exact model and the branch it needs.

---

## OpenWrt-Based Distributions and Forks

### ImmortalWrt

- **Website:** https://immortalwrt.org
- **Source:** https://github.com/immortalwrt/immortalwrt
- An OpenWrt fork with extra device support, additional drivers, and a larger set of pre-packaged apps. Popular for hardware common in the Asian market (Xiaomi, Cudy, Redmi, and others).

### GL.iNet Firmware

- **Website:** https://www.gl-inet.com
- OpenWrt-based vendor firmware with a simplified UI, shipped on GL.iNet travel and home routers. A great stepping stone toward vanilla OpenWrt.

### Turris OS

- **Website:** https://www.turris.com/en/turris-os/
- OpenWrt-based firmware for the **Turris Omnia**, **Turris MOX**, and **Turris Shield** routers. Notable for automatic updates and security-focused features.

### Gargoyle

- **Website:** https://www.gargoyle-router.com
- OpenWrt-based with a focus on bandwidth monitoring, quotas, and per-user usage controls.

### libreCMC

- **Website:** https://librecmc.org
- A fully free-software OpenWrt-derived distribution, endorsed by the Free Software Foundation. Hardware is limited to devices that can run without proprietary blobs.

### Gluon (Freifunk)

- **Website:** https://gluon.freifunk.net
- OpenWrt-based framework for building community mesh network firmware. Targets inexpensive routers such as TP-Link, Ubiquiti, and D-Link models.

### LibreMesh

- **Website:** https://libremesh.org
- OpenWrt-based framework for community mesh networks, centred on easy deployment and auto-configuration.

### OpenMPTCProuter

- **Website:** https://www.openmptcprouter.com
- OpenWrt-based solution for aggregating multiple internet connections (cellular, DSL, fibre) using Multipath TCP and a VPS.

### ROOter (GoldenOrb)

- **Website:** https://ofmodemsandmen.com
- OpenWrt-based firmware focused on 4G/5G cellular modem routers, with extensive modem support.

### X-WRT

- OpenWrt-derived firmware with a modern web UI aimed at consumer routers. Check the project's GitHub for current device lists.

---

## Other Router Firmware

### Padavan

- **Source:** https://gitlab.com/hadzhioglu/padavan-ng
- Lightweight firmware for MediaTek/Ralink-based routers, originally for the **ASUS RT-N56U**. Supports a number of Xiaomi, Netgear, and other devices with limited flash/RAM.

### Freetz-NG

- **Source:** https://github.com/Freetz-NG/freetz-ng
- Modifies the stock AVM firmware for **FRITZ!Box** routers. Lets you add or remove packages and features while keeping AVM's drivers.

### EdgeOS / UniFi Community Builds

- Ubiquiti's own firmware, but with active community add-on projects. EdgeRouter devices can also run OpenWrt.

---

## Firewall and Router Operating Systems (x86/ARM)

These are full operating systems for a PC, mini-PC, or appliance acting as the router, rather than firmware for consumer devices.

| Project | Website | Notes |
|---|---|---|
| OPNsense | https://opnsense.org | FreeBSD-based, modern UI, frequent releases. |
| pfSense CE | https://www.pfsense.org | FreeBSD-based, widely deployed, large community. |
| VyOS | https://vyos.io | Debian-based, CLI-driven, Junos/Vyatta-style router OS. |
| IPFire | https://www.ipfire.org | Linux-based hardened firewall distribution. |
| OpenWrt (x86) | https://openwrt.org | Runs on x86_64 mini-PCs, including N100-class boxes. |
| Tomato64 | https://tomato64.org | Tomato lineage on x86_64. |
| MikroTik RouterOS | https://mikrotik.com | Vendor OS; the CHR image runs as a virtual machine. |

---

## Historical and Discontinued Firmware

Worth knowing about for context, or if you still have old gear.

| Firmware | Notes |
|---|---|
| LEDE | Fork of OpenWrt that merged back into OpenWrt in 2018. |
| Sveasoft (Talisman/Alchemy) | Early WRT54G custom firmware; commercial/subscription model. |
| HyperWRT | Early Linksys WRT54G firmware modification. |
| m0n0wall | Early FreeBSD firewall; precursor to pfSense and OPNsense. |
| Tomato by Shibby | Discontinued; lineage continues in FreshTomato. |
| Toastman Tomato | Discontinued. |
| AdvancedTomato | Discontinued; see FreshTomato. |
| Openwrt-based Lede-forks | Many small forks have come and gone; check activity before adopting. |

---

## Add-ons, Packages and Tools

### Package Managers and Extras

| Tool | Description | Link |
|---|---|---|
| Entware | Package repository for routers that lack their own (Merlin, Tomato, DD-WRT, etc.) | https://github.com/Entware/Entware |
| OpenWrt Image Builder | Build custom images with your packages pre-installed | https://openwrt.org/docs/guide-user/additional-software/imagebuilder |
| Attended Sysupgrade (ASU) | Upgrade OpenWrt while keeping your installed packages | https://openwrt.org/docs/guide-user/installation/sysupgrade.owut |
| OpenWrt Firmware Selector | Web tool to find and download the right image | https://firmware-selector.openwrt.org |

### Network Features and Add-ons

| Tool | Works With | Description |
|---|---|---|
| SQM / CAKE | OpenWrt, others | Smart queue management to reduce bufferbloat |
| WireGuard | OpenWrt, DD-WRT, FreshTomato, Merlin | Modern, fast VPN |
| adblock-fast / adblock / banIP | OpenWrt | Network-wide ad and malware blocking |
| Pi-hole / AdGuard Home | Any (run on router or separate device) | DNS-level ad blocking |
| mwan3 | OpenWrt | Multi-WAN failover and load balancing |
| Diversion | Asuswrt-Merlin | Ad blocking using Pi-hole style lists |
| Skynet | Asuswrt-Merlin | Firewall and IP-blocking addon |
| AMTM | Asuswrt-Merlin | Addon manager for Merlin scripts |
| YazFi / scMerlin / spdMerlin | Asuswrt-Merlin | Guest-network, service-control, and speed-test add-ons |

### Flashing and Recovery Tools

- **TFTP:** Standard recovery method for many routers (e.g. TP-Link, Netgear, ASUS Rescue Mode).
- **Serial (UART) console:** For debugging and recovering bricked devices.
- **U-Boot web recovery:** Used on some devices (e.g. Xiaomi, GL.iNet).
- **Vendor recovery utilities:** ASUS Firmware Restoration, Netgear Nmrp tools, etc.

---

## Choosing Firmware

| If you... | Consider |
|---|---|
| Want maximum flexibility and long-term support | **OpenWrt** |
| Have an older router and want an all-in-one image | **DD-WRT** |
| Have a Broadcom router and want a clean, stable UI | **FreshTomato** |
| Own an ASUS router and want stock-plus | **Asuswrt-Merlin** |
| Want to run on an old PC or mini-PC | **OpenWrt x86**, **OPNsense**, **pfSense**, or **Tomato64** |
| Own a FRITZ!Box | **Freetz-NG** (or OpenWrt on supported FRITZ!Box models) |
| Need cellular failover or bonding | **OpenMPTCProuter** or **ROOter** |
| Run a community mesh | **Gluon** or **LibreMesh** |
| Need a hardened, security-focused router | **Turris OS** or **OpenWrt** |
| Want a simple travel router | **GL.iNet** (OpenWrt-based) |

---

## Before You Flash

1. **Verify the exact model and hardware revision.** Many vendors ship several incompatible versions under one model name.
2. **Read the device page.** OpenWrt Table of Hardware pages and DD-WRT forum threads often list special installation steps.
3. **Back up the original firmware** and your configuration if the device allows it.
4. **Use a wired connection** during flashing; never flash over Wi-Fi.
5. **Do not interrupt power** during the flash.
6. **Know your recovery path** (TFTP, serial, vendor recovery) before you begin.
7. **Check flash and RAM size.** Some builds do not fit on devices with 4 MB flash or 32 MB RAM.
8. **Mind regulations.** Changing transmit power or channels may violate local rules.
9. **Understand proprietary driver limits.** Broadcom Wi-Fi support is often better on Tomato, DD-WRT, and Merlin than on OpenWrt, while Qualcomm/MediaTek devices tend to do well on OpenWrt.

---

## Communities and Learning

- [OpenWrt Forum](https://forum.openwrt.org)
- [OpenWrt Wiki](https://openwrt.org/docs/start)
- [DD-WRT Forum](https://forum.dd-wrt.com)
- [SmallNetBuilder Forums](https://www.snbforums.com) (Asuswrt-Merlin, Tomato, and general router firmware)
- [r/openwrt](https://www.reddit.com/r/openwrt/)
- [r/HomeNetworking](https://www.reddit.com/r/HomeNetworking/)
- [Freifunk](https://freifunk.net)

---

## Contributing

Know of a firmware that is missing, a dead link, or a device that changed status? Open an issue or pull request with:

- The firmware name and link
- A short description
- Link to its official supported-hardware list
- Current maintenance status

## License

Released under [CC0](https://creativecommons.org/publicdomain/zero/1.0/). Do whatever you like with it.

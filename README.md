> ⚠️ This repository is not maintained anymore, I don't own a `NUC9I7QNX` anymore.

# Hackintosh NUC9I7QNX OpenCore

[![tippin_svg]][tippin_url]

[tippin_svg]: https://img.shields.io/badge/donate-BuyMeACoffee-ffdd00?logo=buymeacoffee&style=flat
[tippin_url]: https://www.buymeacoffee.com/bemble

> I love Mac OS and I use it for years. I could buy a Mac Mini M1, but I wont buy an unrepairable and unupgradable desktop computer. I expect durable computers, as much as I can.

![About](about.png)

## System Specification

- Processor: Intel® Core™ i7-9750H Processor (6 cores, 12 MB Cache, 2.6 GHz to 4.50 GHz)
- Network: Built-in Intel `i210` (the bottom one) Built-in Intel `i219-LM` (the top one)
- Wifi/BT: Broadcom `BCM94360CS2` :wrench: + Built-in Intel `AX200`
- Audio: Built-in `Realtek ALC256`
- Graphics: Sapphire Pulse `RX 570` 4GB ITX + Built-in Intel `UHD Graphics 630` 2048 MB
- Thunderbolt: Built-in Intel `JHL7540`
- Memory: G.Skill RIPJAWS 2x16 GB 2666 MHz DDR4
- Main Hard Disk: NVMe Samsung EVO 970 500 GB
- Secondary Hard Disk: M.2 Sata Sandisk 500GB

## OpenCore

- Version: [0.7.8](https://github.com/acidanthera/OpenCorePkg/releases/tag/0.7.8)
- Generate SMBios using `Macmini8,1` type and add to `config.plist > PlatformInfo > Generic`

## Bios Settings

- BIOS Version: `QXCFL579`
- First, restore default BIOS config: `F9 - Optimal Defaults`

### Configuration

- Advanced
  - USB > `Legacy USB Support: Enabled`
- Security
  - Security Features > `Intel Platform Trust Technology: Unchecked`
  - Security Features > `Intel Software Guard Extension (SGX): Disabled`
  - Security Features > `Thunderbold Security Level: Legacy mode`
- Boot
  - Secure Boot > `Secure Boot: Disabled`
  - boot Priority > `Fast Boot: Unchecked`
  - boot Priority > `Network Boot: Disabled`
  - boot Priority > `Ethernet1 Boot: Unchecked`
  - boot Priority > `Ethernet2 Boot: Unchecked`


## Install

Due to USB error on Big Sur 11.3+ and image of 11.2 hard to find, a clean installation has to be done from Catalina using `EFI_INSTALL`.
Once installed, upgrade to Big Sur 11.3+ and use `EFI`.

Don't forget to add the serial number etc in both `config.plist` files.

## Hardware

- [x] GPU acceleration: built-in `Intel UHD 630`
- [x] GPU acceleration: `RX 570` (out of the box)
- [x] Ethernet :zap:
- [x] Audio (Front Panel Headphone)
- [x] Audio (Rear Panel Headphone)
- [x] USB A ports
- [x] SD card slot
- [x] NVMe SSD
- [x] Wifi :zap:
- [x] Bluetooth :zap:
- [x] USB C ports
- [x] Airpods Pro (battery level/noise reduction mode switch)
- [x] CPU power management (tested using Intel Power Gadget)

## Software

- [x] Installer, App Store, App updates
- [x] Update MacOS directly from Apple
- [x] APFS, SSD TRIM
- [x] iMessage, iCloud, Siri, iTunes, other services
- [ ] Handoff, Continuity, Universal Clipboard: **built-in `Intel AX200`**
- [x] Handoff, Continuity, Universal Clipboard: **Broadcom `BCM94360CS2`**
- [x] Metal, GPU accelerated applications: **built-in `Intel UHD 630`**
- [x] Metal, GPU accelerated applications: **Sapphire Pulse `RX 570`**
- [x] Time Machine
- [x] Sleep mode
- [x] Shutdown/Sleep/Wake
- [x] Schedule Start up or Wake
- [x] Screenshare (VNC)
- [ ] Wake On Screenshare

## :wrench: Add Broadcom `BCM94360CS2` wifi card

The idea was to plug the wifi card on a M.2 slot and use built-in wifi card antenna with the new one.
Hardware problem for the antenna: built-in cables are MMCX male and `BCM94360CS2` are MHF4 (IPEX-4) female. The easiest way to have it running is to get antennas

### Hardware needed

- Broadcom `BCM94360CS2` wifi card
- [`BCM94360CS2` to M.2 Key-M adapter](https://www.amazon.fr/gp/product/B09B249QDL/ref=ppx_yo_dt_b_asin_title_o03_s00)
- [Antennas](https://www.amazon.fr/gp/product/B07N2SFZPX/ref=ppx_yo_dt_b_asin_title_o00_s00)

### Bios setting

To prevent any trouble, you should disable built-in wifi:

- Advanced
  - Onboard Devices > `WLAN: uncheck`

## :zap: Errors and other

- Built-in wifi connect on 5Ghz network but does not uses `ac` protocol:  
  ![Wifi](wifi.png)
- Speedtest:  
  ![Speedtest](speedtest.jpg)

## :zap: MacOS Monterey 12.2

- `i210` ethernet (the bottom one) does not work, `SmallTree` causes kernel panic on Monterey ([issue here](https://github.com/khronokernel/SmallTree-I211-AT-patch/issues/3))
- Broadcom `BCM94360CS2` does not work: wifi card is listed in hardware but cannot be enabled

## :zap: MacOS Big Sur 11.3

- No USB after update, to fix it:
  - Enable `config.plist` > `Kernel` > `Add` > `USBInjectAll` kext
  - Disable `config.plist` > `Kernel` > `Add` > `USBMap` kext
  - Disable `config.plist` > `Kernel` > `Quirks` > `XhciPortLimit`

## Not tested Hardware

- Audio (Microphone, Toslink)
- HDMI/DP audio
- Video encoder/decoder hardware
- Multiple displays
- Thunderbolt 3 port
- Secure Boot (with High Security)

## Not tested Software

- FileVault2
- SIP, Gate Keeper, all OSX security features

## OS Version Tested

Here is my install/update history, the upper one is the latest:

- `[update]` MacOS Monterey 12.3.1 (21E258)
- `[update]` MacOS Monterey 12.2.1 (21D62)
- `[install]` MacOS Catalina 10.15.7 (19H15)
- `[update]` MacOS Big Sur 11.4 (20F71)
- `[update]` MacOS Big Sur 11.3 (20E232)
- `[install]` MacOS Big Sur 11.2.3 (20D91)

## Tools

- [MountEFI tool](https://github.com/corpnewt/MountEFI)
- [GenSMBIOS tool](https://github.com/corpnewt/GenSMBIOS)
- [ProperTree tool](https://github.com/corpnewt/ProperTree)
- [USBMap tool](https://github.com/corpnewt/USBMap)
- [OCConfigCompare](https://github.com/corpnewt/OCConfigCompare)
- [gfxutil](https://github.com/acidanthera/gfxutil)

## Kexts

- [Lilu v1.6.0](https://github.com/acidanthera/Lilu/releases/tag/1.6.0)
- [VirtualSMC v1.2.8](https://github.com/acidanthera/VirtualSMC/releases/tag/1.2.8)
- [WhateverGreen v1.5.7](https://github.com/acidanthera/WhateverGreen/releases/tag/1.5.7)
- Audio: [AppleALC v1.6.9](https://github.com/acidanthera/AppleALC/releases/tag/1.6.9)
- LAN: [IntelMausi v1.0.7](https://github.com/acidanthera/IntelMausi/releases/tag/1.0.7)
- Bluetooth: [IntelBluetoothFirmware v2.1.0](https://github.com/OpenIntelWireless/IntelBluetoothFirmware/releases/tag/v2.1.0)
- Built-in Wifi: [AirportItlwm v2.1.0](https://github.com/OpenIntelWireless/itlwm/releases/tag/v2.1.0)
- USB: [USBInjectAll v2018-1108](https://bitbucket.org/RehabMan/os-x-usb-inject-all/downloads/?tab=downloads)
- NVMe: [NVMeFix v1.0.9](https://github.com/acidanthera/NVMeFix/releases/tag/1.0.9)

## Resources

- [OpenCore Sanity Checker](https://opencore.slowgeek.com)
- [Hac Mini Guide](https://osy.gitbook.io/hac-mini-guide/)
- [PcPerspective - Nuc9 Chipset](https://pcper.com/2020/04/intel-nuc-9-extreme-nuc9i9qnx-review/#ftoc-heading-19)
- [OpenCore Guide - config.plist](https://dortania.github.io/OpenCore-Install-Guide/config-laptop.plist/coffee-lake-plus.html#starting-point)
- [OpenCore Guide - Generate SMBios](https://dortania.github.io/OpenCore-Install-Guide/config-laptop.plist/coffee-lake-plus.html#platforminfo)
- [OpenCore Guide - Choosing the right SMBios](https://dortania.github.io/OpenCore-Install-Guide/extras/smbios-support.html#how-to-decide)
- [OpenCore Guide - HDD boot](https://dortania.github.io/OpenCore-Post-Install/universal/oc2hdd.html#grabbing-opencore-off-the-usb)
- [OpenCore Guide - Debug Mode](https://dortania.github.io/OpenCore-Install-Guide/troubleshooting/debug.html)
- [OpenCore Guide - Update OpenCore](https://dortania.github.io/OpenCore-Post-Install/universal/update.html#_2-mount-your-efi)

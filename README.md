# Hackintosh NUC9I7QNX OpenCore

## System Specification
- Processor: Intel® Core™ i7-9750H Processor (6 cores, 12 MB Cache, 2.6 GHz to 4.50 GHz)
- Memory: G.Skill RIPJAWS 2x16 GB 2666 MHz DDR4
- Graphics: Intel UHD Graphics 630 2048 MB
- Hard Disk: NVMe Samsung EVO 970 500 GB 
- Wifi/BT: Built-in OEM

## OpenCore
- Version: [0.6.7](https://github.com/acidanthera/OpenCorePkg/releases/tag/0.6.7)
- Generate SMBios using `iMac19,1` type and add to `config.plist > PlatformInfo > Generic`

## Bios Settings
- BIOS Version: `QXCFL579`
- First, restore default BIOS config: `F9 - Optimal Defaults`

### Configuration
- Advanced
  - USB > `Legacy USB Support: Unchecked`
- Security
  - Security Features > `Intel Platform Trust Technology: Unchecked`
  - Security Features > `Intel Software Guard Extension (SGX): Disabled`
  - Security Features > `Thunderbold Security Level: Legacy mode`
- Power
  - Secondary Power Settings > `Wake On Lan from S4/S5: Stay off`
- Boot
  - Secure Boot > `Secure Boot: Disabled`
  - boot Priority > `Fast Boot: Unchecked`
  - boot Priority > `Network Boot: Disabled`
  - boot Priority > `Ethernet1 Boot: Unchecked`
  - boot Priority > `Ethernet2 Boot: Unchecked`

## Hardware

* [x] GPU acceleration
* [x] Ethernet
* [ ] Audio \(Headphone\)
* [x] USB A ports
* [x] SD card slot
* [x] NVMe SSD
* [ ] Wifi
* [x] Bluetooth \(Audio\)

## Software

* [x] Installer, App Store, App updates
* [x] APFS, SSD TRIM
* [x] iMessage, iCloud, Siri, iTunes, other services
* [ ] Handoff, Continuity, Universal Clipboard (Wifi required)
* [x] Airpods Pro
* [x] Metal, GPU accelerated applications
* [x] Time Machine

## Errors and other

* Could not add MX Keys for Mac keyboard using Bluetooth, nothing happened after adding the code, I had to use Unifying dongle
* Could not add MX Master 1 mouse at all

## Not tested Hardware
* HDMI/DP audio
* Video encoder/decoder hardware
* Multiple displays
* USB C ports
* Thunderbolt 3 port
* CPU power management
* Shutdown/Sleep/Wake
* Secure Boot \(with High Security\)

## Not tested  Software
* FileVault2
* SIP, Gate Keeper, all OSX security features
* Schedule Start up or Wake, Sleep
* Update macOS directly from Apple

## OS Version Tested
- macOS Big Sur 11.2.3 (20D91)

## Ressources
- [OpenCore Guide - config.plist](https://dortania.github.io/OpenCore-Install-Guide/config-laptop.plist/coffee-lake-plus.html#starting-point) 
- [OpenCore Guide - Generate SMBios](https://dortania.github.io/OpenCore-Install-Guide/config-laptop.plist/coffee-lake-plus.html#platforminfo)
- [OpenCore Guide - HDD boot](https://dortania.github.io/OpenCore-Post-Install/universal/oc2hdd.html#grabbing-opencore-off-the-usb)
- [OpenCore Guide - Debug Mode](https://dortania.github.io/OpenCore-Install-Guide/troubleshooting/debug.html)
- [MountEFI tool](https://github.com/corpnewt/MountEFI)
- [GenSMBIOS tool](https://github.com/corpnewt/GenSMBIOS)
- [ProperTree tool](https://github.com/corpnewt/ProperTree)

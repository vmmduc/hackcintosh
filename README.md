
# Acer Nitro 5 AN515-54 Hackintosh

macOS Ventura on Acer Nitro 5 AN515-54 with OpenCore 0.9.3 EFI folder.

## Configuration

| Specifications      | Details                                            |
| ------------------- | -------------------------------------------------- |
| Laptop Model        | AN515-52                                           |
| Processor           | Intel® Core™ i5-8300H                              |
| Graphics            | Intel® UHD Graphics 630 & Nvidia GeForce® GTX 1050 |
| RAM                 | 16GB DDR4-2666Mhz                                  |
| Disk                | SSD SAMSUNG 512gb PCIe® NVMe™                      |
| Audio               | Realtek HD Audio ALC255                            |
| Wifi                | Intel(R) Wireless-AC 9560 160MHz                   |
| Ethernet            | RealTek RTL8168/8111 PCI-E Gigabit Ethernet        |

## What's working

- [x] Audio (Input & Output)
- [x] iGPU
- [x] ACPI Display brightness
- [x] Ethernet
- [x] Sleep + Wake
- [x] Smart Touchpad + Gestures
- [x] WiFi (2.4Ghz and 5GHz)
- [x] Native hotkey support with Fn keys
- [x] iServices (Messages, FaceTime, etc.)

## What's not working

- [ ] GTX 1050 (macOS does not support recent Nvidia GPUs).
- [ ] HDMI port (since it's connected to the GTX 1650).

## Installation

### First-time installation

- Set-up the BIOS configuration:
  - Boot to BIOS by pressing F2 during boot.
  - In the Main screen, enable F12 boot menu, disable Fast Boot, then press Ctrl+S and change the new SATA mode option to AHCI.
  - In the Boot screen, disable secure boot.
  - Finally, go to the Exit screen and select "Exit saving changes".
- Read through the following tutorial to create a bootable USB, and then place the EFI folder inside it:
   - https://dortania.github.io/OpenCore-Install-Guide/
- You should add Serial Number, UUID, MLB and ROM details to Config -> PlatformInfo -> Generic if you want to get iServices working as explained [here](https://dortania.github.io/OpenCore-Post-Install/universal/iservices.html).

## Disable CFG Lock (Advanced users only)

To disable CFG Lock, follow [this](https://www.reddit.com/r/hackintosh/comments/hz2rtm/cfg_lockunlocking_alternative_method/) guide. Note that you'll be modifying the BIOS, so be very careful or you could end up bricking your device. If you're not sure about something, do NOT do it.

After following the guide, disable Kernel -> Quirks -> AppleXcpmCfgLock and you're done.

## How to Fix "Not Enough Disk Space to Copy EFI" error
```bash
sudo -s
diskutil
newfs_msdos -v EFI /dev/disk1s1
```

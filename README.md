# Aorus-B550M-Elite-Hackintosh

Prebuilt opencore EFI for macos

## Specifications

| Specifications      | Detail                                      |
| ------------------- | ------------------------------------------- |
| Motherboard         | Gigabyte Aorus B500M Elite                  |
| CPU                 | AMD Ryzen 5 5600G                           |
| Memory              | 32GB Ram (4x8GB) Corsair Vengences DDR4     |
| SSD                 | Emtec 250GB SDD                             |
| Integrated GrÒaphics | AMD Radeon RX Vega 7 (disabled)             |
| GPU                 | AMD Radeon RX 6600 8GB                      |
| Sound Card          | ALC887                                      |
| Wireless Card       | /                                           |
| Ethernet/LAN        | Realtek® GbE LAN chip                       |

# Supported Version of macos
| MacOS version       | Link                                        |
| ------------------- | ------------------------------------------- |
| Tahoe 26            |  [EFI](https://github.com/GeantW0rld/Aorus-B550M-Elite-Hackintosh/tree/main/Tahoe)  |
| Sequoia 15          |  Tahoe EFI should work for Sequoia                 |
| Sonoma 14           |  [EFI](https://github.com/GeantW0rld/Aorus-B550M-Elite-Hackintosh/tree/main/Sonoma) |
| Ventura 13          |  SHOULD WORK* (Use Sonoma efi)              |
| Monterey 12         |  SHOULD WORK* (Use Sonoma efi)              |
| Big Sur 11          |  SHOULD WORK* (Use Sonoma efi)              |
*You can try it, but I won't be responsible if your system crashes or anything else happens.

# Configurations
You should use [ProperTree](https://github.com/corpnewt/ProperTree) as PLIST Editor or code-oriented text editor, OC Config. and OCAT : They do not always respect OpenCore's schema, They make changes without informing you, and auto-save these changes when opening your config, baking them in and They have no kext load order logic

- change to `Kernel -> Patch` the number of core (source: [AMD_Vanilla](https://github.com/AMD-OSX/AMD_Vanilla/blob/beta/README.md))

|   macOS Version      | Replace Value | New Value |
|----------------------|---------------|-----------|
| 10.13.x, 10.14.x     | B8000000 0000 | B8 < Core Count > 0000 0000 |
| 10.15.x, 11.x        | BA000000 0000 | BA < Core Count > 0000 0000 |
| 12.x, 13.0 to 13.2.1 | BA000000 0090 | BA < Core Count > 0000 0090 |
| 13.3 +               |  BA000000 00  | BA < Core Count > 0000 00 |

  - The Core Count patch needs to be modified to boot your system. Find the four `algrey - Force cpuid_cores_per_package` patches and alter the `Replace` value only.<br>From the table above substitue `< Core Count >` with the hexadecimal value matching your physical core count. Do not use your CPU's thread count. See the table below for the values matching your CPU core count.


| Core Count | Hexadecimal |
|------------|-------------|
|   4 Core   |     `04`    |
|   6 Core   |     `06`    |
|   8 Core   |     `08`    |
|   12 Core  |     `0C`    |
|   16 Core  |     `10`    |
|   24 Core  |     `18`    |
|   32 Core  |     `20`    |

For example, a user with a 6-core processor should use these `Replace` values: `B8 06 0000 0000` / `BA 06 0000 0000` / `BA 06 0000 0090` / `BA 06 0000 00`


- change SMBIOS with [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) and [replace it](https://dortania.github.io/OpenCore-Install-Guide/AMD/zen.html#platforminfo) (use MacPro7,1 or IMacPro1,1)

# Bios Settings
| settings            | Option                                      |
| ------------------- | ------------------------------------------- |
| Fastboot            |  Disabled                 |
| Secure Boot            |  Disabled                 |
| IOMMU            |  Disabled                 |
| CSM            |  Disabled                 |
| Above 4G Decoding            |  Enabled<sup>1</sup>                 |
| Resizable BAR Support           |  Enabled<sup>2</sup>                  |
| SATA Mode           |  AHCI                  |
| OS Type          |  Windows 10/UEFI<sup>3</sup>                  |

- <sup>1</sup> if you can't find the option then add `npci=0x3000` or `npci=0x2000` to boot-args
- <sup>2</sup> When enabling Above 4G, Resizable BAR Support can be enabled Please ensure that Booter -> Quirks -> ResizeAppleGpuBars is set to 0 if this is enabled.
- <sup>3</sup> some motherboards may require "Other OS" instead

# What's work
- Ethernet
- Sounds*
- GPU
- Bluetooth
- Iservices (IMessage, Icloud, etc..)

* It doesn't work on MacOS 26 Tahoe due to removal of AppleHDA

# What's doesn't work
- Cannot run VM due to the cpu

# Some screenshots
![Screenshot](./Images/info.png)

# Download
Go to release or download the repo zip file

# Credits
[Dortania](https://dortania.github.io/OpenCore-Install-Guide/) - Made the OpenCore guide

[AMD Vanilla](https://github.com/AMD-OSX/AMD_Vanilla) - Patch for AMD CPU

[Acidanthera](https://github.com/acidanthera) - OpenCore Bootloader |  AppleALC | Lilu | VirtualSMC | WhateverGreen | etc

[Apple](https://www.apple.com/) - Made MacOS

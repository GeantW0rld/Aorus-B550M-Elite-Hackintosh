# Aorus-B550M-Elite-Hackintosh
 
Prebuilt opencore EFI for macos

# Desktop specs
- CPU: AMD Ryzen 5 5600G
- GPU: AMD Radeon RX 6600
- Wifi: Not installed on this build
- Bluetooth: Cambridge Silicon Radio Ltd. (USB Bluetooth)
- Audio codec: ALC887
- LAN: Realtek® GbE LAN chip
- RAM: 32GB DDR4

# Supported Version of macos
- [MacOS Sonoma (tested)](https://github.com/GeantW0rld/Aorus-B550M-Elite-Hackintosh/tree/main/Sonoma)
- No support for MacOS ventura/Monterey/Big sur because not tested, create PR for update about they version

# Settings up
- change to `Kernel -> Patch` the number of core [more info here](https://dortania.github.io/OpenCore-Install-Guide/AMD/zen.html#patch-2)
![Screenshot](./Images/amd.png)

- change SMBIOS to a valid SMBIOS

# Bios Settings
[Please follow opencore guide for setup the bios!](https://dortania.github.io/OpenCore-Install-Guide/AMD/zen.html#amd-bios-settings)

# What's work
- Internet
- Sounds
- GPU

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
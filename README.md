# Dell-Inspiron-15-3580-Hackintosh
This repository and project hosts the files necessary to boot macOS Ventura successfully on the Dell Inspiron 15 3580 Laptop

# DISCLAIMER
I do not condone piracy, this is for education purposes only.

# Acknowledgements
- Acidanthera for [OpenCore Bootloader](https://github.com/acidanthera/OpenCorePkg)
- Dortania for [OpenCore Install Guide](https://dortania.github.io/OpenCore-Install-Guide)
  -  [Laptop Coffee Lake and Whiskey Lake](https://dortania.github.io/OpenCore-Install-Guide/config-laptop.plist/coffee-lake.html)
- Corpnewt for [SSDT Time](https://github.com/corpnewt/SSDTTime)
- USBToolbox for [USBToolbox](https://github.com/USBToolBox)
- And many more awesome people in the hackintosh community
  
# Deployment
To deploy this project properly, please obtain the EFI folder from this repository, edit the config.plist to generate new serial number, rom, UUID, etcetera, then save config.plist, and place the files onto the appropriate ESP EFI partition in order to boot using OpenCore bootloader and proceed with your installation of macOS.

# Hardware
_The hardware in this Machine is as follows_:
- CPU: Intel Core i5-8265U (Whiskey Lake)
- GPU: Intel UHD Graphics 620
- Mobo: Dell 0DCN56 Rev. A00
- Memory: 2x4GB DDR4 2400MHz 
- Drive: WDC SN530 NVMe 256GB
- DVD: HL-DT-ST DVD+-RW GU90N
- Keyboard & Touchpad: PS2 Keyboard & I2C Touchpad
- Ethernet: Realtek RTL8111
- Wifi & Bluetooth: Intel Wireless-AC 9560
- Audio: Realtek ALC236
- Microphone: Realtek ALC236
- Camera: USB Intergrated Webcam
- SD Card Reader: USB Realtek Memory Card Reader
- HDMI 1.4

# Drivers & Essential Kernel Extensions
| Required Drivers |
| ------------- |
| [HfsPlus.efi](https://github.com/acidanthera/OcBinaryData/blob/master/Drivers/HfsPlus.efi) |
| [OpenRuntime.efi](https://github.com/acidanthera/OpenCorePkg) |

| Essential Kexts |
| ------------- |
| [Lilu.kext](https://github.com/acidanthera/Lilu) |
| [VirtualSMC.kext](https://github.com/acidanthera/VirtualSMC) |

# Kernel Extensions corresponding to hardware
| Hardware  | Kext(s) |
| ------------- | ------------- |
| Intel UHD Graphics 620  | [Whatevergreen.kext](https://github.com/acidanthera/WhateverGreen)  |
| PS2 Keyboard | [VoodooPS2Controller.kext](https://github.com/acidanthera/VoodooPS2)  |
| I2C Touchpad | [VoodooI2C.kext and its satellite VoodooI2CHID.kext](https://github.com/VoodooI2C/VoodooI2C)  |
| Realtek RTL8111 | [RealtekRTL8111.kext](https://github.com/Mieze/RTL8111_driver_for_OS_X) |
| Intel 9560 Wifi | [AirportItlwm.kext](https://github.com/OpenIntelWireless/itlwm)|
| Intel 9560 Bluetooth | [IntelBluetoothFirmware.kext; IntelBTPatcher.kext](https://github.com/OpenIntelWireless/IntelBluetoothFirmware) & [BlueToolFixup.kext](https://github.com/acidanthera/BrcmPatchRAM)|
| NVMe Drive | [CtlnaAHCIPort.kext](https://github.com/dortania/OpenCore-Install-Guide/blob/master/extra-files/CtlnaAHCIPort.kext.zip) & [NVMeFix.kext](https://github.com/acidanthera/NVMeFix) |
| Audio & Microphone | [AppleALC.kext](https://github.com/acidanthera/AppleALC) with layout-id 69  |
| Camera & SD Card Reader | [USBToolBox.kext](https://github.com/USBToolBox/kext) & [UTBMap.kext](https://github.com/USBToolBox/tool)  |
| Brightness Key (Fn + F11/F12)  | [BrightnessKeys.kext](https://github.com/acidanthera/BrightnessKeys)  |

# Result
_Working_:
- iGPU
- Internal/External Audio & Microphone
- Wifi & Bluetooth
- Keyboard
- Touchpad
- USB ports
- Brightness Keys
- Battery Status
- Camera
- DVD Drive
- SD Card Reader
- HDMI 1080p 60fps

_Not working_:
- Airdrop (Intel Wireless)
- HDMI 4K 30fps (BIOS DVMT is 32MB)
  
# BIOS Settings
- **General**
  - Advanced Boot Options ~> Enable Legacy Option ROMS ~> Uncheck
 
- **System Configuration**
  - SATA Operation ~> AHCI
  - Virtualization Technology ~> Enabled
- **Secure Boot**
  - Secure Boot Enable ~> Uncheck
- **Intel Software Guard Extensions**
  - Intel SGX Enable ~> Disabled/Software Controlled
- **POST Behavior**
  - Fastboot ~> Thorough
- **Virtualization Support**
  - Virtualization ~> Enable Intel Virtualization Technology ~> Check
  - VT for Direct I/O ~> Enable VT for Direct I/O ~> Uncheck
> [!NOTE]
> VT for Direct I/O could be enabled if Kernel ~> Quirk ~> DisableIoMaper is enabled

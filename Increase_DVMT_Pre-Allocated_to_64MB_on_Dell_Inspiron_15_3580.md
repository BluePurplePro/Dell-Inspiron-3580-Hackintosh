# Acknowledgements
- [dreamwhite's Dell BIOS Extract Guide](https://github.com/dreamwhite/bios-extraction-guide/blob/master/Dell/README.md)
- [MaLd0n's How to fixing your DVMT Pre-Allocated for the perfect Hackintosh](https://olarila.com/topic/40092-how-to-fixing-your-dvmt-pre-allocated-for-the-perfect-hackintosh/)

## Introduction
I already found the VarOffset (VarStoreInfo/VarName): 0x8E7, VarStoreId: 0x1 (Name: Setup) inside the Inspiron 3580's BIOS (version 1.30)
![00](https://github.com/user-attachments/assets/9b3c6d58-0426-4b96-b3b6-a10f62b3d3bf)

All you have to do is create a boot drive for editing value on 0x8E7 in Setup to 0x2.

## Prepare the USB
1. Take a thumb drive and format it in `FAT32`. Make sure to use `GPT` partitioning scheme.
2. Download [EFI CFG RU.zip](https://github.com/user-attachments/files/19006164/EFI.CFG.RU.zip).
3. Extract EFI.CFG.RU.zip to the USB created in step 1. The directory tree should look like this:
```
EFI
└── BOOT
    └── BOOTx64.efi
```

# Boot from the USB and change the value on 0x8E7 in Setup to 0x2
1. Boot from the pendrive and you will see a screen like this. Press Enter.

![01](https://github.com/user-attachments/assets/c4e43f8b-3814-4b99-bcbf-bc10294cca0a)

2. Press **Alt** + **C** (Config) and select **UEFI variable**.

![02](https://github.com/user-attachments/assets/bfc72a45-5e7b-4a10-bcfb-b39f6d67eddd)

3. Scroll down to **Setup** and press Enter. Navigate to 0x8E7 (Row **08E0**, Colume **07**). After that, change this value to **02** ~> Press Enter. 

![03](https://github.com/user-attachments/assets/9294133e-8723-47c8-9c20-dbc41075e4e2)

4. Use **Ctrl** + **W** to save and **Alt** + **Q** to exit/reboot.

5. Now you can remove ``framebuffer-patch-enable`` in ``Device Properties`` ~> ``PciRoot(0x0)/Pci(0x2,0x0)``


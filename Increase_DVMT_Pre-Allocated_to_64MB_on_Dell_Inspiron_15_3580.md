# Acknowledgements
- [dreamwhite's Dell BIOS Extract Guide](https://github.com/dreamwhite/bios-extraction-guide/blob/master/Dell/README.md)
- [MaLd0n's How to fixing your DVMT Pre-Allocated for the perfect Hackintosh](https://olarila.com/topic/40092-how-to-fixing-your-dvmt-pre-allocated-for-the-perfect-hackintosh/)

## Introduction
I already found the VarOffset (VarStoreInfo/VarName): 0x8E7, VarStoreId: 0x1 (Name: Setup) inside the Inspiron 3580's BIOS (version 1.30)

All you have to do is create a boot drive for editing value on 0x8E7 in Setup to 0x2.

## Prepare the USB
1. Download [Ru.efi](https://ruexe.blogspot.com/)
2. Take a thumb drive and format it in `FAT32`. Make sure to use `GPT` partitioning scheme.
3. Create the following directory tree:
```
EFI
└── BOOT
    └── BOOTx64.efi
```
where `BOOTx64.efi` is nothing more than `RU.efi` renamed.

# Boot from the USB and change the value on 0x8E7 in Setup to 0x2
1. Boot from the pendrive and you will see a screen like this. Press Enter.

2. Press **Alt** + **C** (Config) and select **UEFI variable**.

3. Scroll down to **Setup** and press Enter. Navigate to 0x8E7 (Row **08E0**, Colume **07**)

4. Change this value to **02**. Use **Ctrl** + **W** to save and **Alt** + **Q** to exit/reboot.

5. Now you can remove ``framebuffer-patch-enable`` in ``Device Properties`` ~> ``PciRoot(0x0)/Pci(0x2,0x0)``

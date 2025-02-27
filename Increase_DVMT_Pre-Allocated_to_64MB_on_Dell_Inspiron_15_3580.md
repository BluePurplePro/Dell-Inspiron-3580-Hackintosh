#Increase DVMT Pre-Allocated to 64MB on Dell Inspiron 15 3580
By following Dell BIOS Extract Guide  I found the VarOffset (VarStoreInfo/VarName): 0x8E7, VarStoreId: 0x1 (Name: Setup). All you have to do is create a boot drive for editing value on 0x8E7.


1. Download Ru.efi or this EFI folder EFI CFG RU.zip (You can update the file in the EFI folder. Just rename the RU.efi file to BOOTx64.efi and replace it in the BOOT folder)